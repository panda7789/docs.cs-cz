---
title: Prohlídka Průvodce C# – C#
description: Novinka v jazyce C#? Seznamte se se základy jazyka.
ms.date: 02/26/2020
ms.openlocfilehash: 7476356ceab39d5cccb6ccbeb991653f08a324ea
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141038"
---
# <a name="a-tour-of-the-c-language"></a>Prohlídka jazyka C#

C# (vyslovit "viz Sharp") je moderní, objektově orientovaný programovací jazyk, který je typově bezpečný. Jazyk C# má své kořeny v řadě jazyků C a bude okamžitě známý programátorům jazyka C, C++, Java a JavaScriptu.

Tato prohlídka poskytuje přehled hlavních součástí jazyka v C# 8 a starších verzích. Pokud chcete prozkoumat jazyk pomocí interaktivních příkladů, vyzkoušejte kurz [Úvod do C#](../tutorials/intro-to-csharp/index.md) .

C# je objektově orientovaný jazyk, ale jazyk C# dále zahrnuje podporu pro ***komponenty orientované na součásti*** . Moderní návrh softwaru se stále spoléhá na softwarové komponenty ve formě integrovaných a samoobslužných balíčků funkcí. Klíč k takovým součástem je, že prezentují programovací model s vlastnostmi, metodami a událostmi. Mají atributy, které poskytují deklarativní informace o komponentě. Obsahují svou vlastní dokumentaci. Jazyk c# poskytuje jazykové konstrukce pro podporu přímo těchto konceptů, což C# přirozený jazyk pro vytváření a používání softwarových komponent.

Několik funkcí C# pomáhá při konstrukci robustních a odolných aplikací. ***Uvolňování*** paměti automaticky uvolňuje paměť, kterou zabírá nedosažitelné nepoužívané objekty. ***Zpracování výjimek*** poskytuje strukturovaný a rozšiřitelný přístup k detekci a obnovení chyb. ***Typově bezpečný*** návrh tohoto jazyka znemožňuje čtení z neinicializovaných proměnných, pro indexaci polí nad rámec jejich hranic nebo pro provedení nezaškrtnutých přetypování typu.

Jazyk C# má ***sjednocený systém typů***. Všechny typy C#, včetně primitivních typů, `int` jako `double`jsou a, dědí z jednoho `object` kořenového typu. Všechny typy tedy sdílí sadu běžných operací a hodnoty libovolného typu mohou být uloženy, přepravovány a provozovány konzistentním způsobem. Jazyk C# kromě toho podporuje uživatelsky definované typy odkazů i typy hodnot, což umožňuje dynamické přidělování objektů a ukládání do online formátu prosté struktury.

Aby bylo zajištěno, že programy a knihovny v jazyce C# budou v průběhu času v souladu s kompatibilním způsobem, mnohem zdůraznění ***je v návrhu*** jazyka c#. Řada programovacích jazyků platíte jenom malým pozornostům tohoto problému. V důsledku toho programy napsané v těchto dalších jazycích jsou v případě, že jsou zavedeny novější verze závislých knihoven, často rozdělují, než je potřeba. Aspekty návrhu jazyka C#, které byly přímo ovlivněny aspekty správy verzí, zahrnují samostatné `virtual` a `override` modifikátory, pravidla pro řešení přetížení metod a podporu explicitních deklarací členů rozhraní.

V novějších verzích obsahuje jazyk C# další programovací paradigma. Jazyk C# obsahuje funkce, které podporují techniky funkčního programování, jako jsou lambda výrazy. Další nové funkce podporují oddělení dat a algoritmů, jako je porovnávání vzorů.

## <a name="hello-world"></a>Hello World

Program "Hello, World" se tradičně používá k zavedení programovacího jazyka. Tady je v jazyce C#:

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

Zdrojové soubory jazyka C# mají většinou příponu `.cs`souboru. Chcete-li vytvořit tento program, nejprve Stáhněte a nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download). Pak spusťte příkaz `dotnet new console -o hello` pro vytvoření nového programu a skriptu sestavení. Program a skript sestavení jsou v souborech `Program.cs` a `hello.csproj`v uvedeném pořadí. Aplikaci sestavíte a spustíte s `run` příkazy:

```dotnetcli
cd hello
dotnet run
```

Program vytvoří následující výstup:

```dotnetcli
Hello, World!
```

Program "Hello, World" začíná `using` direktivou, která odkazuje na `System` obor názvů. Obory názvů poskytují hierarchický způsob uspořádání programů a knihoven v jazyce C#. Obory názvů obsahují typy a jiné obory názvů, `System` například obor názvů obsahuje počet typů, jako je `Console` například třída odkazovaná v programu, a řadu dalších oborů názvů, například `IO` a. `Collections` `using` Direktiva, která odkazuje na daný obor názvů, umožňuje nekvalifikované použití typů, které jsou členy tohoto oboru názvů. Z důvodu `using` direktivy může program použít `Console.WriteLine` jako zkrácený pro. `System.Console.WriteLine`

`Hello` Třída deklarovaná programem "Hello, World" má jednoho člena, metodu s názvem `Main`. `Main` Metoda je deklarována se statickým modifikátorem. I když metody instance mohou odkazovat na konkrétní ohraničující objekt instance pomocí klíčového `this`slova, statické metody pracují bez odkazů na konkrétní objekt. Podle konvence, statická metoda s `Main` názvem slouží jako vstupní bod programu.

Výstup programu je vytvořen `WriteLine` metodou `Console` třídy v `System` oboru názvů. Tuto třídu poskytují standardní knihovny tříd, které jsou ve výchozím nastavení automaticky odkazovány kompilátorem.

## <a name="elements-of-the-c-language"></a>Prvky jazyka C#

Existuje spousta dalších informací o jazyce C#. Následující témata obsahují přehled prvků jazyka C#. Tato přehledy poskytují základní informace o všech prvcích jazyka a poskytují informace potřebné k podrobně hlubší:

- [Struktura programu](program-structure.md)
  - Naučte se klíčové organizační koncepty v jazyce C#: ***programy***, ***obory názvů***, ***typy***, ***členy***a ***sestavení***.
- [Typy a proměnné](types-and-variables.md)
  - Přečtěte si o ***typech hodnot***, ***odkazových typech***a ***proměnných*** v jazyce C#.
- [Výrazy](expressions.md)
  - ***Výrazy*** jsou vytvořené z ***operandů*** a ***operátorů***. Výrazy vytvoří hodnotu.
- [Příkazy](statements.md)
  - Pomocí ***příkazů*** můžete vyjádřit akce programu.
- [Třídy a objekty](classes-and-objects.md)
  - ***Třídy*** jsou základem typů jazyka C#. ***Objekty*** jsou instancemi třídy. Třídy jsou sestaveny pomocí ***členů***, které jsou také pokryty v tomto tématu.
- [Pole](arrays.md)
  - ***Pole*** je datová struktura, která obsahuje počet proměnných, které jsou dostupné prostřednictvím počítaných indexů.
- [Rozhraní](interfaces.md)
  - ***Rozhraní*** definuje kontrakt, který může být implementován pomocí tříd a struktur. Rozhraní může obsahovat metody, vlastnosti, události a indexery. Rozhraní neposkytuje implementace členů, které definuje – určuje pouze členy, které musí být poskytnuty třídami nebo strukturami, které implementují rozhraní.
- [Delegáty](delegates.md)
  - ***Typ delegáta*** představuje odkazy na metody s konkrétním seznamem parametrů a návratovým typem. Delegáti umožňují zacházet s metodami jako s entitami, které lze přiřadit proměnným a předávat jako parametry. Delegáti jsou podobní pojmu ukazatelů na funkce nalezené v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce jsou delegáti objektově orientované a typově bezpečné.
- [Atributy](attributes.md)
  - ***Atributy*** umožňují programům určit další deklarativní informace o typech, členech a jiných entitách.
  
> [!NOTE]
> Tyto články se vztahují na C# 7,0 a novější. Některé funkce nemusí být k dispozici v dřívějších verzích.

> [!div class="step-by-step"]
> [Další](program-structure.md)
