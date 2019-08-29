---
title: Prohlídka C# – C# Průvodce
description: Začínáte C#? Seznamte se se základy jazyka.
ms.date: 04/05/2019
ms.custom: seoapril2019
ms.openlocfilehash: eaaa5a259f0776a2749ed899d0406aee041a8442
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105653"
---
# <a name="a-tour-of-the-c-language"></a>Prohlídka C# jazyka

C#(vyslovit "viz Sharp") je jednoduchý, moderní, objektově orientovaný programovací jazyk, který je typově bezpečný. C#má své kořeny v řadě jazyků C a bude se okamžitě seznámit s programátory jazyka C C++,, Java a JavaScriptu. Tato prohlídka poskytuje přehled o hlavních součástech jazyka. Pokud chcete prozkoumat jazyk pomocí interaktivních příkladů, vyzkoušejte naše [Úvod do C# ](../tutorials/intro-to-csharp/index.md) kurzů.

C#je objektově orientovaný jazyk, ale C# dále zahrnuje podporu pro programování ***orientované na komponenty*** . Moderní návrh softwaru se stále spoléhá na softwarové komponenty ve formě integrovaných a samoobslužných balíčků funkcí. Klíč k takovým součástem je, že prezentují programovací model s vlastnostmi, metodami a událostmi. mají atributy, které poskytují deklarativní informace o komponentě. a obsahují vlastní dokumentaci. C#poskytuje jazykové konstrukce pro podporu přímo těchto konceptů C# a vytváří tak velmi přirozený jazyk pro vytváření a používání softwarových komponent.

Několik C# funkcí pomáhá při konstrukci robustních a odolných aplikací: ***Uvolňování*** paměti automaticky uvolňuje paměť, kterou zabírá nedosažitelné nepoužívané objekty; ***zpracování výjimek*** poskytuje strukturovaný a rozšiřitelný přístup k detekci a obnovení chyb. a ***typově bezpečný*** návrh tohoto jazyka znemožňuje čtení z neinicializovaných proměnných, pro indexaci polí nad rámec jejich hranic nebo pro provedení nezaškrtnutých přetypování typu.

C#má ***jednotný systém typů***. Všechny C# typy, včetně primitivních typů `int` , jako jsou a `double`, dědí z jednoho `object` kořenového typu. Všechny typy tedy sdílí sadu běžných operací a hodnoty libovolného typu mohou být uloženy, přepravovány a provozovány konzistentním způsobem. Kromě toho C# podporuje uživatelsky definované typy odkazů i typy hodnot, což umožňuje dynamické přidělování objektů a také vložené úložiště lehkých struktur.

Aby bylo zajištěno, že se programy a knihovny můžou v průběhu času vyvíjejí kompatibilním způsobem, je mnohem zdůrazněno, že C# se v návrhu používá ***Správa verzí*** C#. Řada programovacích jazyků platíte jenom malým pozornostům tohoto problému. v důsledku toho jsou programy napsané v těchto jazycích častěji využívány, pokud jsou zavedeny novější verze závislých knihoven. C#Aspekty návrhu, které byly přímo ovlivněny aspekty správy verzí, zahrnují samostatné `virtual` a `override` modifikátory, pravidla pro řešení přetížení metod a podporu explicitních deklarací členů rozhraní.

## <a name="hello-world"></a>Hello World

Program "Hello, World" se tradičně používá k zavedení programovacího jazyka. Tady je C#:

[!code-csharp[Hello World](../../../samples/snippets/csharp/tour/hello/Program.cs#L1-L8)]

C#zdrojové soubory mají obvykle příponu `.cs`souboru. Za předpokladu, že je program "Hello, World" uložen `hello.cs`v souboru, program může být zkompilován pomocí příkazového řádku:

```console
csc hello.cs
```

který vytváří spustitelné sestavení s názvem Hello. exe. Výstup vytvořený touto aplikací při spuštění:

```console
Hello, World
```

> [!IMPORTANT]
> Příkaz `csc` se zkompiluje pro celou platformu a nemusí být k dispozici na všech platformách.

Program "Hello, World" začíná `using` direktivou, která odkazuje na `System` obor názvů. Obory názvů poskytují hierarchické prostředky pro C# uspořádání programů a knihoven. Obory názvů obsahují `System` typy a jiné obory názvů, například obor názvů obsahuje počet typů, jako je `Console` například třída odkazovaná v programu, a řadu `IO` dalších oborů názvů, například a `Collections`. `using` Direktiva, která odkazuje na daný obor názvů, umožňuje nekvalifikované použití typů, které jsou členy tohoto oboru názvů. Z `using` důvodu direktivy může program použít `Console.WriteLine` jako zkrácený pro `System.Console.WriteLine`.

Třída deklarovaná programem "Hello, World" má jednoho člena, metodu s názvem `Main`. `Hello` `Main` Metoda je deklarována se statickým modifikátorem. I když metody instance mohou odkazovat na konkrétní ohraničující objekt instance pomocí klíčového `this`slova, statické metody pracují bez odkazů na konkrétní objekt. Podle konvence, statická metoda s `Main` názvem slouží jako vstupní bod programu.

Výstup programu je vytvořen `WriteLine` metodou `Console` třídy v `System` oboru názvů. Tuto třídu poskytují standardní knihovny tříd, které jsou ve výchozím nastavení automaticky odkazovány kompilátorem.

Máte spoustu dalších informací o C#.  Následující témata obsahují přehled prvků C# jazyka. Tato přehledy poskytnou základní informace o všech prvcích jazyka a poskytují informace potřebné k podrobně hlouběji do prvků C# jazyka:

- [Struktura programu](program-structure.md)
  - Naučte se klíčové organizační koncepty v C# jazyce: ***programy***, ***obory názvů***, ***typy***, ***členy***a ***sestavení***.
- [Typy a proměnné](types-and-variables.md)
  - Přečtěte si o ***typech hodnot***, ***odkazových typech***a ***proměnných*** v C# jazyce.
- [Výrazy](expressions.md)
  - ***Výrazy*** jsou vytvořené z ***operandů*** a ***operátorů***. Výrazy vytvoří hodnotu.
- [Příkazy](statements.md)
  - Pomocí ***příkazů*** můžete vyjádřit akce programu.
- [Třídy a objekty](classes-and-objects.md)
  - ***Třídy*** jsou základem C#typů. ***Objekty*** jsou instancemi třídy. Třídy jsou sestaveny pomocí ***členů***, které jsou také pokryty v tomto tématu.
- [Struktury](structs.md)
  - ***Struktury*** jsou datové struktury, které jsou na rozdíl od tříd typy hodnot.
- [Pole](arrays.md)
  - ***Pole*** je datová struktura, která obsahuje počet proměnných, které jsou dostupné prostřednictvím počítaných indexů.
- [Rozhraní](interfaces.md)
  - ***Rozhraní*** definuje kontrakt, který může být implementován pomocí tříd a struktur. Rozhraní může obsahovat metody, vlastnosti, události a indexery. Rozhraní neposkytuje implementace členů, které definuje – určuje pouze členy, které musí být poskytnuty třídami nebo strukturami, které implementují rozhraní.
- [Výčty](enums.md)
  - ***Typ výčtu*** je jedinečný typ hodnoty se sadou pojmenovaných konstant.
- [Delegáti](delegates.md)
  - ***Typ delegáta*** představuje odkazy na metody s konkrétním seznamem parametrů a návratovým typem. Delegáti umožňují zacházet s metodami jako s entitami, které lze přiřadit proměnným a předávat jako parametry. Delegáti jsou podobní pojmu ukazatelů na funkce nalezené v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce jsou delegáti objektově orientované a typově bezpečné.
- [Atributy](attributes.md)
  - ***Atributy*** umožňují programům určit další deklarativní informace o typech, členech a jiných entitách.

> [!div class="step-by-step"]
> [Next](program-structure.md)
