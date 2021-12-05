![Strapi](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d2ecfe9f-fa41-4caa-98e6-1354850c39d1/Logo.WhiteBackground.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20211205%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20211205T133805Z&X-Amz-Expires=86400&X-Amz-Signature=a219816661f4556bb53202a46539fa15e9d53a1cf7bdc7098a110de27124272d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Logo.WhiteBackground.png%22&x-id=GetObject)

## _cPanel Node.js install_
---

If you are looking for the Strapi code, please see the [Strapi Monorepo](https://github.com/strapi/strapi). This Repo is only for our [documentation](https://strapi.io/documentation).

---


Strapi is a free and open-source headless CMS delivering your content anywhere you need.

- **Keep control over your data**. With Strapi, you know where your data is stored, and you keep full control at all times.
- **Self-hosted**. You can host and scale Strapi projects the way you want. You can choose any hosting platform you want: AWS, Netlify, Heroku, a VPS, or a dedicated server. You can scale as you grow, 100% independent.
- **Database agnostic**. You can choose the database you prefer. Strapi works with SQL databases: PostgreSQL, MySQL, MariaDB, and SQLite.
- **Customizable**. You can quickly build your logic by fully customizing APIs, routes, or plugins to fit your needs perfectly.

## Documentation Contribution Requirements

The following are required if you are submitting pull requests to the documentation. For more information on how to contribute please see our [contribution guide](./CONTRIBUTING.md)

- NodeJS >=12.x <=14.x
- NPM >= 6.x
- Yarn >= 1.22.x

## Installation

1: Create and configure your application node.js on the cPanel.
2: Load your Strapi project on your node.
3: Add this line to the .env

```sh
HOST=0.0.0.0
PORT=1337
+ PUBLIC_URL=https://my.domain.com
```

4: Add these lines to .htaccess:

```sh
+ RewriteEngine On
+ RewriteRule ^$ http://localhost:1337/ [P]
+ RewriteCond %{REQUEST_FILENAME} !-f
+ RewriteCond %{REQUEST_FILENAME} !-d
+ RewriteRule ^(.*)$ http://localhost:1337/$1 [P]
```

5: Launch your app: enjoy 🎉 

> Look out: If the process stops your application will stop working. You must therefore run the application in the background to allow it to continue working. So you can use `pm2` to keep the process running in the background.

## Configuring `pm2`
1: Install pm2

```sh
npm install -g pm2
```

2: Create a startup file call `start.sh`, with the contents of your script.

```sh
#!/bin/bash
cd /path/to/project
npm start
```

3: Then, start `start.sh` by `pm2`.

```sh
#!/bin/bash
pm2 start start.sh --name appNameYouLike
```

_By LKAOpremier_
