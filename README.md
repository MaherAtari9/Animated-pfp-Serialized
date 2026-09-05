# Animated PFP - Serializd

Upload an animated profile picture (GIF) to [Serializd](https://www.serializd.com) by calling the API directly, since the website's UI doesn't support uploading animated images as a profile picture.

## How to use

### 1. Get your token
- Open [Serializd](https://www.serializd.com) and log in.
- Go to Settings, then open Developer Tools (F12).
- Go to **Application → Cookies**.
- Find the cookie named `tvproject_credentials` and copy its value (a long, random-looking string).

> ⚠️ **Do not share this token with anyone.** It acts as your password — anyone who gets it can take control of your account.

### 2. Prepare your image
Copy the full path to the GIF or image file you want to upload (e.g. `C:\Users\YourName\Downloads\image.gif`).

### 3. Edit the command
Open the `Animated` file or copy the command below, and replace:
- `[YOUR_TOKEN_HERE]` with the token you copied in step 1.
- `[IMAGE_PATH_HERE]` with the image path you prepared in step 2.

```cmd
curl "https://serializd.onrender.com/api/user/settings/updateimage" ^
  -H "accept: application/json, text/plain, */*" ^
  -H "origin: https://www.serializd.com" ^
  -H "referer: https://www.serializd.com/" ^
  -H "x-requested-with: serializd_vercel" ^
  -H "Authorization: Bearer [YOUR_TOKEN_HERE]" ^
  -F "image=@[PATH_TO_YOUR_IMAGE];type=image/gif"
```

### 4. Run the command
Paste the full command into CMD (Command Prompt) and hit Enter.

### 5. Verify
Refresh your profile page on Serializd — your animated picture should now show up. 🎉

## Notes

- If you get a `You must be logged in` error, your token is invalid or expired — repeat step 1.
- The token is tied to your login session, so if you log out or your session expires, you'll need a new one.
- This relies on an undocumented internal endpoint from Serializd, so it may change or stop working at any time.

## Disclaimer

This guide is for personal/educational use only (uploading your own picture to your own account). Do not use anyone else's token, and do not attempt to access accounts that aren't yours.
