# ABNORMAL Store

A public product catalogue for PC, Android and iOS builds. The site does **not** require Google login, create customer accounts, save wishlists, keep customer order history, or connect to a customer database.

## Run it on your PC

Requirements: Node.js 20.9 or newer.

1. Extract the project ZIP.
2. Open the extracted folder in File Explorer.
3. Click the address bar, type `cmd`, and press Enter.
4. Run:

   ```bat
   npm install
   npm run dev
   ```

5. Open `http://localhost:3000` in your browser.

To make a production build, run `npm run build`.

## Orders and privacy

On a product page, choose a duration and payment method. After paying, enter the sender phone number for bKash/Nagad and the transaction ID/number. Binance requires only the transaction number/ID. The website prepares a confirmation summary that you can copy and send to Discord or Telegram with your payment screenshot.

**Important:** order information stays temporarily in page memory so the confirmation screen can show it. It is not uploaded to this website's server, stored in a customer account, or saved in browser storage. If the page is refreshed or the confirmation is left, the details are cleared. Copy the summary before leaving the confirmation page. Orders are not automatically sent to staff; you must submit the details and payment proof to support. Staff verify payment manually before delivery.

This keeps the website public and avoids collecting visitor account/order histories. The site still must serve its pages and images to visitors; the hosting provider may keep ordinary server access logs according to its own policy.

## Payment and support settings

Edit `src/data/store.ts` to change the public payment destinations and the Discord/Telegram URLs. Double-check all payment details before publishing. Values in this file are public and visible to website visitors; never put passwords or private keys here.

## Add a product with the Windows wizard

1. Double-click `add-product.bat`.
2. Enter the category (`PC`, `Android`, or `iOS`).
3. Enter the product name and summary.
4. Add each duration and the real USD and/or BDT price.
5. The wizard adds the product to `src/data/custom-products.json`.
6. Run `npm run dev` to preview it, or rebuild/redeploy the site to publish it online.

Example descriptions:

- **PC:** `Windows PC build with 1 Day and 1 Month access.`
- **Android:** `Android non-root build with 1 Day, 7 Days, or 30 Days access.`
- **iOS:** `iPhone and iPad build with 1 Day or 1 Month access.`

Node.js 20.9 or newer is required for the wizard. Prices must be real amounts you intend to charge.

## Local character artwork and colour themes

All character images are served from `public/art/characters`. The website makes no external anime-image API requests and does not download pictures during install, development, or deployment. Its fixed CSS colour themes remain tied to the active section; character colours never recolour the whole page.

The existing first image for each theme can stay named `anemo.png`, `electro.png`, `dendro.png`, `cryo.png`, `pyro.png`, `hydro.png`, or `geo.png` (WebP, AVIF, JPG and JPEG are also supported). Add as many extra variants as you like using names such as `anemo2.png`, `anemo3.png`, `anemo4.png`, `electro2.png`, or `cryo 2.webp`. The website discovers them automatically, prefers a compact modern format when equivalent versions exist, and rotates through the available local variants. For an optional phone-sized transparent version, use a matching name such as `anemo.mobile.webp` or `anemo2.mobile.webp`.

Keep character files in this folder and redeploy after adding them. Transparent PNG/WebP cut-outs look best; CSS alone cannot remove an opaque image's background.

## Deploy

This is a Next.js application. It can be deployed to Vercel or another host that supports Next.js. No Firebase keys, Google login setup, database, or `.env.local` file is needed. Use the hosting platform's standard import/build steps and test the deployed product and checkout pages before sharing the link.

