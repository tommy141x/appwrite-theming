![Banner](https://tommy141x.github.io/appwrite-theming/mockups/banner.png)

# 🎨 Theming for [Appwrite](https://appwrite.io/)

Want to personalize your Appwrite instance without diving into the source code? I created a CSS file that can be injected server-side to style your Appwrite console in line with your brand, with no need to recompile every update.

![Screenshot](https://tommy141x.github.io/appwrite-theming/mockups/cyan.png)

---

## ⚙️ Setup & Usage

### Nginx Reverse Proxy

To apply the theme, add the following snippet inside the `location` block for the Appwrite console (`/console`) in your `nginx` configuration. If you're using **Nginx Proxy Manager**, you can do this by clicking the gear icon next to the location.

```nginx
proxy_set_header Accept-Encoding "";
sub_filter '</head>' '<style>:root {

  --primary-color-hue: 205deg;
  --primary-color-saturation: 100%;
  --primary-color-brightness: 55%;

  --background-color-hue: 0deg;
  --background-color-saturation: 0%;
  --background-color-brightness: 55%;

  --logo-image: url("https://api.timmygstudios.com/v1/storage/buckets/images/files/logo/view?project=tore");
  --background-image: url("https://api.timmygstudios.com/v1/storage/buckets/images/files/dev09242024header/view?project=tore");

}</style><link rel="stylesheet" type="text/css" href="https://tommy141x.github.io/appwrite-theming/appwrite.css"></head>';
sub_filter_once on;
sub_filter_types text/html;

```
Customize ``--primary-color``, ``--background-color``, ``--logo-image``, and ``--background-image`` to match your liking (background image appears on the authentication screen).

# 📸 More Screenshots
![Screenshot](https://tommy141x.github.io/appwrite-theming/mockups/dark-green.png)
![Screenshot](https://tommy141x.github.io/appwrite-theming/mockups/dark-blue.png)
![Screenshot](https://tommy141x.github.io/appwrite-theming/mockups/login.png)

# 💡 Notes
This approach may also work on other servers like Caddy or Apache, though I haven't tested them yet. If you have improvements, issues, or suggestions, feel free to open a pull request or start a discussion.
