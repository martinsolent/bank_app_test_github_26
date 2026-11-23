# Tutorial: From a Figma page to a clickable bank app prototype

This tutorial shows how to turn every screen on a Figma page into one working, clickable prototype you can use for usability testing. No coding is needed. You paste a link and describe what you want.

In this repository, open `index.html` to run the phone-friendly prototype. The original layout is preserved as `old.html`; on narrow screens, the screen picker is hidden and the app content adjusts to fit the phone width.

**What you end up with:** a single file, `bank-app.html`, that opens in any browser. It contains all 13 screens from the Figma page, linked together so a participant can tap through the app.

**What you need**

- A Figma design file with your screens on one page, and a Figma account that can open it
- A Claude account at claude.ai (the free plan works)
- The Figma connector switched on in Claude (Step 1 shows you how)
- A web browser to open the finished file

## Step 1: Connect Claude to Figma (one-time setup)

You only do this once. Use Claude in your web browser at claude.ai. The free plan is fine: the bank app in this tutorial was built on a free account.

You want the ordinary **Figma connector** that is listed inside Claude. You don't need Figma's Dev Mode MCP server, the Figma desktop app, or any settings files.

1. Go to [claude.ai](https://claude.ai) and sign in.
2. Open the connector settings. Click **Customize** in the left sidebar and choose **Connectors**. (On some versions of Claude this sits under **Settings > Connectors**.)
3. Click **Browse connectors**, type **Figma** in the search box and open the Figma listing.
4. Click **Connect**. A Figma page opens in a new window or tab.
5. Sign in to Figma if it asks, then approve the request to let Claude access your account.
6. You come back to Claude, and Figma now shows as connected.

**Check it's on in your chat.** Start a new chat and click the **+** button below the message box. Find Figma in the list of connectors and make sure it's switched on.

A few things to watch for:

- **Use the right Figma account.** Connect with the account that can open your design file. If a classmate or client owns the file, ask them to share it with you first.
- **Can't see Figma in the list?** Check you are signed in at claude.ai rather than using another app, then refresh the page and look again.
- **Free plan limits.** The free plan has a message limit that resets after a few hours. Reading 13 screens and building them used up most of the allowance in this project, so put your whole request into one message (Step 4). If you run out, the file Claude made is still there to download. You just have to wait before asking for changes.

## Step 2: Get your Figma page ready

1. Open your Figma file and go to the page that holds all of the screens you want to build.
2. Check that every screen is a separate frame and has a clear name (for example "Sign in", "Home", "Pay the bill"). Claude uses these names to tell the screens apart.

## Step 3: Copy the link to the whole page

This is the key step. A link to the page, rather than to a single screen, lets Claude see every screen at once.

1. Click on the canvas and press **Select all** (Ctrl+A on Windows, Cmd+A on Mac).
2. In the **left panel**, find the **Pages** list.
3. **Right-click the page name** and choose **Copy link to page**.

![Figma with every frame selected and the right-click menu on the Prototype page showing Copy link to page](screencaps_fig_claude/Screenshot%202026-11-23%20201628.png)

The link ends with a `node-id=` value that points to the page itself. In this project it was `node-id=3025-2`.

*Note:* Selecting all is not strictly required, because the page link is what tells Claude where to look. It does no harm, and it can help Claude see what you have selected.

## Step 4: Paste the link into Claude and ask for the build

Paste the link into the chat with a short request, for example:

> Turn all the screens on this page into front-end code: \[paste your Figma page link\]

A more specific version also works well:

> Build every screen on this Figma page into one clickable HTML prototype. Link the screens together so I can use it for user testing.

## Step 5: Let Claude read the page

This is where your design comes in from Figma. Claude uses the Figma connector to do the following:

1. List every screen (frame) on the page. Here that was 13 distinct screens, with the sign-in screen appearing twice: once empty and once filled in.
2. Pull the design details for the screens, including layout, colours, fonts and text.
3. Look at a screenshot of each screen so the build matches the original.

You don't need to do anything during this step. In the chat you'll see lines such as **Get Metadata** and **Used Figma integration**. Click one if you want to see what Claude asked Figma for.

![Claude chat after pasting the Figma page link, with the finished bank app open in the preview panel on the right](screencaps_fig_claude/Screenshot%202026-11-23%20202130.png)

## Step 6: Review what Claude builds

Claude produces one file, `bank-app.html`, containing all the screens and the connections between them. It opens in a panel on the right of the chat.

- The **eye** icon shows the working preview, so you can click through the app straight away.
- The **</>** icon shows the code behind it.

![The bank app open in code view in Claude, with the eye and code icons at the top right of the panel](screencaps_fig_claude/Screenshot%202026-11-23%20202151.png)

To save the file, click the small arrow next to **Copy** at the top right of the panel and choose **Download as HTML**. Then open the downloaded file in your browser.

![The Copy menu open, showing Download as HTML and Publish artifact](screencaps_fig_claude/Screenshot%202026-11-23%20202209.png)

*Note:* **Publish artifact** gives you a shareable claude.ai link instead. That is handy for a quick look, but for testing you'll want the downloaded file so you can host it yourself.

The screens in this project were:

- Sign in (empty and filled in)
- Home
- Account and card
- Beneficiary list
- Beneficiary detail (amount empty and filled)
- Transaction successful
- Pay the bill
- Electric bill (empty, number keypad, and £480 with the letter keyboard)
- Electric bill summary
- Electric bill paid

On a desktop, a **screen list** on the left lets you jump straight to any screen. It is hidden on phones.

![The Home screen of the prototype with the screen list on the left](screencaps_fig_claude/Screenshot%202026-11-23%20202815.png)

Compare each screen with Figma. Expect a few differences:

- **Photos:** the Figma photo links expire after 7 days and can't be downloaded, so avatars appear as coloured circles with initials.
- **Illustrations:** the success, wallet and bill illustrations are simplified redraws, not the originals.
- **Typos:** text is copied exactly from your design, including any typos such as "Avalable balance". Ask Claude to correct them if you want.

## Step 7: Set up the prototype for your test tasks

Tell Claude what your participants will do and how the sign-in should behave. In this project the tasks were:

![The three test tasks as set up in the testing tool](screencaps_fig_claude/Screenshot%202026-11-23%20200254.png)

| Task | Name | Description |
| --- | --- | --- |
| 1 | Check Your Account Balance | Find your current account balance and tell me what it is. |
| 2 | Transfer Money to a Friend | Please transfer £150 to Harper. |
| 3 | Pay a bill | Pay your Electric bill. |

The sign-in was set up like this, using a request such as:

> When the user taps the fingerprint, take them to the sign-in screen filled in with the name and password. Then they tap Sign in to go to the Home screen. If they type anything instead, let that work too.

The result:

- **Tapping the fingerprint** fills in the name and password and stays on the sign-in screen.
- **Tapping Sign in** goes to the Home screen.
- **Typing anything** in either field also turns on the Sign in button.

## Step 8: How each task works in the prototype

**Task 1: Check the balance.** Home, then Account and Card. The balances are shown there: Current $20,000, Saver $12,000 and Super Saver $230,000. Decide in advance which one you will accept as the correct answer.

**Task 2: Transfer £150 to Harper.** From Home, the participant opens Transfer or Beneficiary, taps Harper, and types the amount. Confirm stays greyed out until an amount is entered. Then they reach Transaction Successful and tap Home.

**Task 3: Pay the electric bill.** Home, then Pay the bill, then Electric bill. They enter an amount on the number keypad and tap Confirm. After that come the bill summary, Pay the bill, and the success screen.

## Step 9: Run your usability test

1. Open `bank-app.html` in a browser, ideally in a phone-sized window or on a phone.
2. **Refresh the page before each participant.** The prototype does not reset by itself, so refreshing starts them back at Sign in.
3. Hide or ignore the screen list on the left so participants only see the app.
4. Read each task aloud and watch what they do.
5. Check the results yourself. The prototype accepts any amount, so it will not tell you whether a participant typed 150 for Task 2.
6. Tapping a tile that isn't part of the design, such as Water bill or Withdraw, shows a short message instead of opening a screen.

## Step 10: Ask for changes

Send Claude a short request whenever something is not right. Examples:

- "Fix the typo on the Account screen."
- "Make Task 2 only complete if the amount is £150."
- "Add a screen for the Water bill."

Claude updates the same file each time, so you keep using `bank-app.html`.

## Quick recap

1. Connect Claude to Figma once, from **Customize > Connectors** at claude.ai.
2. Get the Figma page ready with named frames.
3. Select all, then right-click the page in the left panel and choose **Copy link to page**.
4. Paste the link into Claude and ask for all screens as a clickable prototype.
5. Review the file against Figma, then download it with **Copy > Download as HTML**.
6. Tell Claude your tasks and how the sign-in should behave.
7. Refresh the page between participants and run your test.
