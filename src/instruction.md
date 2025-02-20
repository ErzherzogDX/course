# Инструкция по сдаче заданий

В рамках курса вам будут предложены домашние задания и практики. В большинстве случаев сдача происходит с помощью GitHub.Classroom.

Вам необходимо настроить взаимодействие с репозиторием через SSH-ключи [по инструкции от Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh). В дальнейшем **ВСЕ** ссылки на репозитории, в частности для клонирования, должны быть в формате ssh. В противном случае у вас сломается настройка репозитория.

## Настройка репозитория с заданием

* К каждому заданию будет приложена инвайт-ссылка на GitHub Classroom, после перехода по ней у вас создастся приватный репозиторий со стартовым кодом, тестами и конфигурациями. Склонируйте его и выполняйте задания в нём.
* После **первого** клона (вообще, а не на какой-то конкретной машине) нужно инициализировать ветки запуском соответствующего скрипта из корня репозитория:
  ```bash
  ./init-repo.sh
  ```
* При каждом **следующем** клоне вашего репозитория, если такие вдруг будут, необходимо добавлять базовый (из которого был создан ваш) в качестве upstream с помощью следующей команды: 
  ```bash
  git remote add upstream <link-to-base-repo>
  ```
  При инициализации репозитория этот шаг делает за вас `init-repo.sh`.
* После этого вы можете коммитить в любые ветки кроме `feedback`, которая будет соответствовать `upstream/master`

## Подтягивание новых тестов и других изменений

Иногда нам приходится править какие-то проблемы в конфигурациях или добавлять новые тесты. Чтобы обновлять репозитории и не ломать PR, пользуйтесь специальным скриптом. 

**ВНИМАНИЕ:** перед его работой вам необходимо либо закоммитить последние изменения, либо сохранить куда-то незакомиченные изменения, например, с помощью [git-stash](https://git-scm.com/docs/git-stash). 

Чтобы подтянуть сами изменения, достаточно выполнить следующую команду из корня репозитория:
```bash
./update-repo.sh
```

## Сдача

Для сдачи решения необходимо сделать следующее:
* Сделайте коммит(ы) с вашим решением. Проследите, чтобы в коммит попали только файлы с решением (при необходимости можете дополнять [.gitignore](https://git-scm.com/docs/gitignore)), а файлы с тестами **не изменились**.
* Перенести решение в ветку `master`, если не делали сразу всё в ней.
* Запушить `master` на удалённый репозиторий.
* Проверьте, что у вас обновлены тесты и конфигурации (можно просто запустить соответствующий скрипт).
* Создайте [Pull Request (PR)](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) `master -> feedback`, если у вас его ещё нет.
* Удостоверьтесь, что тесты в тестирующей системе прошли (в PR появится зелёная галочка, так же можно посмотреть подробности на вкладке "Checks").
* **ВНИМАНИЕ! НИ В КАКОЙ МОМЕНТ ВРЕМЕНИ НЕ НУЖНО МЁРЖИТЬ PR!**
* Пришлите с помощью формы заявку на проверку с ссылкой на этот PR. В случае первой сдачи выберите режим `сдача`, иначе - `правки`.
* Дождитесь проверки. Исправьте замечания и, если они есть, повторите процесс.

## Процесс проверки

* В процессе проверки преподаватель будет оставлять комментарии в вашем пулл-реквесте. Комментарии - это замечания, которые нужно исправлять.
* Некоторые комментарии могут быть помечены `[note]`, их исправление необязательно - чаще всего это предложения альтернативных решений, иногда выходящих за рамки курса.
* Закрывать ("resolve") комментарии может только преподаватель.
* На каждый оставленный комментарий **нужно ответить**: либо кратко написать, как поправили (если комментарий однозначно указывает, как решить проблему - достаточно "fixed"), либо, если вы считаете, что замечание некорректно и вам не нужно ничего исправлять, обосновать это в ответе.
* Задание считается полностью сделанным, только если не осталось ни одного неисправленного комментария кроме `[note]`.
* Не стоит посылать заявку на проверку правок до того, как вы исправили все замечания (или ответили на них).
* Любые коммиты, сделанные после посылки формы и до её проверки, делаются на ваш страх и риск, так как могут произойти уже после того, как преподаватель начал проверку.
