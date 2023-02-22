# Quiz 042

<img width="1032" alt="Screen Shot 2023-02-22 at 11 31 15 PM" src="https://user-images.githubusercontent.com/111751273/220652606-599c177f-9cb6-4d29-9355-a0a274c9d2be.png">

## Python
```.py
from kivymd.app import MDApp
from kivymd.uix.screen import MDScreen



class MysteryPageA(MDScreen):
    pass

class MysteryPageB(MDScreen):
    pass

class quiz042(MDApp):
    def build(self):
        return
test = quiz042()
test.run()
```

## KV
```.kv
ScreenManager:
    MysteryPageA:
        name: "MysteryPageA"

    MysteryPageB:
        name: "MysteryPageB"

<MysteryPageA>
    size: 500,500
    md_bg_color: "#D8DBE2"

    MDLabel:
        text: "Mystery Page A"
        font_style: "H3"
        halign: "center"
        color: "#373F51"

        MDRaisedButton:
            text: "Next page"
            on_press: root.parent.current = "MysteryPageB"
            size_hint: .3, .5
            md_bg_color: "#DAA49A"

<MysteryPageB>
    size: 500,500
    md_bg_color: "#D8DBE2"

    MDLabel:
        text: "Mystery Page B"
        font_style: "H3"
        halign: "center"
        color: "#373F51"

        MDRaisedButton:
            text: "Go back"
            on_press: root.parent.current = "MysteryPageA"
            size_hint: .3, .5
            md_bg_color: "#DAA49A"
```

## Proof
![quiz042](https://user-images.githubusercontent.com/111751273/220655275-e3d810c6-8477-40f3-97e0-c06a160aa4b5.gif)


      
      
