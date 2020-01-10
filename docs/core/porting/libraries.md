---
title: Knihovny portů do .NET Core
description: Naučte se, jak přenést projekty knihovny z .NET Framework do .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 6ff38647f77bbe1d25dd1d0065c4b32c60f87fcd
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777351"
---
# <a name="port-net-framework-libraries-to-net-core"></a>Port .NET Framework knihovny do .NET Core

Naučte se, jak portovat kód .NET Framework knihovny do .NET Core, kde běží na různých platformách a rozšiřuje dosah aplikací, které ho používají.

## <a name="prerequisites"></a>Požadavky

V tomto článku se předpokládá, že máte následující:

- Používáte Visual Studio 2017 nebo novější. (.NET Core není podporované v dřívějších verzích sady Visual Studio.)
- Pochopení [doporučeného procesu přenosu](index.md).
- Vyřešily se případné problémy se [závislostmi třetích stran](third-party-deps.md).

Měli byste se také seznámit s obsahem následujících článků:

[.NET Standard](../../standard/net-standard.md)\
Tento článek popisuje formální specifikaci rozhraní API .NET, která jsou určená k dispozici pro všechny implementace rozhraní .NET.

[Balíčky, metabalíčky a rozhraní](../packages.md)\
Tento článek popisuje, jak .NET Core definuje a používá balíčky a jak balíčky podporují kód běžící na více implementacích rozhraní .NET.

[Vývoj knihoven pomocí nástrojů pro různé platformy](../tutorials/libraries.md)\
Tento článek vysvětluje, jak psát knihovny pro .NET pomocí nástrojů rozhraní příkazového řádku pro různé platformy.

[Přidání do formátu *csproj* pro .NET Core](../tools/csproj.md)\
Tento článek popisuje změny, které byly přidány do souboru projektu v rámci přesunutí do *csproj* a MSBuild.

[Přenos do .NET Core – analýza závislostí](third-party-deps.md) jiných výrobců\
Tento článek pojednává o přenositelnosti závislostí třetích stran a o tom, co dělat, když se závislost balíčku NuGet nespustí v .NET Core.

## <a name="retarget-to-net-framework-472"></a>Změnit cílení na .NET Framework 4.7.2

Pokud váš kód necílí na .NET Framework 4.7.2, doporučujeme změnit cílení na .NET Framework 4.7.2. Tím se zajistí dostupnost nejnovějších alternativ rozhraní API pro případy, kdy .NET Standard nepodporuje existující rozhraní API.

Pro každý z projektů, které chcete přenést, proveďte následující kroky v aplikaci Visual Studio:

1. Klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**.
1. V rozevíracím seznamu **cílové rozhraní** vyberte **.NET Framework 4.7.2**.
1. Zkompilujte projekt znovu.

Vzhledem k tomu, že vaše projekty teď cílí na .NET Framework 4.7.2, použijte tuto verzi .NET Framework jako základ pro přenos kódu.

## <a name="determine-portability"></a>Určení přenositelnosti

Dalším krokem je spuštění analyzátoru přenositelnosti rozhraní API (ApiPort), aby se vygenerovala sestava přenositelnosti pro analýzu.

Ujistěte se, že rozumíte [analyzátoru přenositelnosti rozhraní API (ApiPort)](../../standard/analyzers/portability-analyzer.md) a jak generovat sestavy přenositelnosti pro cílení na .NET Core. Jak to můžete udělat, se může lišit podle vašich potřeb a osobního příchuti. Následující části podrobně popisují několik různých přístupů. V závislosti na tom, jak je váš kód strukturován, se můžete setkat s kombinací kroků těchto přístupů.

### <a name="deal-primarily-with-the-compiler"></a>Primárně se zabývat kompilátorem

Tento přístup funguje dobře pro malé projekty nebo projekty, které nepoužívají mnoho .NET Framework rozhraní API. Přístup je jednoduchý:

1. Volitelně můžete v projektu spustit ApiPort. Pokud spustíte ApiPort, získáte znalosti ze sestavy o problémech, které budete potřebovat řešit.
1. Zkopírujte veškerý kód do nového projektu .NET Core.
1. Při odkazování na sestavu přenositelnosti (Pokud je vygenerováno) se vyřeší chyby kompilátoru, dokud se projekt zcela zkompiluje.

I když je nestrukturované, tento přístup zaměřený na kód často řeší problémy rychleji. Projekt, který obsahuje pouze datové modely, může být ideálním kandidátem pro tento přístup.

### <a name="stay-on-the-net-framework-until-portability-issues-are-resolved"></a>Zůstat na .NET Framework dokud nebudou vyřešeny problémy s přenositelností

Tento přístup může být nejlepší, pokud dáváte přednost kódu, který se zkompiluje během celého procesu. Přístup je následující:

1. Spusťte ApiPort na projektu.
1. Vyřešte problémy pomocí různých rozhraní API, která jsou přenosná.
1. Poznamenejte si všechny oblasti, ve kterých se vám zabrání použití přímé alternativy.
1. Předchozí kroky opakujte pro všechny projekty, které chcete přenést, dokud si nejste jisti, že jsou všechny připravené k zkopírování do nového projektu .NET Core.
1. Zkopírujte kód do nového projektu .NET Core.
1. Vypracujte všechny problémy, kde jste si poznamenali, že nějaká přímá alternativa neexistuje.

Tento pečlivý přístup je více strukturovaný než pouhá práce s kompilátorem, ale je stále poměrně zaměřený na kód a má výhodu vždy, co kompiluje kód. Způsob řešení některých problémů, které nebylo možné vyřešit pouhým použitím jiného rozhraní API, se výrazně liší. Může se stát, že budete potřebovat sestavit komplexnější plán pro určité projekty, který je popsaný v dalším postupu.

### <a name="develop-a-comprehensive-plan-of-attack"></a>Vývoj komplexního plánu útoků

Tento přístup může být nejvhodnější pro větší a složitější projekty, kde může být změna struktury kódu nebo zcela přepisování některých oblastí kódu nutná k podpoře .NET Core. Přístup je následující:

1. Spusťte ApiPort na projektu.
1. Zjistěte, kde se používá každý nepřenosný typ a jak ovlivňuje celkovou přenositelnost.
   - Pochopte charakter těchto typů. Jsou malými čísly, ale často se používají? Jsou velké v čísle, ale používány zřídka? Je jejich použití zahuštěné nebo rozdělené do celého kódu?
   - Je snadné izolovat kód, který není přenosný, abyste se mohli efektivněji zabývat?
   - Potřebujete Refaktorovat kód?
   - U typů, které nejsou přenosné, existují alternativní rozhraní API, která mají stejný úkol? Například pokud používáte třídu <xref:System.Net.WebClient>, je možné místo toho použít třídu <xref:System.Net.Http.HttpClient>.
   - Jsou k dispozici různá přenosná rozhraní API k provedení úkolu, i když není náhrada odkládacího zařízení? Například pokud používáte <xref:System.Xml.Schema.XmlSchema> k analýze XML, ale nepotřebujete zjišťování schématu XML, můžete použít rozhraní API <xref:System.Xml.Linq> a implementovat analýzu sami, a to na rozdíl od toho, aby se spoléhá na rozhraní API.
1. Pokud máte sestavení, která se obtížně portují, je vhodné je nechat .NET Framework pro teď? Tady je několik věcí, které je potřeba vzít v úvahu:
   - Je možné, že máte v knihovně některé funkce, které jsou nekompatibilní s .NET Core, protože spoléhá na .NET Framework nebo specifické funkce systému Windows příliš mnoho. Stojí za to, aby se teď funkce zanechala a uvolnila dočasná verze .NET Core vaší knihovny s menšími funkcemi, dokud nebudou k dispozici prostředky pro přenos funkcí?
   - Je refaktorovaná?
1. Je rozumné napsat vlastní implementaci nedostupného .NET Framework rozhraní API?
   Můžete zvážit kopírování, úpravy a používání kódu z [.NET Frameworkho zdroje odkazů](https://github.com/Microsoft/referencesource). Zdrojový kód odkazu je licencován v rámci [licence MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), takže máte významnou volnost v používání zdroje jako základu pro váš vlastní kód. Stačí se ujistit, že v kódu budete správně atribut Microsoft.
1. Tento postup opakujte podle potřeby pro různé projekty.
 
Fáze analýzy může určitou dobu trvat v závislosti na velikosti vašeho základu kódu. Doba útraty v této fázi k důkladnému pochopení rozsahu změn potřebných pro vývoj plánu obvykle šetří čas v dlouhodobém běhu, zejména v případě, že máte složitý základ kódu.

Váš plán by mohl zahrnovat významné změny v základu kódu a přitom stále cílit .NET Framework 4.7.2, takže tato verze je podrobněji sestavená. Způsob provádění plánu závisí na základu kódu.

### <a name="mixed-approach"></a>Smíšený přístup

Je možné, že se výše uvedené přístupy budou kombinovat na základě jednotlivých projektů. Měli byste postupovat podle svých potřeb a základu kódu.

## <a name="port-your-tests"></a>Portování testů

Nejlepším způsobem, jak zajistit, aby vše fungovalo, když jste svůj kód nastavili jako port, je testování kódu při jeho přenosu do .NET Core. K tomu je nutné použít testovací rozhraní, které sestaví a spustí testy pro .NET Core. V současné době máte tři možnosti:

- [xUnit](https://xunit.github.io/)
  - [Začínáme](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  - [Nástroj k převedení projektu MSTest na xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  - [Začínáme](https://github.com/nunit/docs/wiki/Installation)
  - [Příspěvek na blogu o migraci z MSTest na NUnit](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](/visualstudio/test/unit-test-basics)

## <a name="recommended-approach"></a>Doporučený postup

V konečném důsledku je přenosová intenzita velmi závislá na způsobu strukturování kódu .NET Framework. Dobrým způsobem, jak portovat váš kód, je začít se základem vaší knihovny, což je *základní* komponenty kódu. Může se jednat o datové modely nebo jiné základní třídy a metody, které jinak používá přímo nebo nepřímo.

1. Port testovacího projektu, který testuje vrstvu vaší knihovny, kterou právě napojujete.
1. Zkopírujte základnu vaší knihovny do nového projektu .NET Core a vyberte verzi .NET Standard, kterou chcete podporovat.
1. Proveďte potřebné změny k získání kódu pro zkompilování. Většina toho může vyžadovat přidání závislostí balíčku NuGet do souboru *csproj* .
1. Spusťte testy a proveďte potřebné úpravy.
1. Vyberte další vrstvu kódu pro přesměrování a opakujte předchozí kroky.

Pokud začnete se základem knihovny a přesunete směrem ven od základny a otestujete každou vrstvu podle potřeby, přenos je systematický proces, ve kterém jsou problémy izolované na jednu vrstvu kódu současně.

## <a name="next-steps"></a>Další kroky

>[!div class="nextstepaction"]
>[Uspořádání projektů pro .NET Core](project-structure.md)
