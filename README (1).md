![image](https://github.com/user-attachments/assets/3d6f48fd-d20d-4a57-8b74-b182253162c0)

 Установливаем гостевые дополнения по инструкции: инструкция для VBoxGA.docx Далее выполняем команды `sudo yum install wget` и `sudo yum install curl`

![image](https://github.com/user-attachments/assets/4dd61da1-dc88-46ee-b2fc-34a1be39b030)

скачиваем репозиторий `sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo`

![image](https://github.com/user-attachments/assets/1b4df190-7d49-4a60-bed7-d8a71c9801d4)

устанавливаем docker `sudo yum install docker-ce docker-ce-cli containerd.io`

![image](https://github.com/user-attachments/assets/e4308b29-a2d9-468e-878b-6143a3590fa8)

разрешаем автозапуск `sudo systemctl enable docker --now`
![image](https://github.com/user-attachments/assets/cf08ac09-a654-4d93-871b-772da7e73eca)

Сохраняем номер версии докера в переменную comver `COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)`

![image](https://github.com/user-attachments/assets/b6419287-271a-44ae-96ca-92a827f86ed2)

Проверяем версию `docker -compose --version`

![image](https://github.com/user-attachments/assets/feb0f881-f53c-4d25-a264-4c775371ab6d)

Копируем репозиторий `git clone https://github.com/skl256/grafana_stack_for_docker.git`

![image](https://github.com/user-attachments/assets/55f706e9-876b-4b1e-82b3-ee386dcee5a5)

Переходим в папку `cd grafana_stack_for_docker`

![image](https://github.com/user-attachments/assets/b6d03c69-0f50-4857-a525-ea4c417d103f)

создаем новый дерикторий `sudo mkdir -p /mnt/common_volume/swarm/grafana/config`

![image](https://github.com/user-attachments/assets/0425cd25-1b1e-423e-a89d-9cb59bd743f9)

создаем новые директории для хранения данных Grafana и Prometheus `sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}`

![image](https://github.com/user-attachments/assets/9bbd5c20-d6bf-4b52-ad38-88dfb76602da)
![image](https://github.com/user-attachments/assets/a14e21bc-7962-4779-bc10-ae8deb9543b2)

создаём пустой файл с именем grafana.ini `touch /mnt/common_volume/grafana/grafana-config/grafana.ini`

![image](https://github.com/user-attachments/assets/1be5fdfd-8578-46a7-ad9f-c135ce7667d8)

Копируем файлы с одной папки в другую `cp config/* /mnt/common_volume/swarm/grafana/config/`

![image](https://github.com/user-attachments/assets/7d83a544-e2ac-42dc-a90a-d911e8727d30)

Переименовываем файл `mv grafana.yaml docker-compose.yaml`

![image](https://github.com/user-attachments/assets/dd60769c-6f89-4cda-b32e-6b52933c20e1)

 Поднимаем докер `sudo docker compose up -d`

![image](https://github.com/user-attachments/assets/ac319df7-0c78-43f6-87cd-7391b350d8fa)

Вносим изменения в файл `docker-compose.yaml` и `prometheus.yaml`
Командой `sudo vi docker-compose.yaml` и `sudo vi prometheus.yaml`

Потом переходим в по ссылке `localhost:3000`
Пользователь и пароль: admin. - Код графаны 1816. - Код прометеуса: http://prometheus:9090.

![image](https://github.com/user-attachments/assets/026019eb-3e13-4159-ab81-4ff5e349ed61)

Создаем  Dashboard

![image](https://github.com/user-attachments/assets/6e39af74-6451-4070-bf01-5a486653a9b3)
![image](https://github.com/user-attachments/assets/fc95a2b6-a3e7-4343-9d12-6760677c8ab1)
![image](https://github.com/user-attachments/assets/edec0823-adac-4c8c-ba3d-7ed460814493)
![image](https://github.com/user-attachments/assets/7837219e-804c-4d63-ac3c-6f63a7d55c1b)

Выбираем Prometheus

![image](https://github.com/user-attachments/assets/379cf068-d72b-448b-8682-71ae1acb1c53)

Вводим код прометеуса и меняем аутентификацию

![image](https://github.com/user-attachments/assets/9985264d-3c87-4096-80a2-aa9559739fcb)

Сохраняем все и возвращаемся на пару шагов назад
И выбираем import

![image](https://github.com/user-attachments/assets/4f924a61-bbbd-4b6a-9cad-850f222a2071)

Вводим код графаны

![image](https://github.com/user-attachments/assets/5499396d-bfe4-4feb-bfb8-755f04a2b967)

Нажимаем Load

![image](https://github.com/user-attachments/assets/94f72c4d-746f-4789-b31f-f3f2bbaeb085)

Вводим данные и нажимаем import
И смотрим результат

![image](https://github.com/user-attachments/assets/2eb6a235-013f-49a5-84de-0fbb2d558f2e)

Начинаем работу с викторией метрикс
Переходим на сайт localhost:8428

![image](https://github.com/user-attachments/assets/5ae09ae9-cc16-4d12-9472-ff01c03641e7)

Переходим на сайт localhost:9090

![image](https://github.com/user-attachments/assets/b624eba6-1fef-42b0-ba47-f8f00c636aad)

По предыдущей инструкции создаем вместо прометеуса викторию метрикс
И меняем код прометеуса на http://victoriametrics:8428

![image](https://github.com/user-attachments/assets/735edb21-3a0d-4756-a517-28a55d7702b6)

Возвращаемся назад и открываем викторию

![image](https://github.com/user-attachments/assets/fcfb4b5b-e8aa-4ee3-8b95-26df0c4d9a1c)


Вводим в терминал `echo -e "# TYPE light_metric1 gauge\nlight_metric1 0" | curl --data-binary @- http://localhost:8428/api/v1/import/prometheus`

![image](https://github.com/user-attachments/assets/e03d1d73-3ea7-4283-ab64-fbb0e0d5d0c3)

Возвращаемся на localhost:8428 и открываем ссылку `vmui`
Вставляем  `light_metric1` и нажимаем `execute query`

![image](https://github.com/user-attachments/assets/b8969b29-8843-4c7a-b6e7-cc6ef3826fee)
![image](https://github.com/user-attachments/assets/64b6e36e-7afd-4925-a2a9-8c94822d9cb8)

Возвращаемся в графану и вставляем в строку `light_metric1` 

![image](https://github.com/user-attachments/assets/2e51ff2f-87c0-44b6-b057-e92eb1681275)

















