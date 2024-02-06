# Rec2Slide: Convert video recording slides to PDF

Rec2Slide is a handy tool designed to simplify the process of converting video recordings containing slides into an organized PDF format.

## Methodology

1. Get frames from video every nth frame
2. Compare current frame with previous frame using some similarity score calculation (for now only mean squared error)
3. If the score is more than threshold, then it's a distinct slide
4. Gather all the distinct slide and construct the PDF

## Installation

```bash
$ pip install rec2slide
```

## Usage

```python
from rec2slide import Engine, Config, Utils

def main():
    config = Config(
        interval=20, # small interval = slow = more precise
        threshold=1000.0, # small thresh = more aggresive for determining distinct slides
        score="mse"
    )

    engine = Engine(config)
    result = engine("./data/example.mp4")
    Utils.frames2pdf(result, "./data/example.pdf") # you can also convert to jpg/png. check `./rec2slide/utils.py`

if __name__ == "__main__":
    main()
```

see the result [here](./data/example.pdf)

## Contributions

Contributions are welcome! If you have any ideas for improvement, feature requests, or bug reports, feel free to open an issue or submit a pull request.
