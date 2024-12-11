class: center, up

# Conceptes Avançats de Programació

![:scale 30%](figures/lambda.png)

**Jordi Delgado**, **Gerard Escudero**,

Departament de Ciències de la Computació (UPC)

![:scale 35%](figures/fib50anysUPC.png)

---

# Conceptes Avançats de Programació

**Llegiu la [guia docent](https://www.fib.upc.edu/ca/estudis/graus/grau-en-enginyeria-informatica/pla-destudis/assignatures/CAP)**

### Guió: <ins>Programació funcional</ins> (en Clojure)

* Tema 1: [**Clojure: Introducció**](t1.html)

* Tema 2: [**Funcions _first-class_**](t2.html)

* Tema 3: [**_Closures_ - Model d'entorns**](t3.html)

* Tema 4: [**Tècniques de programació amb funcions d'ordre superior**](t4.html)

* Tema 5: [**Immutabilitat d'Estructures de Dades**](t5.html)

* Tema 6: [**Seqüències _Lazy_**](t6.html)

* Tema 7: [**Macros**](t7.html)

A banda dels [exercicis de les sessions de laboratori](https://gebakx.github.io/cap) i els que hi ha a [les 
transparències de teoria](https://jdelgadopin.github.io/cap/#2), aquí teniu una
[**llista d'exercicis**](problemes.html) addicional.

Finalment: [**Consells generals per a la programació funcional en Clojure**](https://jdelgadopin.github.io/cap/#9)

---

# Conceptes Avançats de Programació

## Teoria:

**Classes magistrals** amb recolzament de transparències (pensades com a guió de la sessió, no com a apunts), basades en:

* **The Joy of Clojure - 2nd edition**, Fogus, Michael; Houser, Chris, Manning, 2014. ISBN: 9781617291418

* **Clojure Programming: Practical Lisp for the Java World**, Emerick, Chas; Carper, Brian; Grand, Christophe, O'Reilly Media, 2012. ISBN: 9781449394707

* **Mastering Clojure Macros: Write Cleaner, Faster, Smarter Code**, Jones, Colin, The Pragmatic Programmers, 2014. ISBN: 9781941222225. Capítols 1-4.

Aquests llibres _haurien_ d'estar a la biblioteca.

### Avaluació teoria: 

Examens parcial i final. **Nota de teoria**: .blue[MAX(final, (parcial + final)/2)]

---

# Conceptes Avançats de Programació

## Laboratori:

### Jutge -  [https://jutge.org](https://jutge.org)

- Cal que us registreu amb el vostre correu **@estudiantat.upc.edu**

- Apunteu-vos al curs **Problemes en Clojure**

### Sessions Laboratori - [gebakx.github.io/cap](https://gebakx.github.io/cap)

### Avaluació laboratori: 

Proposarem un exercici de dificultat mitjana per cada tema (excepte el primer), i caldrà que 
lliureu la solució de tots ells en grups de dos persones al Racó. 
Mirarem de fer públics els enunciats en finalitzar cada tema.

La mitjana de les notes dels projectes serà la nota del laboratori (serà una nota individual, malgrat les solucions dels projectes es facin en grup).

---

# Conceptes Avançats de Programació

## Avaluació total: 

.large[Sigui NT la nota de teoria, i NL la nota de laboratori]

## Nota CAP: &emsp; .red[(NT + NL) / 2 &emsp;&emsp; si &emsp; NT $\geq$ 3.5]
## Nota CAP: &emsp; .red[NT &emsp;&emsp;&emsp;&emsp;&emsp; si &emsp; NT $\lt$ 3.5]

---

# Conceptes Avançats de Programació

## CAP <ins>NO</ins> és un curs de Clojure

Clojure és un llenguatge de programació molt gran, adequat al _món
real_. 

Nosaltres triarem el **subconjunt que ens convingui**.

## Aspectes de Clojure que no veurem, o només per sobre:

* Namespaces
* Java interop
* Specs
* Concurrència/Multi-Threading: refs & STM, Agents
* Protocols i Datatypes: Interfaces, protocols, datatypes, records.
* Multimètodes
* Metadata
* ... i més coses

---

# Conceptes Avançats de Programació

## Treballar amb Clojure

* [the Clojure CLI](https://clojure.org/guides/install_clojure): És l'utilitat de línia de comandes per gestionar projectes en Clojure que farem servir a CAP.
  És una de les eines més utilitzades i _està instal·lada als laboratoris de la FIB_.

* També es fa servir molt una altra eina anomenada [leiningen](https://leiningen.org/). Quan busqueu informació
  _on-line_ sobre Clojure us la trobareu. La podeu fer servir també, si voleu.
  
## Editors

Qualsevol editor una mica actual té algún _plug-in_ o similar per poder editar Clojure amb comoditat. Per exemple:

* [Calva](https://calva.io/) per a [_Visual Studio Code_](https://vscodium.com/).

* [Cider](https://cider.mx/) per a [_Emacs_](https://www.gnu.org/software/emacs/).

---

# Conceptes Avançats de Programació

## Treballar amb Clojure

És habitual fer servir el **REPL** (_Read, Eval, Print Loop_) en treballar amb Clojure. Provem les
funcions que definim fent-ne prototipus i les testem. Accedirem al **REPL** via terminal o 
via editor/IDE. Sigui com sigui, nosaltres el farem servir molt.

.center[![:scale 90%](figures/Screenshot_2024-08-29_12-34-10.png)]

encara que en realitat el que fa és:

.center[![:scale 90%](figures/Screenshot_2024-08-29_12-34-42.png)]

.tiny[.red[Font]: _The Joy of Clojure_, p. 15]

---

# Conceptes Avançats de Programació

Consells generals per a la programació funcional en Clojure:

1. _Avoid direct recursion. The JVM can’t optimize recursive calls, and Clojure
programs that recurse will blow their stack._

2. _Use recur when you’re producing scalar values or small, fixed sequences. Clojure
will optimize calls that use an explicit recur._

3. _When producing large or variable-sized sequences, always be lazy. (Do not
recur.) Then, your callers can consume just the part of the sequence they actually
need._

4. _Be careful not to realize more of a lazy sequence than you need._

5. _Know the sequence library. You can often write code without using recur or the
lazy APIs at all._

6. _Subdivide. Divide even simple-seeming problems into smaller pieces, and you’ll
often find solutions in the sequence library that lead to more general, reusable
code._

.tiny[.red[Font]: _Programming Clojure, 3rd ed._, Alex Miller with Stuart Halloway and Aaron Bedra,
Pragmatic 2018, p. 85]
