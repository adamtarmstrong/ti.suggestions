<p>
<a href="http://www.appcelerator.com/titanium/"><img src="https://camo.githubusercontent.com/ecc6562b9e8446bbf967b69b4180fef9080068b3/687474703a2f2f7777772d7374617469632e61707063656c657261746f722e636f6d2f6261646765732f746974616e69756d2d6769742d62616467652d73712e706e67" alt="Titanium" data-canonical-src="http://www-static.appcelerator.com/badges/titanium-git-badge-sq.png" style="max-width:100%;"></a>

<a href="http://www.appcelerator.com/alloy/"><img src="https://camo.githubusercontent.com/f5a543c2128b182c327afc82e9abea66f496a1db/687474703a2f2f7777772d7374617469632e61707063656c657261746f722e636f6d2f6261646765732f616c6c6f792d6769742d62616467652d73712e706e67" alt="Alloy" data-canonical-src="http://www-static.appcelerator.com/badges/alloy-git-badge-sq.png" style="max-width:100%;"></a>

<a href="http://choosealicense.com/licenses/apache-2.0/"><img src="https://camo.githubusercontent.com/84295be0136e01cd8e9d2107d69c695a052f065d/687474703a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d417061636865253230322e302d626c75652e7376673f7374796c653d666c6174" alt="License" data-canonical-src="http://img.shields.io/badge/license-Apache%202.0-blue.svg?style=flat" style="max-width:100%;"></a>
</p>

# ti.suggestions
#### Titanium Axway Suggestions
As a user types text into TextField - this widget filters the array/results and populates a TableView Overlay

![Demo](demo.gif)

###### index.xml
```xml
<Widget id="categorySearchTextField" hintText="Begin typing for a list of categories..." src="ti.suggestions" onChange="handleChange" onExportData="handleExportData" onClear="handleClear" />
```

###### index.js
```javascript
var categoriesArrayData =
    [{title: "Action Book [Books]", id: 1},
    {title: "Dog Food [Pet Supplies]", id: 2},
    {title: "Guitar [Musical Instruments]", id: 3},
    {title: "Refrigerator [Appliances]", id: 4},
    {title: "Xylophone [Musical Instruments]", id: 5}];

// SEND REQUEST TO GET NEW DATA
function handleChange(e) {			//e.value
    //Ti.API.info("Value Changed: " + $.categorySearchTextField.getValue());

    var filteredArray =
        _.filter(categoriesArrayData, function(element){
            return element.title.toLowerCase().indexOf( e.value.toLowerCase() ) > -1;
    });

    $.categorySearchTextField.setSuggestions(filteredArray);
}

// HANDLE RETURNED DATA WHEN USER CLICKED ON A SUGGESTION ROW
function handleExportData(data) {
    Ti.API.info("User clicked: " + JSON.stringify(data));
}

//HANDLE WHEN TEXTFIELD IS CLEARED
function handleClear(){
	//Ti.API.info("Value Cleared");
}
```

###### index.tss
```stylesheet
"#categorySearchTextField": {
  font: { fontSize: 12 },
  color: "#545454",
  backgroundColor: "#F7f7f7",
  width: "80%",
  height: 44,
  top: 50,
    clearButtonMode : Titanium.UI.INPUT_BUTTONMODE_ONFOCUS,
    returnKeyType: Titanium.UI.RETURNKEY_SEARCH,
    zIndex: 1,
    suggestions: {
        bottom : 15,
        height: Ti.UI.SIZE,
        width: "80%",
        visible : false,
        opacity : 0,
        zIndex: 10
    }
}
```

Contributions to: https://github.com/TheSmiths-Widgets/ts.suggestionfield
> Various UI tweaks and a few methods added
