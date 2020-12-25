# Набор плейбуков для добавления новых нод к существующему Патрони кластеру
# inventory file - hosts. В нем 2 группы хостов. [test_servers] Сущ ноды   [new_test] Те что раскатываем [DB_TEST:children] обе группы
# Порядок использования: Новые хосты добавить в [new_test] ВСЕ playbook-и запускаем по общей группе [DB_TEST], обновятся конфиги. Запускать можно много раз. Все идемподентно.
#
# Порядок запуска:
#
# ЗАПОЛНИТЬ /etc/hosts НА ВСЕХ НОДАХ КЛАСТЕРА
# 1) ansible-playbook -i hosts play_etc_hosts.yml
#
# РАСКАТАТЬ etcd и ПОДКЛЮЧИТЬ К КЛАСТЕРУ (Рестарт нод.На работу кластера не влияет)
# 2) ansible-playbook -i hosts play_etcd.yml
#
# РАСКАТАТЬ PG (тут рестарт кластера из-за pg_hba.conf последовательно через patronictl)
# 3) ansible-playbook -i hosts play_pg.yml
#
# РАСКАТАТЬ pg_bouncer
# 4) ansible-playbook -i hosts play_pgbouncer.yml
#
# РАСКАТАТЬ PATRONI (Тут только reload конфигов через patronictl)
# 5) ansible-playbook -i hosts play_patroni.yml
#
# РАСКАТАТЬ haproxy
# 6) ansible-playbook -i hosts play_haproxy.yml
######################
