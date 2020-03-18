---
title: Koncepty a objektový model platformy kompilátoru .NET
description: Tento přehled poskytuje pozadí, které potřebujete efektivně pracovat s kompilátorem .NET SDK. Dozvíte se vrstvy rozhraní API, hlavní typy a celkový objektový model.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: e563260e21fb8807017db90ff63e30fec0415a48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156958"
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>Principy modelu sady .NET Compiler Platform SDK

Kompilátory zpracovávají kód, který píšete podle strukturovaných pravidel, která se často liší od způsobu, jakým lidé čtou a rozumí kódu. Základní znalost modelu používaného kompilátory je nezbytné pro pochopení api, která používáte při vytváření nástrojů založených na Roslyn.

## <a name="compiler-pipeline-functional-areas"></a>Funkční oblasti kanálu kompilátoru

Sada SDK platformy kompilátoru .NET zpřístupňuje analýzu kódu kompilátorů jazyka C# a Visual Basic vám jako spotřebiteli tím, že poskytuje vrstvu rozhraní API, která zrcadlí tradiční kanál kompilátoru.

![kroky kanálu kompilátoru zpracování zdrojového kódu objektu](media/compiler-api-model/compiler-pipeline.png)

Každá fáze tohoto kanálu je samostatnou součástí. Nejprve fáze analýzy tokenizuje a analyzuje zdrojový text do syntaxe, která následuje za jazykovou gramatikou. Za druhé fáze deklarace analyzuje zdroj a importovaná metadata do formuláře s názvem symboly. Dále fáze vazby odpovídá identifikátorům v kódu se symboly. Nakonec fáze emitu vydává sestavení se všemi informacemi vytvořenými kompilátorem.

![Rozhraní API kanálu kompilátoru poskytuje přístup ke každému kroku, který je součástí kanálu kompilátoru](media/compiler-api-model/compiler-pipeline-api.png)

Odpovídající každé z těchto fází, sada SDK platformy kompilátoru .NET zpřístupňuje objektový model, který umožňuje přístup k informacím v této fázi. Fáze analýzy zpřístupňuje strom syntaxe, fáze deklarace zpřístupňuje hierarchickou tabulku symbolů, fáze vazby zpřístupňuje výsledek sémantické analýzy kompilátoru a fáze emitu je rozhraní API, které vytváří kódy bajtů IL.

![jazykové služby dostupné z rozhraní API kompilátoru v každém kroku kanálu kompilátoru](media/compiler-api-model/compiler-pipeline-lang-svc.png)

Každý kompilátor kombinuje tyto součásti dohromady jako jeden celek od konce.

Tato api jsou stejné ty, které používá Visual Studio. Například funkce osnovy a formátování kódu používají stromy syntaxe, prohlížeč objektů a navigační funkce používají tabulku symbolů, refaktoringy a Přejít na definici používají sémantický model a funkce Upravit a pokračovat používá všechny tyto funkce, včetně rozhraní EMIT API.

## <a name="api-layers"></a>Vrstvy rozhraní API

Sada SDK kompilátoru .NET se skládá ze dvou hlavních vrstev rozhraní API: rozhraní API kompilátoru a rozhraní API pracovních prostorů.

![vrstvy rozhraní API reprezentované rozhraními kanálu kompilátoru](media/compiler-api-model/api-layers.png)

### <a name="compiler-apis"></a>Api kompilátoru

Vrstva kompilátoru obsahuje objektové modely, které odpovídají informacím vystaveným v každé fázi kanálu kompilátoru, syntaktické ho i sémantické. Vrstva kompilátoru také obsahuje neměnný snímek jednoho vyvolání kompilátoru, včetně odkazů na sestavení, možností kompilátoru a souborů zdrojového kódu. Existují dvě odlišná rozhraní API, která představují jazyk C# a jazyk jazyka Visual Basic. Tato dvě rozhraní API mají podobný tvar, ale jsou přizpůsobena pro vysokou věrnost jednotlivým jazykům. Tato vrstva nemá žádné závislosti na součástech sady Visual Studio.

### <a name="diagnostic-apis"></a>Diagnostická api

V rámci své analýzy může kompilátor vytvořit sadu diagnostiky pokrývající vše od syntaxe, sémantického a jednoznačného přiřazení chyb až po různá upozornění a informační diagnostiku. Vrstva rozhraní API kompilátoru zpřístupňuje diagnostiku prostřednictvím rozšiřitelného rozhraní API, které umožňuje připojení uživatelem definovaných analyzátorů do procesu kompilace. Umožňuje uživatelsky definovanou diagnostiku, například ty, které jsou vyráběny nástroji, jako je StyleCop nebo FxCop, které mají být vyrobeny vedle diagnostiky definované kompilátorem. Vytváření diagnostiky tímto způsobem má tu výhodu, že se přirozeně integruje s nástroji, jako jsou MSBuild a Visual Studio, které závisí na diagnostice pro prostředí, jako je zastavení sestavení založené na zásadách a zobrazení živých vlnovek v editoru a navrhování kódu Opravy.

### <a name="scripting-apis"></a>Skriptovací api

Hostování a skriptování API jsou součástí vrstvy kompilátoru. Můžete je použít pro provádění fragmentů kódu a akumulaci kontextu spuštění modulu runtime.
C# interaktivní REPL (Read-Evaluate-Print Loop) používá tato api. REPL umožňuje používat C# jako skriptovací jazyk, provádění kódu interaktivně při psaní.

### <a name="workspaces-apis"></a>Api pracovních prostorů

Vrstva pracovních prostorů obsahuje rozhraní API pracovního prostoru, které je výchozím bodem pro provádění analýzy kódu a refaktoringu přes celá řešení. Pomáhá při uspořádání všech informací o projektech v řešení do jednoho objektového modelu a nabízí přímý přístup k objektovým modelům vrstvy kompilátoru bez nutnosti analyzovat soubory, konfigurovat možnosti nebo spravovat závislosti mezi projekty .

Kromě toho vrstva pracovních prostorů zobrazí sadu rozhraní API používaných při implementaci nástrojů pro analýzu kódu a refaktoringu, které fungují v hostitelském prostředí, jako je ide visual studia. Mezi příklady patří najít všechny odkazy, formátování a generování kódu API.

Tato vrstva nemá žádné závislosti na součástech sady Visual Studio.
