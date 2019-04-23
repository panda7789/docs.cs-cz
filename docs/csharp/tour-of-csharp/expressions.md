---
title: C#Výrazy – připravuje C# jazyka
description: výrazy, operandy a operátory jsou stavební bloky C# jazyka
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 4ffe947a4cb8c36a5925a4b3846486e44a9d8ec4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480752"
---
# <a name="expressions"></a>Výrazy

*Výrazy* se vytvářejí na základě *operandy* a *operátory*. Operátory výrazu označují operace, které chcete použít pro operandy. Příklady operátorů `+`, `-`, `*`, `/`, a `new`. Příklady operandy: literály, pole, místní proměnné a výrazy.

Pokud výraz obsahuje více operátorů *prioritu* operátorů určuje pořadí, ve kterém jsou jednotlivé operátory vyhodnocovány. Například výraz `x + y * z` se vyhodnotí jako `x + (y * z)` protože `*` má vyšší prioritu než operátor `+` operátor.

Dojde-li operand mezi dva operátory se stejnou prioritou, *asociativita* operátorů určuje pořadí, ve kterém jsou operace prováděny:

* S výjimkou operátory přiřazení jsou všechny binární operátory *asociativní zleva*, což znamená, že operace se provádějí zleva doprava. Například `x + y + z` se vyhodnotí jako `(x + y) + z`.
* Operátory přiřazení a podmiňovací operátor (`?:`) jsou *asociativní zprava*, což znamená, že operace se provádějí zprava doleva. Například `x = y = z` se vyhodnotí jako `x = (y = z)`.

Přednost a asociativita operátorů lze ovládat pomocí závorek. Například `x + y * z` nejprve vynásobí `y` podle `z` a pak přidá výsledek, který má `x`, ale `(x + y) * z` nejprve přidá `x` a `y` a pak vynásobí výsledků `z`.

Většina operátory mohou být *přetížené*. Přetížení operátoru umožňuje uživatelem definovaný operátor implementace pro operace, kde jeden nebo oba operandy jsou třídy nebo struktury typu uživatelem definované.

Shrnuje následující C#pro operátory, výpis operátor kategorií v pořadí podle priority od nejvyšší k nejnižší. Operátory ve stejné kategorii mají stejnou prioritu. V rámci každé kategorie je seznamem výrazů v dané kategorii spolu s popis tohoto typu výrazu.

* Primární
  - `x.m`: Přístup ke členům
  - `x(...)`: Vyvolání metod a delegátů
  - `x[...]`: Přístup k poli a indexeru
  - `x++`: Postinkrementace
  - `x--`: Postdekrementace
  - `new T(...)`: Vytvoření objektu a delegátu
  - `new T(...){...}`: Vytvoření objektu s inicializátorem
  - `new {...}`:  Inicializátor anonymních objektů
  - `new T[...]`: Vytvoření pole
  - `typeof(T)`: Získat <xref:System.Type> objekt pro `T`
  - `checked(x)`: Vyhodnocení výrazu ve zkontrolovaném kontextu
  - `unchecked(x)`: Vyhodnocení výrazu v nezkontrolovaném kontextu
  - `default(T)`: Získat výchozí hodnotu typu `T`
  - `delegate {...}`: Anonymní funkce (anonymní metoda)
* Unární
  - `+x`: Identita
  - `-x`: Negace
  - `!x`: Logická negace
  - `~x`: Bitová negace.
  - `++x`: Preinkrementace
  - `--x`: Predekrementace
  - `(T)x`: Explicitně převést `x` na typ `T`
  - `await x`: Asynchronně počkejte `x` k dokončení
* Násobení
  - `x * y`: Násobení
  - `x / y`: Dělení
  - `x % y`: Zbytek
* Additive
  - `x + y`: Sčítání, řetězení řetězců, kombinování delegátů
  - `x – y`: Odčítání, odebrání delegátů
* SHIFT
  - `x << y`: Posun doleva
  - `x >> y`: Posun doprava
* Relační a typové zkoušky
  - `x < y`: Menší než
  - `x > y`: Větší než
  - `x <= y`: Menší nebo rovno
  - `x >= y`: Větší nebo rovno
  - `x is T`: Vrátí `true` Pokud `x` je `T`, `false` jinak
  - `x as T`: Vrátí `x` zadán jako `T`, nebo `null` Pokud `x` není `T`
* Rovnost
  - `x == y`: Rovno
  - `x != y`: Nerovná se
* Logický operátor AND
  - `x & y`: Celočíselné bitové a logických logický operátor AND
* Logický operátor XOR
  - `x ^ y`: Bitový operátor XOR celého čísla, logická hodnota operátoru XOR
* Logický operátor OR
  - `x | y`: Bitový operátor OR celého čísla, logická hodnota operátoru OR
* Podmiňovací operátor AND
  - `x && y`: Vyhodnotí `y` pouze tehdy, pokud `x` není `false`
* Podmiňovací operátor OR
  - `x || y`: Vyhodnotí `y` pouze tehdy, pokud `x` není `true`
* Nulové sloučení
  - `x ?? y`: Vyhodnotí jako `y` Pokud `x` má hodnotu null, `x` jinak
* Podmiňovací operátor
  - `x ? y : z`: Vyhodnotí `y` Pokud `x` je `true`, `z` Pokud `x` je `false`
* Přiřazení nebo anonymní funkce
  - `x = y`: Přiřazení
  - `x op= y`: Složené přiřazení. podporované operátory jsou
    - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
  - `(T x) => y`: Anonymní funkce (výraz lambda)

> [!div class="step-by-step"]
> [Předchozí](types-and-variables.md)
> [další](statements.md)
