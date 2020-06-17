# Git
  **Source code repository** adalah sebuah media pengarsipan yang digunakan untuk menyimpan sekumpulan atau banyak source code 
yang bersifat public maupun private. Untuk saat ini sudah ada beberapa layanan yang bersifat free atau open-source. 
Source code repository juga menyediakan fitur version control system, bug tracking, release management, mailing lists 
dan wiki-based documentation. Ada banyak contoh dari code repository seperti assembla, bitbuckets, buddy, cloudforge, 
github, gitlab, gnu savannah, helix teamhub, launchpad, osdn, sourceforge, dan sebagainya. 

  **Version control** merupakan sebuah sistem yang digunakan untuk mencatat setiap perubahan yang terjadi pada file atau sekumpulan 
file seiring dengan waktu, sehingga memudahakan penggunakan ketika ingin menggunakan atau memeriksa versi tertentu pada waktu 
tertentu juga. Terdapat beberapa VCS yang telah dikembangkan, seperti bazaar, subversion(svn), mercurial, cvs, rcs, perforce, 
clearcase, gnu arch, gnu cssc ,dan git.

## Pre-requisites
1. Dijalankan di Ubuntu 19.04
2. Git latest version(2.20.1)
3. Memiliki akun github

## Instalasi
1. Untuk instalasi git pada Ubuntu versi 19.04 bisa menggunakan paket manager dengan perintah.    
`$ sudo apt update && sudo apt install git -y`   
Atau bisa melihat link berikut, [klik](https://www.atlassian.com/git/tutorials/install-git). 

2. Kemudian setelah selesai melakukan instalasi, coba cek versi dari git menggunakan perintah berikut.   
`$ git --version`   
Output:    
![ALT HERE!](/images/pict_1.png "Git verion")

3. Kemudian tambahkan identitas username dan email yang nantinya akan dikenali sebagai author oleh git.    
`$ git config --global user.email "youremailaddress"`    
And   
`$ git config --global user.name "yourusername"`    
![ALT HERE!](/images/pict_10.png "Git configuration author")

## Usage
#### - Basic
1. Langkah pertama yang harus dilakukan adalah menginisiasi directory yang akan digunakan sebagai repository. Dapat dilakukan dengan cara perintah berikut:     
`$ git init namaDirectory`     
Output:   
![ALT HERE!](/images/pict_2.png "Git initiation")

2. Kemudian selanjutnya adalah pindah kedalam directory tersebut dan bisa dilihat bahwa ada subdirectory yang bernama `.git/` yang dimana directory ini akan digunakan git untuk menyimpan perubahan yang dilakukan pada proyek. Ini adalah bagian terpenting dari git, dan inilah yang akan disalin ketika melakukan kloning sebuah repository.  
`$ cd namaDirectoy && ls -la`   
Output:    
![ALT HERE!](/images/pict_3.png "Change directory")

3. Selanjutnya ada file yang bernama file .gitignore, yang merupakan sebuah file yang berisi daftar nama-nama file dan directory yang akan diabaikan oleh git. Sehingga perubahan apapun yang kita lakukan terhadap file dan directory yang sudah masuk ke dalam daftar .gitignore tidak akan dicatat oleh git. Untuk menggunakan file .gitignore, tinggal buat saja file bernama .gitignore didalam repository/directory proyek.    
`$ touch .gitignore`    

4. Pada contoh file dibawah, dapat dilihat terdapat file config.enc dan directory /vendor yang ada didalam file .gitignore, sehingga git akan mengabaikan file dan directory tersebut. Pembuatan file .gitignore sebaiknya dilakukan diawal pembuatan repository.    
`$ cat .gitignore`    
Output:     
![ALT HERE!](/images/pict_4.png "File .gitignore")

5. Selanjutnya tambahkan beberapa file dan directory.     

6. Setelah ditambahkan, jalankan perintah git status untuk melihat status dari repository.    
`$ git status`    
![ALT HERE](/images/pict_5.png "Git status")

7. Berdasarkan keterangan diatas, dapat dilihat user berada pada branch master dan terdapat 3 file yang belum ditambahkan ke Git. 
Selanjutnya, Git memiliki 3 keadaan utama dimana berkas berada: committed, modified, dan staged. Committed berarti data telah tersimpan secara aman pada basisdata lokal. Modified keadaan dimana ketika terdapat perubahan pada berkas namun belum melakukan commit pada basisdata. Sedangkan staged berarti berkas atau file yang sebelumnya telah dicommit dan diberikan tanda setelah melakukan perubahan namun belum dicommit kembali.    
![ALT HERE!](/images/git_kondisi.png "Condition git")

8. Selanjutnya, ubah kondisi ketiga file sebelumnya menjadi staged dengan perintah.    
`$ git add filename`    
![ALT HERE!](/images/pict_6.png "Git add")       
 Atau     
`$ git add .gitignore file.html index.html`   
![ALT HERE!](/images/pict_7.png "Git add")   
 Atau    
`$ git add .`    
![ALT HERE!](/images/pict_8.png "Git add")

9. Selanjutnya coba cek status dari repository, kondisi file sekarang akan menjadi staged.
`$ git status`   
![ALT HERE!](/images/pict_9.png "Git status")

10. Setelah itu, ubah kondisi file tersebut menjadi committed agar semua perubahan tersimpan oleh Git.   
`$ git commit -m "Message"`    
![ALT HERE!](/images/pict_11.png "Git commit")

11. Selanjutnya, untuk kasus ketika terdapat perubahan pada file index.html(edit file index.html).   
`$ cat index.html`    
![ALT HERE!](/images/pict_12.png "Edit file index.html")

12. Selanjutnya cek status dari repository.   
`$ git status`    
![ALT HERE!](/images/pict_13.png "Git status")

13. Atau bisa juga menggunakan perintah `$ git diff` berikut untuk melihat lebih detail bagian mana yang mengalami perubahan.     

14. Ternyata keadaan file yang telah diubah tadi berubah menjadi modified, sehingga perlu dilakukan commit kembali untuk menambahkan perubahan kedalam git.   
`$ git add index.html && git commit -m "Message"`     
![ALT HERE!](/images/pict_14.png "Git commit")

15. Sekarang git sudah mencatat beberap revisi yang sudah user lakukan. Bisa diibaratkan revisi-revisi ini sebagai checkpoint pada Game, ketika terjadi kesalahan bisa kembali ke checkpoint ini. Selanjutnya git juga sudah menyediakan perintah `$ git log` untuk melihat catatan log perubahan pada repository.
![ALT HERE!](/images/pict_16.png "Git log")

16. Atau bisa lebih dispesifikkan melihat log per file yang diubah dengan perintah `$ git log namafile`.    
![ALT HERE!](/images/pict_17.png "Git log")

17. Atau juga bisa melihat log berdasarkan author yang melakukan commit dengan perintah `$ git log --author=’namaauthor’`.    
![ALT HERE!](/images/pict_18.png "Git log")

#### - Medium
1. Selanjutnya adalah branching model, yang dimana tujuan penggunaan branch adalah untuk menghindari terjadi konflik ketika melakukan kolaborasi pada saat mengerjakan suatu proyek secara berkelompok.   
![ALT HERE!](/images/konflik-branch-repositori-git.png "Branching model")

2. Untuk membuat sebuah branch, gunakan bantuan perintah `$ git branch namabranch`.    
![ALT HERE!](/images/pict_37.png "Adding branch")

3. Kemudian untuk melihat daftar branch yang telah ada pada repository bisa menggunakan bantuan perintah `$ git branch`. Tanda bintang (\*) menandakan posisi branch saat ini.    
![ALT HERE!](/images/pict_38.png "Git branch")

4. Selanjutnya pindah ke branch yang telah dibuat tadi menggunakan bantuan perintah `$ git checkout namabranch`.   
![ALT HERE!](/images/pict_39.png "Git checkout")

5. Selanjutnya coba tambahkan file lalu dicommit.   
`$ touch register.html; git add register.html; git commit -m "Message"`    
![ALT HERE!](/images/pict_40.png "Git commit")

6. Selanjutnya coba pindah ke branch master lalu cek apakah file register.html ada atau tidak.   
`$ git checkout master && tree .`     
![ALT HERE!](/images/pict_41.png "Git checkout")

7. Kemudian coba kembali ke branch sebelumnya untuk mengecek apakah file register tadi ada atau tidak.    
`$ git checkout namabranch && tree .`    
![ALT HERE!](/images/pict_42.png "Git checkout")

8. Kemudian, untuk menggabungkan branch yang dibuat tadi dengan branch utama (master) gunakan bantuan perintah. `$ git merge namabranch.` tapi sebelumnya pinda dulu ke branch utama(master) `$ git checkout master`.    
![ALT HERE!](/images/pict_43.png "Git checkout")

9. Selanjutnya coba cek kembali apakah file yang di branch sebelumnya tadi sudah ada pada branch master.    
`$ tree .`   
![ALT HERE!](/images/pict_44.png "Git checkout")

10. Selanjutnya untuk branch yang sudah tidak digunakan lagi lebih baik dihapus sehingga repository terlihat lebih rapi. Untuk menghapus branch, gunakan bantuan perintah `$ git branch -d namabranch`    
![ALT HERE!](/images/pict_45.png "Git checkout")

11. And finally, the branch looks like this.   
![ALT HERE!](/images/penggabungan-cabang-git.png "Merge branch")

#### - Advance
1. Selanjutnya, pengerjaan proyek yang melakukan kolaborasi atau melibatkan orang lain tidak mungkin hanya akan menyimpan proyek pada repository lokal saja. Kemudian untuk mengabungkannya digunakan repository inti atau remote yang akan menyimpan semua source code atau proyek yang telah dikerjakan setiap orang.    
![ALT HERE!](/images/sistem-git.png "Git remote workflow")

2. Untuk penggunaan source code repository remote akan menggunakan bantuan Github, selanjutnya hal pertama yang perlu dilakukan untuk membuat repository remote adalah membuat repository pada akun github.    
![ALT HERE!](/images/pict_46.png "Create repository on Github")

3. Selanjutnya, create repository.    
![ALT HERE!](/images/pict_47.png "After created repository")

4. Kemudian untuk menghubungkan repository lokal dengan repository remote, terlebih dahulu harus ditambahkan remotenya dengan bantuan perintah `$ git remote add namaremote urlrepository`.    
![ALT HERE!](/images/pict_48.png "Add remote repository")

5. Selanjutnya cek remote apa saja yang tersedia untuk repository tersebut dengan bantuan perintah `$ git remote -v`.    
![ALT HERE!](/images/pict_49.png "Check remote option")

6. Kemudian untuk mencek namaremote bisa menggunakan bantuan perintah `$ git remote`.
![ALT HERE!](/images/pict_50.png "Check remote name")

7. Selanjutnya untuk mengirim atau menambahkan proyek yang ada pada repository lokal menuju repository remote menggunakan bantuan perintah `$ git push namaremote master`.   
![ALT HERE!](/images/pict_51.png "Push resource to remote repository")

8. Selanjutnya coba cek halaman github atau repository remote yang dibuat tadi, untuk memastikan apakah proyek yang ada pada repository lokal tadi sudah masuk ke repository remote.    
![ALT HERE!](/images/pict_52.png "Check remote repository")

9. Kemudian coba ubah sebuah file, kemudian lihat perubahannya dengan perintah `$ git diff`.     
![ALT HERE!](/images/pict_53.png "Edit register.html file")

10. Kemudian commit `$ git add namafile && git commit -m "Message"`, lalu setelah itu langsung dipush `$ git push namaremote master` saja ke repository remote.     
![ALT HERE!](/images/pict_54.png "Commit the file and then push")

11. Selanjutnya cek pada halaman github repository remote yang digunakan sebelumnya.     
![ALT HERE!](/images/git_1.png "Check remote repository")

12. Selanjutnya untuk mengambil perubahan atau source code dari repository remote. Saat bekerja dengan repository secara kolaborasi atau memiliki banyak kontributor, seharusnya terlebih dahulu mengambil perubahan yang ada pada repository remote sehingga tidak terjadi bentrokan pada repository remote/inti. Selanjutnya, untuk mengambil revisi juga terdapat 2 perintah yaitu, git fetch namaremote namabranch dan git pull namaremote namabranch. Dimana perintah git fetch hanya akan mengambil revisi(commit) saja dan tidak langsung melakukan penggabungan(merge) terhadap repository lokal. Sedangkan perintah git pull akan mengambil revisi(commit) dan langsung melakukan penggabungan(merge) terhadap repository lokal.     
![ALT HERE!](/images/git-fetch-pull.png "Git fetch and pull")

13. Selanjutnya, melakukan pengambilan revisi dengan perintah git fetch. Terlebih dahulu pergi ke halaman github, kemudian tambahkan file README.md melalui github.   
![ALT HERE!](/images/pict_55.png "Add a README.md file")

14. Kemudian isi bagian file README.md.    
![ALT HERE!](/images/pict_57.png "Add content to the file")

15. Setelah itu commit.   
![ALT HERE!](/images/pict_58.png "Commit")

16. Selanjutnya ambil revisi menggunkan bantuan perintah `$ git fetch namaremote master`.     
![ALT HERE!](/images/pict_59.png "Git fetch")

17. Selanjutnya coba cek log pada repository lokal menggunakan bantuan perintah `$ git log --oneline`.    
![ALT HERE!](/images/pict_60.png "Git log")

18. Ternyata commit yang dilakukan pada github sebelumnya belum terncatat pada log di repository lokal. Kemudian coba cek log pada repository remote menggunakan bantuan perintah `$ git log namaremote/master --oneline`.     
![ALT HERE!](/images/pict_61.png "Git log")

19. Kemudian bisa juga melakukan pengecekan menggunakan bantuan perintah `$ git diff master namaremote/master`.      
![ALT HERE!](/images/pict_62.png "Git log")

20. Lalu untuk menggabungkannya bisa menggunakan bantuan perintah `$ git merge master namaremote/master`.    
![ALT HERE!](/images/pict_63.png "Git merge")

21. Kemudian coba cek log repository lokal kembali untuk memastikan apakah telah terjadi perubahan, dengan bantuan perintah `$ git log --oneline`. Dan berhasil menggabungkan dan mengambil revisi menggunakan bantuan perintah git fetch.    
![ALT HERE!](/images/pict_64.png "Git log")

22. Selanjutnya mengambil revisi menggunakan bantuan perintah git pull. Hal pertama yang harus dilakukan adalah menambahkan file baru pada halaman repository remote github.     
![ALT HERE!](/images/pict_65.png "Add new file")

23. Kemudian buat nama dan isi dari file baru yang akan ditambahkan.    
![ALT HERE!](/images/pict_66.png "Add content to the file")

24. And then commit.   
![ALT HERE!](/images/pict_67.png "Commit")

25. Selanjutnya ambil perubahan yang ada pada repository remote menggunakan bantuan perintah `$ git pull namaremote master`.    
![ALT HERE!](/images/pict_68.png "Git pull")

26. Kemudian cek log dari repository lokal dengan bantuan perintah `$ git log --oneline`.     
![ALT HERE!](/images/pict_69.png "Git log")

27. Kemudian, git juga bisa mengcopy source code atau proyek yang ada pada repository remote ke lokal dengan menggunakan bantuan perintah `$ git clone url`.   
![ALT HERE!](/images/pict_70.png "Git clone")

28. Kemudian coba masuk kedalam directory hasil cloning repository remote. Dan kemudian cek remote apa saja yang diberikan `$ git remote -v`    
![ALT HERE!](/images/pict_71.png "Git remote")

29. Coba cek log dari repository lokal dengan bantuan perintah `$ git log --oneline`.
![ALT HERE!](/images/pict_72.png "Git log")

## Referensi
1. [Git documentation](https://git-scm.com/doc)
2. [Petanikode](https://www.petanikode.com/tutorial/git/)
3. 
