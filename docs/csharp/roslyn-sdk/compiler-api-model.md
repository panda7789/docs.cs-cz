---
title: Koncepce sady SDK platformy kompilátoru .NET a objektový model
description: V tomto přehledu najdete na pozadí, které potřebujete k práci efektivně pomocí kompilátoru .NET SDK. Naučíte se vrstvy rozhraní API, hlavní typy používané a celkové objektový model.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: ee8f902bf1df8b63e229fd518e7a0c592fcd47ca
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675703"
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>Pochopení modelu sada SDK platformy kompilátoru .NET

Zpracování kódu, který napíšete následující strukturovaných pravidla, které často se liší od lidí způsob, jak číst a pochopení kódu. Základní znalosti o model používaný kompilátory je zásadní pro pochopení rozhraní API používat při sestavení založené na platformě Roslyn nástroje. 

## <a name="compiler-pipeline-functional-areas"></a>Kompilátor kanálu funkčních oblastí

Sada SDK platformy kompilátoru .NET poskytuje C# a kompilátory jazyka Visual Basic code analýzy vám jako spotřebitel poskytuje úroveň rozhraní API, která odráží tradiční kompilátoru kanálu.

![kroky zpracování zdrojový kód a kód objektu kompilátoru kanálu](media/compiler-api-model/compiler-pipeline.png)

Jednotlivé fáze tohoto kanálu je samostatná komponenta. Nejprve fáze analýzy tokenizes a analyzuje zdrojový text do syntaxe, která následuje jazyk gramatiky. Za druhé fáze deklarace analyzuje zdroje a importovaná metadata do formuláře s názvem symboly. V dalším kroku fáze vazby odpovídá identifikátory v kódu na symboly. A konečně fáze vygeneruje vysílá sestavení všechny informace, které jsou vytvářeny pomocí kompilátoru.

![Kompilátor kanálu rozhraní api poskytuje přístup k každého kroku, který je součástí kompilátoru kanálu](media/compiler-api-model/compiler-pipeline-api.png)

Odpovídající každé z těchto fází, sada SDK platformy kompilátoru .NET poskytuje objektový model, který umožňuje přístup k informacím v této fázi. Parsování fáze zpřístupňuje stromu syntaxe, fáze deklaraci vystavuje tabulky hierarchické symbolů, fáze vazby zpřístupňuje výsledek sémantické analýzy kompilátoru a vygeneruje fáze je rozhraní API, který generuje kódy bajtů IL.

![k dispozici z kompilátoru jazykových služeb rozhraní api v každém kroku kompilátoru kanálu](media/compiler-api-model/compiler-pipeline-lang-svc.png)

Každý kompilátor kombinuje tyto součásti společně jako jeden celek začátku do konce.

Tato rozhraní API jsou stejné ty, které používá sada Visual Studio. Například použití kódu, sbalování a formátování funkce stromu syntaxe, prohlížeče objektů a navigace funkce používají tabulky symbolů, refaktoring a přejít k definici použití sémantického modelu a všechny z nich, včetně rozhraní API pro generování využívá funkce upravit a pokračovat. 

## <a name="api-layers"></a>Rozhraní API vrstvy

Kompilátor .NET SDK se skládá ze dvou vrstev hlavní rozhraní API: kompilátoru rozhraní API a pracovním prostorům rozhraní API.

![rozhraní api vrstvy reprezentována kompilátor kanálu rozhraní API](media/compiler-api-model/api-layers.png)

### <a name="compiler-apis"></a>Rozhraní API kompilátoru

Kompilátor vrstva obsahuje objektové modely, které odpovídají informace, které jsou zveřejněné v jednotlivých fázích kanálu kompilátor syntaktický a sémantický. Vrstva kompilátoru také obsahuje neměnné snímek na jediné vyvolání kompilátoru, včetně odkazů na sestavení, možnosti kompilátoru a soubory zdrojového kódu. Existují dvě různá rozhraní API, které představují C# jazyka a jazyk Visual Basic. Tato dvě rozhraní API jsou podobné jako u obrazce ale navržených pro vysokou věrností pro každý jednotlivých jazyků. Tato vrstva nemá žádné závislosti na součásti sady Visual Studio.

### <a name="diagnostic-apis"></a>Diagnostických rozhraní API

Jako součást své analýzy kompilátor může vytvořit sadu diagnostiky, které pokrývají vše od syntaxe sémantické a chyby jednoznačného přiřazení do různých upozornění a informativní diagnostiky. Vrstvu rozhraní API služby kompilátoru zpřístupňuje diagnostiky prostřednictvím rozšiřitelné rozhraní API, která umožňuje uživatelem definované analyzátory zapojené do kompilace. To umožňuje diagnostiky definovaný uživatelem, například vytvořené metodou nástrojů, jako je StyleCop nebo FxCop, bude vytvořen spolu s definované kompilátorem diagnostiky. Vytváření diagnostiky tímto způsobem má výhodu přirozeně integrace pomocí nástrojů, jako je MSBuild a sadě Visual Studio, který je závislý na diagnostiky pro prostředí, jako je zastavení sestavení na základě zásad a zobrazují živé podtržení vlnovkou v editoru a navrhněte kódu opravy.

### <a name="scripting-apis"></a>Skriptovací rozhraní API

Hostování a skriptovací rozhraní API jsou součástí kompilátoru vrstvy. Můžete využít pro provádění kódu a shromažďování kontextu spuštění modulu runtime.
C# Interaktivní okno REPL (čtení-vyhodnocení-Print smyčky) používá tato rozhraní API. REPL umožňuje používat C# jako skriptovací jazyk, spouští kód interaktivně při psaní.

### <a name="workspaces-apis"></a>Rozhraní API pro pracovní prostory

Pracovní prostory vrstva obsahuje rozhraní API pracovní prostor, který je výchozím bodem pro provedení analýzy kódu a refaktoring přes celé řešení. Slouží k uspořádání všechny informace o projekty v řešení do jediného objektu modelu, nabízející přímý přístup k modelů kompilátoru vrstvy objektu bez nutnosti analyzovat soubory, nakonfigurujte možnosti, nebo spravovat závislosti projektu na projekt .

Kromě toho v pracovních prostorech vrstvy povrchy sadu rozhraní API používá při provádění analýzu kódu a refaktoring nástroje, které fungují v rámci hostitelského prostředí, jako je integrované vývojové prostředí sady Visual Studio. Mezi příklady patří najít všechny odkazy, formátování a rozhraní API pro generování kódu.

Tato vrstva nemá žádné závislosti na součásti sady Visual Studio.
