---
title: Knihovny portů do .NET Core
description: Naučte se, jak přenést projekty knihovny z .NET Framework do .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: c7a770ba2da8c245ba9140852fc7c2a33a55f7a2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660699"
---
# <a name="port-net-framework-libraries-to-net-core"></a>Port .NET Framework knihovny do .NET Core

Naučte se, jak portovat kód knihovny .NET Framework do .NET Core, abyste mohli provozovat různé platformy a rozšiřovat dosah aplikací, které ji používají.

## <a name="prerequisites"></a>Požadavky

V tomto článku se předpokládá, že máte následující:

- Používáte Visual Studio 2017 nebo novější.
  - V dřívějších verzích sady Visual Studio není podporováno rozhraní .NET Core
- Pochopení [doporučeného procesu přenosu](index.md).
- Vyřešily se případné problémy se [závislostmi třetích stran](third-party-deps.md).

Měli byste se také seznámit s obsahem následujících témat:

[.NET Standard](../../standard/net-standard.md)\
Toto téma popisuje formální specifikaci rozhraní API .NET, která jsou určená k dispozici pro všechny implementace rozhraní .NET.

[Balíčky, metabalíčky a architektury](../packages.md)   
Tento článek popisuje, jak .NET Core definuje a používá balíčky a jak balíčky podporují kód běžící na více implementacích rozhraní .NET.

[Vývoj knihoven pomocí nástrojů pro různé platformy](../tutorials/libraries.md)   
Toto téma vysvětluje, jak psát knihovny pro .NET pomocí nástrojů rozhraní příkazového řádku pro různé platformy.

[Přidání do formátu *csproj* pro .NET Core](../tools/csproj.md)   
Tento článek popisuje změny, které byly přidány do souboru projektu v rámci přesunutí do *csproj* a MSBuild.

[Přenos do .NET Core – analýza závislostí třetích stran](third-party-deps.md)   
Toto téma popisuje přenositelnost závislostí třetích stran a postup v případě, že se závislost balíčku NuGet nespustí v rozhraní .NET Core.

## <a name="retargeting-your-net-framework-code-to-net-framework-472"></a>Změna cílení kódu .NET Framework na .NET Framework 4.7.2

Pokud váš kód necílí na .NET Framework 4.7.2, doporučujeme změnit cílení na .NET Framework 4.7.2. Tím se zajistí dostupnost nejnovějších alternativ rozhraní API pro případy, kdy .NET Standard nepodporuje existující rozhraní API.

Pro každý projekt v aplikaci Visual Studio, který chcete přenést, udělejte toto:

1. Klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**.
1. V rozevíracím seznamu **cílové rozhraní** vyberte **.NET Framework 4.7.2**.
1. Znovu zkompilujte projekty.

Vzhledem k tomu, že vaše projekty teď cílí na .NET Framework 4.7.2, použijte tuto verzi .NET Framework jako základ pro přenos kódu.

## <a name="determining-the-portability-of-your-code"></a>Určení přenositelnosti kódu

Dalším krokem je spuštění analyzátoru přenositelnosti rozhraní API (ApiPort), aby se vygenerovala sestava přenositelnosti pro analýzu.

Ujistěte se, že rozumíte [analyzátoru přenositelnosti rozhraní API (ApiPort)](../../standard/analyzers/portability-analyzer.md) a jak generovat sestavy přenositelnosti pro cílení na .NET Core. Jak to můžete udělat, se může lišit podle vašich potřeb a osobního příchuti. Níže je uvedeno několik různých přístupů. V závislosti na tom, jak je váš kód strukturován, se můžete setkat s kombinací kroků těchto přístupů.

### <a name="dealing-primarily-with-the-compiler"></a>Primárně se zabývat kompilátorem

Tento přístup může být nejvhodnější pro malé projekty nebo projekty, které nepoužívají mnoho .NET Framework rozhraní API. Přístup je jednoduchý:

1. Volitelně můžete v projektu spustit ApiPort. Pokud spustíte ApiPort, získáte znalosti ze sestavy o problémech, které budete potřebovat řešit.
1. Zkopírujte veškerý kód do nového projektu .NET Core.
1. Při odkazování na sestavu přenositelnosti (Pokud je vygenerováno) se vyřeší chyby kompilátoru, dokud se projekt zcela zkompiluje.

I když je tento přístup nestrukturované, přístup zaměřený na kód často vede k rychlému řešení problémů a může se jednat o nejlepší přístup pro menší projekty nebo knihovny. Projekt, který obsahuje pouze datové modely, může být ideálním kandidátem pro tento přístup.

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>Zastavování .NET Framework až do vyřešení problémů s přenositelností

Tento přístup může být nejlepší, pokud dáváte přednost kódu, který se zkompiluje během celého procesu. Přístup je následující:

1. Spusťte ApiPort na projektu.
1. Vyřešte problémy pomocí různých rozhraní API, která jsou přenosná.
1. Poznamenejte si všechny oblasti, ve kterých se vám zabrání použití přímé alternativy.
1. Předchozí kroky opakujte pro všechny projekty, které chcete přenést, dokud si nejste jisti, že jsou všechny připravené k zkopírování do nového projektu .NET Core.
1. Zkopírujte kód do nového projektu .NET Core.
1. Vypracujte všechny problémy, kde jste si poznamenali, že nějaká přímá alternativa neexistuje.

Tento pečlivý přístup je více strukturovaný než pouhá práce s kompilátorem, ale je stále poměrně zaměřený na kód a má výhodu vždy, co kompiluje kód. Způsob řešení některých problémů, které nebylo možné vyřešit pouhým použitím jiného rozhraní API, se výrazně liší. Může se stát, že budete potřebovat sestavit komplexnější plán pro určité projekty, který je popsaný jako další přístup.

### <a name="developing-a-comprehensive-plan-of-attack"></a>Vývoj komplexního plánu útoků

Tento přístup může být nejvhodnější pro větší a složitější projekty, kde může být změna struktury kódu nebo zcela přepisování některých oblastí kódu nutná k podpoře .NET Core. Přístup je následující:

1. Spusťte ApiPort na projektu.
1. Zjistěte, kde se používá každý nepřenosný typ a jak ovlivňuje celkovou přenositelnost.
   - Pochopte charakter těchto typů. Jsou malými čísly, ale často se používají? Jsou velké v čísle, ale používány zřídka? Je jejich použití zahuštěné nebo rozdělené do celého kódu?
   - Je snadné izolovat kód, který není přenosný, abyste se mohli efektivněji zabývat?
   - Potřebujete Refaktorovat kód?
   - U typů, které nejsou přenosné, jsou k dispozici alternativní rozhraní API, která mají stejný úkol? Například pokud <xref:System.Net.WebClient> používáte třídu, je možné místo toho <xref:System.Net.Http.HttpClient> použít třídu.
   - Jsou k dispozici různá přenosná rozhraní API k provedení úkolu, i když není náhrada odkládacího zařízení? Například pokud používáte <xref:System.Xml.Schema.XmlSchema> k analýze XML, ale nepotřebujete zjišťování schématu XML, můžete použít <xref:System.Xml.Linq> rozhraní API a implementovat analýzu sami, a to i na rozdíl od spoléhání na rozhraní API.
1. Pokud máte sestavení, která se obtížně portují, je vhodné je nechat .NET Framework pro teď? Tady je několik věcí, které je potřeba vzít v úvahu:
   - Je možné, že máte v knihovně některé funkce, které jsou nekompatibilní s .NET Core, protože spoléhá na .NET Framework nebo specifické funkce systému Windows příliš mnoho. Stojí za to, aby se teď zanechaly funkce a uvolnila se verze .NET Core vaší knihovny s méně funkcemi na dočasné úrovni, dokud nebudou k dispozici prostředky pro přenos funkcí?
   - Je refaktorovaná?
1. Je rozumné napsat vlastní implementaci nedostupného .NET Framework rozhraní API?
   Můžete zvážit kopírování, úpravy a používání kódu z [.NET Frameworkho zdroje odkazů](https://github.com/Microsoft/referencesource). Zdrojový kód odkazu je licencován v rámci [licence MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), takže máte významnou volnost v používání zdroje jako základu pro váš vlastní kód. Stačí se ujistit, že v kódu budete správně atribut Microsoft.
1. Tento postup opakujte podle potřeby pro různé projekty.
 
Fáze analýzy může určitou dobu trvat v závislosti na velikosti vašeho základu kódu. Doba útraty v této fázi k důkladnému pochopení rozsahu změn potřebných pro vývoj plánu obvykle šetří čas v dlouhodobém běhu, zejména v případě, že máte složitý základ kódu.

Váš plán by mohl zahrnovat významné změny v základu kódu a přitom stále cílit .NET Framework 4.7.2, takže tato verze je podrobněji sestavená. Způsob provádění plánu závisí na základu kódu.

### <a name="mixing-approaches"></a>Kombinování přístupů

Je možné, že se výše uvedené přístupy budou kombinovat na základě jednotlivých projektů. Měli byste postupovat podle svých potřeb a základu kódu.

## <a name="porting-your-tests"></a>Přenos testů

Nejlepším způsobem, jak zajistit, aby vše fungovalo, když jste svůj kód nastavili jako port, je testování kódu při jeho přenosu do .NET Core. K tomu je nutné použít testovací rozhraní, které sestaví a spustí testy pro .NET Core. V současné době máte tři možnosti:

- [xUnit](https://xunit.github.io/)
  * [Začínáme](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [Nástroj k převedení projektu MSTest na xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  * [Začínáme](https://github.com/nunit/docs/wiki/Installation)
  * [Příspěvek na blogu o migraci z MSTest na NUnit](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>Doporučený přístup k přenosu

V konečném důsledku je přenosová intenzita velmi závislá na způsobu strukturování kódu .NET Framework. Dobrým způsobem, jak portovat váš kód, je začít se *základem* vaší knihovny, které jsou základními komponentami kódu. Může se jednat o datové modely nebo jiné základní třídy a metody, které jinak používá přímo nebo nepřímo.

1. Port testovacího projektu, který testuje vrstvu vaší knihovny, kterou právě napojujete.
1. Zkopírujte základnu vaší knihovny do nového projektu .NET Core a vyberte verzi .NET Standard, kterou chcete podporovat.
1. Proveďte potřebné změny k získání kódu pro zkompilování. Většina toho může vyžadovat přidání závislostí balíčku NuGet do souboru *csproj* .
1. Spusťte testy a proveďte potřebné úpravy.
1. Vyberte další vrstvu kódu pro přesměrování a opakujte předchozí kroky.

Pokud začnete se základem knihovny a přesunete směrem ven od základny a otestujete každou vrstvu podle potřeby, přenos je systematický proces, ve kterém jsou problémy izolované na jednu vrstvu kódu současně.

>[!div class="step-by-step"]
>[Next](project-structure.md)
