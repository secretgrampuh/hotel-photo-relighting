# Hotel Photo Relighting Pipeline

**Bringing a hotel's old photo library back to life, without a reshoot.**

A prototype I built in 2026 for a global hotel group. This repo shows the results. The code is private. I'm happy to walk through it in an interview.

<table><tr>
<td align="center"><b>Before</b><br><img src="images/01_boardroom_before.jpg" width="400"></td>
<td align="center"><b>After</b><br><img src="images/01_boardroom_after.jpg" width="400"></td>
</tr></table>

## The problem

A big hotel chain has thousands of photos per property, and a lot of them look dated: shot at night, warm and flat, windows closed. Nobody can reshoot a whole portfolio. Sending photographers back to thousands of properties costs a fortune.

## What I built

A Python batch pipeline that:

1. **Relights** each photo in several approved lighting looks.
2. **Color grades** every result with a local pass I tuned to match a modern, bright, cool look.
3. **Leaves a spread for an artist to pick from.** It saves both the raw and graded version of every look, so a person makes the final call, not the pipeline.

It is built to be scattershot on purpose. Not every look works on every photo, so instead of fighting for one perfect generation, it makes four cheap ones and lets a person keep the winners.

> **About $0.04 per image · 2–3 usable looks out of 4**

## The savings

This is where it gets interesting. Here's a rough comparison for a chain with about **7,000 properties** and we assume roughly **2,000 select photos per property**:

| | Per property | Whole portfolio |
|---|---|---|
| **Reshoot** (professional hotel shoot, $3,000–$10,000+ per project) | $3,000–$10,000+ | **$21M–$70M+** |
| **Relight the whole library** (4 looks per photo × $0.04) | about $320 | **about $2.2M** |

That's tens of millions of dollars, before counting photographer travel and rooms taken out of service for a shoot. Per image, commercial photography runs about $50–$150 per finished photo, against about $0.16 for four relit looks.

Of course, running a pipeline like this against your entire portfolio of selects is an inefficient spend of money, so I designed it as a drag/drop folder to be used a-la-carte. Whenever an artist wants a new look on an older/dated photo they simply drag that photo into the folder, a python script runs and generates 4 different looks for them, costs about $0.16 and takes 1 minute, instead of the artist having to waste part of an afternoon relighting manually in photoshop. In this way the client would probably only spend a few thousand across their entire portfolio during revamping of their web presence for these properties.

*Shoot pricing is from published photographer rates found online.*

## Results

### One source, many looks
<table><tr>
<td align="center"><b>Before</b><br><img src="images/04_lobby_before.jpg" width="260"></td>
<td align="center"><b>Look 1</b><br><img src="images/04_lobby_after_look1.jpg" width="260"></td>
<td align="center"><b>Look 2</b><br><img src="images/04_lobby_after_look2.jpg" width="260"></td>
</tr><tr>
<td></td>
<td align="center"><b>Look 3</b><br><img src="images/04_lobby_after_look3.jpg" width="260"></td>
<td align="center"><b>Look 4</b><br><img src="images/04_lobby_after_look4.jpg" width="260"></td>
</tr></table>

### Before and after
<table>
<tr>
<td align="center"><b>Before</b><br><img src="images/05_restaurant_before.jpg" width="400"></td>
<td align="center"><b>After</b><br><img src="images/05_restaurant_after.jpg" width="400"></td>
</tr>
<tr>
<td align="center"><b>Before</b><br><img src="images/02_bathroom_before.jpg" width="400"></td>
<td align="center"><b>After</b><br><img src="images/02_bathroom_after.jpg" width="400"></td>
</tr>
<tr>
<td align="center"><b>Before</b><br><img src="images/03_buffet_before.jpg" width="400"></td>
<td align="center"><b>After</b><br><img src="images/03_buffet_after.jpg" width="400"></td>
</tr>
</table>

### The artist chooses: raw or graded
The grading pass isn't always the right call, so both versions are kept side by side.

<table>
<tr>
<td align="center"><b>Raw</b><br><img src="images/06_bedroom_after_raw.jpg" width="400"></td>
<td align="center"><b>Graded</b><br><img src="images/06_bedroom_after_graded.jpg" width="400"></td>
</tr>
<tr>
<td align="center"><b>Raw</b><br><img src="images/07_bedroom_night_after_raw.jpg" width="400"></td>
<td align="center"><b>Graded</b><br><img src="images/07_bedroom_night_after_graded.jpg" width="400"></td>
</tr>
</table>

### Off the approved list
The approved styles are deliberately safe, but the same pipeline can go a lot further for editorial or campaign work.

<table><tr>
<td><img src="images/08_extreme_style_01.jpg" width="260"></td>
<td><img src="images/08_extreme_style_02.jpg" width="260"></td>
<td><img src="images/08_extreme_style_03.jpg" width="260"></td>
</tr><tr>
<td><img src="images/08_extreme_style_04.jpg" width="260"></td>
<td><img src="images/08_extreme_style_05.jpg" width="260"></td>
<td></td>
</tr></table>

## What I learned

- **Some looks invent things.** On a windowless restaurant, one look added a glass skylight that doesn't exist. I tested it head to head and found the look itself was the cause, so enclosed rooms now get looks that don't imply daylight.
- **Batches beat hand-picking.** The first hand-tuned boardroom result looked like the best it would get. Once the pipeline ran in batches across many rooms, several results beat it.

---

**Built with:** Python · generative AI relighting · custom color grading
**Related:** [Market-compliance image editing](https://github.com/secretgrampuh/market-compliance-image-editing), from the same project · [Full portfolio](https://secretgrampuh.github.io)
**Contact:** [lamplughvideo@gmail.com](mailto:lamplughvideo@gmail.com) · [LinkedIn](https://www.linkedin.com/in/zachary-l-7b384833/)
