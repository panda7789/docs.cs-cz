---
title: "F# – funkce vývojového prostředí"
description: "Další informace, které funkce sady Visual Studio 2012 jsou podporovány v jazyce F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 809e9a34-b271-4c87-8356-2426b44f4721
ms.openlocfilehash: 05727bf11eccfd64f823dd280b1a19210815ca5a
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="visual-f-development-environment-features"></a>Visual F # – funkce vývojového prostředí

> [!NOTE]
V tomto článku není aktuální pomocí nejnovější sady Visual Studio.  Bude aktualizována.

Toto téma obsahuje informace o tom, které funkce sady Visual Studio 2012 jsou podporovány v F #.

## <a name="project-features"></a>Funkce projektu
Následující tabulka shrnuje šablony, které jsou k dispozici pro použití v projektech F #. Informace o šablonách projektů a položek najdete v tématu [NIB vytváření projektů ze šablon](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2).

|Typ šablony|Popis|Podporované šablony|
|-------------|-----------|-------------------|
|Šablony projektů|Typy projektů, které jsou k dispozici v **nový projekt** dialogové okno.|<ul><li>Aplikace v F #<br /></li><li>Knihovny F #<br /></li><li>F # – tutoriál<br /></li><li>Knihovny F # přenositelností<br /></li><ul/>|
|Šablony položek|K dispozici v typy souborů **přidat novou položku** dialogové okno.|<ul><li>F # zdrojový soubor (.fs)<br /></li><li>F # skript (.fsx)<br /></li><li>F # podpisu souboru (.fsi)<br /></li><li>Konfigurační soubor (config)<br /></li><li>Připojení k databázi SQL (Zprostředkovatel typu LINQ to SQL)<br /></li><li>Připojení k databázi SQL (technologie LINQ to Entities – zprostředkovatel typu)<br /></li><li>Připojení služby OData (Zprostředkovatel LINQ typu)<br /></li><li>Připojení služby WSDL (Zprostředkovatel typu)<br /></li><li>Soubor XML (.xml)<br /></li><li>Textový soubor<br /></li><ul/>|
Pokud chcete vytvořit aplikaci, která může běžet jako samostatný spustitelný soubor, vyberte typ projektu aplikace F #. Chcete-li vytvořit knihovnu (to znamená, spravované sestavení nebo. Soubor DLL) pro použití na platformě Windows desktop, zvolte knihovny F #. Chcete-li vytvořit přenosné knihovny, který lze použít na všech podporovaných platformách, zvolte přenosné knihovny F #. Přenosné knihovny F # projekty odkazovat na verzi FSharp.Core.dll, který je vhodný pro vytvoření knihovny F #, která lze použít s aplikací, které běží na platformách, například aplikace pro Windows Store, rozhraní .NET Framework 4.5, Xamarin.iOS a Xamarin.Android.

Další informace o šablonách položek pro přístup k datům najdete v tématu [zprostředkovatelů typů](../tutorials/type-providers/index.md).

Následující tabulka shrnuje funkce vlastnosti projektu podporované a nepodporované v F #. Další informace najdete v tématu [konfigurace projekty](configuring-projects.md) a [Úvod do Návrhář projektu](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7).

|Nastavení projektu|Podporované v jazyce F #?|Poznámky|
|---------------|----------------|-----|
|Soubory prostředků|Ano||
|Odkaz na nastavení, ladění a sestavení|Ano||
|Cílení na více verzí|Ano||
|Ikona a manifestu|Ne|K dispozici prostřednictvím možnosti příkazového řádku kompilátoru.|
|Klient služby ASP.NET|Ne||
|ClickOnce|Ne|Pomocí projektu klienta v jiném jazyce rozhraní .NET Framework, pokud je k dispozici.|
|Silné názvy|Ne|K dispozici prostřednictvím možnosti příkazového řádku kompilátoru.|
|Sestavení publikování a správa verzí|Ne||
|Analýza kódu|Ne|Nástrojů pro analýzu kódu můžete spustit ručně nebo jako součást příkazu po sestavení.|
|Zabezpečení (Změna úrovně důvěryhodnosti)|Ne||

## <a name="code-and-text-editor-features"></a>Kódu a textovém editoru funkce
Následující funkce sady Visual Studiocode a textové editory jsou podporovány v jazyce F #. Obecné informace o úpravách kód v sadě Visual Studio a funkce textového editoru najdete v tématu [psaní kódu v editoru kódu a textovém editoru](/visualstudio/ide/writing-code-in-the-code-and-text-editor).

|Funkce|Popis|Podporované v jazyce F #?|
|-------|-----------|----------------|
|Automaticky komentář|Umožňuje komentování nebo zrušte komentář u sekcí kódu.|Ano|
|Automatické formátování|Přeformátuje kódu pomocí standardní odsazení a stylu.|Ne|
|Záložky|Umožňuje uložit míst v editoru.|Ano|
|Změnit odsazení|Odsadí nebo unindents vybrané řádky.|Ano|
|[Hledání a nahrazení textu](/visualstudio/ide/finding-and-replacing-text)|Umožňuje hledat v souboru, projekt nebo řešení a potenciálně Změna textu.|Ano|
|Přechod na definici pro rozhraní .NET Framework API|Když kurzor je nastavený na rozhraní API rozhraní .NET Framework, ukazuje kód, který vygenerovala z metadata rozhraní .NET Framework.|Ne|
|Přechod na definici pro uživatelské rozhraní API|Pokud je kurzor u entity program, který jste definovali, přesune kurzor na umístění ve vašem kódu, kde je definován entity.|Ano|
|Přechod na řádek|Umožňuje přejít na konkrétní řádek v souboru, podle čísla řádku.|Ano|
|Navigační panely v horní části souboru|Umožňuje přejít do umístění v kódu, například název funkce.|Ano|
|Osnova. V tématu [osnovy](/visualstudio/ide/outlining).|Umožňuje sbalit části kódu můžete vytvořit kompaktnější zobrazení.|Ano|
|Převedení na tabulátory|Převede mezery na kartách.|Ano|
|Zabarvení typu|Zobrazuje názvy typů definované v speciální barev.|Ano|
|Rychle najít. V tématu rychle najít, najít a nahradit okno.|Umožňuje hledat v souboru nebo v projektu.|Ano|

## <a name="intellisense-features"></a>Funkce technologie IntelliSense
Následující tabulka shrnuje funkce IntelliSense podporované a nepodporované v F #. Obecné informace o technologii IntelliSense, najdete v části [pomocí IntelliSense](/visualstudio/ide/using-intellisense).

|Funkce|Popis|Podporované v jazyce F #?|
|-------|-----------|----------------|
|Automaticky implementovat rozhraní|Generuje kód zástupných procedur pro metody rozhraní.|Ne|
|Fragmenty kódu|Vloží kód z knihovny běžných kódování konstrukce do témata.|Ne|
|Dokončit slovo|Uloží zadáním provedením slova a názvy během psaní.|Ano|
|Režim dokončení využívat první|Když je povolené, způsobí, že dokončení slova na první shodu vyberte, jak budete zadávat, místo abyste čekali, vyberte jednu nebo stiskněte klávesu **CTRL + MEZERNÍK**.|Ne|
|Generovat elementy kódu|Umožňuje generovat stub kódu pro různé konstrukce.|Ne|
|Vypsat členy|Když zadáte operátor přístupu členů (.), uvádí členy typu.|Ano|
|Uspořádání direktiv Using/otevřít|Slouží k uspořádání obory názvů odkazuje **pomocí** příkazy v jazyce C# nebo **otevřete** direktivy v jazyce F #.|Ne|
|Informace o parametrech|Užitečné informace o parametrech ukazuje, jak budete zadávat volání funkce.|Ano|
|Rychlé informace|Zobrazí úplnou deklaraci pro všechny identifikátor ve vašem kódu.|Ano|
Refaktoring kódu F # nepodporuje v sadě Visual Studio 2012.

## <a name="debugging-features"></a>Funkce ladění
Následující tabulka shrnuje funkce, které jsou k dispozici při ladění kódu F #. Obecné informace o ladicím programu sady Visual Studio najdete v tématu [ladění v sadě Visual Studio](https://msdn.microsoft.com/library/sc65sadd.aspx).

|Funkce|Popis|Podporované v jazyce F #?|
|-------|-----------|----------------|
|Automatické hodnoty – okno|Zobrazuje proměnné automatické nebo dočasné.|Ne|
|Zarážky|Umožňuje pozastavit provádění kódu v určitých bodech během ladění.|Ano|
|Podmíněné zarážky|Umožňuje zarážky, které podmínku, která určuje, zda by měl pozastavit provádění testů.|Ano|
|Upravit a pokračovat|Umožňuje kódu se dají upravit a kompilovat jako ladění spuštěným programem bez zastavení a spuštění ladicího programu.|Ne|
|Vyhodnocení výrazu|Vyhodnotí a spustí kód v době běhu.|Ne, ale jazyka C# vyhodnocovací filtr výrazů lze použít, i když je nutné použít syntaxi C#.|
|Historické ladění|Umožňuje krok do dříve spuštění kódu.|Ano|
|Místní hodnoty – okno|Zobrazí místně definované hodnoty a proměnné.|Ano|
|Spustit ke kurzoru|Umožňuje spouštění kódu, dokud nebude dosaženo řádek, který obsahuje kurzor.|Ano|
|Krok do|Umožňuje provedení zálohy a přesunout do jakékoli volání funkce.|Ano|
|Krok přes|Umožňuje spouštění v aktuální rámec zásobníku zálohy a přesun za jakékoli volání funkce.|Ano|

## <a name="additional-tools"></a>Další nástroje
Následující tabulka shrnuje podporu pro F # v sadě Visual Studio tools.

|Nástroj|Popis|Podporované v jazyce F #?|
|----|-----------|----------------|
|Hierarchie volání|Zobrazí strukturu vnořené funkce zavolá do vašeho kódu.|Ne|
|Metriky kódu|Shromažďuje informace o kódu, jako jsou počty řádků.|Ne|
|zobrazení tříd|Poskytuje založený na typu zobrazení kódu v projektu.|Ne|
|[Okno Seznam chyb](/visualstudio/ide/reference/error-list-window)|Zobrazí seznam chyb v kódu.|Ano|
|[F # interaktivní](../tutorials/fsharp-interactive/index.md)|Umožňuje vám zadejte (nebo zkopírujte a vložte) F # code a spustit okamžitě, nezávisle na vytvoření projektu. F # interaktivních okna je pro čtení, hodnocení, tisk smyčky (REPL).|Ano|
|prohlížeč objektů|Umožňuje zobrazit typy v sestavení.|Typy F # jak se zobrazují v kompilovaném sestavení se nezobrazí přesně tak, jak je vytváříte. Můžete procházet kompilované reprezentace typů F #, ale typy nelze zobrazit, jak vypadají z F #.|
|[Okno Výstup](/visualstudio/ide/reference/output-window)|Zobrazí sestavení výstupu.|Ano|
|Analýza výkonu|Poskytuje nástroje pro měření výkonu vašeho kódu.|Ano|
|Okno vlastností|Zobrazuje a umožňuje úpravy vlastností objektu ve vývojovém prostředí, který má právě fokus.|Ano|
|[V Průzkumníku serveru](https://msdn.microsoft.com/library/x603htbk.aspx)|Poskytuje způsoby, jak pracovat s různými prostředky serveru.|Ano|
|Průzkumník řešení|Umožňuje zobrazení a správa projektů a soubory.|Ano|
|Seznam úloh|Umožňuje spravovat pracovní položky, která se týkají vašeho kódu.|Ano|
|Testování projektů|Poskytuje funkce, které vám pomůžou Otestujte svůj kód.|Ne|
|Sada nástrojů|Zobrazí karty, které obsahují přetahovatelným objekty, jako jsou ovládací prvky a části textu nebo kódu.|Ano|

## <a name="see-also"></a>Viz také
 [Začínáme s F # v sadě Visual Studio](../get-started/get-started-visual-studio.md)  
 [Konfigurace projektů](configuring-projects.md)  
