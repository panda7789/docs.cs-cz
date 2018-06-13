---
title: A prohlídka jazyka C# – průvodce v C#
description: Nové jazyka C#? Naučte se základy jazyka.
ms.date: 08/10/2016
ms.assetid: ebc727cd-8112-42e7-b59c-3c2873ad661c
ms.openlocfilehash: bdb8a84083b391c27d39f5c566a01b2db318123f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359004"
---
# <a name="a-tour-of-the-c-language"></a>Přehled používání jazyka C#  

C# (výrazný "v tématu Sharp") je jednoduché, moderní, objektově orientovaný a bezpečnost typů programovací jazyk. C# má jeho kořeny řady C jazyky a bude okamžitě známé pro programátory v jazyce C, C++, Java a JavaScript.

C# je jazyk objektově orientované, ale C# další zahrnuje podporu pro ***zaměřené na konkrétní součásti*** programování. Návrh moderní softwaru stále spoléhá na softwarové součásti ve formě balíčků nezávislý a popisující samy sebe funkcí. Klíč na tyto složky je nepředstavují programovací model s vlastností, metod a událostí; mají atributy, které obsahují deklarativní informace o komponentě; a jejich začlenit vlastní dokumentace. C# poskytuje jazyk vytvoří pro podporu přímo tyto koncepty provedení C# velmi přirozený jazyk, ve kterém se má vytvořit a používat softwarové součásti.

Několik funkcí jazyka C# pomáhají při vytváření žádostí o robustní a trvanlivé: ***uvolňování paměti*** automaticky získá paměti obsazena nedostupný nepoužívané objekty; ***výjimek*** poskytuje strukturovaných a rozšiřitelné přístup ke zjištění chyby a obnovení; a ***bezpečnost typů*** návrhu jazyka, který znemožňuje čtení z Neinicializovaný proměnné, do pole index mimo jejich rozsah nebo provést přetypování nezaškrtnuté typu.

C# má ***unified systém typů***. Všechny typy C#, včetně primitivní typy, jako například `int` a `double`, dědí jeden kořenový `object` typu. Proto všechny typy sdílejí sadu běžných operací a hodnoty libovolného typu lze uložené, přenášet a provozován konzistentním způsobem. Kromě toho C# podporuje uživatelem definované odkazové typy a typy hodnot, povolení dynamické přidělování objektů, a také v řádku úložiště lightweight struktury.

Aby se zajistilo, že programy C# a knihovny můžete vyvíjet časem kompatibilní způsobem, se nachází mnohem důraz na ***Správa verzí*** v C# pro návrh. Malé zaměřte v řadě programovacích jazyků pro tento problém, a v důsledku toho byly zavedeny programy vytvořené v těchto jazyků zalomení častěji, než nezbytné při novější verze knihoven závislé. Aspekty návrhu C# na, které byly přímo ovlivňován aspekty správy verzí jsou zvláštní `virtual` a `override` modifikátory, pravidla pro rozlišení přetížení metody a podpora pro deklarace členů explicitního rozhraní.

## <a name="hello-world"></a>Ahoj světe

Program "Hello, World" tradičně používá k zavedení programovací jazyk. Tady je v jazyce C#:

[!code-csharp[Hello World](../../../samples/snippets/csharp/tour/hello/Program.cs#L1-L8)]

Zdrojové soubory C# obvykle mají příponu souboru `.cs`. Za předpokladu, že program "Hello, World" je uložené v souboru `hello.cs`, program může být zkompilovány pomocí příkazového řádku:

```console
csc hello.cs
```

spustitelný soubor sestavení s názvem hello.exe produkuje. Výstup vyprodukované tuto aplikaci při spuštění je:

```console
Hello, World
```

> [!IMPORTANT]
> `csc` Příkaz zkompiluje pro úplné framework a nemusí být k dispozici na všech platformách.


Začíná programu "Hello, World" `using` direktiva, která odkazuje `System` oboru názvů. Obory názvů pro zajištění hierarchické uspořádání programy C# a knihovny. Obory názvů obsahují typy a jiných oborech názvů – například `System` obor názvů obsahuje několik typů, jako jsou například `Console` třídy, kterou se odkazuje v program a počet jiných oborech názvů, jako například `IO` a `Collections`. A `using` direktiva, která odkazuje na daném oboru názvů umožňuje nekvalifikované použít typy, které jsou členy této oboru názvů. Z důvodu `using` direktivy, můžete použít program `Console.WriteLine` jako sdružená `System.Console.WriteLine`.

`Hello` Třída deklarovaná programu "Hello, World" obsahuje jednoho člena, metodu s názvem `Main`. `Main` Metoda je deklarovaný s statický modifikátor. Během metody instance, můžete odkazovat konkrétní nadřazených instance objektu pomocí klíčového slova `this`, statické metody fungovat i bez odkaz na konkrétní objekt. Podle konvence statickou metodu s názvem `Main` slouží jako vstupní bod programu.

Výstup programu je produkovaný `WriteLine` metodu `Console` třídy v `System` oboru názvů. Tato třída poskytuje knihovny standardní tříd, které ve výchozím nastavení, se automaticky odkazuje kompilátoru.

Je mnohem víc další informace o C#.  Následující témata poskytují přehled elementy jazyka C#. Tyto přehledy bude obsahují základní informace o všech elementů jazyka a získáte informace potřebné k ponořte hlubší do elementy jazyka C#:

* [Struktura programu](program-structure.md)
    - Seznamte se se klíče organizace koncepty v jazyce C#: ***programy***, ***obory názvů***, ***typy***, ***členy***, a  ***sestavení***.
* [Typy a proměnné](types-and-variables.md)
    - Další informace o ***typů hodnot***, ***odkazové typy***, a ***proměnné*** v jazyce C#.
* [Výrazy](expressions.md)
    - ***Výrazy*** se vytvářejí na základě ***operandy*** a ***operátory***. Výrazy vytvořit hodnotu.
* [Příkazy](statements.md)
    - Používáte ***příkazy*** vyjádřit akce programu.
* [Třídy a objekty](classes-and-objects.md)
    - ***Třídy*** jsou nejvíce základní typy C# na. ***Objekty*** jsou instance třídy. Třídy jsou vytvořeny pomocí ***členy***, které jsou také zahrnuté v tomto tématu.
* [Struktury](structs.md)
    - ***Struktury*** jsou datové struktury, které na rozdíl od třídy, jsou typy hodnot.
* [Pole](arrays.md)
    - ***Pole*** je datová struktura, která obsahuje počet proměnných, které jsou přístupné prostřednictvím počítaný indexy.
* [Rozhraní](interfaces.md)
    - ***Rozhraní*** definuje kontrakt, který může být implementována třídy a struktury. Rozhraní může obsahovat metody, vlastnosti, události a indexery. Rozhraní neposkytuje implementace členů definuje – jenom určuje členů, které je nutné zadat třídy nebo struktury, které implementují rozhraní.
* [Výčty](enums.md)
    - ***Typ výčtu*** je typ odlišné hodnoty sadu pojmenované konstanty.
* [Delegáti](delegates.md)
    - A ***delegovat typ*** seznamu představuje odkazy na metody s konkrétní parametr a návratovým typem. Delegáti umožňují považovat za entit, které může být přiřazena k proměnné a předány jako parametry metody. Delegáti jsou podobná koncept ukazatelů na funkce najít v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce, jsou delegáti objektově orientované a bezpečnost typů.
* [Atributy](attributes.md)
    * ***Atributy*** povolit programy zadat další deklarativní informace o typech, členů a ostatní entity.

>[!div class="step-by-step"]
[Next](program-structure.md)
