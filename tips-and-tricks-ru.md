## То, что, похоже, никто не знает о cjdns
### (даже те, кто его очень долго использовал)

#### В cjdns есть опция работы в фоновом режиме

```Bash
./cjdroute --nobg < /path/to/cjdroute.conf
```

#### Вам не нужно запускать cjdroute от имени суперпользователя (root)

Закомментируйте секцию _router.interface_ <!-- требуется исправление --> файла конфигурации, и можете запускать.
Теперь ваш узел будет перенаправлять и передавать траффик, но вы не сможете запустить сервисы.

Также, вы можете настроить туннельное устройство вручную. Это потребует прав суперпользователя, но, после настройки, вы сможете
запускать cjdroute от имени непривилегированного пользователя.

#### Стилизация конфигурационного файла с помощью JSHint/jsonlint

Этот маленький совет поможет стилизовать файл конфигурации (`cjdroute.conf`) перед запуском cjdns.

##### JSHint
Разрешает использование комментариев, просьба обратить внимание, на то, что JSHint рассчитан на JS, и может
не всегда отобраджать предупреждения или ошибки.
```Bash
jshint ./cjdroute.conf; if [[ $? == 0 ]]; then ./cjdroute < ./cjdroute.conf; fi
```

##### jsonlint
Комментарии и прочие функции JavaScript будут запрещены.
```Bash
jsonlint ./cjdroute.conf; if [[ $? == 0 ]]; then ./cjdroute < ./cjdroute.conf; fi
```
