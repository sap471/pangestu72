---
title: 'Mengatasi Error Console pada EsLint'
description: 'mengatasi error console.log pada eslint'
summary: "Saat pertama kali membuat project nuxt, saya heran sama eslint. kenapa setiap saya menulis 'console.log','console.error','console.warn' selalu keluar pernyataan warning."
author: 'sap471'
comment: 0
date: {
  created: 1593816650,
  updated: 0,
}
published: true
hasThumbnail: false
category: 'js'
tags: 'eslint, nuxt'
---

Saat pertama kali membuat project nuxt, saya heran sama eslint. kenapa setiap saya menulis 'console.log','console.error','console.warn' selalu keluar pernyataan warning.

```
Unexpected console statement no-console
```

Ternyata warning tersebut memang bawaan dari eslint yang mengharuskan kita mengkonfigurasi pengaturan eslint agar dapat menggunakan class console.
karena konfigurasi awal dari eslint, tidak memperbolehkan kita menggunakan console.

Konfigurasinya seperti dibawah ini, Tambahkan ini di object rules dalam file .eslintrc.js di folder project anda.
```js
// ...
rules: {
    // ...
    "no-console": "off",
    "no-restricted-syntax": [
      "error",
      {
        selector:
          "CallExpression[callee.object.name='console'][callee.property.name!=/^(log|warn|error|info|trace)$/]",
        message: "Unexpected property on console object was called",
      },
    ],
    // ...
  },
```

