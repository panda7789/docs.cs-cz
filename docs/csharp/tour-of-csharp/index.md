---
title: Prohlídka C# – C# Průvodce
description: Začínáte C#? Seznamte se se základy jazyka.
ms.date: 02/26/2020
ms.openlocfilehash: 69651d6233bfaf217366be3850f6b3d9c550d8e2
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159140"
---
# <a name="a-tour-of-the-c-language"></a>Prohlídka C# jazyka

C#(vyslovější "viz Sharp") je moderní, objektově orientovaný programovací jazyk, který je typově bezpečný. C#má své kořeny v řadě jazyků C a bude se okamžitě seznámit s programátory jazyka C C++,, Java a JavaScriptu.

Tato prohlídka poskytuje přehled hlavních součástí jazyka v C# 8 a starších verzích. Pokud chcete prozkoumat jazyk pomocí interaktivních příkladů, zkuste [Úvod do C# ](../tutorials/intro-to-csharp/index.md) kurzů.

C#je objektově orientovaný jazyk, ale C# dále zahrnuje podporu pro programování ***orientované na komponenty*** . Moderní návrh softwaru se stále spoléhá na softwarové komponenty ve formě integrovaných a samoobslužných balíčků funkcí. Klíč k takovým součástem je, že prezentují programovací model s vlastnostmi, metodami a událostmi. Mají atributy, které poskytují deklarativní informace o komponentě. Obsahují svou vlastní dokumentaci. C#poskytuje jazykové konstrukce pro podporu přímo těchto konceptů C# a vytváří přirozený jazyk pro vytváření a používání softwarových komponent.

Několik C# funkcí pomáhá při konstrukci robustních a odolných aplikací. ***Uvolňování*** paměti automaticky uvolňuje paměť, kterou zabírá nedosažitelné nepoužívané objekty. ***Zpracování výjimek*** poskytuje strukturovaný a rozšiřitelný přístup k detekci a obnovení chyb. ***Typově bezpečný*** návrh tohoto jazyka znemožňuje čtení z neinicializovaných proměnných, pro indexaci polí nad rámec jejich hranic nebo pro provedení nezaškrtnutých přetypování typu.

C#má ***jednotný systém typů***. Všechny C# typy, včetně primitivních typů, například `int` a `double`, dědí z jednoho kořenového typu `object`. Všechny typy tedy sdílí sadu běžných operací a hodnoty libovolného typu mohou být uloženy, přepravovány a provozovány konzistentním způsobem. Kromě toho C# podporuje uživatelsky definované typy odkazů i typy hodnot, což umožňuje dynamické přidělování objektů a také vložené úložiště lehkých struktur.

Aby bylo zajištěno, že se programy a knihovny můžou v průběhu času vyvíjejí kompatibilním způsobem, je mnohem zdůrazněno, že C# se v návrhu používá ***Správa verzí*** C#. Řada programovacích jazyků platíte jenom malým pozornostům tohoto problému. V důsledku toho programy napsané v těchto dalších jazycích jsou v případě, že jsou zavedeny novější verze závislých knihoven, často rozdělují, než je potřeba. C#Aspekty návrhu, které byly přímo ovlivněny aspekty správy verzí, zahrnují samostatné modifikátory `virtual` a `override`, pravidla pro řešení přetížení metod a podporu explicitních deklarací členů rozhraní.

V novějších verzích C# zahrnuje další programovací paradigma. C#obsahuje funkce, které podporují techniky funkčního programování, jako jsou lambda výrazy. Další nové funkce podporují oddělení dat a algoritmů, jako je porovnávání vzorů.

## <a name="hello-world"></a>Hello World

Program "Hello, World" se tradičně používá k zavedení programovacího jazyka. Tady je C#:

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

C#zdrojové soubory mají obvykle `.cs`příponu souboru. Chcete-li vytvořit tento program, nejprve Stáhněte a nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download). Pak spusťte příkaz `dotnet new console -o hello` pro vytvoření nového programu a skriptu sestavení. Program a skript sestavení jsou v souborech `Program.cs` a `hello.csproj`, v uvedeném pořadí. Aplikaci sestavíte a spustíte s příkazy `run`:

```console
cd hello
dotnet run
```

Program vytvoří následující výstup: 

```console
Hello, World!
```

Program "Hello, World" začíná pomocí direktivy `using`, která odkazuje na obor názvů `System`. Obory názvů poskytují hierarchické prostředky pro C# uspořádání programů a knihoven. Obory názvů obsahují typy a jiné obory názvů, například obor názvů `System` obsahuje několik typů, jako je `Console` třída odkazovaná v programu, a řadu dalších oborů názvů, jako je například `IO` a `Collections`. Direktiva `using`, která odkazuje na daný obor názvů, umožňuje nekvalifikované použití typů, které jsou členy tohoto oboru názvů. Z důvodu direktivy `using` může program používat `Console.WriteLine` jako zkratku pro `System.Console.WriteLine`.

Třída `Hello` deklarovaná programem "Hello, World" má jednoho člena, metodu s názvem `Main`. Metoda `Main` je deklarována se statickým modifikátorem. I když metody instance mohou odkazovat na konkrétní ohraničující objekt instance pomocí klíčového slova `this`, statické metody pracují bez odkazů na konkrétní objekt. Podle konvence statická metoda s názvem `Main` slouží jako vstupní bod programu.

Výstup programu je vytvořen metodou `WriteLine` `Console` třídy v oboru názvů `System`. Tuto třídu poskytují standardní knihovny tříd, které jsou ve výchozím nastavení automaticky odkazovány kompilátorem.

## <a name="elements-of-the-c-language"></a>Prvky C# jazyka

Máte spoustu dalších informací o C#. Následující témata obsahují přehled prvků C# jazyka. Tato přehledy poskytují základní informace o všech prvcích jazyka a poskytují informace potřebné k podrobně hlubší:

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
- [Pole](arrays.md)
  - ***Pole*** je datová struktura, která obsahuje počet proměnných, které jsou dostupné prostřednictvím počítaných indexů.
- [Rozhraní](interfaces.md)
  - ***Rozhraní*** definuje kontrakt, který může být implementován pomocí tříd a struktur. Rozhraní může obsahovat metody, vlastnosti, události a indexery. Rozhraní neposkytuje implementace členů, které definuje – určuje pouze členy, které musí být poskytnuty třídami nebo strukturami, které implementují rozhraní.
- [Delegáty](delegates.md)
  - ***Typ delegáta*** představuje odkazy na metody s konkrétním seznamem parametrů a návratovým typem. Delegáti umožňují zacházet s metodami jako s entitami, které lze přiřadit proměnným a předávat jako parametry. Delegáti jsou podobní pojmu ukazatelů na funkce nalezené v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce jsou delegáti objektově orientované a typově bezpečné.
- [Atributy](attributes.md)
  - ***Atributy*** umožňují programům určit další deklarativní informace o typech, členech a jiných entitách.
  
> [!NOTE]
> Tyto články se vztahují C# na 7,0 a novější verzi. Některé funkce nemusí být k dispozici v dřívějších verzích.

> [!div class="step-by-step"]
> [Next](program-structure.md)
