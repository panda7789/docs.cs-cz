---
title: .NET Compiler Platform koncepty a objektový model sady SDK
description: Tento přehled poskytuje pozadí, které potřebujete pro efektivní práci se sadou .NET Compiler SDK. Naučíte se vrstvy rozhraní API, hlavní typy a celkový objektový model.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: 529ce6fbdef22964251c8b22abbd5d8aadab633d
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975937"
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>Principy modelu .NET Compiler Platform SDK

Kompilátory zpracovávají kód, který zapisujete po strukturovaných pravidel, která se často liší od způsobu, jakým člověk čte a pochopit kód. Základní porozumění modelu používanému kompilátory je zásadní pro porozumění rozhraním API, která používáte při vytváření nástrojů založených na Roslyn.

## <a name="compiler-pipeline-functional-areas"></a>Funkční oblasti kanálu kompilátoru

Sada .NET Compiler Platform SDK zpřístupňuje analýzu kódu C# a Visual Basic kompilátorů jako příjemce tím, že poskytuje vrstvu rozhraní API, která zrcadlí tradiční kanál kompilátoru.

![kroky zdrojového kódu zpracování kanálu kompilátoru do kódu objektu](media/compiler-api-model/compiler-pipeline.png)

Každá fáze tohoto kanálu je samostatná součást. Nejprve fáze analýzy tokenizes a analyzuje zdrojový text do syntaxe, která následuje po jazykové gramatice. V druhé fázi deklarace analyzuje zdrojová a importovaná metadata do formuláře s pojmenovanými symboly. Dále fáze vazby porovná identifikátory v kódu ke symbolům. Nakonec fáze generování generuje sestavení se všemi informacemi sestavenými kompilátorem.

![rozhraní API kanálu kompilátoru poskytuje přístup k jednotlivým krokům, které jsou součástí kanálu kompilátoru.](media/compiler-api-model/compiler-pipeline-api.png)

V rámci každé z těchto fází sada SDK .NET Compiler Platform zpřístupňuje objektový model, který umožňuje přístup k informacím v této fázi. Fáze analýzy zveřejňuje strom syntaxe, fáze deklarace zveřejňuje hierarchickou tabulku symbolů. fáze vazby zpřístupňuje výsledek sémantické analýzy kompilátoru a fáze generování je rozhraní API, které vytváří bajtové kódy IL.

![jazykové služby, které jsou dostupné z rozhraní API kompilátoru v každém kroku kanálu kompilátoru](media/compiler-api-model/compiler-pipeline-lang-svc.png)

Každý kompilátor kombinuje tyto komponenty dohromady jako jeden celý celek.

Tato rozhraní API jsou stejná jako ta, která používá aplikace Visual Studio. Například funkce navigace v kódu a formátování používají stromy syntaxe, Prohlížeč objektů a navigační funkce používají tabulku symbolů, refaktoringy, přejít k definici používá sémantický model a příkaz Upravit a pokračovat používá všechny z nich, včetně rozhraní Emit API.

## <a name="api-layers"></a>Vrstvy API

Sada SDK kompilátoru .NET se skládá ze dvou hlavních vrstev rozhraní API: rozhraní API pro kompilátor a rozhraní API pracovních prostorů.

![vrstvy rozhraní API reprezentované rozhraními API kanálu kompilátoru](media/compiler-api-model/api-layers.png)

### <a name="compiler-apis"></a>Rozhraní API kompilátoru

Vrstva kompilátoru obsahuje objektové modely, které odpovídají informacím zveřejněným v každé fázi kanálu kompilátoru, syntaktické i sémantické. Vrstva kompilátoru obsahuje také neproměnlivý snímek jediného vyvolání kompilátoru, včetně odkazů na sestavení, možností kompilátoru a souborů zdrojového kódu. K dispozici jsou dvě odlišná rozhraní API, která představují jazyk C# a jazyk Visual Basic. Tato dvě rozhraní API jsou podobná v tvarování, ale jsou upraveny pro vysokou věrnost pro každý jednotlivý jazyk. Tato vrstva nemá žádné závislosti na komponentách sady Visual Studio.

### <a name="diagnostic-apis"></a>Rozhraní API pro diagnostiku

V rámci analýzy může kompilátor vytvořit sadu diagnostiky, která pokrývá vše od syntaxe, sémantické a omezené Chyby přiřazení k různým upozorněním a informativní diagnostice. Vrstva rozhraní API kompilátoru zpřístupňuje diagnostiku prostřednictvím rozšiřitelného rozhraní API, které umožňuje připojit uživatelsky definované analyzátory do procesu kompilace. Umožňuje vytvářet uživatelsky definované diagnostiky, jako jsou ty, které vytvořily nástroje jako StyleCop nebo FxCop, a to společně s diagnostikou definovanou kompilátorem. Vytváření diagnostiky tímto způsobem má za následek integraci přirozeně s nástroji, jako je MSBuild a Visual Studio, které závisí na diagnostice pro prostředí, jako je například zastavení sestavení založeného na zásadách a zobrazení živých vlnovek v editoru a návrh oprav kódu.

### <a name="scripting-apis"></a>Rozhraní API pro skriptování

Rozhraní API pro hostování a skriptování jsou součástí vrstvy kompilátoru. Můžete je použít pro spouštění fragmentů kódu a nahromadění kontextu spuštění modulu runtime.
Tato rozhraní API používají interaktivní REPL C# (čtení-vyhodnocení-tisk smyčky). REPL umožňuje používat C# jako skriptovací jazyk a při psaní kódu interaktivně spouštět kód.

### <a name="workspaces-apis"></a>Rozhraní API pracovních prostorů

Vrstva pracovní prostory obsahuje rozhraní API pracovního prostoru, což je výchozí bod pro analýzu kódu a refaktoring přes celá řešení. Pomáhá vám při organizování všech informací o projektech v řešení do jediného objektového modelu a nabízí vám přímý přístup k modelům objektů vrstvy kompilátoru bez nutnosti analyzovat soubory, konfigurovat možnosti nebo spravovat závislosti mezi projekty.

Kromě toho pracovní prostory rozsvítí sadu rozhraní API, která se používají při implementaci nástroje pro analýzu kódu a nástroje refaktoringu, které fungují v hostitelském prostředí, jako je například integrované vývojové prostředí (IDE) sady Visual Studio. Příklady zahrnují rozhraní API najít všechny odkazy, formátování a generování kódu.

Tato vrstva nemá žádné závislosti na komponentách sady Visual Studio.
