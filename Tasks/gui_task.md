 # Task 1: Currency Converter
 
 ## Code
 
 ### Python
 
```.py
from kivymd.app import MDApp

class converter(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.input = 0
        self.output = 0

    def build(self):
        return

    def set_amount(self):
        if not self.root.ids.input_amount.text.isdigit():
            self.root.ids.show_converted_amount.text = "Please enter a valid number"
        number= int(self.root.ids.input_amount.text)
        self.input = number

    def convert_to_usd(self):
        self.exchanged_result = round(self.input*1.09, 2)
        self.root.ids.show_converted_amount.text = f" {self.exchanged_result} USD"

    def convert_to_jpy(self):
        self.exchanged_result = round(self.input*141.44, 2)
        self.root.ids.show_converted_amount.text = f" {self.exchanged_result} JPY"

run = converter()
run.run()
```

### Kivy

```
Screen:
    size: 500,500
    MDBoxLayout:
        id: main
        orientation: 'vertical'
        size_hint:1,.8
        pos_hint: {'center_x': .5, 'center_y': .5}

        MDLabel:
            text:"Currency Converter"
            halign: 'center'
            font_style: 'H3'
            size_hint: 1, .2
            pos_hint: {'center_x': .5}

        MDTextField:
            id: input_amount
            hint_text: "Enter Amount in EUR"
            pos_hint: {'center_x':0.5}
            size_hint: .7, .2
            on_text:

                app.set_amount()

        MDBoxLayout:
            id: exchange_and_results
            orientation: 'horizontal'
            size_hint: 1, .4
            pos_hint: {'center_x':0.5}

            MDLabel:
                id : hint
                text: "CLICK TO CONVERT"
                halign: 'center'
                size_hint: .3, 1
                pos_hint: {'center_x':0.2, 'center_y':0.5}
            MDBoxLayout:
                id: buttons_and_result
                orientation:"vertical"
                size_hint: .3, 1
                MDBoxLayout:
                    id: buttons_box
                    orientation: "horizontal"
                    size_hint: .7, 1
                    pos_hint: {'center_x':0.7, 'center_y':0.9}
                    MDRaisedButton:
                        id: usd
                        text: "USD"
                        pos_hint: {"center_x": 0.25, "center_y": .25}
                        on_release: app.convert_to_usd()
                        md_bg_color:"#002B41"
                    MDRaisedButton:
                        id: jpn
                        text: "JPY"
                        pos_hint: {"center_x": 0.75, "center_y": .25}
                        on_release: app.convert_to_jpy()
                        md_bg_color:"#F20021"
                MDLabel:
                    id: show_converted_amount
                    text: "0"
                    halign: 'center'
                    font_style: 'H5'
                    text_color: "#000000"
                    size_hint: .3, 1
                    pos_hint: {'center_x':0.6}
                    font_size:80
```

