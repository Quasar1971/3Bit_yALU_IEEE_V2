![](../../workflows/gds/badge.svg) ![](../../workflows/docs/badge.svg) ![](../../workflows/wokwi_test/badge.svg) ![](../../workflows/fpga/badge.svg)

# Tiny Tapeout Wokwi Project Template

- [Read the documentation for project](docs/info.md)

## What is Tiny Tapeout?

Tiny Tapeout is an educational project that aims to make it easier and cheaper than ever to get your digital and analog designs manufactured on a real chip.

To learn more and get started, visit https://tinytapeout.com.

## Wokwi Projects

Edit the [info.yaml](info.yaml) and change the `wokwi_id` to the ID of your Wokwi project. You can find the ID in the URL of your project, it's the big number after `wokwi.com/projects/`.

The GitHub action will automatically fetch the digital netlist from Wokwi and build the ASIC files.

## Enable GitHub actions to build the results page

- [Enabling GitHub Pages](https://tinytapeout.com/faq/#my-github-action-is-failing-on-the-pages-part)

## Resources

- [FAQ](https://tinytapeout.com/faq/)
- [Digital design lessons](https://tinytapeout.com/digital_design/)
- [Learn how semiconductors work](https://tinytapeout.com/siliwiz/)
- [Join the community](https://tinytapeout.com/discord)
- [Build your design locally](https://www.tinytapeout.com/guides/local-hardening/)

## What next?

- [Submit your design to the next shuttle](https://app.tinytapeout.com/).
- Edit [this README](README.md) and explain your design, how it works, and how to test it.
- Share your project on your social network of choice:
  - LinkedIn [#tinytapeout](https://www.linkedin.com/search/results/content/?keywords=%23tinytapeout) [@TinyTapeout](https://www.linkedin.com/company/100708654/)
  - Mastodon [#tinytapeout](https://chaos.social/tags/tinytapeout) [@matthewvenn](https://chaos.social/@matthewvenn)
  - X (formerly Twitter) [#tinytapeout](https://twitter.com/hashtag/tinytapeout) [@tinytapeout](https://twitter.com/tinytapeout)
  - Bluesky [@tinytapeout.com](https://bsky.app/profile/tinytapeout.com)

## How my design works
You have 8 switches and 8 outputs. The first three switches determine the first 3 bit number, while the next three switches determine the second 3 bit number. the last two switches determine the mode for your ALU where 00 = addition, 10 = subtraction, 01 = multiplication. Note that the last mode (11), simply passes the switch, clock (10KHz), and reset signals to the output.

## How to test
Let's go through an example where you would add two 3 bit numbers together. Flip the first three switches to the following bits 101, and the next three switches to 100. Make sure that the last 2 switches remain in there 00 state. Your output pins should have a signal that corresponds to the bit sequence 00001001. Congratulations! you just performed 5 + 4 (=9) in binary. You can keep your initial 6 switches as they are (two 3 bit numbers), and simply switch the mode of operation to multiplication (01), or any other mode, and instantly observe the change in output.

## External hardware
This design interfaces its outputs using a 7 segment display, however the segments won't light up the result in decimal, rather it will light up the segments that are connected to the output pins which might initially seem incoherent. What I have done is that I assingned labels to the segments, and placed them on a sequence that starts with the segment connected to the first output pin, and all the way to the last. In this manner I can decode what might seem like an incoherent LED 7 segment display!
