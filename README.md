<a name="readme-top"></a>

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/kaylaa0/generative-panning-with-outpainting">
    <img src="logo.gif" alt="Logo" height="250">
  </a>
  <p align="center">
    <h3 align="center">Generative Panning With Outpainting</h3>
    <a href="https://github.com/kaylaa0/generative-panning-with-outpainting/tree/main/Documents"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/kaylaa0/generative-panning-with-outpainting/">View Demo</a>
    ·
    <a href="https://github.com/kaylaa0/generative-panning-with-outpainting/issues">Report Bug</a>
    ·
    <a href="https://github.com/kaylaa0/generative-panning-with-outpainting/issues">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->

## About The Project

As a term project for the BBM444 course at Hacettepe University, I have explored and researched the concept of generative panning using outpainting. In this repository, you will find my report documents, presentations, and code, as well as sample inputs used and some outputs.

In this project, I investigated the possibility of panning via outpainting on warped images. The devised solution is based on my original idea that if we can warp an image to mimic a panning effect, we can use outpainting to fill the empty spaces. The AI understands the context of the image and fills these spaces with the appropriate content.

For warping, I used OpenCV and NumPy, researching parameters to achieve desirable results, which are detailed in the report documents. For outpainting, I used the [Fooocus-API](https://github.com/mrhan1993/Fooocus-API).


### Built With

* [![OpenCV][Opencv.org]][Opencv-url]
* [![NumPy][Numpy.org]][Numpy-url]

<!-- GETTING STARTED -->

## Getting Started

### Prerequisites

Ensure you have the following installed on your system:

- [Python](https://www.python.org/downloads/)
- [Fooocus-API](https://github.com/mrhan1993/Fooocus-API) (Follow the installation instructions provided in the repository)
- [Jupyter Notebook](https://jupyter.org/) (for running the provided Jupyter notebook)

### Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/kaylaa0/generative-panning-with-outpainting.git
   ```
2. Navigate to the project directory:
   ```sh
   cd generative-panning-with-outpainting
   ```
3. Install the required Python packages:
   ```sh
   pip install -r requirements.txt
   ```
4. Open the Jupyter notebook:
   ```sh
   jupyter notebook
   ```
5. Run the provided Jupyter notebook file to start using the project.


<!-- USAGE GUIDE -->

## Usage

1. **Set Up Host and Model**: Ensure the `host` variable points to the running Fooocus API instance and specify the desired model:
   ```python
   host = "http://127.0.0.1:8888"  # Address of the Fooocus API
   model = "juggernautXL_juggernautX.safetensors"  # Model for generation
   ```

2. **Warp Image**: Use the provided functions to warp your images:
    ```python
    # Load your image
    image = cv2.imread('path/to/your/image.png')
    # Set the angle and direction for warping
    angle = 5
    direction = 'left'
    # Run the warp pipeline
    warped_image, mask_image, _ = run_warp_pipeline(image, angle, direction, save=True, display=False)
    ```
3. **Outpaint Image**: Use the Fooocus API to outpaint the warped image:
    ```python
    result = run_outpaint_pipeline(warped_image, mask_image)
    print(json.dumps(result, indent=4, ensure_ascii=False))
    ```
4. **Continuous Pipeline**: For continuous panning, use the `continuous_pipeline` function:
    ```python
    final_image = continuous_pipeline(image, direction, degree, times, prompt)
    ```

5. **Look Around Pipeline**: For a complete panning experience, use the `look_around` function:
    ```python
    path = ['right'] * 10 + ['up'] * 5 + ['left'] * 35  # Define the panning path
    path_angle = 5  # Define the angle increment
    look_around(image, path_angle, path)
    ```
#### Notes
- **Adjusting Parameters**: Modify the parameters such as angle, direction, and prompt to achieve desired results. Read the research documents on details about proper values for angle and path. 
- **Saving Results**: Images are saved in the specified directory, or you can use the built-in saving mechanism to save them in any desired folder.


<!-- ROADMAP -->

## Roadmap

- [x] Create README.md
- [&ensp;] Create a Colab Notebook


<!-- LICENSE -->
## License

<br />
<div style="display: flex; align-items: center;">
  <img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png" />
  <span style="margin-left: 10px;">This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a>.</span>
</div>
<br />

See `LICENSE.md` for more information.

<!-- CONTACT -->

## Contact

Kayla Akyüz - kaylakyuz@gmail.com

Project Link: [GitHub](https://github.com/kaylaa0/generative-panning-with-outpainting)

[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- ACKNOWLEDGMENTS
## Acknowledgments
 -->

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->

[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=0077B5&colorA=0077B5
[linkedin-url]: https://www.linkedin.com/in/-kayla-/
[product-screenshot]: images/screenshot.png
[Numpy.org]: https://img.shields.io/badge/NumPy-4DABCF?style=for-the-badge&logo=numpy&logoColor=white
[Numpy-url]: https://numpy.org/
[Opencv.org]: https://img.shields.io/badge/OpenCV-8ADA67?style=for-the-badge&logo=opencv&logoColor=white
[Opencv-url]: https://opencv.org/