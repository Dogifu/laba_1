## laba_1
1. Скачайте библиотеку "boost" с помощью утилиты wget. Адрес для скачивания
https://sourceforge.net/projects/boost/files/boost/1.78.0/boost_1_78_0.tar.gz.

``$ wget https://sourceforge.net/projects/boost/files/boost/1.78.0/boost_1_78_0.tar.gz``

2.Разархивируйте скаченный файл в директорию ~/boost_1_78_0
``$tar -xvf boost_1_78_0.tar.gz »``

3.Подсчитайте количество файлов в директории ~/boost_1_78_0 не включая вложенные директории
``$find ./boost_1_78_0 -maxdepth 1 -type f | wc -l ``

``>>13``

4.Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.
``$find ./boost_1_78_0 -type f | wc -l ``

``>>71039``

5.Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).

Заголовочные файлы

``$find boost_1_78_0 -type f -name '*.h' -o -name '*.hpp' | wc -l``

``>>16789``

cpp файлы
``$find boost_1_78_0 -type f -name '*.cpp' | wc -l``

``>>16267``

остальные файлы

``$find boost_1_78_0 -type f -a -not -name '*.h' -a -not -name '*.hpp' -a -not -name '*.cpp' | wc -l``

``>>37983``

6.Найдите полный пусть до файла any.hpp внутри библиотеки boost.

``$find `pwd`/boost_1_69_0/boost -name 'any.hpp'``

``>>home/maks/workspace/boost_1_78_0/boost/hana/any.hpp
/home/maks/workspace/boost_1_78_0/boost/hana/fwd/any.hpp
/home/maks/workspace/boost_1_78_0/boost/xpressive/detail/utility/any.hpp
/home/maks/workspace/boost_1_78_0/boost/any.hpp
/home/maks/workspace/boost_1_78_0/boost/type_erasure/any.hpp
/home/maks/workspace/boost_1_78_0/boost/spirit/home/support/algorithm/any.hpp
/home/maks/workspace/boost_1_78_0/boost/fusion/include/any.hpp
/home/maks/workspace/boost_1_78_0/boost/fusion/algorithm/query/detail/any.hpp
/home/maks/workspace/boost_1_78_0/boost/fusion/algorithm/query/any.hpp
/home/maks/workspace/boost_1_78_0/boost/geometry/geometries/adapted/detail/any.hpp
/home/maks/workspace/boost_1_78_0/boost/proto/detail/any.hpp``

7.Выведите в консоль все файлы, где упоминается последовательность.

``$grep -rlw "boost::asio" ``

``>>boost_1_78_0/tools/docca/include/docca/base-config.xsl
boost_1_78_0/doc/html/boost_asio/examples/cpp03_examples.html
boost_1_78_0/doc/html/boost_asio/examples/cpp11_examples.html
boost_1_78_0/doc/html/boost_asio/net_ts.html
boost_1_78_0/doc/html/boost_asio/std_executors.html
boost_1_78_0/doc/html/boost_asio/example/cpp03/windows/transmit_file.cpp
boost_1_78_0/doc/html/boost_asio/example/cpp03/spawn/parallel_grep.cpp``

``......``

``2071 total``

8.Скомпилируйте boost. 

``$ ./bootstrap.sh``

``$ ./b2``

9.Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.

``$ cp -r boost_1_69_0/libs ~/boost-libs``

10.Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.

``$ ls -l -R -S -h``

``total 680K``

11.Найдите топ10 самых "тяжёлых".

``$ ls -l -R -S | head -10``

``total 3900
-rw-rw-r— 1 maks maks 3295319 мар 23 23:21 Test10.txt
-rw-r--r— 1 maks maks 80088 дек 2 10:18 libraries.htm
-rw-r--r— 1 maks maks 13707 дек 2 09:45 maintainers.txt
drwxr-xr-x 6 maks maks 4096 дек 2 10:18 accumulators
drwxr-xr-x 8 maks maks 4096 дек 2 10:18 algorithm
drwxr-xr-x 5 maks maks 4096 дек 2 10:18 align
drwxr-xr-x 5 maks maks 4096 дек 2 10:18 any
drwxr-xr-x 5 maks maks 4096 дек 2 10:18 array``
