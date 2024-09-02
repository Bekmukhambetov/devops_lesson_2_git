# devops_lesson_2_git
Створення репозиторію та доступи:
● Створіть репозиторій, налаштуйте доступ за допомогою ssh.
Налаштовано доступ по SSH ключу
   ![image](https://github.com/user-attachments/assets/bf2d6125-5db2-489c-9136-5dd3b7b77bf5)

Репозиторій створював через WEB

Далі клонував в wsl через термінал в visual studio code.

git clone git@github.com:Bekmukhambetov/devops_lesson_2_git.git
![image](https://github.com/user-attachments/assets/ae72f96f-ce93-4807-b319-e80cfa83b478)
![image](https://github.com/user-attachments/assets/5f4593fc-2819-42aa-8d26-853c3e78e69d)

Створення завдання:
● Закиньте у “main/master” скрипти з попередніх завдань.
Створення файлу в локальному репозиторії
   
![image](https://github.com/user-attachments/assets/14d40709-1754-4df3-916f-3b03214a3f5c)
![image](https://github.com/user-attachments/assets/40e7063b-5d78-48a6-8821-4ff059878812)

Перший локальний коміт

![image](https://github.com/user-attachments/assets/67245bc1-8a0d-4363-85d1-a357362893b2)

Створення гілок:
● Створіть дві фіч-гілки: `feature-1` та `feature-2` з мастеру.
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git branch feature-1
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git branch feature-2


Розробка функціональності на feature-1:
● Розробіть окрему функціональність для кожної фічі на відповідних гілках.
● Це може бути довільний файл з вільним змістом.
Merge feature-1 у “main/master”:

bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git checkout feature-1 
Switched to branch 'feature-1'
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ touch feature.html
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ cat > feature.html 
 ![image](https://github.com/user-attachments/assets/6f2b7e38-a894-4e48-85a1-8f5873235912)
   
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git add feature.html 
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git commit -m "add file feature.html in branch feature-1"
[feature-1 fdd3023] add file feature.html in branch feature-1
 1 file changed, 13 insertions(+)
 create mode 100644 feature.html

● Залийте зміни з feature-1 у “main/master” за допомогою merge.
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git checkout main 
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git merge future-1
merge: future-1 - not something we can merge
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git branch
  feature-1
  feature-2
* main
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git merge feature-1
Updating 4d6172b..fdd3023
Fast-forward
 feature.html | 13 +++++++++++++
 1 file changed, 13 insertions(+)
 create mode 100644 feature.html


Розробка функціональності на `feature-2`:
● Внесіть зміни у тому ж рядку на гілці `feature-2`, де були зміни на гілці `feature-1`.

bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git checkout feature-2 
Switched to branch 'feature-1'
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ touch feature.html
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ cat > feature.html 
![image](https://github.com/user-attachments/assets/9eadcfce-2349-485e-9b03-bae47ac6f87c)

● Спробуйте злити `feature-2` з головною гілкою та розв'яжіть виниклі конфлікти, також
у вашій гілці в результаті має бути один коміт (git squash).

bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git add feature.html 
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git status 
On branch feature-2
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   feature.html

bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git commit -m "add file feature.html in branch feature-2"
[feature-2 31a06fd] add file feature.html in branch feature-2
 1 file changed, 14 insertions(+)
 create mode 100644 feature.html
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git checkout main 
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

● Спробуйте вирішити конфлікт декількома способами (як в IDE так і з консолі)
![image](https://github.com/user-attachments/assets/8ccf9503-eccf-481b-88fc-41a37fdf6935)

PR на `feature-1`:
● Внесіть нові зміни на гілці `feature-1` та спробуйте злити з головною гілкою шляхом Pull Request.

Злиття Pull Request:
● Перевірте, що у вас більше немає помилок у вашому Pull Request, та злийте його у головну гілку.

