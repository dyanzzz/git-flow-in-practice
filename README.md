# Gitflow in Practice
### _Bagaimana menggunakan git?_

[![N|Solid](https://miro.medium.com/max/1400/1*8-zDz1s5Atux_yNW_mXmfg.png)](https://miro.medium.com/max/1400/1*8-zDz1s5Atux_yNW_mXmfg.png)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://github.com/dyanzzz/git-flow-in-practice)

Pada kali ini saya ingin membahas salah satu branching model git mulai dari membuat repositori sampai release. Untuk pengaplikasianya saya menggunakan github.

- Create A Repository
- Getting Started with Gitflow
    - Develop and Master Branches
    - Feature Branches
    - Release Branches
    - Hotfix Branches
    - 

## Create A Repository

Langkah pertama dalam menggunakan github ialah membuat repositori. Bagaimana cara membuat repositori di github?
- Di sudut kanan atas halaman klik + dan pilih new repository
[![N|Solid](https://miro.medium.com/max/248/1*e_VsOoVl4Vc3iT3t8WzoWA.png)](https://miro.medium.com/max/248/1*e_VsOoVl4Vc3iT3t8WzoWA.png)
- Tulis nama repositori yang ingin dibuat, lalu tambahkan deskripsi singkat mengenai repositori, jenis repositori, dan biasanya saya memilih untuk membuat repositori baru yang disertakan file readme dan gitignore.
[![N|Solid](https://miro.medium.com/max/808/1*Up6-qL3p1aYS9hKr0xRcDQ.png)](https://miro.medium.com/max/808/1*Up6-qL3p1aYS9hKr0xRcDQ.png)
Setelah semua form terisi klik Create Repository.

## Getting Started with Gitflow
_Gitflow_ adalah sebuah branching model git yang diciptakan oleh [Vincent Driessen]. Gitflow sangat ideal untuk proyek yang memiliki siklus rilis yang terjadwal. Untuk lebih jelasnya saya akan menjelaskan satu siklus penggunaan gitflow.
- Pertama, import repositori yang telah dibuat terlebih dahulu.
    ```sh
    $ git clone git@github.com:{username git}/gitflow-in-practice.git
    ```
#### Develop and Master Branches
- Gunakan _command_ `git flow init` dalam folder repositori.
    ```sh
    $ git flow init
    ```
    [![N|Solid](https://miro.medium.com/max/714/0*mdbFVAu6MBm_zWWY)](https://miro.medium.com/max/714/0*mdbFVAu6MBm_zWWY)
- Gunakan _command_ `git branch` untuk melihat branch yang telah terbentuk
    ```sh
    $ git branch
    ```
    [![N|Solid](https://miro.medium.com/max/531/0*i7ZDks3Y92nvFXJU)](https://miro.medium.com/max/531/0*i7ZDks3Y92nvFXJU)
- Create sebuah `file.txt` yang akan digunakan sebagai bahan praktik dalam penggunaan _gitflow_. Sebaiknya file yang dibuat langsung di _push_ ke _master_ untuk mempermudah membandingkan ketika melakukan _merge_ dalam tahap selanjutnya.

#### Feature Branches
- _Feature branches_ digunakan untuk membangun fitur yang akan digunakan. Esensi dari _feature branch_ adalah _branch_ akan ada selama proses _development_. Singkatnya, _feature branch_ hanya ada di _developer_ bukan di _origin_. Proses di _feature branch_ yaitu :
    ```sh
    $ git flow feature start MyFeature
    ```
    [![N|Solid](https://miro.medium.com/max/753/0*n0YbjU1Bt9OBmhPL)](https://miro.medium.com/max/753/0*n0YbjU1Bt9OBmhPL)
    Selama pengerjaan fitur di sistem, _developer_ akan berada di _branch MyFeature_. Sebagai ganti dari fitur, tuliskan sesuatu di dalam file yang telah dibuat sebelumnya sebagai pertanda bahwa sudah ada penambahan. Jangan lupa untuk melakukan proses _commit_ agar gitnya terupdate.
    ```sh
    $ git flow feature finish MyFeature
    ```
    
    [![N|Solid](https://miro.medium.com/max/773/0*FdLY0ysb12WU2PQ4)](https://miro.medium.com/max/773/0*FdLY0ysb12WU2PQ4)
    Sebelum dilakukan proses _finish_ pada _branch_, terlebih dahulu yang dilakukan adalah proses _testing_. Hal ini dilakukan untuk mencegah adanya _error_ ketika _branch dimerge_ ke _develop_.
    
#### Release Branches
- Setelah selesai dari _branch develop_, langkah selanjutnya yaitu proses _release_. _Branch release_ biasanya digunakan untuk persiapan ke _production_, dalam _branch_ ini masih diperbolehkan untuk melakukan perubahan tetapi hanya untuk skala kecil saja. Jika terdapat bug yang memerlukan banyak perubahan seperti fitur tambahan maka _branch_ akan dikembalikan ke _develop_. _Branch release_ dibuat dari _branch develop_ dengan penambahan _version number_. Langkah pembuatan _branch release_ yaitu :
    ```sh
    $ git flow release start 0.1.0
    ```
    [![N|Solid](https://miro.medium.com/max/715/0*uty7WzOqORjlm4q8)](https://miro.medium.com/max/715/0*uty7WzOqORjlm4q8)
    Setelah sistem telah melalui proses testing maka proses release dapat diakhiri.
    ```sh
    $ git flow release finish 0.1.0
    ```
    Setelah proses release selesai maka branch akan di merge ke branch master dan develop.
#### Hotfix Branches
- Tidak dapat dipungkiri bahwa akan ada masanya branch di master terdapat error oleh karena itu diperlukan branch hotfix untuk melakukan perbaikan secepatnya. Oleh karena itu branch hotfix hanya akan di buat dari master. Berikut adalah tahapan dalam branch hotfix.
    ```sh
    $ git flow hotfix start branch_hotfix
    ```
    [![N|Solid](https://miro.medium.com/max/808/0*WBU9-d7G_0U0vOo5)](https://miro.medium.com/max/808/0*WBU9-d7G_0U0vOo5)
    ```sh
    $ git flow hotfix finish branch_hotfix
    ```
    Untuk melihat log gitnya dapat menggunakan tools git seperti gitkraken, sourcetree, dll. Demikian yang dapat saya bagikan semoga teman-teman developer dapat mencobanya. Terima kasih dan __Keep learning!__

## Referensi

https://medium.com/easyread/gitflow-in-practice-1d8a2bbdc3a1
https://help.github.com/articles/create-a-repo/
https://nvie.com/posts/a-successful-git-branching-model/
https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow

**Free Software, Hell Yeah!**

> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.

Dillinger requires [Node.js](https://nodejs.org/) v10+ to run.

**Membuat Table**

Dillinger is currently extended with the following plugins.
Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

[//]: # (this is a comment => These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [vincent driessen]: <https://nvie.com/posts/a-successful-git-branching-model/>
