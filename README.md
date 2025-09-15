# JsonEditorSample

## About
A Simple one level Json File Editor.

- Properties with scalar values. _Name:Value pairs._
- No Schema required.
- Number of properties is not fixed.

**One Level** means the file has a comma separated list of name value pairs where the values are scalar 
_(have a single value)_. 

## Valid Data Types

Integer,Float/Double, Boolean or Date/DateTime. No enum types.

As per this validation code: 

```cs
    private void ValidateValue()
    {
        try
        {
            IsValid = ExpectedType switch
            {
                JTokenType.Integer => int.TryParse(Value, out _),
                JTokenType.Float => double.TryParse(Value, out _),
                JTokenType.Boolean => bool.TryParse(Value, out _),
                JTokenType.Date => System.DateTime.TryParse(Value, out _),
                _ => true
            };
        }
        catch
        {
            IsValid = false;
        }

        OnPropertyChanged(nameof(IsValid));
    }
```

Load a one level json file.
You can edit any node value by entering any valid _(as above)_ C# string for the value for a node.
- Node Names can't be changed.
- You can't add nodes.

> No validation against the loaded data type so on edutting a node value you can change the data type.


##  Development

Was developed with a little help from AI: GitHub Copilot and ChatGPT. 
Was developed with a view to adding a Json Editor as a popup control to a WPF applicationWit.
With that, ended up a fixed set of name:value pairs with fixed data types.
This is a more general purpose editor. That is working. See [JsonEditorWindows.xaml/.cs](https://github.com/djaus2/PhotoTimingDjaus/tree/master/AthStitcher) in that project