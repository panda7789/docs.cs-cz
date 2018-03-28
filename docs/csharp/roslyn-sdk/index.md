---
title: Kompilátoru platformy .NET SDK (Roslyn rozhraní API)
description: Naučte se používat sadu .NET SDK platformy kompilátoru (také nazývané Roslyn rozhraní API) a pochopit kód .NET, odhalit chyby, opravte tyto chyby.
keywords: roslyn, analyzátor kódu oprava
author: billwagner
ms.author: wiwagn
ms.date: 10/10/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: c627903743f8867e05bac9ce835659fc7270b94e
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="the-net-compiler-platform-sdk"></a>Kompilátoru platformy .NET SDK

Kompilátory sestavení podrobné model kódu aplikace podle jejich ověření syntaxe a sémantiku tento kód. Tento model používají k vytvoření spustitelného souboru výstup zdrojového kódu. Platforma kompilátoru .NET SDK poskytuje přístup k tomuto modelu. Stále, spoléháme na integrované vývojové prostředí (IDE) funkce, jako je technologie IntelliSense, refaktoring, inteligentního přejmenování "Najít všechny odkazy na" a "Přechod na definici" zvýšení naše produktivity. Spoléháme na nástrojů pro analýzu kódu ke zlepšení našeho kvality kódu a generátory kódu, které pomáhají při vytváření aplikace. Jak tyto nástroje lépe, třeba na další a další modelu, který pouze kompilátory vytvořit, protože budou zpracovávat kód aplikace přístup. To je zvláště jádra rozhraní API Roslyn: otevření až do černé polí a povolení nástrojů a koncovým uživatelům sdílet v rozsáhlých kompilátory informace mají o našem kódu.
Namísto neprůhledného zdrojového kódu- a objekt kódu překladatelé prostřednictvím Roslyn, kompilátory stát platformy: rozhraní API, které můžete použít pro úlohy související s kódem v nástrojů a aplikací.

## <a name="net-compiler-platform-sdk-concepts"></a>Koncepty SDK pro platformu .NET kompilátoru

.NET SDK platformy kompilátoru výrazně snižuje překážku vstupu pro vytváření kódu zaměřuje nástrojů a aplikací. Vytvoří mnoho příležitosti pro inovace v oblastech, jako např. meta-programovací generování kódu a transformace, interaktivní použít jazyky C# a VB a vložení jazyka C# a VB v jazycích konkrétní domény.

Platforma kompilátoru .NET SDK umožňuje vytvářet ***analyzátorů*** a ***code opravy*** , najít a opravit chyby kódování. ***Analyzátory*** pochopit syntaxe a struktury kódu a zjistit postupy, které by měly být opraveny. ***Kód opravy*** zadejte jednu nebo více oprav navržené pro adresování kódování chyby nalezené pomocí analyzátorů. Obvykle analyzátoru a opravy přidružený kód spojených společně v jednom projektu. 

Analyzátory a opravy kódu slouží k pochopení kódu statických analýzy. Není spustit kód nebo další testování výhody. Mohou, ale upozorňovat na postupy, které často vést k ověření standardní platí, unmaintanable kódu nebo chyby.

Sada SDK kompilátoru platformu .NET poskytuje jednu sadu rozhraní API, která vám umožní zkoumat a pochopit codebase C# nebo Visual Basic. Vzhledem k tomu, že budete moci použít tento jeden základu kódu, můžete napsat analyzátorů a kód opravy snadněji s využitím analýzy syntaktické a sémantické rozhraní API poskytovaných platformy kompilátoru .NET SDK. Vydání z velké úlohy replikace anaysis provádí kompilátor, můžete soustředit na úlohu přesněji zaměřené hledání a odstraňování běžných chyb kódování pro váš projekt nebo knihovny.

Menší výhodou je, že analyzátory a opravy kódu jsou menší a použít mnohem méně paměti při načítání v sadě Visual Studio, než se by pokud jste napsali vlastní kód pochopit kódu v projektu. S využitím stejné třídy používané kompilátoru a Visual Studio, můžete vytvořit vlastní statické analytických nástrojů. To znamená, že váš tým můžete použít analyzátorů a kód opravy bez znatelný dopad na výkon rozhraní IDE.

Existují tři hlavní scénáře pro zápis analyzátory a opravy kódu:

1. [*Vynutit team kódování standardy*](#enforce-team-coding-standards)
1. [*Poskytovat pokyny balíčky knihovny*](#provide-guidance-with-library-packages)
1. [*Zadejte obecné pokyny pro kódování*](#provide-general-coding-guidance)

## <a name="enforce-team-coding-standards"></a>Vynutit team kódování standardy

Mnoho týmy mají kódování standardů, které se vynucují prostřednictvím kódu recenze s jinými členy týmu. Analyzátory a opravy kódu může být tento proces mnohem efektivnější. Kód recenze dojít v případě, že vývojář sdílí svou práci s ostatními uživateli v týmu. Mu bude investovaly všechny čas potřebný k dokončení novou funkci před získáním jakékoli komentáře. Týdny může přejít při mu posiluje návyky, které se neshodují. tým služby postupy.

Analyzátory spustit jako vývojář zapíše kódu. Získá mu okamžitou zpětnou vazbu, která podporuje následující pokyny okamžitě. Si vytvoří zvyklosti napsat kód, kompatibilní ihned zahájí při vytváření prototypu. Když tato funkce je připraven pro člověka ke kontrole, bylo vynuceno standardní pokyny.

Týmy můžete vytvořit analyzátorů a kód opravy podívejte se na tomto nejběžnější postupy, které porušují team kódování postupy. Ty lze nainstalovat na každý vývojář počítače k vynucení standardy.

## <a name="provide-guidance-with-library-packages"></a>Poskytovat pokyny balíčky knihovny

Nejsou k dispozici pro vývojáře .NET na NuGet širokou řadu knihovny.
Některé z těchto přijde od Microsoftu, některé z jiných společností a ostatními členy komunity a dobrovolníků. Tyto knihovny získat další přijetí a vyšší recenze, když vývojáři může uspět s tyto knihovny.

Kromě poskytují dokumentaci, můžete poskytnout analyzátory a opravy kódu, které najít a opravit běžné chybná používá své knihovny. Tyto okamžité opravy bude pomoci vývojářům při úspěšné rychleji. 

Můžete balíček analyzátorů a kód opravy s knihovnu na NuGet. V tomto scénáři bude každý vývojář, který nainstaluje balíček NuGet také nainstalovat balíček analyzátor. Všechny vývojáře, kteří používají vaše knihovna okamžitě získat pokyny od vašeho týmu ve formě okamžitou zpětnou vazbu na chyb a navrhované opravy.

## <a name="provide-general-guidance"></a>Zadejte obecné pokyny

Komunity vývojářů .NET zjistí prostřednictvím vzory prostředí, které pracují také a vzorů, které jsou nejlépe vyhnout. Několik členy komunity jste vytvořili analyzátory, které vynucují tyto doporučené vzorce. Jak jsme dozvědět víc, je vždy místo pro nové návrhy.

Tyto analyzátorů lze uložit [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) a stáhnout vývojáři pomocí sady Visual Studio. Nové uživatele na jazyk a platformu rychle zjistěte zásad a zvýšení produktivity dříve v cestě .NET. Jak tyto stát více nejběžněji používané, Společenství přijme tyto postupy.

## <a name="next-steps"></a>Další kroky

Sada SDK kompilátoru platformu .NET zahrnuje nejnovější objektové modely jazyk pro generování kódu, analýzu a refaktoring. Tato část obsahuje přehled sady SDK kompilátoru platformy .NET. Další podrobnosti naleznete v částech – elementy QuickStart, ukázky a výukové programy.

Podrobnější informace o konceptech v sadě SDK pro platformu .NET kompilátoru v těchto tématech čtyři:

 - [Seznamte se s vizualizér syntaxe kódu](syntax-visualizer.md)
 - [Pochopení modelu rozhraní API kompilátoru](compiler-api-model.md)
 - [Práce se syntaxí](work-with-syntax.md)
 - [Práce se sémantikou](work-with-semantics.md)
 - [Práce s pracovním prostorem](work-with-workspace.md)
 
Abyste mohli začít, budete muset nainstalovat **SDK pro platformu .NET kompilátoru**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
