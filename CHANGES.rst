================
Список изменений
================

Версия 0.1.1
============

**25.03.2020**

**Закончено документирование всех классов и основных методов!**

**Переломные изменения**

- Классы отметок "мне нравится" для альбомов, плейлистов и исполнителей обобщены. Теперь представлены одним классом.
    - Удаленные классы:
        - ``ArtistsLikes``.
        - ``AlbumsLikes``.
        - ``PlaylistsLikes``.
    - Новый класс: ``Like`` (поле ``type`` для определения содержимого).
- Изменено название пакета с ``status`` на ``account`` (`#195`_).
- Исправлено выбрасываемое исключение при таймауте:
    - Прошлое исключение: ``TimeoutError`` (built-in).
    - Новое исключение: ``TimedOut`` (``yandex_music.exceptions``).
- Удалены следующие файлы: ``requirements.txt``, ``requirements-dev.txt``, ``requirements-docs.txt``.

**Крупные изменения**

- Добавлено обнаружение новых полей с просьбой сообщить о них (`#216`_).
    - Добавлена проверка на неизвестные поля.
    - Добавлен вывод отладочной информации в виде warning'a.
    - Добавлен шаблон issue для отправки логов.
- Добавлено поле ``type`` для класса ``SearchResult`` для определения типа результата поиска по объекту.
- Добавлены настройки пользователя (`#195`_):
    - Добавлен класс ``UserSettings``.
    - Добавлен метод для получения своих настроек (``account_settings``).
    - Добавлен метод для получения настроек другого пользователя (``users_settings``).
    - Добавлен метод для изменения настроек (``account_settings_set``).
- Добавлен возможность получить похожие треки (`#197`_):
    - Добавлен класс ``TracksSimilar`` с полями трека и списка похожих треков.
    - Добавлен метод для получения похожих треков (``tracks_similar``).
- Добавлены шоты от Алисы (`#185`_):
    - Добавлен метод ``after_track`` в класс ``Client`` для получения контента для воспоризведения после трека (реклама, шот).
    - Добавлены методы для загрузки обложки и аудиоверсии шота.
    - Добавлены новые классы:
        - ``Shot``
        - ``ShotData``
        - ``ShotEvent``
        - ``ShotType``
- Добавлен метод для изменения видимости плейлиста (`#179`_).
- Добавлена поддержка Яндекс.Радио (`#20`_):
    - Исправлена отправка фидбека.
    - Написана инструкция по использованию (в доке к методу).
    - Добавлен аругмент для перехода по цепочке треков.
    - Добавлен метод для изменения настроек станции.

**Незначительные изменения и/или исправления**

- Убрано дублирование информации в документации (`#247`_).
- Добавленые новые поля в класс ``Track``: ``version``, ``remember_position`` (`#238`_).
- Добавлено исключение ``InvalidBitrate`` при попытке загрузить недопустимый трек по критериям (кодек, битрейт).
- Исправлено получение прямой ссылки на файл с кодеком AAC (`#237`_, `#25`_).
- Исправлено получение плейлиста с Алисой в лендинге (`#185`_).
- Исправлено название поля с ссылкой на источник в классе ``Description`` (с ``url`` на ``uri``).
- Исправлена десериализация несуществующего исполнителя.
- Добавлено поле ``version`` в класс ``Album`` (`#178`_).
- Поле ``picture`` класса ``Vinyl`` теперь опциональное.
- Поле ``week`` класса ``Ratings`` теперь опциональное.
- Поле ``product_id`` класса ``AutoRenewable`` теперь опциональное (`#182`_).
- Правки замечаний по codacy.

.. _`#216`: https://github.com/MarshalX/yandex-music-api/issues/216
.. _`#247`: https://github.com/MarshalX/yandex-music-api/issues/247
.. _`#237`: https://github.com/MarshalX/yandex-music-api/issues/237
.. _`#25`: https://github.com/MarshalX/yandex-music-api/issues/25
.. _`#238`: https://github.com/MarshalX/yandex-music-api/issues/238
.. _`#182`: https://github.com/MarshalX/yandex-music-api/issues/182
.. _`#195`: https://github.com/MarshalX/yandex-music-api/issues/195
.. _`#197`: https://github.com/MarshalX/yandex-music-api/issues/197
.. _`#20`: https://github.com/MarshalX/yandex-music-api/issues/20
.. _`#185`: https://github.com/MarshalX/yandex-music-api/issues/185
.. _`#179`: https://github.com/MarshalX/yandex-music-api/issues/179
.. _`#178`: https://github.com/MarshalX/yandex-music-api/issues/178

Версия 0.0.16
=============

**29.12.2019**

**Переломные изменения**

- Поле ``account`` переименовано в ``me`` и теперь содержит объект ``Status``, вместо ``Account`` (`#162`_).
- Убрано использование зарезервированных имён в аргументах конструкторов (теперь они с ``_`` на конце). Имена с нижними подчёркиваниями есть как при сериализации так и при десериализации (`#168`_).

**Крупные изменения**

- **Добавлены аннотации типов во всей библиотеке!**

**Незначительные изменения и/или исправления**

- Добавлен аргумент ``fetch_account_status`` для опциональности получения информации об аккаунте при инициализации клиента (`#162`_).
- Добавлены тесты c передачей пустого словаря в ``de_json`` и ``de_list`` (`#174`_).
- Использование ``ujson`` при наличии, обновлены зависимости (`#161`_).
- Добавлен в зависимости для разработки ``importlib_metadata`` для поддержки старых версий (в новой версии ``pytest`` его больше не используют, в угоду ``importlib.metadata`` `#pytest-5537`_)) (`#161`_).
- Добавлен в зависимости для разработки ``atomicwrites``, который используется ``pytest`` теперь только на ``Windows`` - `#pytest-6148`_ (`#161`_).
- Исправлен баг с передачей ``timeout`` аргумента в аргумент ``params`` в следующих методах: ``artists``, ``albums``, ``playlists_list`` (`#120`_).
- Исправлена иницилазиация клиента при помощи логина и пароля с использованием прокси (`#159`_).
- Исправлен баг в загрузке обложки альбома.

.. _`#162`: https://github.com/MarshalX/yandex-music-api/issues/162
.. _`#161`: https://github.com/MarshalX/yandex-music-api/issues/161
.. _`#159`: https://github.com/MarshalX/yandex-music-api/issues/159
.. _`#168`: https://github.com/MarshalX/yandex-music-api/issues/168
.. _`#120`: https://github.com/MarshalX/yandex-music-api/issues/120
.. _`#174`: https://github.com/MarshalX/yandex-music-api/issues/174
.. _`#pytest-5537`: https://github.com/pytest-dev/pytest/issues/5537
.. _`#pytest-6148`: https://github.com/pytest-dev/pytest/pull/6148

Версия 0.0.15
=============

**01.12.2019**

**Переломные изменения**

- У классов ``Artist``, ``Track`` и ``Playlist`` изменился перечень полей для генерации хеша.

**Крупные изменения**

- Добавлена возможность выполнять запросы через прокси-сервер для использовании библиотеки на зарубежных серверах (`#139`_).
    - Добавлен пример использования в ``README``.
- Добавлена обработка капчи при авторизации с возможностью использования callback-функции для её обработки (`#140`_):
    - Новые исключения:
        - Captcha:
            - CaptchaRequired.
            - CaptchaWrong.
    - Новые классы:
        - CaptchaResponse.
    - Новые примеры в ``README``:
        - Пример обработки с использованием callback-функции.
        - Пример полностью своей обработки капчи.
- Добавлена документация для класса ``Search`` (`#83`_).
- Добавлена возможность получения всех альбомов исполнителя (`#141`_):
    - Новые классы:
        - ArtistAlbums.
    - Новые методы:
        - ``artists_direct_albums`` у ``Client``.
        - ``get_albums`` у ``Artist``.
- Добавлена обработка несуществующего плейлиста (`#147`_):
    - Новые классы:
        - ``PlaylistAbsence``.

**Незначительные изменения и/или исправления**

- Исправлен баг с загрузкой файлов (`#149`_).
- Исправлен баг некорректной десериализации плейлиста при отсутствии прав на него (`#147`_).
- Исправлен баг неправильной десериализации треков и артистов у собственных загруженных файлов (`#154`_).

.. _`#139`: https://github.com/MarshalX/yandex-music-api/issues/139
.. _`#140`: https://github.com/MarshalX/yandex-music-api/issues/140
.. _`#83`: https://github.com/MarshalX/yandex-music-api/issues/83
.. _`#141`: https://github.com/MarshalX/yandex-music-api/issues/141
.. _`#149`: https://github.com/MarshalX/yandex-music-api/issues/149
.. _`#147`: https://github.com/MarshalX/yandex-music-api/issues/147
.. _`#154`: https://github.com/MarshalX/yandex-music-api/issues/154

Версия 0.0.14
=============

**10.11.2019**

**Переломные изменения**

- Практически у всех классов был обновлён список полей участвующих при сравнении объектов.
- Если в атрибутах для стравнения объектов присутствуют списки, то они будут преобразованы к frozenset.
- Убрано конвертирование даты из строки в объект. Теперь все даты представляны строками в ISO формате.
- Классы ``AlbumSearchResult``, ``ArtistSearchResult``, ``PlaylistSearchResult``, ``TrackSearchResult``, ``VideoSearchResult`` были объединены в один - ``SearchResult``.

**Крупные изменения**

- Добавлен метод получения треков исполнителя (`#123`_).
- Добавлены классы-обёртки над пагинацией (``Pager``) и списка треков артиста (``ArtistsTracks``).
- Добавлено **554** unit-теста для всех классов-обёрток над объектами API.
- Добавлен codecov и workflows для GitHub Actions.

.. _`#123`: https://github.com/MarshalX/yandex-music-api/pull/123

**Незначительные изменения и/или исправления**

- Поле ``cover_uri`` класса ``Album`` теперь опциональное.
- Поле ``region`` у класса ``Account`` теперь не обязательное.
- Исправлен баг в ``.to_dict()`` методе, связанный с десериализцией объектов списков и словарей.
- Исправлен баг в ``.to_dict()`` методе, связанный с не рекурсивной десериализацией.
- Исправлена десериализация ``similar_artists`` в ``BriefInfo``.
- Исправлен баг с десериализацией ``artist`` в классе ``ArtistEvent``.
- Исправлен баг десериализации списка альбомов и артистов у класса ``Track`` (`#122`_).
- Исправлена загрузка обложки у трека.
- Исправлены сравнения объектов.

.. _`#122`: https://github.com/MarshalX/yandex-music-api/pull/122
