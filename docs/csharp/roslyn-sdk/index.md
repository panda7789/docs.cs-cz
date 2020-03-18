---
title: Sada .NET Compiler Platform SDK (rozhraní Roslyn API)
description: Naučte se používat .NET Compiler Platform SDK (také volal Roslyn API) pochopit .NET kód, na mávat chyby a opravit tyto chyby.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: a1ceb1d11cf846e67be2c6558978e01133e591da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76742740"
---
# <a name="the-net-compiler-platform-sdk"></a>Sada SDK platformy kompilátoru ROZHRANÍ .NET

Kompilátory vytvořit podrobný model kódu aplikace, protože ověřují syntaxi a sémantiku tohoto kódu. Používají tento model k vytvoření spustitelného výstupu ze zdrojového kódu. Sada SDK platformy kompilátoru .NET poskytuje přístup k tomuto modelu. Stále více se spoléháme na funkce integrovaného vývojového prostředí (IDE), jako je IntelliSense, refaktoring, inteligentní přejmenování, "Najít všechny odkazy" a "Přejít na definici", abychom zvýšili naši produktivitu. Spoléháme se na nástroje pro analýzu kódu ke zlepšení kvality kódu a generátory kódu na pomoc při konstrukci aplikací. Jak tyto nástroje získat chytřejší, potřebují přístup k více a více modelu, který pouze kompilátory vytvořit při zpracování kódu aplikace. To je hlavní poslání roslynských API: otevření černých skříněk a umožnění nástrojům a koncovým uživatelům sdílet množství kompilátorů informací o našem kódu.
Místo toho, aby neprůhledné source-code-in a překladače kódu objektu, prostřednictvím Roslyn, kompilátory stanou platformy: API, které můžete použít pro úlohy související s kódem ve vašich nástrojích a aplikacích.

## <a name="net-compiler-platform-sdk-concepts"></a>Koncepty platformy s kompilátorem rozhraní .NET

Sada SDK platformy kompilátoru .NET výrazně snižuje bariéru vstupu pro vytváření nástrojů a aplikací zaměřených na kód. Vytváří mnoho příležitostí pro inovace v oblastech, jako je metaprogramování, generování kódu a transformace, interaktivní použití jazyka C# a Visual Basic a vkládání jazyka C# a Visual Basic v jazycích specifických pro doménu.

Sada SDK platformy kompilátoru .NET umožňuje vytvářet ***analyzátory*** a ***opravy kódu,*** které naleznou a opraví chyby v kódování. ***Analyzátory*** pochopit syntaxi a strukturu kódu a zjistit postupy, které by měly být opraveny. ***Opravy kódu*** poskytují jednu nebo více navrhovaných oprav pro řešení chyb kódování zjištěných analyzátory. Analyzátor a související opravy kódu jsou obvykle zabaleny společně v jednom projektu.

Analyzátory a opravy kódu používají statickou analýzu k pochopení kódu. Nespouštějí kód ani neposkytují další výhody testování. Mohou však poukázat na postupy, které často vedou k chybám, neopravitelný kód nebo porušení standardní pokyny.

Sada SDK platformy kompilátoru .NET poskytuje jednu sadu rozhraní API, která umožňují prozkoumat a pochopit základ kódu jazyka C# nebo Visual Basic. Vzhledem k tomu, že můžete použít tento jeden základ kódu, můžete snadněji psát analyzátory a opravy kódu využitím syntaktické a sémantické analýzy rozhraní API poskytované .NET Compiler Platform SDK. Osvobozeni od velkého úkolu replikace analýzy provedené kompilátorem, můžete se soustředit na cílenější úkol hledání a opravy běžných chyb kódování pro váš projekt nebo knihovnu.

Menší výhodou je, že analyzátory a opravy kódu jsou menší a při načtení v sadě Visual Studio používají mnohem méně paměti než v případě, že byste napsali vlastní základ kódu, abyste pochopili kód v projektu. Využitím stejné třídy používané kompilátora a Visual Studio, můžete vytvořit vlastní statické analytické nástroje. To znamená, že váš tým můžete použít analyzátory a opravy kódu bez znatelné dopad na výkon ide.

Existují tři hlavní scénáře pro psaní analyzátorů a opravy kódu:

1. [*Vynucení standardů kódování týmu*](#enforce-team-coding-standards)
1. [*Poskytnutí pokynů k balíčkům knihoven*](#provide-guidance-with-library-packages)
1. [*Poskytovat obecné pokyny*](#provide-general-guidance)

## <a name="enforce-team-coding-standards"></a>Vynucení standardů kódování týmu

Mnoho týmů má standardy kódování, které jsou vynuceny prostřednictvím revize kódu s ostatními členy týmu. Analyzátory a opravy kódu může tento proces mnohem efektivnější. Ke recenzím kódu dochází, když vývojář sdílí svou práci s ostatními v týmu. Vývojář bude mít investovali po celou dobu potřebnou k dokončení nové funkce před získáním nějaké připomínky. Týdny mohou ujít, zatímco vývojář posiluje návyky, které neodpovídají postupům týmu.

Analyzátory spustit jako vývojář píše kód. Vývojář získá okamžitou zpětnou vazbu, která doporučuje okamžité sledování pokynů. Vývojář vytváří návyky psát kompatibilní kód, jakmile začnou prototypování. Když je funkce připravena k přezkoumání, všechny standardní pokyny byly vynuceny.

Týmy můžou vytvářet analyzátory a opravy kódu, které hledají nejběžnější postupy, které porušují postupy kódování týmu. Ty mohou být nainstalovány na počítači každého vývojáře k vynucení standardů.

## <a name="provide-guidance-with-library-packages"></a>Poskytnutí pokynů k balíčkům knihoven

K dispozici je velké množství knihoven k dispozici pro vývojáře .NET na NuGet.
Některé z nich pocházejí od společnosti Microsoft, některé od společností třetích stran a jiné od členů komunity a dobrovolníků. Tyto knihovny získat více přijetí a vyšší recenze, když vývojáři mohou uspět s těmito knihovnami.

Kromě poskytnutí dokumentace můžete poskytnout analyzátory a opravy kódu, které vyhledává a opravují běžné nesprávné použití knihovny. Tyto okamžité opravy pomohou vývojářům uspět rychleji.

Můžete balíček analyzátory a opravy kódu s vaší knihovny na NuGet. V tomto scénáři každý vývojář, který nainstaluje balíček NuGet také nainstalovat balíček analyzátoru. Všichni vývojáři, kteří používají vaši knihovnu, okamžitě získají pokyny od vašeho týmu ve formě okamžité zpětné vazby o chybách a navrhovaných opravách.

## <a name="provide-general-guidance"></a>Poskytovat obecné pokyny

Komunita vývojářů .NET zjistila prostřednictvím vzorců zkušeností, které fungují dobře a vzory, kterým se nejlépe vyhnete. Několik členů komunity vytvořilo analyzátory, které vynucují tyto doporučené vzory. Jak se dozvídáme více, je zde vždy prostor pro nové nápady.

Tyto analyzátory lze nahrát na [tržiště Sady Visual Studio](https://marketplace.visualstudio.com/vs) a stáhnout vývojáři pomocí sady Visual Studio. Nováčci v jazyce a platformě se rychle učí přijímané postupy a stávají se produktivními dříve na své cestě .NET. Jak se tyto stále více široce používány, komunita přijímá tyto postupy.

## <a name="next-steps"></a>Další kroky

Sada SDK platformy kompilátoru .NET obsahuje nejnovější jazykové objektové modely pro generování kódu, analýzu a refaktoring. Tato část obsahuje koncepční přehled sady SDK platformy kompilátoru .NET. Další podrobnosti naleznete v rychlých startech, ukázkách a kurzech.

Další informace o konceptech v sada SDK platformy kompilátoru .NET naleznete v těchto pěti tématech:

- [Prozkoumání kódu pomocí vizualizéru syntaxe](syntax-visualizer.md)
- [Pochopení modelu rozhraní API kompilátoru](compiler-api-model.md)
- [Práce se syntaxí](work-with-syntax.md)
- [Práce se sémantikou](work-with-semantics.md)
- [Práce s pracovním prostorem](work-with-workspace.md)

Chcete-li začít, budete muset nainstalovat **sdk platformy kompilátoru .NET**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
