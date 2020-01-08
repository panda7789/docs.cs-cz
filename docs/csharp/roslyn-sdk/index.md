---
title: Sada .NET Compiler Platform SDK (rozhraní Roslyn API)
description: Naučte se používat sadu SDK .NET Compiler Platform (označovanou také jako rozhraní API Roslyn), která vám pomůže pochopit kód .NET, odhalit chyby a opravit tyto chyby.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: 3a202d977237ce716e3f8c0cf906894efd02196d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346958"
---
# <a name="the-net-compiler-platform-sdk"></a>Sada .NET Compiler Platform SDK

Kompilátory sestaví podrobný model kódu aplikace při ověřování syntaxe a sémantiky daného kódu. Používají tento model k sestavení spustitelného výstupu ze zdrojového kódu. Sada .NET Compiler Platform SDK poskytuje přístup k tomuto modelu. Stále se spoléháme na funkce integrovaného vývojového prostředí (IDE), jako je IntelliSense, refaktoring, inteligentní přejmenování, hledání všech odkazů a přejít k definici, aby se zvýšila produktivita. Na nástrojích pro analýzu kódu spoléháme na vylepšení naší kvality kódu a generátory kódu pro pomoc při vytváření aplikací. Jak tyto nástroje získají inteligentnější, potřebují přístup k více a více modelům, které jsou vytvořeny pouze kompilátory při zpracování kódu aplikace. Toto je základní poslání rozhraní API Roslyn: otevření černých polí a povolení nástrojů a koncových uživatelů, aby mohli sdílet s širokou škálou informačních kompilátorů, které mají náš kód.
Namísto neprůhledných překladatelů zdrojového kódu a překladatelů objektů pomocí Roslyn se kompilátory stávají platformami: rozhraní API, které můžete použít pro úlohy související s kódem ve vašich nástrojích a aplikacích.

## <a name="net-compiler-platform-sdk-concepts"></a>Koncepty .NET Compiler Platform SDK

Sada .NET Compiler Platform SDK výrazně snižuje překážku pro vytvoření kódu zaměřeného na nástroje a aplikace. Vytváří mnoho příležitostí pro inovace v oblastech, jako jsou meta programování, generování kódu a transformace, interaktivní použití jazyků C# a Visual Basic a vkládání C# a Visual Basic v jazycích specifických pro doménu.

Sada .NET Compiler Platform SDK umožňuje sestavit ***analyzátory*** a ***opravy kódu*** , které hledají a opravují chyby kódování. ***Analyzátory*** rozumí syntaxi a struktury kódu a zjišťující postupy, které by měly být opraveny. ***Opravy kódu*** poskytují jednu nebo více navrhovaných oprav pro řešení chyb kódování zjištěných analyzátory. Analyzátor a související opravy kódu jsou obvykle zabaleny společně v jednom projektu.

Analyzátory a opravy kódu používají statickou analýzu pro pochopení kódu. Nespouštějí kód ani neposkytují žádné výhody testování. Můžou však Ukázat postupy, které často vedou k chybám, neudržovatelnému kódu nebo standardnímu ověření pokynů.

Sada .NET Compiler Platform SDK poskytuje jednu sadu rozhraní API, která vám umožní kontrolovat a pochopit základ kódu C# nebo Visual Basic. Vzhledem k tomu, že můžete použít tento jediný základ kódu, můžete snadněji psát analyzátory a opravy kódu pomocí rozhraní API pro syntaktickou a sémantickou analýzu poskytovanou sadou .NET Compiler Platform SDK. V rámci velkého úkolu replikace analýzy provedené kompilátorem se můžete soustředit na více zaměřenou úlohu hledání a opravování běžných chyb kódování pro váš projekt nebo knihovnu.

Menší výhodou je, že vaše analyzátory a opravy kódu jsou menší a při načítání do sady Visual Studio použít mnohem méně paměti, než kdyby jste napsali vlastní základ kódu pro pochopení kódu v projektu. Použitím stejných tříd, které jsou používány kompilátorem a aplikací Visual Studio, můžete vytvořit vlastní nástroje statické analýzy. To znamená, že váš tým může používat analyzátory a opravy kódu bez znatelného dopadu na výkon integrovaného vývojového prostředí.

Pro psaní analyzátorů a oprav kódu existují tři hlavní scénáře:

1. [*Vyhovět standardům pro tvorbu kódu týmu*](#enforce-team-coding-standards)
1. [*Poskytnutí pokynů pro balíčky knihoven*](#provide-guidance-with-library-packages)
1. [*Zadat obecné pokyny*](#provide-general-guidance)

## <a name="enforce-team-coding-standards"></a>Vyhovět standardům pro tvorbu kódu týmu

Mnoho týmů má standardy kódování, které jsou vynutily prostřednictvím revize kódu s ostatními členy týmu. Analyzátory a opravy kódu můžou tento proces mnohem efektivněji udělat. Revize kódu se vyskytují, když vývojář sdílí svou práci s ostatními v týmu. Před získáním jakýchkoli komentářů bude vývojář investovat celý čas potřebný k dokončení nové funkce. Týdny může docházet, zatímco vývojář posiluje zvyky, které neodpovídají zvyklostem týmu.

Analyzátory se spustí jako vývojář, který zapisuje kód. Vývojář získá okamžitou zpětnou vazbu, která okamžitě po vás vyzývá pokyny. Vývojář sestaví zvyklosti na zápis vyhovujícího kódu hned po zahájení vytváření prototypů. Když je funkce připravená na lidi ke kontrole, vynutily se všechny standardní doprovodné materiály.

Týmy mohou sestavovat analyzátory a opravy kódu, které hledají nejběžnější postupy, které porušují postupy programování v kódu. Je možné je nainstalovat na počítač pro každého vývojáře, aby se tyto standardy vynutily.

## <a name="provide-guidance-with-library-packages"></a>Poskytnutí pokynů pro balíčky knihoven

K dispozici je spousta knihoven pro vývojáře na platformě .NET v NuGet.
Některé z nich pocházejí od Microsoftu, od jiných výrobců a dalších od členů komunity a dobrovolníků. Tyto knihovny získají větší množství a vyšší kontrolu, když vývojáři můžou s těmito knihovnami úspěšně probíhat.

Kromě poskytování dokumentace můžete poskytovat analyzátory a opravy kódu, které hledají a opravují běžné nesprávné používání vaší knihovny. Tyto okamžité opravy pomůže vývojářům podařit se rychleji.

Analyzátory a opravy kódu můžete zabalit do knihovny na NuGetu. V takovém případě každý vývojář, který nainstaluje balíček NuGet, nainstaluje také balíček analyzátoru. Všichni vývojáři, kteří používají vaši knihovnu, budou okamžitě získávat pokyny od týmu ve formě okamžité zpětné vazby k chybám a navrhovaným opravám.

## <a name="provide-general-guidance"></a>Zadat obecné pokyny

Komunita vývojářů .NET zjistila prostřednictvím vzorů prostředí, které fungují dobře a vzorce, které se jim nejlépe vyloučí. Několik členů komunity vytvořil analyzátory, které tyto Doporučené vzory vynutily. Jak se dozvím víc, pro nové nápady je vždy místo pro nové myšlenky.

Tyto analyzátory je možné odeslat do [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) a stáhnout je vývojáři pomocí sady Visual Studio. Newcomers se na jazyk a platformu a Naučte se rychle přijmout postupy, které se v jejich cestě .NET stanou produktivní. Jak se tyto informace stanou široce používat, komunita tyto postupy přijme.

## <a name="next-steps"></a>Další kroky

Sada .NET Compiler Platform SDK obsahuje nejnovější jazykové modely pro generování kódu, analýzu a refaktoring. Tato část obsahuje koncepční přehled .NET Compiler Platform SDK. Další podrobnosti najdete v částech rychlé starty, ukázky a kurzy.

Další informace o konceptech v sadě .NET Compiler Platform SDK najdete v těchto pěti tématech:

- [Prozkoumání kódu pomocí vizualizéru syntaxe](syntax-visualizer.md)
- [Pochopení modelu rozhraní API kompilátoru](compiler-api-model.md)
- [Práce se syntaxí](work-with-syntax.md)
- [Práce se sémantikou](work-with-semantics.md)
- [Práce s pracovním prostorem](work-with-workspace.md)

Abyste mohli začít, musíte nainstalovat **sadu .NET Compiler Platform SDK**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
