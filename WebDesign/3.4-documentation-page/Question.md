
## 1
I create a navbar in my index.html, but when I adjust my browser, the navbar is fixed and cannot adjust it's size automatically,  I need it always on the left side and adjust size according to viewport and so on, here is my css,  I only use  html and css
---
#navbar {
    position: fixed;
    top: 0;
    left: 0;
    width: 200px;
    height: 100%;
    background-color: #333;
    color: #fff;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: flex-start;
    flex-wrap: wrap;  /* Allow items to wrap */
    padding: 10px 0;
    box-shadow: 0 0 10px rgba(0,0,0,0.5);
    overflow-y: auto;
}

#navbar > * {
    flex-grow: 1;  /* Allow items to grow and shrink */
}

/* Media Query to hide navbar on smaller screens */
@media (max-width: 600px) {
    #navbar {
        display: none;  /* Hide navbar */
    }
}

## 2 there is still problem , when I shrink my browser, the navbar covered part of my words,  I need to keep navbar not changing, but the words can adjust auto, and will not be covered by navbar
---
#navbar {
    position: fixed;
    top: 0;
    left: 0;
    width: 200px;
    height: 100%;
    background-color: #333;
    color: #fff;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: flex-start;
    flex-wrap: wrap;  /* Allow items to wrap */
    padding: 10px 0;
    box-shadow: 0 0 10px rgba(0,0,0,0.5);
    overflow-y: auto;
}

#navbar > * {
    flex-grow: 1;  /* Allow items to grow and shrink */
}

/* Media Query to hide navbar on smaller screens */
@media (max-width: 600px) {
    #navbar {
        display: none;  /* Hide navbar */
    }
}

