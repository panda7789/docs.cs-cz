---
title: Standardní rozhraní .NET
description: Další informace o .NET Standard, její verze a implementace rozhraní .NET, které ji podporují.
author: mairaw
ms.author: mairaw
ms.date: 05/18/2018
ms.technology: dotnet-standard
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 8f4490edfc06fcc3ec06daffdb0966ac9ee72e23
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298172"
---
# <a name="net-standard"></a>Standardní rozhraní .NET

[.NET Standard](https://github.com/dotnet/standard) je formální specifikace rozhraní API .NET, která by měla být k dispozici na všech implementace rozhraní .NET. Motivace za .NET Standard je stanovení větší jednotnost v ekosystému .NET. [ECMA 335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) pokračuje k navázání jednotnost chování implementace rozhraní .NET, ale neexistuje žádné podobné specifikace pro knihovny pro třídy Base rozhraní .NET (BCL) pro implementace knihovny .NET. 

Standardní rozhraní .NET umožňuje následující klíčové scénáře: 

- Definuje uniform sadu rozhraní API BCL pro všechny implementace rozhraní .NET pro implementovat, nezávisle na zatížení.
- Umožňuje vývojářům vytvářet přenosné knihovny, které jsou použitelné pro implementace rozhraní .NET, pomocí této stejnou sadu rozhraní API.
- Snižuje nebo i eliminuje Podmíněná kompilace sdílené zdroje z důvodu rozhraní API technologie .NET, pouze pro rozhraní API operačního systému.

Různé implementace rozhraní .NET mít určité verze .NET Standard. Každou verzi implementace rozhraní .NET oznamuje, že nejvyšší .NET Standard verze, které podporuje, příkazu, který znamená, že také podporuje předchozí verze. Například rozhraní .NET Framework 4.6 implementuje standardní 1.3 .NET, což znamená, že zpřístupňuje všechna rozhraní API definované v rozhraní .NET standardní verze 1.0 prostřednictvím 1.3. Podobně rozhraní .NET Framework 4.6.1 implementuje .NET standardní 1.4, zatímco .NET Core 1.0 implementuje standardní 1.6 .NET.

## <a name="net-implementation-support"></a>Podpora implementace rozhraní .NET

V následující tabulce jsou uvedeny všechny verze rozhraní .NET Standard a podporované platformy:

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

K vyhledání nejvyšší verze Standard .NET, můžete se zaměřit, postupujte takto:
1. Najde řádek, která určuje, které chcete spustit na implementaci rozhraní .NET.
2. Sloupec najít v daném řádku, která určuje vaší verzí spouštění zprava doleva.
3. Záhlaví sloupce určuje .NET Standard verzi, která podporuje cílových (a je také podporuje všechny nižší verze .NET Standard).
4. Tento postup opakujte pro každou platformu, kterou chcete zacílit. Pokud máte více než jeden cílovou platformu, měli byste vybrat menší verze mezi nimi. Pokud chcete spustit v rozhraní .NET Framework 4.5 a .NET Core 1.0, je nejvyšší verze .NET Standard, které můžete použít například standardní .NET 1.1.

### <a name="which-net-standard-version-to-target"></a>Která verze .NET Standard k cíli

Při výběru .NET Standard verze, je třeba zvážit tento kompromis:

- Vyšší verzi, další rozhraní API jsou k dispozici.
- Čím nižší verzi, další platformy implementaci.

Obecně doporučujeme cílit *nejnižší* verzi rozhraní .NET standardní možné. Ano po zjistíte, nejvyšší verze .NET Standard, které můžete vybrat, postupujte takto:
1. Cíle další nižší verze .NET Standard a sestavte projekt.
2. Pokud váš projekt sestavení úspěšně, opakujte krok 1. Změňte cíl, jinak hodnota na další vyšší verzi, kterým je verze, kterou byste měli používat.

### <a name="net-standard-versioning-rules"></a>Rozhraní .NET standardní pravidla Správa verzí

Existují dvě pravidla primární Správa verzí:

- Doplňkové: Standardní verze rozhraní .NET jsou logicky soustředných kroužky: vyšších verzí obsahovat všechna rozhraní API z předchozích verzí. Neexistují žádné narušující změny mezi verzemi.
- Neměnný Po odeslání, verze .NET Standard jsou pozastaveny. Nejprve bude dostupná v konkrétní implementace rozhraní .NET, jako je například .NET Core nových rozhraní API. Pokud .NET Standard zkontrolujte panel dochází k závěru, že nová rozhraní API by měly být k dispozici everywhere, přidá se v nové verzi .NET Standard.

## <a name="comparison-to-portable-class-libraries"></a>Porovnání se knihovny přenosných tříd

.NET standard je náhradou [přenosných třída knihovny PCL ()](./cross-platform/cross-platform-development-with-the-portable-class-library.md). .NET Standard zlepšuje na vlastní uživatelské prostředí vytvoření přenosné knihovny Správa standardní BCL a v důsledku vytvoření větší jednotnost napříč implementace rozhraní .NET. Knihovnu, která je cílena .NET Standard je PCL nebo ".NET založené na standardu PCL". Existující PCLs jsou "na základě profilu PCLs".

Profily rozhraní .NET standardní a PCL byly vytvořeny pro podobné účely, ale způsoby klíče se také liší.

Podobnosti:

- Definuje rozhraní API, která lze použít pro sdílení binární kód.

Rozdíly:

- .NET standard je kurátorované sady rozhraní API, zatímco PCL profily jsou definovány průnikům existujícími platformami.
- .NET standard lineárně verze, zatímco PCL profily nepodporují.
- Profily PCL představuje platformy Microsoft, zatímco .NET Standard nerozlišuje platformy.

## <a name="specification"></a>Specifikace

Specifikace .NET Standard je sada standardních rozhraní API. Specifikace se spravuje pomocí rozhraní .NET implementors, konkrétně společnosti Microsoft (zahrnuje rozhraní .NET Framework, .NET Core a Mono) a Unity. Proces veřejné zpětné vazby se používá jako součást vytvoření nové verze .NET Standard prostřednictvím [Githubu](https://github.com/dotnet/standard).

### <a name="official-artifacts"></a>Oficiální artefaktů

Specifikace oficiální je sada .cs soubory, které definují rozhraní API, které jsou součástí standardní. [Ref directory](https://github.com/dotnet/standard/tree/master/netstandard/ref) v [dotnet a standardní úložiště](https://github.com/dotnet/standard) definuje standardní API technologie .NET.

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) metapackage ([zdroj](https://github.com/dotnet/standard/blob/master/netstandard/pkg/NETStandard.Library.dependencies.props)) popisuje sadu knihoven, které definují (součást) jeden nebo více .NET Standard verze.

Dané součásti, jako je System.Runtime, popisuje:

- Část Standard .NET (jenom jeho rozsah).
- Několik verzí .NET Standard pro tento obor.

Odvozené artefakty jsou k dispozici, povolte čtení pohodlnější a povolit určité scénáře developer (například pomocí kompilátor).

- [Rozhraní API seznamu v markdownu](https://github.com/dotnet/standard/tree/master/docs/versions)
- Referenční sestavení, distribuovaných jako [balíčky NuGet](../core/packages.md) a odkazuje [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) metapackage.

### <a name="package-representation"></a>Reprezentace balíčku

Vehicle primární distribuce pro .NET Standard referenční sestavení je [balíčky NuGet](../core/packages.md). Implementace budou doručeny různými způsoby, které jsou vhodné pro každý implementace rozhraní .NET.

Balíčky NuGet cílí na jeden nebo více [rozhraní](frameworks.md). .NET Standard balíčky cílí na rozhraní ".NET Standard". Můžete se zaměřit na rozhraní .NET Framework standardní pomocí `netstandard` [compact TFM](frameworks.md) (například `netstandard1.4`). Cílem toto rozhraní by měl být knihovny, které jsou určeny ke spuštění na víc moduly runtime. 

`NETStandard.Library` Metapackage odkazuje kompletní sadu balíčky NuGet, které definují .NET Standard.  Nejběžnější způsob, jak cíl `netstandard` je odkazující na tuto metapackage. Popisuje a poskytuje přístup k ~ 40 knihovny .NET a přidružených rozhraní API, které definují .NET Standard. Další balíčky můžete odkazovat cílených `netstandard` získat přístup k další rozhraní API. 

### <a name="versioning"></a>Správa verzí

Specifikace není jednotném čísle, ale postupně narůstají a lineárně verzí sadu rozhraní API. První verze součásti standardní vytváří základní sada rozhraní API. Další verze přidat rozhraní API a dědí definované v předchozích verzích rozhraní API. Neexistuje žádné zavedených zřizování pro odebrání ze standardní rozhraní API.

.NET standard, která není specifická pro žádné jeden implementace rozhraní .NET, ani neshoduje verze schématu žádnou z těchto moduly runtime.

Přidání rozhraní API do jakéhokoli z implementace (například, rozhraní .NET Framework, .NET Core a Mono) lze považovat za kandidáty pro přidání do specifikace, především v případě, že jsou považované za základní ve své podstatě. Nové [verze rozhraní .NET standardní](https://github.com/dotnet/standard/blob/master/docs/versions.md) vytvářejí podle verze implementace rozhraní .NET, umožňuje cíle nových rozhraní API z standardní PCL rozhraní .NET. Správa verzí mechanismů jsou podrobněji popsané v v [verze rozhraní .NET Core](../core/versions/index.md).

Správa verzí .NET standard je důležité pro použití. S ohledem na rozhraní .NET standardní verzi, můžete použít knihovny, které tuto verzi stejnou nebo nižší. Následující postup popisuje pracovní postup pro používání rozhraní .NET standardní PCLs specifické pro cílení na rozhraní .NET standardní.

- Vyberte .NET Standard verze se má použít pro vaše PCL.
- Použití knihovny, které jsou závislé na stejné verzi rozhraní .NET standardní nebo nižší.
- Pokud najít knihovnu, která je závislá na vyšší verzi rozhraní .NET standardní, buď musíte použít stejnou verzi nebo rozhodnout, že použití této knihovny.

### <a name="pcl-compatibility"></a>PCL kompatibility

.NET standard je kompatibilní s podmnožinu PCL profily. .NET standardní 1.0, 1.1 a 1.2 Každý překrývají s sada PCL profilů. Tato překrývají byl vytvořen dvou důvodů:

- Povolte .NET Standard na základě PCLs tak, aby odkazovaly na základě profilu PCLs.
- Povolte na základě profilu PCLs k zabalené jako .NET Standard na základě PCLs.

Na základě profilu kompatibility PCL zajišťuje [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) balíček NuGet. Při odkazování na balíčky NuGet, které obsahují PCLs na základě profilu, je potřeba tuto závislost.

Na základě profilu PCLs zabalené jako `netstandard` se snadněji využívat než obvykle zabalené PCLs na základě profilu. `netstandard` balení je kompatibilní s stávající uživatele.

Sady profilů PCL, které jsou kompatibilní s .NET Standard, můžete zjistit: 

| PCL profilu | Standardní rozhraní .NET | PCL platformy
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profile7    | 1.1           | Rozhraní .NET framework 4.5, Windows 8
| Profile31   | 1.0           | Windows 8.1, Windows Phone Silverlight 8.1
| Profile32   | 1.2           | Windows 8.1, Windows Phone 8.1
| Profile44   | 1.2           | Rozhraní .NET framework 4.5.1, Windows 8.1
| Profile49   | 1.0           | Rozhraní .NET framework 4.5, Windows Phone Silverlight 8
| Profile78   | 1.0           | Rozhraní .NET framework 4.5, Windows 8, Windows Phone Silverlight 8
| Profile84   | 1.0           | Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile111  | 1.1           | Rozhraní .NET framework 4.5, Windows 8, Windows Phone 8.1
| Profile151  | 1.2           | Rozhraní .NET framework 4.5.1, Windows 8.1, Windows Phone 8.1
| Profile157  | 1.0           | Windows 8.1, Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile259  | 1.0           | Rozhraní .NET framework 4.5, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8


## <a name="targeting-net-standard"></a>Cílení na rozhraní .NET Standard

Můžete [sestavení standardní knihovny .NET](../core/tutorials/libraries.md) pomocí kombinace `netstandard` framework a NETStandard.Library metapackage. Zobrazí příklady [cílí na Standard .NET pomocí nástrojů .NET Core](../core/packages.md).

## <a name="see-also"></a>Viz také:
[Standardní verze rozhraní .NET](https://github.com/dotnet/standard/blob/master/docs/versions.md)
