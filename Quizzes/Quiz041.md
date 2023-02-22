# Quiz 041

Create tic tac toe game for 2 players [HL]

## Python
```.py
from kivymd.app import MDApp
class quiz041(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.values = [0,0,0,0,0,0,0,0,0]
        self.player = "X"

    def build(self):
        return

    def button_press(self,button_id):
        print(button_id)
        current_player = self.player
        temp = "self.root.ids.button" + button_id
        current_button = eval(temp)
        if self.values[int(button_id)-1] == 0:
            current_button.text = current_player
            if current_player == "X":
                self.player = "O"
                current_button.md_bg_color = "#FE5F55"
                self.values[int(button_id)-1] = 1
            else:
                self.player = "X"
                current_button.md_bg_color = "#1A1B41"
                self.values[int(button_id)-1] = 2


        print(self.values)

        winning_combinations = [(0, 1, 2), (3, 4, 5), (6, 7, 8),
                                (0, 3, 6), (1, 4, 7), (2, 5, 8),
                                (0, 4, 8), (2, 4, 6)]

        for indices in winning_combinations:
            if all(self.values[i] == self.values[indices[0]] and self.values[i] != 0 for i in indices):
                print(f"Winner is {current_player}")
                self.root.ids.label2.text = f"Winner is {current_player}"
                break
        else:
            print("No Winner Yet")
            self.root.ids.label2.text = f"Current Player: {self.player}"

    def reset(self):
        self.values = [0,0,0,0,0,0,0,0,0]
        self.player = "X"
        for i in range(1,10):
            temp = "self.root.ids.button" + str(i)
            current_button = eval(temp)
            current_button.text = ""
            current_button.md_bg_color = "grey"
        self.root.ids.label2.text = f"Current Player: {self.player}"

run = quiz041()
run.run()
```


## KV

```.kv
Screen:
    size: 500, 500
    MDBoxLayout:
        id:main_scr
        orientation: "vertical"
        size_hint: .7, .9
        pos_hint: {"center_x":.5, "center_y":.5}
        MDBoxLayout:
            id: box1
            size_hint: 1, .2
            orientation: "vertical"

            MDLabel:
                id:label1
                text: "Tic Tac Toe by Jonathan"
                halign: "center"
                font_style: "H3"
            MDLabel:
                id:label2
                text: "Current player: " + app.player
                halign: "center"
                font_style: "H5"


        MDBoxLayout:
            id: box2
            size_hint: 1, .8
            orientation: 'vertical'
            pos_hint: {'center_x': .5, 'center_y': .5}
            MDBoxLayout:
                id: layerone
                size_hint:1,.33
                orientation:"horizontal"
                MDRaisedButton:
                    id: button1
                    text: ""
                    size_hint: .33, 1
                    md_bg_color: "#C7EFCF"
                    on_release: app.button_press("1")
                MDRaisedButton:
                    id: button2
                    text: ""
                    size_hint: .33, 1
                    md_bg_color: "#C7EFCF"
                    on_release: app.button_press("2")
                MDRaisedButton:
                    id: button3
                    text: ""
                    size_hint: .33, 1
                    md_bg_color: "#C7EFCF"
                    on_release: app.button_press("3")
            MDBoxLayout:
                id: layertwo
                size_hint:1,.33
                orientation:"horizontal"
                MDRaisedButton:
                    id: button4
                    text: ""
                    size_hint: .33, 1
                    md_bg_color: "#C7EFCF"
                    on_release: app.button_press("4")
                MDRaisedButton:
                    id: button5
                    text: ""
                    size_hint: .33, 1
                    md_bg_color: "#C7EFCF"
                    on_release: app.button_press("5")
                MDRaisedButton:
                    id: button6
                    text: ""
                    size_hint: .33, 1
                    md_bg_color: "#C7EFCF"
                    on_release: app.button_press("6")

            MDBoxLayout:
                id: layerthree
                size_hint:1,.33
                orientation:"horizontal"
                MDRaisedButton:
                    id: button7
                    text: ""
                    size_hint: .33, 1
                    md_bg_color: "#C7EFCF"
                    on_release: app.button_press("7")
                MDRaisedButton:
                    id: button8
                    text: ""
                    size_hint: .33, 1
                    md_bg_color: "#C7EFCF"
                    on_release: app.button_press("8")
                MDRaisedButton:
                    id: button9
                    text: ""
                    size_hint: .33, 1
                    md_bg_color: "#C7EFCF"
                    on_release: app.button_press("9")

        MDBoxLayout:
            id: resetbox
            size_hint: 1, .2
            orientation: 'vertical'
            MDRaisedButton:
                id: resetbutton
                text: "Reset"
                size_hint: .5, .75
                pos_hint: {'center_x': .5, 'center_y': .5}
                on_release: app.reset()
```

## Proof
![quiz041](https://user-images.githubusercontent.com/111751273/220651997-3157cabd-9632-4e3d-bd43-59683bff24d5.gif)
