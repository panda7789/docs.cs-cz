---
title: C# výrazy - přehled používání jazyka C#
description: výrazy, operandy a operátory jsou stavební bloky jazyka C#
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 8fa1c5d0464644b26eb457bca8ecaf007c288f42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="expressions"></a>Výrazy

*Výrazy* se vytvářejí na základě *operandy* a *operátory*. Operátory výrazu znamenat operací, které chcete použít pro operandy. Příklady operátory `+`, `-`, `*`, `/`, a `new`. Příklady operandy: literály, pole, místní proměnné a výrazy.

Pokud některý výraz obsahuje více operátorů *přednost před* operátory ovládací prvky pořadí, ve kterém jsou jednotlivé operátory vyhodnocena. Například výraz `x + y * z` je vyhodnoceno jako `x + (y * z)` protože `*` operátor má vyšší prioritu než `+` operátor.

Když dojde k operand mezi dva operátory se stejnou prioritou, *asociativnost* operátory ovládací prvky pořadí, ve kterém jsou prováděny operace:

*   S výjimkou operátory přiřazení jsou všechny binární operátory *asociativní zleva*, což znamená, že operace se provádí zleva doprava. Například `x + y + z` je vyhodnoceno jako `(x + y) + z`.
*   Operátory přiřazení a podmíněný operátor (`?:`) jsou *zprava asociativní*, což znamená, že operací zprava doleva. Například `x = y = z` je vyhodnoceno jako `x = (y = z)`.

Přednost a asociativnost se dá řídit pomocí závorek. Například `x + y * z` nejprve vynásobí `y` podle `z` a pak přidává výsledek, který má `x`, ale `(x + y) * z` nejprve přidá `x` a `y` a potom vynásobí výsledek podle `z`.

Většina operátory mohou být *přetížený*. Přetížení operátoru umožňuje implementace uživatelem definovaný operátor zadat pro operace, kde jsou jedno nebo obě operandy typu uživatelem definované třídě nebo struktuře.

Následující možnost shrne operátory jazyka C# na, výpis kategorií operátor v pořadí podle priority od nejvyšší po nejnižší. Operátory ve stejné kategorii nemá přednost. V rámci každé kategorie je seznam výrazů v dané kategorii společně s popisem příslušného typu výraz.

* primární
    - `x.m`: Přístup ke členu
    - `x(...)`: Metoda a delegáta volání
    - `x[...]`: Pole a indexer přístup
    - `x++`: Přírůstek po
    - `x--`: Po snížení
    - `new T(...)`: Objekt a delegovat vytvoření
    - `new T(...){...}`: Vytvoření objektu pomocí inicializátoru
    - `new {...}`: Inicializátor anonymní objekt
    - `new T[...]`: Při vytváření pole
    - `typeof(T)`: Získat <xref:System.Type> objekt pro `T`
    - `checked(x)`: Výraz v kontextu zaškrtnuté vyhodnocení
    - `unchecked(x)`: Vyhodnocení výrazu v kontextu nezaškrtnuto
    - `default(T)`: Výchozí hodnota typu získat `T`
    - `delegate {...}`: Anonymní funkce (anonymní metoda)
* Unární
    - `+x`: Identity
    - `-x`: Negace
    - `!x`: Logická negace
    - `~x`: Bitovou negaci
    - `++x`: Přírůstek před
    - `--x`: Snížení před
    - `(T)x`: Explicitně převést `x` na typ `T`
    - `await x`: Asynchronně počkejte `x` k dokončení
* Multiplikativní
    - `x * y`: Násobení
    - `x / y`: Dělení
    - `x % y`: Zbývající
* Doplňkové
    - `x + y`: Zřetězení řetězců přidání, kombinace delegáta
    - `x – y`: Odčítání, odebrání delegáta
* Posunutí
    - `x << y`: Posunutí doleva
    - `x >> y`: Posunutí doprava
* Relační a typ testování
    - `x < y`: Menší než
    - `x > y`: Větší než
    - `x <= y`: Menší než nebo rovno
    - `x >= y`: Větší než nebo rovno
    - `x is T`: Návratový `true` Pokud `x` je `T`, `false` jinak
    - `x as T`: Návratový `x` zadán jako `T`, nebo `null` Pokud `x` není `T`
* Rovnost
    - `x == y`: Rovná
    - `x != y`: Není rovno
* Logický operátor AND
    - `x & y`: Celé číslo bitové a boolean logické a
* Logický operátor XOR
    - `x ^ y`: Bitové operace XOR celé číslo, logickou logické XOR
* Logický operátor OR
    - `x | y`: Celé číslo bitové nebo logická hodnota logické nebo
* Podmiňovací operátor AND
    - `x && y`: Vyhodnotí `y` pouze v případě `x` není `false`
* Podmiňovací operátor OR
    - `x || y`: Vyhodnotí `y` pouze v případě `x` není `true`
* Nulové sloučení
    - `x ?? y`: Vyhodnocen `y` Pokud `x` má hodnotu null, k `x` jinak
* Podmiňovací operátor
    - `x ? y : z`: Vyhodnotí `y` Pokud `x` je `true`, `z` Pokud `x` je `false`
* Přiřazení nebo anonymní funkce
    - `x = y`: Přiřazení
    - `x op= y`: Složené přiřazení; jsou podporované operátory
        - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
    - `(T x) => y`: Anonymní funkce (výrazu lambda)

>[!div class="step-by-step"]
[Předchozí](types-and-variables.md)
[další](statements.md)
