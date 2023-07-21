## Blog Post Title From First Header

Due to a plugin called `jekyll-titles-from-headings` which is supported by GitHub Pages by default. The above header (in the markdown file) will be automatically used as the pages title.

If the file does not start with a header, then the post title will be derived from the filename.

This is a sample blog post. You can talk about all sorts of fun things here.

```python
import PySimpleGUI as psg
import gui_converter_functions as ff

textbox_input = psg.Input(key='-INPUT-')
spinner_units = psg.Spin(['KM to M',
                          'KG to P',
                          'Sec to Min'],
                         key='-SPINNER-')
button_convert = psg.Button('Convert', key='-BUTTON-')
label_output = psg.Text('Output: ')
label_result = psg.Text(' ', key='-LABEL-')

layout = [[textbox_input, spinner_units, button_convert],
          [label_output, label_result]]

converter_window = psg.Window('Base Unit Converter1.0', layout)

while True:
    event, values = converter_window.read()

    if event == '-BUTTON-':
        grab_value = values['-INPUT-']
        # obtain spinner conversion units
        which_conversion = values['-SPINNER-']
        # only continue if input makes sense
        if grab_value.isnumeric():
            # converter_window['-LABEL-'].update(value=ff.km_to_m(grab_value))
            # check which conversion
            if which_conversion == 'KM to M':
                converter_window['-LABEL-'].update(value=ff.km_to_m(grab_value))
            elif which_conversion == 'KG to P':
                converter_window['-LABEL-'].update(value=ff.kg_to_p(grab_value))
            elif which_conversion == 'Sec to Min':
                converter_window['-LABEL-'].update(value=ff.sec_to_min(grab_value))
        else:
            converter_window['-LABEL-'].update('Please recheck input')

    elif event == psg.WINDOW_CLOSED:
        print('terminate called')
        break
    else:
        continue

converter_window.close()
```

---

### This is a header

#### Some T-SQL Code

```tsql
SELECT This, [Is], A, Code, Block -- Using SSMS style syntax highlighting
    , REVERSE('abc')
FROM dbo.SomeTable s
    CROSS JOIN dbo.OtherTable o;
```

#### Some PowerShell Code

```powershell
Write-Host "This is a powershell Code block";

# There are many other languages you can use, but the style has to be loaded first

ForEach ($thing in $things) {
    Write-Output "It highlights it using the GitHub style"
}
```
