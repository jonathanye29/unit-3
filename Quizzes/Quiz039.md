# Quiz 039

Write a program that creates the GUI below:
<img width="1011" alt="Screen Shot 2023-02-05 at 4 23 11 PM" src="https://user-images.githubusercontent.com/111751273/216806896-25c058d9-764b-4860-b347-e00dc61e8088.png">

## Python
```.py
from kivymd.app import MDApp

class quiz039(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.t = 0
        self.i = 0

    def build(self):
        return

    def add(self):
        self.t += 1
        print(self.t)
        self.i += 1
        self.root.ids.label.text = f"{self.i}"

demonstration = quiz039()
demonstration.run()
```

## KV
```
Screen:
    id: scr_manager

    MDBoxLayout:
        orientation: "horizontal"
        pos_hint:{"center_x": .5, "center_y": .5}
        size_hint: .7, .3

        MDLabel:
            id: label
            size_hint: .5, .5
            text:
                "Count 15"
            halign: "left"
            font_size:'34pt'

        MDRaisedButton:
            id: click_me_btn
            size_hint: .5, .5
            text: "Add +1"
            md_bg_color: 0, 0, 0
            on_release:
                app.add()
```

<img width="800" alt="Screen Shot 2023-02-05 at 4 24 36 PM" src="https://user-images.githubusercontent.com/111751273/216806933-d2a8a2e6-bacd-42ae-a075-97149969c48e.png">
