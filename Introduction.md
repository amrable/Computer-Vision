
# Computer Vision 👁 

> **_NOTE:_**  Sections 1.0 and 1.1 are almost the same as the slide, it is boring and I could not make it more entertaining 😞

## 1.0 Human Vision 👶🏻
#### What is vision?
 - Recognize objects
    - people we know
    - things we own
- Locate objects in space
    - to pick them up
- Track objects in motion
    - catching a baseball
    - avoiding collisions with cars on the road
- Recognize actions
    - walking, running, pushing

#### Vision is deceivingly easy 
Although it does not require efforts or skills like for eaxample, thinking, we use nearly 70% of our brains for visual perception! Also not all creatures see alike.

#### Vision is deceptive  🕵🏻‍♂️
Vision is **strong** and **immediate** sensation, but it is illusional
- We perceive the visual world as external to ourselves, but it is a reconstruction within our brains
- We regard how we see as reflecting the world “as it is;” but human vision is
    - **Subject to illusions**
        - The human visual system picks an interpretation of each part that makes the whole consistent.
    - **Quantitatively imprecise**
        - Our estimations for quantitative measuremesnt are imprecise
    - **Limited to a narrow range of frequencies of radiation**
        - We “see” only a small part of the energy spectrum of sunlight, We see less than .1% of the energy that reaches our eyes
        - We don’t see ultraviolet or lower frequencies of light
        - We don’t see infrared or higher frequencies of light
        - But objects in the world reflect and emit energy in these and other parts of the spectrum
        - Non-human vision **Infrared , Ultrasound , X-ray ans RADAR vision**
        - **Infrared Visiom**:  Vision systems exist that can see reflected and emitted infrared light
            - visual system of the pit viper
            - infrared cameras used for night vision
    - **Passive**    
        - It relies on external energy sources (sunlight, light bulbs, fires) providing light that reflects off of objects to our eyes
        - Vision systems can be “active” - carry their own energy sources
            - Radars
            - Bat acoustic imaging systems.

___
## 1.1 Computer Vision 🖥
### Definition
Computer Vision is developing computer programs to understand the content of images and videos.
| Types of related fields |
| ------ |
| 2D --- Image Processing---> 2D |
| 2D --- Computer Vision ---> 3D |
| 3D ---Computer Graphics--> 2D |

### Why study Computer Vision?
- Images and movies are everywhere
- Fast-growing collection of useful applications
    - building representations of the 3D world from pictures
    - automated surveillance (who’s doing what)
    - movie post-processing
    - face finding
- Various deep and attractive scientific mysteries
    - how does object recognition work?
- Greater understanding of human vision

### Computer vision contributes in many fields 
- Critical to many applications in
- Medicine
- Transportation
- Entertainment
- Agriculture
- Defense
- Visual Surveillance

---


## 1.2 Image Formation, Histograms, and Point Operations 📊

### 1.2.1 Image Formation

<img width="400" alt="Screen Shot 2020-02-24 at 21 00 07" src="https://user-images.githubusercontent.com/31357623/75182501-331d2a80-5749-11ea-8844-7037682c823d.png">  <img width="300" alt="Screen Shot 2020-02-24 at 21 00 33" src="https://user-images.githubusercontent.com/31357623/75182872-f3a30e00-5749-11ea-9afe-119fcb18c275.png">


### Digital images
- Sample the 2D space on a regular grid
- Quantize each sample (round to nearest integer)
- Image thus represented as a matrix of integer values.


### Digital camera 📸
- A digital camera replaces film with a sensor array
- Each cell in the array is light-sensitive diode that converts photons to electrons

![rgb](https://user-images.githubusercontent.com/31357623/75183219-bee38680-574a-11ea-8d59-7863e4745089.png)


### What is a histogram?
- A compact representation of statistical distribution of intensity values in the image,
- No spatial information is encoded, different images could have exactly the same histogram

### Why do we use histogram?
- Determine quality of an image
- Determine whether an image has been manipulated or not
- Enhance image properties
- Represent the pattern in an image

### Interpreting Histograms
| Property | Effect | Illustration| 
|----------|-------------|------------|
|Contrust| Difference between the maximum and minimum intensity values recorded| <img width="953" alt="Screen Shot 2020-02-24 at 21 34 26" src="https://user-images.githubusercontent.com/31357623/75184685-72e61100-574d-11ea-84fc-fb84664c40c6.png"> |
|Dynamic Range| Number of distinct pixel values in the image|<img width="953" alt="Screen Shot 2020-02-24 at 21 36 57" src="https://user-images.githubusercontent.com/31357623/75184886-cce6d680-574d-11ea-8fe3-4c164cb25667.png">|
|Exposure: the quantity of light reaching a photographic film| Poor image exposure appears as High density at one end of the histogram and low density at the other end | <img width="534" alt="Screen Shot 2020-02-24 at 21 44 07" src="https://user-images.githubusercontent.com/31357623/75185456-cc9b0b00-574e-11ea-892d-ac5b5bc9a66a.png"> |

# TBD 
- Detect image defects by histograms
- Color Image Histograms
- Binning
- Point operations
