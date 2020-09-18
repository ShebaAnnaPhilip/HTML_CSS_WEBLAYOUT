## HTML/CSS

**BOX MODEL**

All elements in a webpage are rendered as a box of rectangular shape. Whether it is a text, a button, a div or span, every single element is a box. Each box has 4 different areas: content, border, padding and margin.
`Content` - I call it "a house". This is where the content of the element lives (Text, images etc). Width and height properties are applied to the content area by default.
`Padding` - Or otherwise space between "house" and "fence". This is the space between the content of the element and the border of the element. These increases the total width and height of the element in addition to the content.
`Border` - "The fence". This is the visual divider around the element.
`Margin` - Determines the distance between the element and other elements around it. 

When the width and height of an element is set using the CSS width and height properties, in reality, only the width and height of the content area of that element is set. 

The actual space that an element's box takes on a web page is calculated as follows:
totalWidth = width + padding-left + padding-right + border-left + border-right
totalHeight = height + padding-top + padding-bottom + border-top + border-bottom 

`Margin` doesn't affect the size of the box itself. It affects other elements around the box.

`box-sizing : content-box` is the default value given to all elements. Here, in this case if we add padding or border value to the element, the element size will get increased. For example:

    width: 200px;
    height: 200px;
    padding: 10px; 
    border: 15px solid black; 

In the above example, the size of the element will be `250px * 250px(200+10+10+15+15)` and not `200px * 200px`

If the element property is `box-sizing:border-box`, the padding and border sizes will be accounted within the values set in the element's width and height property. In the example above, when `box-sizing:border-box`, then the size of the element is `200px * 200px`.
In this case, the content size of the element is adjusted to `150px`.

    

## JS EXERCISE
const sales = [
{ itemSold: 'Football', price: 19.99, dateSold: '2018-04-07', id: 'j_123' },
{ itemSold: 'Trainers', price: 159.95, dateSold: '2018-03-02', id: 't_acds1' },
{ itemSold: 'Cricket bat', price: 204.97, dateSold: '2018-04-05', id: 'j_456'},
{ itemSold: 'Rugby ball', price: 30.00, dateSold: '2017-04-22', id: 't_acds3' },
{ itemSold: 'Hockey stick', price: 54.95, dateSold: '2017-03-19', id: 'j_999' }
]


**1. Return the sum of the price of all properties as a single value**

/**
 * get the total sum of the price of all properties
 * @returns {int}
 */

const getTotalSalesPrice = () => {
    const totalPrice =sales.map(item => item.price).reduce((acc, value) => acc + value);
    return totalPrice.toFixed(2);
};
console.log('Total Sales Price: ', getTotalSalesPrice());

**2. Return the items which were sold in 2017.**
/**
 * get items sold in 2017
 * @returns {array} of items sold in 2017
 */
 const getItemSold = () => sales.filter(item => item.dateSold.includes(2017));
 console.log('Items sold in 2017: ',getItemSold());

 **3. Return an array of all of the itemsSold properties as strings, sorted alphabetically.**
 /**
 * get sorted ItemSold 
 * @returns {array} of ItemSold sorted alphabetically
*/
 const getItemSoldSorted = () => sales.map(item => item.itemSold).sort();
 console.log('ItemSold sorted: ',getItemSoldSorted());

**4. Using id as an argument, return the sale which matches the id.**
 /**
 * get sales matching the ID
 * @param {string} Id of the sale
 * @returns {object} saleById
*/
 const getSalesById = (Id) => {
     if(Id === undefined){
        console.log('Please enter valid ID');
        return;
     }
     return sales.find(sale =>sale.id === Id)
};
 console.log(getSalesById('j_123'));
 console.log(getSalesById('t_acds1'));
 console.log(getSalesById());
 


## Replicate Layout
**Technical and design decisions.**
 My First step was to create a plan about how the layout should behave in different screens. I wanted the layout to behave in a way that in small screens like mobile and tablet, the columns should be stacked. The Header section with the search box and icon on top, the main content below the Header section, and the sidebar below it, all of full width. For desktop, I wanted to put the Header on top, the main content on the left and sidebar on the right, both below the Header. In this case, I wanted the sidebar to always have a fixed width and the main content taking the remaining available space. Mobile styles were written first, and for desktop, I wanted the styles to get triggered when getting to a certain viewport width. 
 For the design layout, I used `CSS-GRID` layout. This has been used because it is one of the easiest and fastest methods to build a responsive layout and CSS-GRID makes it possibile to easily change the placement of the grid items according to the device screen. 

