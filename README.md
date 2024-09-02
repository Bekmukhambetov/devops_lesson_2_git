# devops_lesson_2_git
_Створення репозиторію та доступи:_

**● Створіть репозиторій, налаштуйте доступ за допомогою ssh.**

Налаштовано доступ по SSH ключу
   ![image](https://github.com/user-attachments/assets/bf2d6125-5db2-489c-9136-5dd3b7b77bf5)

Репозиторій створював через WEB

Далі клонував в wsl через термінал в visual studio code.

git clone git@github.com:Bekmukhambetov/devops_lesson_2_git.git
![image](https://github.com/user-attachments/assets/ae72f96f-ce93-4807-b319-e80cfa83b478)
![image](https://github.com/user-attachments/assets/5f4593fc-2819-42aa-8d26-853c3e78e69d)

_Створення завдання:_

**● Закиньте у “main/master” скрипти з попередніх завдань.**
Створення файлу в локальному репозиторії
   
![image](https://github.com/user-attachments/assets/14d40709-1754-4df3-916f-3b03214a3f5c)
![image](https://github.com/user-attachments/assets/40e7063b-5d78-48a6-8821-4ff059878812)

Перший локальний коміт

![image](https://github.com/user-attachments/assets/67245bc1-8a0d-4363-85d1-a357362893b2)

_Створення гілок:_

**● Створіть дві фіч-гілки: `feature-1` та `feature-2` з мастеру.**
```
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git branch feature-1
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git branch feature-2
```
_Розробка функціональності на feature-1:_

**● Розробіть окрему функціональність для кожної фічі на відповідних гілках.
● Це може бути довільний файл з вільним змістом.**
Merge feature-1 у “main/master”:
```
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git checkout feature-1 
Switched to branch 'feature-1'
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ touch feature.html
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ cat > feature.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Demo</title>
</head>
<body>
    <div class="container">
        <h1>Feature1</h1>
        <button>Feature1</button>
    </div>
    <div class="container">
        <h1>Feature</h1>
        <button>Feature</button>
    </div>
</body>

bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git add feature.html 
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git commit -m "add file feature.html in branch feature-1"
[feature-1 fdd3023] add file feature.html in branch feature-1
 1 file changed, 13 insertions(+)
 create mode 100644 feature.html
 ```

**● Залийте зміни з feature-1 у “main/master” за допомогою merge.**
```
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git checkout main 
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
bekmukhambetov@ZenBook:/devops/devops_lesson_2_git$ git merge feature-1
Updating 4d6172b..fdd3023
Fast-forward
 feature.html | 17 +++++++++++++++++
 1 file changed, 17 insertions(+)
 create mode 100644 feature.html
```

_Розробка функціональності на `feature-2`:_

**● Внесіть зміни у тому ж рядку на гілці `feature-2`, де були зміни на гілці `feature-1`.**
```
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git checkout feature-2 
Switched to branch 'feature-1'
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ touch feature.html
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ cat > feature.html 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Demo</title>
</head>
<body>
    <div class="container">
        <h1>Feature2</h1>
        <button>Feature2</button>
    </div>
    <div class="container">
        <h1>Feature</h1>
        <button>Feature</button>
    </div>
</body>
```

**● Спробуйте злити `feature-2` з головною гілкою та розв'яжіть виниклі конфлікти, також
у вашій гілці в результаті має бути один коміт (git squash).**

_пропустив на даному єтапі зробити це завдання (git squash), тому роблю його вже з іншими комітами_ 
```
git rebase -i HEAD~7

```
![image](https://github.com/user-attachments/assets/f70d48fa-997d-4649-a893-cf0690d7fd3d)
![image](https://github.com/user-attachments/assets/7271ff38-33df-4b5b-9c21-c9915ffd571b)


```
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git add feature.html 
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git status 
On branch feature-2
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   feature.html
bekmukhambetov@ZenBook:/devops/devops_lesson_2_git$ git commit -m "add file feature.html in branch feature-2"
[feature-2 31a06fd] add file feature.html in branch feature-2
 1 file changed, 14 insertions(+)
 create mode 100644 feature.html
bekmukhambetov@ZenBook:/devops/devops_lesson_2_git$ git checkout main 
Switched to branch 'main'
Your branch and 'origin/main' have diverged,
and have 1 and 2 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git merge feature-2
Auto-merging feature.html
CONFLICT (add/add): Merge conflict in feature.html
Automatic merge failed; fix conflicts and then commit the result.
```
**● Спробуйте вирішити конфлікт декількома способами (як в IDE так і з консолі)**

_тут в мене якась дурня вийшла, тому що з першого разу не заскрінив і скрін нижче це вже результат другої зміни гілки feature-2 і другого merge_
![image](https://github.com/user-attachments/assets/8ccf9503-eccf-481b-88fc-41a37fdf6935)

PR на `feature-1`:
**● Внесіть нові зміни на гілці `feature-1` та спробуйте злити з головною гілкою шляхом Pull Request.**
```
bekmukhambetov@ZenBook:/devops/devops_lesson_2_git$ git checkout feature-1
Switched to branch 'feature-1'
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ cat > feature.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Demo</title>
</head>
<body>
    <div class="container">
        <h1>Pull-Requests</h1>
        <button>Pull-Requests</button>
    </div>
    <div class="container">
        <h1>Feature</h1>
        <button>Feature</button>
    </div>
</body>
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git add feature.html 
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git status 
On branch feature-1
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   feature.html
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git commit -m "change file feature.html"
[feature-1 bbf54dd] change file feature.html
 1 file changed, 3 insertions(+), 3 deletions(-)
bekmukhambetov@ZenBook:~/devops/devops_lesson_2_git$ git push origin feature-1
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 857 bytes | 857.00 KiB/s, done.
Total 6 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
remote: 
remote: Create a pull request for 'feature-1' on GitHub by visiting:
remote:      https://github.com/Bekmukhambetov/devops_lesson_2_git/pull/new/feature-1
remote: 
To github.com:Bekmukhambetov/devops_lesson_2_git.git
 * [new branch]      feature-1 -> feature-1
```
_Злиття Pull Request:_

**● Перевірте, що у вас більше немає помилок у вашому Pull Request, та злийте його у головну гілку.**

![image](https://github.com/user-attachments/assets/c724add9-cdda-4871-a1fd-ab6eabf9749b)
![image](https://github.com/user-attachments/assets/f1294f81-5288-4b4d-a3e9-4c24965d56b4)
![image](https://github.com/user-attachments/assets/5e17c4aa-2e00-4a1e-aa32-fa153917c5e4)
![image](https://github.com/user-attachments/assets/0358f306-98a2-43fe-9555-6cdb31d289ce)
![image](https://github.com/user-attachments/assets/cc9bb783-a4b5-407c-8941-199a8f916928)



