---
title: Prohlídka c# - Průvodce C#
description: Začínáte s C#? Naučte se základy jazyka.
ms.date: 02/26/2020
ms.openlocfilehash: bf5a200f2ee777698ae8564f348ffc117d9abab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79156841"
---
# <a name="a-tour-of-the-c-language"></a>Prohlídka jazyka C#

C# (vyslovuje se "Viz Sharp") je moderní, objektově orientovaný a typově bezpečný programovací jazyk. C# má své kořeny v rodině jazyků C a bude okamžitě známé c, c ++, java a java programátory.

Tato prohlídka poskytuje přehled hlavních součástí jazyka v jazyce C# 8 a starší. Pokud chcete prozkoumat jazyk prostřednictvím interaktivních příkladů, zkuste [úvod do c#](../tutorials/intro-to-csharp/index.md) kurzy.

C# je objektově orientovaný jazyk, ale C# dále zahrnuje podporu pro programování ***orientované na komponenty.*** Současný softwarový design se stále více spoléhá na softwarové komponenty ve formě samostatných a samopopisných balíčků funkčnosti. Klíčem k těmto součástem je, že představují programovací model s vlastnostmi, metodami a událostmi. Mají atributy, které poskytují deklarativní informace o součásti. Obsahují vlastní dokumentaci. C# poskytuje konstrukce jazyka pro přímou podporu těchto konceptů, což C# přirozený jazyk, ve kterém chcete vytvořit a používat softwarové součásti.

Několik C# funkce podpory při konstrukci robustní a trvanlivé aplikace. ***Uvolňování paměti*** automaticky uvolní paměť obsazenou nedostupnými nepoužívanými objekty. ***Zpracování výjimek*** poskytuje strukturovaný a rozšiřitelný přístup k detekci chyb a obnovení. ***Typově bezpečný*** návrh jazyka znemožňuje čtení z neinicializovaných proměnných, indexovat pole mimo jejich hranice nebo provádět nekontrolované přetypování typu.

C# má ***jednotný systém typů***. Všechny typy Jazyka C#, `int` včetně `double`primitivních typů, `object` jako jsou například a , dědí z jednoho kořenového typu. Proto všechny typy sdílejí sadu běžných operací a hodnoty libovolného typu mohou být uloženy, přepravovány a provozovány konzistentním způsobem. Kromě toho C# podporuje uživatelem definované typy odkazů a typy hodnot, což umožňuje dynamické přidělování objektů, jakož i in-line ukládání lehkých struktur.

Chcete-li zajistit, že c# programy a knihovny se mohou vyvíjet v průběhu času kompatibilním způsobem, velký důraz byl kladen na ***správu verzí*** v návrhu jazyka C#. Mnoho programovacích jazyků věnovat malou pozornost tomuto problému. V důsledku toho programy napsané v těchto jiných jazycích break častěji, než je nutné při zavedení novější verze závislých knihoven. Aspekty návrhu jazyka C#, které byly přímo ovlivněny aspekty správy verzí, zahrnují samostatné `virtual` a `override` modifikátory, pravidla pro řešení přetížení metody a podporu explicitních deklarací členů rozhraní.

V novějších verzích C# přijal a další paradigmata programování. C# obsahuje funkce, které podporují funkční programovací techniky, jako jsou výrazy lambda. Další nové funkce podporují oddělení dat a algoritmů, jako je porovnávání vzorů.

## <a name="hello-world"></a>Hello World

Program "Hello, World" se tradičně používá k zavedení programovacího jazyka. Tady je to v C#:

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

C# zdrojové soubory mají `.cs`obvykle příponu . Chcete-li vytvořit tento program, nejprve stáhněte a nainstalujte sadu [.NET Core SDK](https://dotnet.microsoft.com/download). Potom spusťte `dotnet new console -o hello` příkaz k vytvoření nového programu a skriptsestavení. Program a skript sestavení jsou `Program.cs` `hello.csproj`v souborech a , resp. Vytvoření a spuštění aplikace `run` pomocí příkazů:

```dotnetcli
cd hello
dotnet run
```

Program vytváří následující výstup:

```console
Hello, World!
```

Program "Hello, World" začíná `using` direktivou, která odkazuje na obor `System` názvů. Obory názvů poskytují hierarchické prostředky pro uspořádání programů a knihoven jazyka C#. Obory názvů obsahují typy a další `System` obory názvů – například obor `Console` názvů obsahuje řadu typů, například třídu uvedenou v programu, a řadu dalších oborů názvů, například `IO` a `Collections`. Direktiva, `using` která odkazuje na daný obor názvů, umožňuje nekvalifikované použití typů, které jsou členy tohoto oboru názvů. Z důvodu `using` směrnice, program `Console.WriteLine` lze použít `System.Console.WriteLine`jako zkratka pro .

Třída `Hello` deklarovaná programem "Hello, World" má `Main`jeden člen, metodu s názvem . Metoda `Main` je deklarována statickým modifikátorem. Zatímco metody instance mohou odkazovat na konkrétní `this`ohraničující instanci objektu pomocí klíčového slova , statické metody pracují bez odkazu na konkrétní objekt. Podle konvence statickou `Main` metodu s názvem slouží jako vstupní bod programu.

Výstup programu je vytvořen `WriteLine` metodou třídy `Console` v `System` oboru názvů. Tato třída je poskytována knihovnami standardnítřídy, které jsou ve výchozím nastavení automaticky odkazovány kompilátorem.

## <a name="elements-of-the-c-language"></a>Prvky jazyka C#

Je tu mnohem více se dozvědět o C #. Následující témata poskytují přehled prvků jazyka C#. Tyto přehledy poskytují základní informace o všech prvcích jazyka a poskytují informace potřebné k hlubšímu prosazení:

- [Struktura programu](program-structure.md)
  - Naučte se klíčové organizační koncepty v jazyce C#: ***programy***, ***obory názvů***, ***typy***, ***členy***a ***sestavení***.
- [Typy a proměnné](types-and-variables.md)
  - Další informace o ***typech hodnot***, ***typech odkazů***a ***proměnných*** v jazyce C#.
- [Výrazy](expressions.md)
  - ***Výrazy*** jsou vytvořeny z ***operandů*** a ***operátorů***. Výrazy vytvářejí hodnotu.
- [Příkazy](statements.md)
  - ***Příkazy*** slouží k vyjádření akcí programu.
- [Třídy a objekty](classes-and-objects.md)
  - ***Třídy*** jsou nejzákladnější c#'s typy. ***Objekty*** jsou instance třídy. Třídy jsou sestaveny pomocí ***členů***, které jsou také zahrnuty v tomto tématu.
- [Pole](arrays.md)
  - ***Pole*** je datová struktura, která obsahuje řadu proměnných, které jsou přístupné prostřednictvím vypočítaných indexů.
- [Rozhraní](interfaces.md)
  - ***Rozhraní*** definuje smlouvu, která může být implementována třídami a strukturami. Rozhraní může obsahovat metody, vlastnosti, události a indexery. Rozhraní neposkytuje implementace členů, které definuje – pouze určuje členy, které musí být dodány třídy nebo struktury, které implementují rozhraní.
- [Delegáty](delegates.md)
  - ***Typ delegáta*** představuje odkazy na metody s určitým seznamem parametrů a návratovým typem. Delegáti umožňují považovat metody za entity, které lze přiřadit proměnným a předat jako parametry. Delegáti jsou podobné konceptu ukazatelů funkce v některých jiných jazycích, ale na rozdíl od ukazatelů funkce jsou delegáti objektově orientovaní a typově bezpeční.
- [Atributy](attributes.md)
  - ***Atributy*** umožňují programům určit další deklarativní informace o typech, členech a dalších entitách.
  
> [!NOTE]
> Tyto články platí pro C# 7.0 a novější. Některé funkce nemusí být k dispozici v dřívějších verzích.

> [!div class="step-by-step"]
> [Další](program-structure.md)
