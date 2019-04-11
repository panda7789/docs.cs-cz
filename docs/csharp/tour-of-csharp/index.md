---
title: Prohlídku C# - C# Průvodce
description: Teprve se C#? Naučte se základy jazyka.
ms.date: 04/05/2019
ms.custom: seoapril2019
ms.openlocfilehash: c3a117d660c02702e900b827c2eed9c6b56b5606
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481090"
---
# <a name="a-tour-of-the-c-language"></a>Připravuje C# jazyka

C# (čteno "v tématu Sharp") je jednoduchý, moderní, objektově orientované a bezpečnost typů programovací jazyk. C#má jeho kořeny řady jazyků C a bude okamžitě znát programátory C, C++, Javy a JavaScriptu. Tato ukázka poskytuje přehled o součástech jazyka. Pokud chcete prozkoumat jazyka pomocí interaktivního příklady, vyzkoušejte naše [Úvod do C# ](../tutorials/intro-to-csharp/index.md) kurzy.

C# je objektově orientovaný jazyk, ale jazyka C# dále zahrnuje podporu pro ***komponenty objektově orientovaný*** programování. Návrh moderní softwaru stále spoléhá na softwarové komponenty v podobě samostatné a popisující samy sebe balíčky funkcí. Klíčem k takové součásti je, že představují programovací model s vlastnosti, metody a události; mají atributy, které poskytují deklarativní informace o komponentě; a zahrnují vlastní dokumentace. C#poskytuje pro podporu těchto konceptů, což přímo vytvoří jazyk C# velmi přirozeného jazyka, ve kterém chcete vytvořit a používat softwarové součásti.

Několik C# funkce podpory ve vytváření robustních a odolných aplikací: ***Uvolňování paměti*** automaticky uvolní paměť obsazena nedostupný nepoužívaných objektů; ***zpracování výjimek*** přináší strukturovaných a rozšiřitelné přístup k detekce chyb a obnovení; a ***zajišťující bezpečnost typů*** návrh jazyka znemožňuje čtení z neinicializovaného proměnné k indexování pole, mimo jejich rozsah nebo k provádění zaškrtnuté políčko typu přetypování.

C# má ***unified systém typů***. Všechny typy C#, včetně primitivní typy, jako například `int` a `double`, dědit z jednoho kořene `object` typu. Proto sdílejí sadu běžných operací pro všechny typy a hodnoty libovolného typu lze ukládat, přenášet a provozován konzistentním způsobem. Kromě toho C# podporuje uživatelem definované referenční typy a typy hodnot, povolení dynamické přidělování objektů a úložiště v řádku zjednodušené struktur.

Chcete-li zajistit C# programů a knihoven můžete v průběhu času vyvíjejí kompatibilní způsobem, mnoho důraz na ***správy verzí*** v C#návrh. Mnoho programovacích jazyků věnovat trochu tento problém, a v důsledku toho jsou zavedeny programy napsané v těchto jazyků přerušení častěji, než pokud je novější verze závislé knihovny. Aspekty C#je návrh, který byly přímo ovlivňován aspekty správy verzí obsahovat samostatné `virtual` a `override` modifikátory, pravidla pro řešení přetížení metody a podpora deklarací členů explicitního rozhraní.

## <a name="hello-world"></a>Ahoj světe

Program "Hello, World" tradičně slouží k uvození programovací jazyk. Tady je v jazyce C#:

[!code-csharp[Hello World](../../../samples/snippets/csharp/tour/hello/Program.cs#L1-L8)]

Zdrojové soubory jazyka C# obvykle mají příponu `.cs`. Za předpokladu, že program "Hello, World" je uložen v souboru `hello.cs`, program může být zkompilovány pomocí příkazového řádku:

```console
csc hello.cs
```

produkuje spustitelného sestavení s názvem hello.exe. Výstup vytvořeného touto aplikací při spuštění je:

```console
Hello, World
```

> [!IMPORTANT]
> `csc` Příkaz kompiluje pro úplné rozhraní framework a možná není k dispozici na všech platformách.

Program "Hello, World" začíná `using` direktiva, která odkazuje `System` oboru názvů. Obory názvů umožňují hierarchické uspořádání programy jazyka C# a knihovny. Obory názvů obsahují typy a jiných oborech názvů – například `System` obor názvů obsahuje několik typů, například `Console` třída odkazovaná v programu a několik jiných oborech názvů, jako například `IO` a `Collections`. A `using` umožňuje direktiva, která odkazuje na daný obor názvů nekvalifikované použití typů, které jsou členy tohoto oboru názvů. Z důvodu `using` direktiv, můžete použít program `Console.WriteLine` jako zkratka pro `System.Console.WriteLine`.

`Hello` Třídy deklarované jako programem "Hello, World" obsahuje jeden člen metodu s názvem `Main`. `Main` Metoda je deklarována s modifikátorem statické. Zatímco instanční metody může odkazovat na konkrétní nadřazeného objektu instanci pomocí klíčového slova `this`, statické metody fungovat bez ohledu na konkrétní objekt. Podle konvence statickou metodu s názvem `Main` slouží jako vstupní bod programu.

Výstup programu je vytvořen `WriteLine` metodu `Console` třídy v `System` oboru názvů. Tato třída poskytuje standardní knihovny tříd rozhraní, které ve výchozím nastavení, je automaticky odkazován kompilátorem.

Další informace o mnohem víc C#.  V následujících tématech přehledu elementů C# jazyka. Tyto přehledy zadání základních informací o všechny prvky jazyka, který se vám poskytnou informace potřebné k Ponořte se hlouběji do prvků C# jazyka:

* [Struktura programu](program-structure.md)
  - Informace o klíčových konceptech organizace v C# jazyka: ***programy***, ***obory názvů***, ***typy***, ***členy***a ***sestavení***.
* [Typy a proměnné](types-and-variables.md)
  - Další informace o ***typů hodnot***, ***referenční typy***, a ***proměnné*** v C# jazyka.
* [Výrazy](expressions.md)
  - ***Výrazy*** se vytvářejí na základě ***operandy*** a ***operátory***. Výrazy výsledkem hodnota.
* [Příkazy](statements.md)
  - Použijete ***příkazy*** vyjádřit akce programu.
* [Třídy a objekty](classes-and-objects.md)
  - ***Třídy*** jsou nejvíce základní typy jazyka C#. ***Objekty*** jsou instancemi třídy. Třídy jsou sestaveny na základě ***členy***, které jsou také uvedené v tomto tématu.
* [Struktury](structs.md)
  - ***Struktury*** jsou datové struktury, které na rozdíl od tříd, jsou typy hodnot.
* [Pole](arrays.md)
  - ***Pole*** je datová struktura, která obsahuje několik proměnných, které jsou přístupné prostřednictvím vypočítané indexy.
* [Rozhraní](interfaces.md)
  - ***Rozhraní*** definuje kontrakt, který může být implementována třídy a struktury. Rozhraní může obsahovat metody, vlastnosti, události a indexery. Rozhraní neposkytuje implementace členů definuje – pouze Určuje členy, které je třeba dodat ze třídy nebo struktury, které implementují rozhraní.
* [Výčty](enums.md)
  - ***Typ výčtu*** je typ odlišné hodnoty se sadou pojmenovaných konstant.
* [Delegáty](delegates.md)
  - A ***typ delegáta*** seznamu představuje odkazy na metody pomocí konkrétních parametrů a návratový typ. Delegáty umožňují považovat za entity, které může být přiřazena k proměnné a předány jako parametry metod. Delegáti jsou podobný koncept ukazatelů na funkce v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce, Delegáti jsou objektově orientované a typově bezpečné.
* [Atributy](attributes.md)
  * ***Atributy*** programu povolit programy k určení dalších deklarativní informace o typy, členy a dalších entit.

> [!div class="step-by-step"]
> [Next](program-structure.md)
