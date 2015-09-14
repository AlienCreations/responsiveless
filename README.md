# responsiveLESS
Media query mixins for common devices.

---
Credit and special thanks goes to [CSS-Tricks.com](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/) for 
providing the actual media queries, which we simply converted to mixins for rule and orientation pass-through.

## Usage

All mixins will take one `@rules` argument and an optional `@orientation` argument. Omitting the 
`@orientation` argument will enforce the rule on both orientations.

Example contract: 

    .tablets(@rules)
    .tablets(@rules, @orientation)
    
This allows targeting all tablets in either orientation like so: 

    .tablets({ margin : 20px; });
    
Or, specifying unique rules respectively:

    .tablets({ margin : 20px; }, portrait);
    .tablets({ margin : 40px; }, landscape);
    
*Example:*

    @import '/bower_components/responsiveless/index'
    
    .some-element-class {
      font-size        : 1.5rem;
      background-color : #EFEFEF;
      color            : #000;
      
      .phones({
        color : red;
      }, portrait);
      
      .tablets({
        color : blue;
      }, portrait);
      
    }


## Mixins Included
The mixins are inclusively hierarchical, meaning `.phones()` will leverage rules from `.iPhones()`, which will 
leverage rules from `.iPhone4()`, `.iPhone5()`, `.iPhone6()`, and `.iPhone6Plus()`, for example. Due to the way the 
rules were written, some targeting overlap will occur. 

*All mixins invoked with `(@rules, [@orientation])`:* 

    .laptops
        .retina
        .nonRetina
    .phones
        .galaxyPhones
            .galaxyS3
            .galaxyS4
            .galaxyS5
        .htcPhones
            .htcOne
        .iPhones
            .iPhone4
            .iPhone5
            .iPhone6
            .iPhone6Plus
    .tablets
        .galaxyTablets
            .galaxyTab10
        .iPads
            .iPad1stGen
                .iPad1
                .iPad2
            .iPad2ndGen
                .iPad3
                .iPad4
            .iPadMini
        .kindleFireTablets
            .kindleFire7Inch
            .kindleFire8Point9Inch
        .nexusTablets
            .asusNexus7
    .wearables
        .appleWearables
            .appleWatch
        .motoWearables
            .moto360
            
