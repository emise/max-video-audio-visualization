A live visualization of a classical music performance via Max Jitter

## Requirements:
* Max 6 or newer
* CNMAT Max Externals http://cnmat.berkeley.edu/downloads

## Explanation
* Load videos via `jit.qt.movie`
* Use the CNMAT external `analyser~` to get the `loudness` and the `noisiness` (based on the Bark scale) of input audio
* Use `jit.brcosa` to adjust the brightness, contrast, and saturation of the video via input values
* Map `loudness` to brightness and contrast, map `noisiness` to saturation - higher loudness equals brighter and more contrast, lower noisiness equals more saturation
* Scale the input values into reasonable ranges using `scale` so we don't get washed-out or too-dark video
* Change the values gradually so we don't get random jumps in brightness/contrast/saturation using `line~` (encapsulated in `p smoooth`)
