---
title: "SDK pro platformu .NET kompilátoru koncepty a objektový model"
description: "Tento přehled poskytuje na pozadí, které potřebujete k efektivní práci s kompilátoru .NET SDK. Dozvíte vrstvy rozhraní API, hlavní typy související se situací a celkové objektový model."
author: billwagner
ms.author: wiwagn
ms.date: 10/10/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: d230d334eba4e438635a4c70e8c1b5fc5075b065
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>Pochopení modelu SDK pro platformu .NET kompilátoru

Kompilátory zpracovat kód, který můžete psát následující strukturovaných pravidla, která se často liší od lidí způsob čtení a pochopení kódu. Základní znalosti o modelu používaný kompilátory je nezbytné k pochopení rozhraní API používat při sestavení na základě Roslyn nástroje. 

## <a name="compiler-pipeline-functional-areas"></a>Kompilátoru kanálu funkčním oblastem

.NET SDK platformy kompilátoru zpřístupní analýza kódu C# a Visual Basic kompilátory vám jako příjemce tím, že poskytuje vrstvu rozhraní API, které odpovídá tradiční kompilátoru kanálu.

![postup zpracování zdrojového kódu pro kód objektu kanálu kompilátoru](media/compiler-pipeline.png)

Jednotlivé fáze kanálu je samostatná komponenta. Nejprve fázi analýzy tokenizes a analyzuje zdrojový text do syntaxi, která následuje gramatika jazyka. Druhé fázi deklarace analyzuje zdroje a importované metadata do formuláře s názvem symboly. V dalším kroku fázi vazby odpovídá identifikátory v kódu na symboly. Nakonec fázi vysílat vysílá sestavení všechny informace sestavena kompilátoru.

![kanál kompilátoru rozhraní api poskytuje přístup k každý krok, který je součástí pipelien kompilátoru](media/compiler-pipeline-api.png)

Odpovídající každé z těchto fází, .NET SDK platformy kompilátoru zpřístupní objektový model, který umožňuje přístup k informacím v této fázi. Analýzy fáze zpřístupní stromu syntaxe, fázi deklarace zpřístupní tabulky hierarchické symbolů, fázi vazby zpřístupní výsledek analýzy sémantického kompilátoru a fázi vysílat je rozhraní API, které vytváří IL bajtů kódy.

![k dispozici z kompilátoru jazyka služby rozhraní api v každém kroku kanálu kompilátoru](media/compiler-pipeline-lang-svc.png)

Každý kompilátoru kombinuje tyto součásti společně jako jeden celek začátku do konce.

Tato rozhraní API jsou stejné ty, které slouží Visual Studio. Například kód osnovy a formátování funkce použití syntaxe stromů, prohlížeč objektů a navigační funkce pomocí tabulky symbolů, refaktoring a přejít na definici použití sémantického modelu a upravit a pokračovat používá všechny tyto včetně emitování rozhraní API. 

## <a name="api-layers"></a>Rozhraní API vrstvy

Kompilátor .NET SDK se skládá ze dvou vrstev hlavní rozhraní API: kompilátoru rozhraní API a pracovní prostory rozhraní API.

![rozhraní api vrstvy reprezentována kompilátor kanálu rozhraní API](media/api-layers.png)

### <a name="compiler-apis"></a>Rozhraní API kompilátoru

Vrstva kompilátoru obsahuje objektové modely, které odpovídají vystavený v jednotlivých fázích kanálu kompilátoru syntaktické a sémantické informace. Vrstva kompilátoru také obsahuje neměnné snímku jednoho volání kompilátoru, včetně odkazů na sestavení, – možnosti kompilátoru a soubory zdrojového kódu. Existují dva odlišné rozhraní API, které představují jazyka C# a jazyk Visual Basic. Tato dvě rozhraní API jsou podobné ve tvaru ale přizpůsobit pro zachováním pro jednotlivé jednotlivé jazyky. Tato vrstva nemá žádné závislosti na součásti sady Visual Studio.

### <a name="diagnostic-apis"></a>Diagnostické rozhraní API

V rámci analýzy kompilátor může vytvořit sadu diagnostiky pokrývajících vše z syntaxe, sémantického a chyby jednoznačné přiřazení do různých upozornění a informační diagnostiky. Vrstvu rozhraní API kompilátoru zpřístupní diagnostiky prostřednictvím rozšiřitelné rozhraní API, která umožňuje uživatelem definované analyzátorů zapojené do procesu kompilace. To umožňuje diagnostics definovaný uživatelem, jako jsou ty vyprodukované nástroje, například StyleCop nebo FxCop, se vytváří spolu s definované kompilátoru diagnostiky. Vytváření diagnostiky tímto způsobem má výhodu přirozeně Integrování nástroje, jako je MSBuild a Visual Studio, který je závislý na diagnostiku pro činnosti, jako je například zastavení sestavení na základě zásad a zobrazující podtržení vlnovkou za provozu v editoru a návrhy kódu opravy.

### <a name="scripting-apis"></a>Skriptovací rozhraní API

Hostování a skriptovací rozhraní API jsou součástí vrstvě kompilátoru. Můžete je používat pro provádění fragmenty kódu a shromažďování kontext spuštění modulu runtime.
Jazyce C# interaktivní REPL (čtení vyhodnotit tiskových smyčky) používá tato rozhraní API. REPL umožňuje použít c jako skriptovací jazyk, provádění kódu interaktivně, jako je.

### <a name="workspaces-apis"></a>Rozhraní API pracovních prostorů

Pracovní prostory vrstva obsahuje rozhraní API pracovní prostor, který je výchozím bodem pro provádění analýzy kódu a refaktoring přes celé řešení. Je vám usnadní uspořádání všechny informace o projekty v řešení do jednoho objektu modelu, nabídky přímý přístup k objektové modely vrstvy kompilátoru bez nutnosti analyzovat souborů, nakonfigurujte možnosti, nebo spravovat závislosti projektu projektu .

Kromě toho pracovních prostorů vrstvy povrchy sada rozhraní API používá při implementaci analýza kódu a refaktoring nástroje, které funkce v prostředí hostitele, jako třeba Visual Studio IDE. Mezi příklady patří najít všechny odkazy, formátování a rozhraní API pro generování kódu.

Tato vrstva nemá žádné závislosti na součásti sady Visual Studio.
