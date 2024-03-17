## Урок 6 Текстовый редактор vi.

Все задачи обязательны к выполнению (кроме заданий с "\*"). Пожалуйста, присылайте на проверку все задачи сразу.
**Пожалуйста, не прикладывайте никакие файлы, в том числе на Google Диск или Яндекс.Диск.**

Любые вопросы по решению задач задавайте в чате учебной группы.

---

## Цели задания:

- Освоить работу с текстовым редактором **vi** в Linux (Ubuntu) через терминал.

---

## Порядок выполнения работы

_1. Изучите теоретический материал._ <br/>
_2. Выполните задание._ <br/>
_3. Ответьте на контрольные вопросы._ <br/>

## Инструкция к заданию

### **Вариант 1**
1. Создайте файл, содержащий следующий текст. Сохраните его с именем `text1`.
```
function f=deb_1(x)
f1_x1 = x(1);
g_x2 = 1 + 9 * sum((x(2:$)-x(1)).^2) / (length(x) - 1);
h= 1 - sqrt(f1_x1 / g_x2);
f(1,1) = f1_x1;
f(1,2) = g_x2 * h;
endfunction
PopSize= 100;
Proba_cross = 0.5;
Proba_mut= 0.3;
NbGen= 4;
NbCouples= 110;
Log= %T;
nb_disp= 10; // Nb point to display from the optimal population
pressure= 0.1;
ga_params = init_param();
ga_params = add_param(ga_params,’dimension’,2);
ga_params = add_param(ga_params,’minbound’,zeros(2,1));
ga_params = add_param(ga_params,’maxbound’,ones(2,1));
[pop_opt, fobj_pop_opt, pop_init, fobj_pop_init] = optim_
moga(deb_1, PopSize,NbGen, Proba_mut, Proba_cross, Log,
ga_params)
```
2. С помощью команды поиска и замены измените имя переменной `h` на `step`. Сохраните результат в файле с именем `text2`.
3. Удалите из файла `text2` строку `// Nb point to display from the optimal population`. Сохраните результат в файле `text3`.
4. В файле `text3` после строки `PopSize = 100;` вставьте строку `//--`. Сохраните полученный результат в файле `text4`.
5. В файле `text4` удалите строки: 
```
ga_params = init_param();
ga_params = add_param(ga_params,’dimension’,2);
ga_params = add_param(ga_params,’minbound’,zeros(2,1));
ga_params = add_param(ga_params,’maxbound’,ones(2,1));
[pop_opt, fobj_pop_opt, pop_init, fobj_pop_init] = optim_
moga(deb_1, PopSize,NbGen, Proba_mut, Proba_cross, Log,
ga_params)
```
Сохраните результат в файле `text5`.

6. Продемонстрируйте файлы `text1 – text5` преподавателю.

### **Вариант 2**
1. Создайте файл, содержащий следующий текст. Сохраните его с именем `file1.txt`
```
function y=rastrigin(x)
y = x(1)^2+x(2)^2-cos(12*x(1))-cos(18*x(2));
endfunction
x0 = [2 2];
Proba_start = 0.7;
It_Pre= 100;
It_extern= 100;
It_intern = 1000;
x_test = neigh_func_default(x0);
T0 = compute_initial_temp(x0, rastrigin, Proba_start, It_Pre);
Log = %T;
[x_opt, f_opt, sa_mean_list, sa_var_list] = optim_sa(x0, rastrigin,
It_extern, It_intern, T0, Log);
mprintf(«optimal solution:\n»); disp(x_opt);
mprintf(«value of the objective function = %f\n», f_opt);
t = 1:length(sa_mean_list);
plot(t,sa_mean_list,»r»,t,sa_var_list,»g»);
```
2. С помощью команды поиска и замены измените имя переменной `Proba_start` на `start`. Сохраните результат в файле с именем `text2`.
3. Удалите из файла `text2` строку `Log = %T;`. Сохраните результат в файле `text3`.
4. В файле `text3` строк `It_Pre= 100;` перенесите после строк `It_intern = 1000;`. Сохраните полученный результат в файле `text4`.
5. В файле `text4` удалите строки:
```
mprintf(«optimal solution:\n»); disp(x_opt);
mprintf(«value of the objective function = %f\n», f_opt);
```
Сохраните результат в файле `text5`.

6. Продемонстрируйте файлы `text1 – text5` преподавателю.

### **Вариант 3**
1. Создайте файл, содержащий следующий текст. Сохраните его с именем `file1`.
```
// Construction of the sinusoid
w=%pi/4; // angular frequency
T=0.1; // period
t=0:T:500;
signal=cos(w*t);
// Sinusoid with noise
v=rand(t,»normal»);
y=signal+v;
// Plot the sinusoid with noise
subplot(2,1,1);
plot(t,y);
xtitle(«sinusoid with noise»,»t»);
// System
n=2; // system order
f=[cos(w*T) -sin(w*T); sin(w*T) cos(w*T)];
g=0;
h=[1 0];
p0=[1000 0; 0 0];
R=1;
Q=0;
x0=zeros(n,1);
// Initialize for loop
x1=x0;
p1=p0;
// Kalman filter
for i=1:length(t)-1
[x1(:,i+1),p1,x,p]=kalm(y(i),x1(:,i),p1,f,g,h,Q,R);
end
// Plot the results (in red) to compare with the sinusoid (in
green)
```
2. Удалите из файла все комментарии. Сохраните результат в файле с именем `file2`.
3. Поменяйте местами строки `w=%pi/4; // angular frequency` и `T=0.1; // period`. Сохраните результат в файле `file3`.
4. В файле `file3` замените строку `green` на строку `blue`. Сохраните результат в файле `file4`.
5. В файле `file3` удалите строки:
```
for i=1:length(t)-1
[x1(:,i+1),p1,x,p]=kalm(y(i),x1(:,i),p1,f,g,h,Q,R);
end
```
Сохраните результат в файле `file5`.

6. Продемонстрируйте файлы `text1 – text5` преподавателю.

## Контрольные вопросы

#### 1. Какие режимы существуют у редактора vi?
#### 2. Прокомментируйте диаграмму переключения режимов vi.
#### 3. Как получать помощь по использованию vi?
#### 4. Расскажите о командах позиционирования курсора и их использованию. Приведите примеры.
#### 5. Расскажите о командах вставки. Приведите примеры.
#### 6. Расскажите о командах изменения. Приведите примеры их использования.
#### 7. Расскажите о командах вырезания, вставки и удаления. Приведите примеры.
   
---

**В качестве результата пришлите проверяющему ссылку на ваш репозиторий на GitHub.**
