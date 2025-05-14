# nyc-data-adv-react-lab-1 StreetSmart NYC 🚕🗽  
*Alternate‑Side Parking & Trash‑Day Buddy — React Lab*

> **Lab type:** Intermediate / 2–3 hrs  
> **Theme:** Real‑world NYC everyday headaches  
> **Tech:** React 19, Vite, Context API, custom hooks, React Router
> **Team:** Work in groups of (2-3) for this lab. If you work alone you must write a blog about your process and present to class.

---

## 1 | Why build this?

Every New Yorker with a car dreads the neon‑orange **alternate‑side** ticket, and nobody enjoys schlepping garbage bags downstairs just to learn pickup is tomorrow.  
In this lab you’ll create a tiny single‑page React app that answers two questions for *any* NYC address:

1. **“Do I need to move my car today?”**  
2. **“Is tomorrow trash day on my block?”**

Along the way you’ll practice modern React patterns (hooks, context, routing) in a project that’s small enough to finish but useful enough to keep on your phone.

---

## 2 | Learning goals

| Goal | What you’ll practice |
|------|----------------------|
| `useState` & controlled inputs | Manage address + borough form fields |
| `useEffect` | Fetch data when the address changes |
| **Custom Hook** (`useNYCData`) | Encapsulate fetch / caching logic |
| **Context API** | Global favorites list without prop drilling |
| **React Router** (v6) | Simple `/today` & `/settings` routes |
| UX polish | Loading skeletons & error states |

*Stretch:* replace Context with `useReducer`, add PWA features, or wire up real NYC open‑data APIs.

---

## 3 | Prerequisites

| Skill / Tool | Needed? | Quick Ref |
|--------------|---------|-----------|
| Modern JS (ES6+) | ✅ | [MDN cheatsheet](https://developer.mozilla.org/en-US/docs/Web/JavaScript) |
| Git basics | ✅ | Slides #1–2 – Git |
| Node ≥ 18 + npm | ✅ | `node -v` |
| React fundamentals | ✅ | [react.dev/learn](https://react.dev/learn) |

---

## 4 | Project scaffold

```text
streetsmart-nyc/
├─ public/
│  └─ mock-data.json
├─ src/
│  ├─ api/useNYCData.js
│  ├─ components/
│  │   ├─ AddressForm.jsx
│  │   ├─ ResultsCard.jsx
│  │   └─ FavoritesBar.jsx
│  ├─ context/FavoritesContext.jsx
│  ├─ pages/Today.jsx
│  ├─ pages/Settings.jsx
│  ├─ styles/main.css
│  └─ App.jsx
└─ README.md   ← you are here
````

> **Start from scratch:**
>
> ```bash
> npm create vite@latest streetsmart-nyc -- --template react
> cd streetsmart-nyc && npm i
> ```

---

## 5 | Mock API

Located at **`/public/mock-data.json`** — a simplified stand‑in for NYC DOT & DSNY endpoints.

```jsonc
{
  "brooklyn": {
    "123_fake_st": {
      "alt_side": { "status": "MOVE", "clean_start": "11:00" },
      "collection": { "tomorrow": "trash+recycling" }
    }
  }
}
```

`useNYCData(addressObj)` should:

1. Simulate a 600 ms network delay.
2. Return `{ data, status, error }`.
3. Cache results in memory for the session.

---

## 6 | Checkpoint roadmap (with time boxes)

| # | Task                                                     | Est.   |
| - | -------------------------------------------------------- | ------ |
| 1 | **Spin up Vite** project, add CSS from `styles/main.css` | 10 min |
| 2 | Build **FavoritesContext** (`localStorage` persistence)  | 15 min |
| 3 | Write **`useNYCData`** hook (mock fetch)                 | 20 min |
| 4 | Create **AddressForm** (controlled inputs)               | 15 min |
| 5 | Render **ResultsCard** (badge colors & icons)            | 25 min |
| 6 | Wire **React Router** (`/` & `/settings`)                | 5 min  |
| 7 | Add **FavoritesBar** (star toggle & quick‑load)          | 15 min |
| 8 | Polish UX (loading skeleton, skyline header)             | Flex   |

---

## 7 | Stretch goals

* Hook up the **NYC 311 Alternate‑Side Calendar API** (date‑level).
* Replace Context with `useReducer` for more explicit state transitions.
* Register as a **Progressive Web App** (offline cache last fetch).
* Dark‑mode toggle powered by CSS variables + Context.

---

## 8 | Submission

1. Push to a public GitHub repo (`streetsmart-nyc`).
2. Add screenshots/GIF to `README.md` (`npm run dev` → grab <kbd>⌘⇧4</kbd>).
3. Submit the repo URL.

---

## 9 | Grading rubric (20 pts)

| Area                                 | Pts | Details                       |
| ------------------------------------ | --- | ----------------------------- |
| Core features (parking + trash info) | 8   | Accurate logic & rendering    |
| Proper hook & Context usage          | 4   | No prop‑drilling antipatterns |
| Clean component structure / naming   | 3   | Self‑documenting code         |
| UX polish (loading, error, NYC vibe) | 3   | Badge colors, skyline header  |
| README completeness                  | 2   | Setup steps + images          |

---

## 10 | Helpful resources

* React Docs **Thinking in React** – [https://react.dev/learn/thinking-in-react](https://react.dev/learn/thinking-in-react)
* React Router Quick Start – [https://reactrouter.com/en/main/start/overview](https://reactrouter.com/en/main/start/overview)
* NYC Open Data 311 API – [https://dev.socrata.com/foundry/portal.311.nyc.gov/f9mf-jf7m](https://dev.socrata.com/foundry/portal.311.nyc.gov/f9mf-jf7m)
* DSNY Service Lookup – [https://www.nyc.gov/assets/dsny/site/services/collection-day](https://www.nyc.gov/assets/dsny/site/services/collection-day)

(Oh No! It looks like your PM at work gave you the wrong links use your reserch skills to find the correct links. Lowkey this really happend to me at an old job)
---

### Seen a parking officer lately?

Ship your app, keep those curbside tickets at bay, and help fellow New Yorkers own the **streetsmart** super‑power. Good luck! 🍎

