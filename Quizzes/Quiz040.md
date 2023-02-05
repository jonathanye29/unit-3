# Quiz 040

Write a program that creates the GUI below (HL: Change the color of the button as well):
<img width="937" alt="Screen Shot 2023-02-05 at 4 25 32 PM" src="https://user-images.githubusercontent.com/111751273/216806962-d5be270f-7b98-4749-b061-ff69c77c9414.png">

## Python
```.py
from kivymd.app import MDApp
class quiz040(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
    def build(self):
        return
    def change_mode(self):
        print(self.root.ids.main_screen.md_bg_color)
        if self.root.ids.main_screen.md_bg_color == [1.0, 1.0, 1.0, 1.0]:
            self.root.ids.main_screen.md_bg_color = "#000000"
            self.root.ids.changerbutton.text_color = 1,1,1,1
            self.root.ids.name.text_color = 1, 1, 1, 1
            self.root.ids.changerbutton.text = "Light Mode"
            self.root.ids.changerbutton.md_bg_color = "#96BE8C"
        else:
            self.root.ids.main_screen.md_bg_color = "#FFFFFF"
            self.root.ids.changerbutton.text_color = 0,0,0,1
            self.root.ids.name.text_color = 0, 0, 0, 1
            self.root.ids.changerbutton.text = "Dark Mode"

quiz40 = quiz040()
quiz40.run()
```

## KV
```
Screen:
    size:500,500
    MDBoxLayout:
        id: main_screen
        orientation:"vertical"
        md_bg_color: "#FFFFFF"
        MDLabel:
            id:name
            text: "Jonathan Ye"
            halign: "center"
            font_style: "H2"
            theme_text_color: "Custom"
            text_color: 0, 0, 0, 1
            pos_hint: {"center_x": .5, "center_y": .5}
        MDRaisedButton:
            id: changerbutton
            text: "Dark Mode"
            pos_hint: {"center_x": 0.06, "center_y": 0.1}
            on_release: app.change_mode()
```

<img width="800" alt="Screen Shot 2023-02-05 at 4 26 49 PM" src="https://user-images.githubusercontent.com/111751273/216806996-dd8b4d24-70d3-410e-8793-d5f1f46d1fac.png">
<img width="801" alt="Screen Shot 2023-02-05 at 4 27 04 PM" src="https://user-images.githubusercontent.com/111751273/216807009-44a4d0fd-abb3-40d5-a9e6-67fcd8aeb140.png">
