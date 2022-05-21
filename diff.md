## git diff

Команда **git diff** используется для вычисления разницы между любыми двумя Git деревьями. Это может быть разница между вашей рабочей директорией и индексом (собственно git diff), разница между индексом и последним коммитом (git diff --staged), или между любыми двумя коммитами (git diff master branchB).

*Пример*
```hash = 
git diff 4612297 5e356cf - сравнение двух commit
git diff branch1 branch2 - сравнение двух веток
git diff branch1 branch2 ./myfile.cpp -сравнение файлов между двумя ветками
```
*Описание*

https://git-scm.com/docs/git-diff

***[<<на главную](./readme.md)***
