---
title: Knihovny portů do jádra .NET Core
description: Zjistěte, jak portovat projekty knihovny z rozhraní .NET Framework do jádra .NET.
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 68fe36e543d949dc76bdb0c19ef3482936ad9e79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398907"
---
# <a name="port-net-framework-libraries-to-net-core"></a>Port .NET Framework knihovny na .NET Core

Naučte se portovat kód knihovny Rozhraní .NET Framework do .NET Core, kde se spouští napříč platformami a rozšiřuje dosah aplikací, které ji používají.

## <a name="prerequisites"></a>Požadavky

Tento článek předpokládá, že:

- Používají visual studio 2017 nebo novější. (.NET Core není podporována v dřívějších verzích Sady Visual Studio.)
- Seznamte se s [doporučeným procesem přenosu](index.md).
- Byly vyřešeny všechny problémy se [závislostmi třetích stran](third-party-deps.md).

Měli byste se také seznámit s obsahem následujících článků:

[Standard .NET](../../standard/net-standard.md)\
Tento článek popisuje formální specifikaci rozhraní API rozhraní .NET, které jsou určeny k dispozici na všech implementacích rozhraní .NET.

[Balíčky, metabalíčky a rámce](../packages.md)\
Tento článek popisuje, jak rozhraní .NET Core definuje a používá balíčky a jak balíčky podporují kód spuštěný na více implementacích rozhraní .NET.

[Vývoj knihoven pomocí nástrojů pro různé platformy](../tutorials/libraries.md)\
Tento článek vysvětluje, jak psát knihovny pomocí rozhraní CLI jádra .NET.

[Dodatky k formátu *csproj* pro .NET Core](../tools/csproj.md)\
Tento článek popisuje změny, které byly přidány do souboru projektu jako součást přesunutí *csproj* a MSBuild.

[Přenos na jádro .NET – analýza závislostí třetích stran](third-party-deps.md)\
Tento článek popisuje přenositelnost závislostí třetích stran a co dělat, když závislost balíčku NuGet nespustí na .NET Core.

## <a name="retarget-to-net-framework-472"></a>Přecílení na rozhraní .NET Framework 4.7.2

Pokud váš kód není cílení .NET Framework 4.7.2, doporučujeme znovu zacílit na rozhraní .NET Framework 4.7.2. Tím je zajištěna dostupnost nejnovějších alternativ rozhraní API pro případy, kdy standard .NET nepodporuje existující rozhraní API.

Pro každý z projektů, které chcete portovat, postupujte v sadě Visual Studio takto:

1. Klikněte pravým tlačítkem myši na projekt a vyberte **příkaz Vlastnosti**.
1. V rozevíracím souboru **Cílová architektura** vyberte **rozhraní .NET Framework 4.7.2**.
1. Překompilujte projekt.

Vzhledem k tomu, že vaše projekty nyní cíl .NET Framework 4.7.2, použijte tuto verzi rozhraní .NET Framework jako základ pro portování kódu.

## <a name="determine-portability"></a>Určení přenositelnosti

Dalším krokem je spuštění analyzátoru přenositelnosti rozhraní API (ApiPort) pro generování sestavy přenositelnosti pro analýzu.

Ujistěte se, že rozumíte [analyzátoru portability rozhraní API (ApiPort)](../../standard/analyzers/portability-analyzer.md) a způsobu generování sestav přenositelnosti pro cílení na .NET Core. Jak to děláte, se pravděpodobně liší v závislosti na vašich potřebách a osobním vkusu. V následujících částech je podrobně popsáno několik různých přístupů. Můžete najít sami míchání kroky těchto přístupů v závislosti na tom, jak je strukturován váš kód.

### <a name="deal-primarily-with-the-compiler"></a>Zabývat se především kompilátorem

Tento přístup funguje dobře pro malé projekty nebo projekty, které nepoužívají mnoho rozhraní API rozhraní .NET Framework. Přístup je jednoduchý:

1. Volitelně spusťte Rozhraní ApiPort v projektu. Pokud provozujete ApiPort, získejte znalosti ze sestavy o problémech, které budete muset řešit.
1. Zkopírujte veškerý kód do nového projektu .NET Core.
1. Při odkazování na sestavu přenositelnosti (pokud jsou generovány), vyřešit chyby kompilátoru, dokud se plně nezkompiluje projekt.

I když je nestrukturovaný, tento přístup zaměřený na kód často řeší problémy rychle. Projekt, který obsahuje pouze datové modely může být ideálním kandidátem pro tento přístup.

### <a name="stay-on-the-net-framework-until-portability-issues-are-resolved"></a>Zůstaňte v rozhraní .NET Framework, dokud nebudou vyřešeny problémy s přenositelností

Tento přístup může být nejlepší, pokud dáváte přednost kódu, který se zkompiluje během celého procesu. Přístup je následující:

1. Spusťte Rozhraní ApiPort v projektu.
1. Řešení problémů pomocí různých přenosných api.
1. Vezměte na vědomí všechny oblasti, kde máte možnost používat přímou alternativu.
1. Opakujte předchozí kroky pro všechny projekty, které přepojíte, dokud si nejste jisti, že každý z nich je připraven ke kopírování do nového projektu .NET Core.
1. Zkopírujte kód do nového projektu .NET Core.
1. Vypracujte všechny problémy, kde jste si všimli, že přímá alternativa neexistuje.

Tento pečlivý přístup je strukturovanější než pouhé zpracování chyb kompilátoru, ale je stále relativně zaměřený na kód a má tu výhodu, že má vždy kód, který kompiluje. Způsob řešení určitých problémů, které nelze vyřešit pouhým použitím jiného rozhraní API, se značně liší. Možná zjistíte, že je třeba vypracovat komplexnější plán pro určité projekty, který je zahrnut v příštím přístupu.

### <a name="develop-a-comprehensive-plan-of-attack"></a>Vypracovat komplexní plán útoku

Tento přístup může být nejvhodnější pro větší a složitější projekty, kde restrukturalizační kód nebo úplné přepsání určitých oblastí kódu může být nezbytné pro podporu .NET Core. Přístup je následující:

1. Spusťte Rozhraní ApiPort v projektu.
1. Zjistěte, kde se jednotlivé nepřenosné typy používají a jak to ovlivňuje celkovou přenositelnost.
   - Pochopit povahu těchto typů. Jsou malé v počtu, ale často se používají? Jsou velké v počtu, ale používají se zřídka? Je jejich použití koncentrované, nebo je rozloženo v celém kódu?
   - Je snadné izolovat kód, který není přenosný, takže se s ním můžete vypořádat efektivněji?
   - Potřebujete refaktorovat svůj kód?
   - Pro ty typy, které nejsou přenosné, existují alternativní api, která provádějí stejný úkol? Například pokud používáte třídu, <xref:System.Net.WebClient> můžete být schopni <xref:System.Net.Http.HttpClient> použít třídu místo.
   - Existují různá přenosná rozhraní API, která mohou být k dispozici k provedení úkolu, i když se nejedná o náhradu za přetažení? Například pokud používáte <xref:System.Xml.Schema.XmlSchema> k analýzě XML, ale nevyžadují zjišťování schématu XML, můžete použít <xref:System.Xml.Linq> rozhraní API a implementovat analýzu sami na rozdíl od spoléhání se na rozhraní API.
1. Pokud máte sestavení, která je obtížné portovat, stojí za to je prozatím ponechat v rozhraní .NET Framework? Zde je několik věcí, které je třeba zvážit:
   - V knihovně mohou být některé funkce, které nejsou kompatibilní s jádrem .NET Core, protože příliš silně závisí na rozhraní .NET Framework nebo funkcích specifických pro systém Windows. Stojí za to nechat tuto funkci prozatím za sebou a uvolnit dočasnou verzi knihovny .NET Core s menšími funkcemi, dokud nebudou k dispozici prostředky pro přenos funkcí?
   - Pomohl by refaktor?
1. Je rozumné napsat vlastní implementaci nedostupného rozhraní API rozhraní .NET Framework?
   Můžete zvážit kopírování, úpravy a použití kódu ze [zdroje odkazu rozhraní .NET Framework](https://github.com/Microsoft/referencesource). Referenční zdrojový kód je licencován pod [licencí MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), takže máte značnou svobodu používat zdroj jako základ pro svůj vlastní kód. Jen se ujistěte, že správně atribut Microsoft ve vašem kódu.
1. Tento postup opakujte podle potřeby pro různé projekty.

Fáze analýzy může nějakou dobu trvat v závislosti na velikosti základu kódu. Trávit čas v této fázi důkladně pochopit rozsah potřebných změn a vytvořit plán obvykle šetří čas v dlouhodobém horizontu, zejména pokud máte komplexní základ kódu.

Váš plán může zahrnovat provádění významných změn v základu kódu při stále cílení .NET Framework 4.7.2, což je strukturovanější verze předchozího přístupu. Způsob provádění plánu závisí na základu kódu.

### <a name="mixed-approach"></a>Smíšený přístup

Je pravděpodobné, že budete míchat výše uvedené přístupy na základě projektu. Měli byste udělat to, co dává největší smysl pro vás a pro váš základ kódu.

## <a name="port-your-tests"></a>Port vaše testy

Nejlepší způsob, jak zajistit, aby vše fungovalo, když jste portovali kód, je otestovat kód při přenosu do .NET Core. Chcete-li to provést, budete muset použít rozhraní pro testování, které vytváří a spouští testy pro .NET Core. V současné době máte tři možnosti:

- [xJednotka](https://xunit.github.io/)
  - [Začínáme](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  - [Nástroj pro převod projektu MSTest na xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NJednotka](https://nunit.org/)
  - [Začínáme](https://github.com/nunit/docs/wiki/Installation)
  - [Příspěvek na blogu o migraci z MSTestu na NUnit](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](/visualstudio/test/unit-test-basics)

## <a name="recommended-approach"></a>Doporučený přístup

Nakonec přenos úsilí závisí do značné míry na tom, jak je strukturován kód rozhraní .NET Framework. Dobrým způsobem přenosu kódu je začít se *základnou* knihovny, což jsou základní součásti kódu. To může být datové modely nebo některé jiné základní třídy a metody, které vše ostatní používá přímo nebo nepřímo.

1. Port testovací projekt, který testuje vrstvu knihovny, kterou právě portujete.
1. Zkopírujte základnu knihovny do nového projektu .NET Core a vyberte verzi standardu .NET, kterou chcete podporovat.
1. Proveďte všechny změny potřebné k získání kódu ke kompilaci. Hodně z toho může vyžadovat přidání nuget balíček závislostí do souboru *csproj.*
1. Spusťte testy a proveďte potřebné úpravy.
1. Vyberte další vrstvu kódu, kterou chcete přenést, a opakujte předchozí kroky.

Pokud začnete se základnou knihovny a přesunete se ven ze základny a podle potřeby otestujete každou vrstvu, přenos je systematický proces, při kterém jsou problémy izolovány na jednu vrstvu kódu najednou.

## <a name="next-steps"></a>Další kroky

>[!div class="nextstepaction"]
>[Uspořádání projektů pro .NET Core](project-structure.md)
