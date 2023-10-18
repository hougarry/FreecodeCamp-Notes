in my scss file, the nav part is not correct, it's not shown in phone device, help me figure out why is this happen:
here is my nav scss part:
```
@media(max-width: 700px){
    .text-box{
        h1{
            font-size: 20px;
        }
        p{
            font-size: 12px;
        }
    }
    nav{
        // .fa-solid{
        //     display: block;
        //     color: white;
        //     margin-top: 5px;
        //     font-size: 20px;
        //     cursor: pointer;
        // }
    ...
    }
```
The reason is that my nav was not well written, I should use the class name to select the nav, not the tag name, so the correct way is:
```scss
    .header nav{
        .fa-solid{
            display: block;
            color: white;
            margin-top: 5px;
            font-size: 20px;
            cursor: pointer;
        }
```
use .header nav to select the nav part, then it works.