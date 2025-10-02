# Push Notifications Not Showing on Web

### Error code

ERR-20251002-001

### 📌 Category

Frontend

### 💻 Technology / Language

React 18, OneSignal Web SDK v16, Chrome v140

### 🌍 Environment

Local / Staging / Production

---

## ❌ Error Message

Notifications sent from the OneSignal dashboard do not appear in the browser, even though the app is initialized.

---

## 🔍 Cause

* User is not fully subscribed to push notifications (opt-in not completed).
* Notifications may be **blocked** in browser site settings.
* The **App ID** or **site URL** configured in the OneSignal dashboard does not match the environment.
* Testing on localhost without `allowLocalhostAsSecureOrigin: true`.
* Sending notifications to the wrong audience segment (e.g., unsubscribed users).

---

## ✅ Solution

* **Step 1:** Check subscription status in the browser console:

  ```js
  console.log("Permission:", Notification.permission);
  console.log("Opted In:", OneSignal.User.PushSubscription.optedIn);
  console.log("Push ID:", OneSignal.User.PushSubscription.id);
  ```
* **Step 2:** If `Permission` is `denied`, reset site notification settings in the browser (Site Settings → Notifications → Allow).
* **Step 3:** Ensure `Opted In: true` and `Push ID` is not null.
* **Step 4:** Verify OneSignal `appId` in code matches the dashboard app ID.
* **Step 5:** In OneSignal dashboard → Audience, confirm your device appears as **Subscribed**.
* **Step 6:** Send a **Test Notification** from your user profile in the dashboard instead of using “All Users” to confirm delivery.
* **Step 7:** For localhost, include `allowLocalhostAsSecureOrigin: true` in `OneSignal.init`.

---

## 🔎 Verification

* User shows as **Subscribed** in OneSignal Dashboard → Audience.
* Sending a Test Notification from the dashboard to that user immediately shows a browser notification.
* Browser console confirms:

  * `Permission: granted`
  * `Opted In: true`
  * `Push ID: <uuid>`

---

## 📚 References

* [OneSignal Web Push Setup Docs](https://documentation.onesignal.com/docs/web-push-setup)
* [MDN Web Notifications API](https://developer.mozilla.org/en-US/docs/Web/API/Notifications_API)
