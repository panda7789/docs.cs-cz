---
title: .NET Compiler Platform SDK (rozhraní Roslyn API)
description: Zjistěte, jak pomocí sady SDK platformy kompilátoru .NET (také nazývané rozhraní Roslyn API) a pochopení kódu .NET, přímé chyby, opravte tyto chyby.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: ea733d4c5c54c18e510a028f3a724f89490db9dd
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185841"
---
# <a name="the-net-compiler-platform-sdk"></a>.NET Compiler Platform SDK

Kompilátory sestavení prováděcí model kódu aplikace, protože ověří syntaxi a sémantiku tohoto kódu. Tento model se použít k sestavení spustitelného ze zdrojového kódu. Sada SDK platformy kompilátoru .NET poskytuje přístup k tomuto modelu. Čím dál, spoléháme na funkce integrovaného vývojového prostředí (IDE), jako jsou IntelliSense, refaktoring, inteligentní přejmenování "Najít všechny odkazy" a "Přejít k definici" zvýšit naši produktivitu. Spoléháme na nástroji pro analýzu kódu pro zlepšení našeho kvalitu kódu a generátory kódu pro vytváření aplikací. Protože tyto nástroje získat inteligentnější, přistupují potřebovat více a více modelu, který pouze kompilátory vytvořit, protože budou zpracovávat kódu aplikace. To je zvlášť jádro Roslyn API: černé skříňky vám otevírají a povolení nástrojů a koncovým uživatelům sdílet v řadu informace kompilátory si našeho kódu.
Namísto neprůhledné zdrojového kódu – se změnami a objekt code-out překladatele, prostřednictvím Roslyn, kompilátory stát platformy: Rozhraní API, která můžete použít pro úlohy související s kódem v nástroje a aplikace.

## <a name="net-compiler-platform-sdk-concepts"></a>Koncepce sady SDK platformy kompilátoru .NET

Sada SDK platformy kompilátoru .NET výrazně snižuje překážku vstupu pro vytváření kódu, zaměřuje nástroje a aplikace. Vytvoří řadu příležitostí pro inovace v oblasti, jako je meta programování, generování kódu a transformace, interaktivní pomocí jazyků C# a VB a vkládání C# a VB v jazycích specifické domény.

Sada SDK platformy kompilátoru .NET umožňuje vytvářet ***analyzátory*** a ***opravy kódu*** , najít a opravit chyby kódování. ***Analyzátory*** pochopení syntaxe a struktura kódu a zjišťování postupy, které by měly být opraveny. ***Opravy kódu*** adresování programovacích chyb zjištěných aplikací analyzátory zadejte jeden nebo více návrhy jejich oprav. Obvykle analyzátor a přidružený kód opravy jsou umístěné společně v jednom projektu.

Analyzátory a opravy kódu pomocí statické analýzy můžete pochopit kód. Nevytvářejí spusťte kód ani další testování výhody. Můžete však zdůraznit postupy, které často způsobit chyby, neudržovatelnému kódu nebo standardní obecných zásad ověřování.

Sada SDK platformy kompilátoru .NET poskytuje jednu sadu rozhraní API, která vám umožní zkoumat a pochopit základ kódu C# nebo Visual Basic. Vzhledem k tomu můžete tuto jedinou kódovou základnou, můžete napsat analyzátory a opravy kódu snadněji díky využití syntaktická a sémantická analýza rozhraní API poskytovaných platformě kompilátoru .NET SDK. Uvolněna z velké úlohy replikace analýzy kompilátorem, můžete soustředit na více zaměřených úlohu Najít a opravit běžné chyby kódování projektu nebo knihovny.

Menší výhodou je, že analyzátory a opravy kódu jsou menší a použít mnohem méně paměti při načtení v sadě Visual Studio, než se bude Pokud jste napsali vlastní codebase porozumět kódu v projektu. S využitím stejné třídy používané kompilátorem a sady Visual Studio, můžete vytvořit své vlastní nástroje pro statickou analýzu. To znamená, že váš tým může použít analyzátory a opravy kódu bez znatelnému dopadu na výkon, rozhraní IDE.

Existují tři hlavní scénáře pro zápis analyzátory a opravy kódu:

1. [*Vynucovat standardy kódování týmu*](#enforce-team-coding-standards)
1. [*Poskytovat pokyny balíčků knihovny*](#provide-guidance-with-library-packages)
1. [*Obecné pokyny*](#provide-general-guidance)

## <a name="enforce-team-coding-standards"></a>Vynucovat standardy kódování týmu

Mnoho týmů mít kódování standardů, které se vynucují prostřednictvím revize kódu s ostatními členy týmu. Analyzátory a opravy kódu provést tento postup mnohem efektivnější. Když vývojář v týmu práci sdílí s ostatními probíhat revize kódu. Vývojář bude investovali všechny čas potřebný k dokončení novou funkci před získáním žádné komentáře. Týdny může jít zatímco vývojář posiluje návyky, které neodpovídají postupy týmu.

Analyzátory spustit jako vývojář píše kód. Vývojář získá okamžitou zpětnou vazbu, která vývojářům umožňuje následující pokyny okamžitě. Vývojář vytvoří návyky psát kód kompatibilní, jakmile začnou vytváření prototypů. Když tato funkce je připravený pro člověka ke kontrole, bylo vynuceno standardní doprovodné materiály.

Týmy mohou vytvářet analyzátory a opravy kódu. Tento vzhled pro nejběžnější postupy, které porušují tým postupy psaní kódu. Ty lze nainstalovat na počítači každý vývojář vynucovat standardy.

## <a name="provide-guidance-with-library-packages"></a>Poskytovat pokyny balíčků knihovny

Nejsou k dispozici pro vývojáře na platformě .NET na webu NuGet velkému množství knihoven.
Některé z těchto přijde od Microsoftu, některé z jiných společností a ostatními členy komunity a dobrovolníků. Tyto knihovny získat další přijetí a vyšší kontroly při vývojářů může uspět s těmito knihovnami.

Kromě toho, že dokumentace ke službě, můžete zadat analyzátory a opravy kódu, které najít a opravit běžné chybné použití knihovny. Tyto okamžité opravy se pomoci vývojářům při úspěšné rychleji.

Můžete zabalit analyzátory a opravy kódu ke knihovně na webu NuGet. V tomto scénáři se každý vývojář, který nainstaluje balíček NuGet také nainstalovat balíček analyzátor. Všichni vývojáři pomocí knihovny okamžitě získejte pokyny od vašeho týmu ve formě okamžitou zpětnou vazbu na chyby a navrhovaných oprav.

## <a name="provide-general-guidance"></a>Obecné pokyny

Komunita vývojářů .NET byly zjištěny prostřednictvím prostředí vzory, které fungují dobře a vzory, které jsou nejlépe vyhnout. Několik členů komunity vytvořili analyzátory, které vynucují tyto doporučené způsoby. Jak se Učíme informace, je vždy místo pro nové nápady.

Tyto analyzátory můžou být odeslán do [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) a stahují vývojářům používajícím Visual Studio. Nové uživatele na jazyk a platformu Seznamte se s postupy přijaté rychle a být tak produktivní dříve v cestě .NET. Podle těchto stane více široce využívají, komunity přijímá tyto postupy.

## <a name="next-steps"></a>Další kroky

Sada SDK platformy kompilátoru .NET obsahuje nejnovější objektové modely jazyka pro generování kódu, analýzy a refaktoringu. Tato část obsahuje přehled sady SDK platformy kompilátoru .NET. Další podrobnosti najdete v části šablony rychlý start, ukázek a kurzů.

Můžete další informace o konceptech v sadě SDK platformy kompilátoru .NET v těchto tématech pět:

- [Prozkoumání kódu pomocí vizualizéru syntaxe](syntax-visualizer.md)
- [Pochopení modelu rozhraní API kompilátoru](compiler-api-model.md)
- [Práce se syntaxí](work-with-syntax.md)
- [Práce se sémantikou](work-with-semantics.md)
- [Práce s pracovním prostorem](work-with-workspace.md)

Abyste mohli začít, budete muset nainstalovat **sada SDK platformy kompilátoru .NET**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
