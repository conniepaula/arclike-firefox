# Arc-Like Firefox using CSS

After switching from Arc to Firefox, I badly missed Arc’s beautiful UI. So, I decided to create a custom `userChrome.css` to make Firefox look and feel more like Arc while preserving Firefox's native functionality. 

While there are extensions that attempt to replicate the Arc UI, most are no longer maintained and rely on JavaScript to create their own sidebar. I wanted to take a simpler, CSS-only approach that makes use of Firefox's built-in vertical tabs, giving it an Arc-like appearance without moving the address bar or altering the tab navigation. This means:

- The address bar stays at the top, and when using keyboard shortcuts, it won’t move to the center of the screen.
- While it is possible to move the address bar using CSS, that proved to be hard to manage in all its states, so I decided pursuing it would give me diminishing returns.

## How to Set Up Firefox to Use This

To make Firefox look more like Arc, follow these steps:

### 1. Enable Vertical Tabs

Vertical tabs are key to replicating Arc’s layout. To enable them:

1. Open Firefox.
2. Right-click the toolbox beside the address bar.
3. Select **"Turn On Vertical Tabs"**.
4. Right click the sidebar and select **"Customize Sidebar"**.
5. In **"Sidebar settings"**, check **"Hide tabs and sidebar"**.

Now, to open and close the sidebar, use `CTRL+Z` on Mac.

### 2. Disable the Bookmarks Toolbar
Optional but recommended.

To disable it:

1. Right-click on the **Bookmarks Toolbar** (if visible).
2. Select **"Never Show"**.

If you prefer to keep it, the CSS does change its colour to match the rest of the UI.

### 3. Use Full-Screen Mode and Hide Toolbars
 Optional but recommended.

1. On macOS, press `Cmd + Shift + F` to enter full-screen mode.
   - On Windows and Linux, the shortcut is `F11`.
2. Right-click the main toolbar (where the address bar is) and choose **"Hide Toolbars"** to keep it hidden when not in use.

Remember: this only works in full-screen mode, so otherwise the address bar will still be visible if you're not using it.

### 4. Enable `userChrome.css` in `about:config`

By default, Firefox does not load custom styles, so you must  explicitly enable it. To do that:

1. Type `about:config` into the address bar and press Enter.
2. Accept the warning if prompted (this is a necessary step for advanced settings).
3. Search for the preference `toolkit.legacyUserProfileCustomizations.stylesheets`.
4. Double-click it to set the value to **true**.

### 5. Add `userChrome.css` to Your Firefox Profile

Now that you've enabled custom styles, it’s time to add the `userChrome.css` file:

1. Type `about:support` in the address bar and press Enter.
2. Under the **"Application Basics"** section, look for the **"Profile Folder"** row and click **"Open Folder"**.
3. Inside your profile folder, create a new folder called **"chrome"** if it doesn't already exist.
4. Place the `userChrome.css` file from this repository into the **chrome** folder, or paste its contents into a new userChrome.css file you've created.
5. Restart Firefox to apply the changes.

### 6. Change your Firefox theme

By default, Firefox comes with the 'System theme - auto' activated. Since this is changing the colours of the browser, this will no longer be beneficial, as changing you computer's system theme will cause a colour mismatch on Firefox.

The `userChrome.css` file I'm providing here has a light pink and blue gradient and therefore uses the light theme.
I also have some commented rules for a dark theme, but they're a WIP.

1. Type `themes` into the address bar and click **"Manage Themes"**.
2. Choose the theme you want (Light or Dark) and press **"Enable"**.

### 7. Change the colours in `userChrome.css` and make the theme your own

The pink and blue gradient was my preference, but it doesn't have to be yours. You can change the CSS rules to match your own style.

You can tinker with everything in your `userChrome.css`, but avoid rules I've explicitly written should be untouched, as changing those will cause bugs.

You can change your CSS file in your preferred code editor, but then you'll have to restart Firefox every time to see the changes you've made. To see the changes in real time:

1. Open **"Developer Tools"** and in the three little dots, go to **"Settings"**.
2. If **"Enable browser chrome and add-on debugging toolboxes"** is not checked, check it and restart Firefox.
3. Go back to the Developer Tools Settings and check **"Enable remote debugging"**. This must be done after step 2.
4. In the main toolbox, open the application menu and go to **"More tools > Browser toolbox"**. Accept the connection.
5. Under **"Style Editor"**, look for `userChrome.css` and make changes there. As you save them, they'll be immediately applied.

To choose my colours, I used [cssgradient.io](https://cssgradient.io/), but you can use whatever tool you prefer.


### 8. Multiple Profiles

If you have more than one Firefox profile, remember that each profile has its own **chrome** folder for custom styles. You'll need to follow the same steps for each profile you want to customize.

---

## Notes

In the future, I might create a tool to generate a `userChrome.css` file depending on the colours you choose, but for now you'll have to manually modify it yourself.

Feel free to contribute or open issues if you have suggestions or encounter problems.
