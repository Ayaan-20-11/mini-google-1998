<div align="center">

<img src="assets/mini-google-logo.gif" alt="Mini Google 1998 animated logo" width="760">

<p>
  <img src="https://img.shields.io/badge/Single%20File-index.html-4285F4?style=for-the-badge" alt="Single File index.html">
  <img src="https://img.shields.io/badge/Algorithm-Random%20Surfer-EA4335?style=for-the-badge" alt="Algorithm Random Surfer">
  <img src="https://img.shields.io/badge/Simulation-100%2C000%20Moves-FBBC05?style=for-the-badge" alt="100,000 Moves">
  <img src="https://img.shields.io/badge/Zero-Dependencies-34A853?style=for-the-badge" alt="Zero Dependencies">
</p>

**A first-year AI lab search engine showing why 1998 Google PageRank beat keyword stuffing.**

</div>

---

## Old Way vs. PageRank Way

Search for **`pizza`** and watch two ranking algorithms compete side by side:

<div align="center">
  <img src="assets/pagerank-demo.gif" alt="Random surfer graph and Old vs PageRank search results for pizza" width="820">
</div>

- **Left — Old way (Word Count):** Ranks pages strictly by how many times the search word appears in the text. A spammy page repeating `"pizza"` 10 times (`pizza-pizza-pizza.com`) steals **#1** even though nobody links to it.
- **Right — PageRank way (1998):** Simulates a **random surfer** taking **100,000 moves** across the web graph. Because trusted pages link to `best-pizza-pune.com`, it earns the highest PageRank (**~39%**) and wins **#1**.

---

## How the Random Surfer Works

1. Start on a **random page** among the 6 pages.
2. Repeat **100,000 times**:
   - **15% chance:** The surfer gets bored and jumps to any random page.
   - **85% chance:** The surfer follows one of the current page's outgoing links at random.
   - Record a visit to whichever page the surfer lands on.
3. Compute each page's score:

$$\text{PageRank (\%)} = \frac{\text{Visits}}{\text{100,000}} \times 100$$

---

## Dataset & Link Graph

```mermaid
flowchart LR
  1["1: pune-food-guide.com"] --> 2["2: best-pizza-pune.com"]
  2 --> 1
  2 --> 3["3: college-canteen-blog.com"]
  3 --> 2
  3 --> 4["4: pizza-recipes-home.com"]
  4 --> 2
  4 --> 5["5: cheap-eats-pune.com"]
  5 --> 2
  6["6: pizza-pizza-pizza.com"] --> 1
```

| Page | URL | Text | Links To |
| :---: | :--- | :--- | :---: |
| **1** | `pune-food-guide.com` | Where to eat in Pune - vada pav and biryani and pizza | `2` |
| **2** | `best-pizza-pune.com` | Fresh wood-fired pizza made daily - try our cheese pizza | `1, 3` |
| **3** | `college-canteen-blog.com` | Student reviews of canteen food and chai and Friday pizza | `2, 4` |
| **4** | `pizza-recipes-home.com` | Make pizza at home - pizza dough and pizza sauce | `2, 5` |
| **5** | `cheap-eats-pune.com` | Good food under 100 rupees - misal and dosa and pizza slices | `2` |
| **6** | `pizza-pizza-pizza.com` | pizza pizza pizza pizza pizza pizza pizza pizza pizza pizza | `1` |

---

## How to Run

No installs, no build step, and no server required:

1. Download or clone this repository.
2. Double-click **`index.html`** to open it in any web browser.
3. Type a word like `pizza`, `pune`, `food`, or `chai` and click **Search**!
