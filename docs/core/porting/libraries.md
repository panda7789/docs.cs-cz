---
title: Port knihoven pro .NET Core
description: Zjistěte, jak přenést projekty knihovny z rozhraní .NET Framework do .NET Core.
author: cartermp
ms.date: 12/7/2018
ms.custom: seodec18
ms.openlocfilehash: 8190dcfd3ffed9051c7724752a19d88e7bef4f4d
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904704"
---
# <a name="port-net-framework-libraries-to-net-core"></a>Port knihovny rozhraní .NET Framework do .NET Core

Zjistěte, jak přenést kód knihovny rozhraní .NET Framework do .NET Core, ke spuštění napříč platformami a rozšiřte dosah aplikací, které ji používají.

## <a name="prerequisites"></a>Požadavky

Tento článek předpokládá, že jste:

- Používání sady Visual Studio 2017 nebo novější.
  - .NET core není podporované v dřívějších verzích sady Visual Studio
- Vysvětlení [doporučuje portování procesu](index.md).
- Byly vyřešeny problémy s [závislostí třetích stran](third-party-deps.md).

Měli byste si také se seznámit s obsahem v následujících tématech:

[.NET Standard](~/docs/standard/net-standard.md)   
Toto téma popisuje formální specifikaci rozhraní API .NET, která mají být k dispozici na všech implementace .NET.

[Balíčky, Metabalíčky a architektury](~/docs/core/packages.md)   
Tento článek popisuje, jak definuje a používá balíčky .NET Core a jak balíčky podporují kód spuštěný na více implementací rozhraní .NET.

[Vývoj knihoven pomocí nástrojů pro různé platformy](~/docs/core/tutorials/libraries.md)   
Toto téma vysvětluje, jak psát knihoven pro .NET pomocí nástrojů příkazového řádku pro různé platformy.

[Doplňky *csproj* formát pro .NET Core](~/docs/core/tools/csproj.md)   
Tento článek popisuje změny, které byly přidány do souboru projektu jako součást přesunu do *csproj* a MSBuild.

[Přenos aplikací .NET Core – analýza závislostí třetích stran strany](~/docs/core/porting/third-party-deps.md)   
Toto téma popisuje přenositelnost závislostí třetích stran a co dělat, když závislost balíčku NuGet není spuštěna v rozhraní .NET Core.

## <a name="retargeting-your-net-framework-code-to-net-framework-472"></a>Mění se cílení na rozhraní .NET Framework 4.7.2 kódu rozhraní .NET Framework

Pokud je váš kód není zaměřen na rozhraní .NET Framework 4.7.2, doporučujeme změnit cílení na rozhraní .NET Framework 4.7.2. Tím se zajistí dostupnosti nejnovější alternativy rozhraní API pro případy, kdy .NET Standard nepodporuje existující rozhraní API.

Pro každý ze svých projektů v sadě Visual Studio, budete chtít port, postupujte takto:

1. Klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**.
1. V **Cílová architektura** rozevíracího seznamu vyberte **rozhraní .NET Framework 4.7.2**.
1. Znovu zkompilujte vaše projekty.

Protože projekty teď cílí na rozhraní .NET Framework 4.7.2, použijte tuto verzi rozhraní .NET Framework jako základu pro portování kódu.

## <a name="determining-the-portability-of-your-code"></a>Určení přenositelnost kódu

Dalším krokem je spuštění Portability Analyzeru rozhraní API (ApiPort), aby se vygenerovala sestava přenositelnost pro analýzu.

Ujistěte se, že rozumíte [analyzátor přenositelnosti rozhraní API (ApiPort)](../../standard/analyzers/portability-analyzer.md) a generování sestav přenositelnost pro cílení na .NET Core. Postup tuto pravděpodobně se liší podle vašich potřeb a osobní chutí. Následují několik různých přístupů. Může být pro vás sami kombinování kroky těchto přístupů v závislosti na tom, jak váš kód strukturovaná.

### <a name="dealing-primarily-with-the-compiler"></a>Především zabývají kompilátor

Tento přístup může být nejvhodnější pro malé projekty nebo projekty, které nepoužívají mnoho rozhraní API .NET Framework. Tento přístup je jednoduchý:

1. Volitelně můžete spustit ApiPort na váš projekt. Pokud spustíte ApiPort, seznamte se ze sestavy na problémy, se kterými budete potřebovat adresu.
1. Zkopírujte celý kód do nového projektu .NET Core.
1. Při odkazování na sestavy přenositelnost (je-li generovat), řešení chyb kompilátoru, dokud se projekt zkompiluje plně.

Přestože tento přístup nestrukturovaných, přístup zaměřený na kód často vede k řešení problémů rychle a může být nejlepším řešením pro menší projekty nebo knihovny. Projekt obsahující pouze datových modelů může být ideální volbou pro tento přístup.

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>Zachování na rozhraní .NET Framework, dokud se nevyřeší problémy s přenositelností

Tento přístup může být nejlepší, pokud chcete mít kód, který zkompiluje během celého procesu. Tento přístup je následujícím způsobem:

1. Spusťte ApiPort na projektu.
1. Řešení potíží s pomocí různých rozhraní API, která jsou přenositelné.
1. Poznamenejte si všechny oblasti, kde budete moci používat s přímým přístupem alternativní.
1. Opakujte předchozí kroky pro všechny projekty, které jste přenos, dokud nejste jisti, že každá je připraven k zkopírovat do nového projektu .NET Core.
1. Zkopírujte kód do nového projektu .NET Core.
1. Fungovat případné potíže, pokud jste si poznamenali, že s přímým přístupem alternativní neexistuje.

Tento přístup opatrní je více strukturovanými než jednoduše práce si chyby kompilátoru, ale je stále poměrně zaměřený na kód a má výhodu vždy mít kód, který zkompiluje. Způsob, jak vyřešit některé problémy, které nejde ji adresovat podle pouze pomocí jiného rozhraní API se výrazně liší. Můžete zjistit, které potřebujete pro vývoj další komplexní plánování pro určité projekty, které se vztahuje na další přístup se považuje za.

### <a name="developing-a-comprehensive-plan-of-attack"></a>Komplexní plán útoku

Tento přístup může být nejvhodnější pro projekty větší a složitější, kde změna struktury kódu nebo zcela přepsání některých oblastech kódu může být potřeba podporovat .NET Core. Tento přístup je následujícím způsobem:

1. Spusťte ApiPort na projektu.
1. Vysvětlení použití jednotlivých typů nepřenosné a že má vliv celkové přenositelnost.
   - Pochopení povahy z těchto typů. Jsou malá v číslech ale používané často? Jsou velké číslo, ale používá zřídka? Jejich používání se soustřeďuje nebo se šíří prostřednictvím vašeho kódu?
   - Je snadné k izolaci kód, který není přenosné, takže můžete s ním naložit efektivněji?
   - Je třeba jak Refaktorovat kód?
   - Pro tyto typy, které nejsou přenosné existují alternativní rozhraní API, která stejný úkol provést? Například pokud používáte <xref:System.Net.WebClient> třídy, je možné použít <xref:System.Net.Http.HttpClient> namísto třídy.
   - Existují různé Přenositelná rozhraní API dostupné pro provádění různých úloh, i v případě, že se nejedná o což je náhrada databáze? Například pokud používáte <xref:System.Xml.Schema.XmlSchema> k analyzovat soubor XML, ale nevyžadují XML schématu zjišťování, které můžete využít <xref:System.Xml.Linq> rozhraní API a implementovat parsování sami na rozdíl od spoléhání se na rozhraní API.
1. Pokud máte sestavení, které je obtížné port stojí všechnu je nyní v rozhraní .NET Framework? Tady je pár věcí k uvážení:
   - Některé funkce mohou mít v knihovně, která je nekompatibilní s .NET Core, protože příliš často závisí na funkcích rozhraní .NET Framework nebo s Windows. Je může být vhodné zanechání, které tuto funkci teď a uvolněním verzi .NET Core knihovny s méně funkcemi dočasně, dokud prostředky jsou k dispozici k portu funkce?
   - By Refaktorujte pomoct?
1. Je přijatelné pro zápis vlastní implementaci rozhraní není k dispozici rozhraní API .NET?
   Zvažte kopírování, úpravou a použitím kódu z [referenční zdroje rozhraní .NET Framework](https://github.com/Microsoft/referencesource). Odkaz na zdrojový kód je licencován [licencí MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), takže budete mít významný dá volnost, abyste zdroj jako základ pro váš vlastní kód. Jenom nezapomeňte správně atribut Microsoft ve vašem kódu.
1. Tento postup opakujte podle potřeby pro různé projekty.
 
Z analytické fáze může chvíli trvat v závislosti na velikosti vašeho základu kódu. Výdaje v této fázi chcete důkladně porozumět rozsahu, změny potřebné a obvykle při vytváření plánu vám ušetří čas čas v dlouhodobém horizontu, zejména v případě, že máte komplexní základ kódu.

Váš plán může zahrnovat provedení významných změn do vašeho základu kódu zároveň stále cílí na rozhraní .NET Framework 4.7.2, takže jde strukturovanějších verzi předchozí postup. Jak přejít o spuštění vašeho plánu je závislá na vašem základu kódu.

### <a name="mixing-approaches"></a>Kombinováním přístupů

Je pravděpodobné, že budete kombinaci výše uvedených přístupů na základě jednotlivých projektů. Byste měli dělat to, co vám nejvíce vyhovuje vám a pro vašeho základu kódu.

## <a name="porting-your-tests"></a>Portování testů

Nejlepší způsob, jak Ujistěte se, že všechno funguje, když jste přenést váš kód je k testování kódu, protože port až po .NET Core. K tomuto účelu, budete muset použít testovací rozhraní, které sestaví a spustí testy pro .NET Core. V současné době máte tři možnosti:

- [xUnit](https://xunit.github.io/)
  * [Začínáme](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [Nástroj pro převod projekt MSTest xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  * [Začínáme](https://github.com/nunit/docs/wiki/Installation)
  * [Blogový příspěvek o migraci z MSTest na NUnit](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>Doporučený postup pro přenos

Nakonec přenosem úsilí závisí do značné míry na strukturování kódu rozhraní .NET Framework. Než začneme je dobrým způsobem, jak přeneste kód *základní* knihovny, které jsou základní součástí kódu. To může být datové modely nebo některé základní třídy a metody, které všechno ostatní používá přímo nebo nepřímo.

1. Port testovacího projektu, který testuje vrstvě knihovny, který jste právě přenos.
1. Zkopírovat základní knihovny do nového projektu .NET Core a vyberte verzi jazyka .NET Standard si přejete podporovat.
1. Proveďte změny nutná, aby se kód mohl zkompilovat. Velká část to může být nutné přidat závislosti balíčků NuGet do vaší *csproj* souboru.
1. Spustit testy a provést všechny potřebné úpravy.
1. Vyberte další vrstvu kódu na port a opakujte předchozí kroky.

Je-li začít se základnou knihovny a přesunout ven ze základní třídy a otestovat každou vrstvu podle potřeby, přenos provádí systematické kde problémy jsou izolované na jednu vrstvu kódu v čase.

>[!div class="step-by-step"]
>[Next](project-structure.md)
