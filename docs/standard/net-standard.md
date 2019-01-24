---
title: .NET Standard
description: Další informace o .NET Standard, jeho verze a implementace .NET, kteří jej podporují.
author: mairaw
ms.author: mairaw
ms.date: 07/19/2018
ms.technology: dotnet-standard
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: d759ab8fe436ad68ca67943b7a4330cea093ae52
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535915"
---
# <a name="net-standard"></a>.NET Standard

[.NET Standard](https://github.com/dotnet/standard) je formální specifikaci rozhraní API .NET, která mají být k dispozici na všech implementace .NET. Motivace za .NET Standard navazuje větší sjednocení v ekosystému .NET. [335 Standard ECMA](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) pokračuje k navázání sjednocení pro chování implementace .NET, ale neexistuje žádná podobné specifikace pro knihovny pro třídy Base .NET (BCL) pro implementace knihovny .NET.

.NET Standard umožňuje následující klíčové scénáře:

- Definuje jednotnou sadu BCL API pro všechny implementace .NET k implementaci, nezávisle na úloze.
- Umožňuje vývojářům vytvářet přenosných knihoven, které jsou použitelné v rámci implementace .NET pomocí stejné sady rozhraní API.
- Snižuje nebo dokonce eliminuje podmíněné kompilace sdílené zdroje z důvodu rozhraní API pro .NET, jenom pro rozhraní API operačního systému.

Různé implementace .NET cílit na konkrétní verzi .NET Standard. Každá verze implementace .NET inzeruje, že nejvyšší .NET Standard verze, které podporuje, příkaz, který znamená, že podporuje taky předchozí verze. Například rozhraní .NET Framework 4.6 implementuje .NET Standard 1.3, což znamená, že poskytuje všechna rozhraní API definované v .NET Standard verze 1.0 prostřednictvím 1.3. Obdobně rozhraní .NET Framework 4.6.1 implementuje .NET Standard 1.4, zatímco .NET Core 1.0 implementuje .NET Standard 1.6.

## <a name="net-implementation-support"></a>Podpora pro implementaci rozhraní .NET

V následující tabulce jsou uvedeny minimální verze platformy, které podporují jednotlivé verze rozhraní .NET Standard.

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

K nalezení nejvyšší verze rozhraní .NET Standard, která se může zaměřit, proveďte následující kroky:

1. Najděte řádek, který označuje, který chcete spustit na implementaci rozhraní .NET.
2. Najdete sloupce v daném řádku, která určuje verzi od zprava doleva.
3. Záhlaví sloupce označuje .NET Standard, která podporuje vaše cílové verze. Může také směrovat všechny nižší verze rozhraní .NET Standard. Vyšší verze rozhraní .NET Standard bude také podporovat vaši implementaci.
4. Tento postup opakujte pro každou platformu, kterou chcete cílit. Pokud máte více než jedna cílová platforma, měli byste vybrat menší verze mezi nimi. Například pokud chcete spustit v rozhraní .NET Framework 4.5 a .NET Core 1.0, nejvyšší verze .NET Standard, která vám pomůže je standardní 1.1 rozhraní .NET.

### <a name="which-net-standard-version-to-target"></a>Kterou verzi .NET Standard do cíle

Při výběru verze .NET Standard, je třeba zvážit tento kompromis:

- Vyšší verzi, další rozhraní API jsou k dispozici.
- Čím nižší verzi, další platformy, pro jeho implementaci.

Obecně platí, doporučujeme vám umožní zacílit *nejnižší* verzi .NET Standard možné. Po nalezení nejvyšší verze .NET Standard, kterou je možné cílit na Ano, postupujte takto:

1. Cílení na další nižší verzi .NET Standard a sestavte projekt.
2. Pokud váš projekt se sestaví úspěšně, opakujte kroku 1. V opačném případě změnit cílení na další vyšší verze a verze, kterou byste měli použít.

Cílení na .NET Standard nižší verze však zavádí řadu závislostí podpory. Pokud váš projekt cílí na .NET Standard 1.x, doporučujeme vám *také* cílit na .NET Standard 2.0. To zjednodušuje graf závislostí pro uživatele vaší knihovny, které běží na rozhraní .NET Standard 2.0 kompatibilní, a snižuje počet balíčků, které potřebují ke stažení.

### <a name="net-standard-versioning-rules"></a>.NET standard pravidla správy verzí

Existují dvě pravidla primární správy verzí:

- Additive: Standardní verze rozhraní .NET jsou logicky soustředných kruhy: vyšších verzích začlenit všechna rozhraní API z předchozích verzí. Nejsou žádné zásadní změny mezi verzí.
- Neměnné: Po vydání verze .NET Standard jsou zmražená. Nová rozhraní API nejdříve zpřístupněny v konkrétní implementace .NET, jako je .NET Core. Pokud panelu .NET Standard revize se řídí zásadou nová rozhraní API by měla být k dispozici pro všechny implementace .NET, přidané v nové verzi .NET Standard.

## <a name="specification"></a>Specifikace

Specifikaci .NET Standard je sada standardních rozhraní API. Specifikace se spravuje pomocí .NET implementors, konkrétně Microsoft (zahrnuje rozhraní .NET Framework a .NET Core, Mono) a Unity. Veřejné zpětnou vazbu proces se používá jako součást vytváření nové verze .NET Standard prostřednictvím [Githubu](https://github.com/dotnet/standard).

### <a name="official-artifacts"></a>Oficiální artefaktů

Oficiální specifikace je sada .cs soubory, které definují rozhraní API, která jsou součástí standardní. [Ref directory](https://github.com/dotnet/standard/tree/master/src/netstandard/ref) v [úložišti dotnet/standard](https://github.com/dotnet/standard) definuje standardní rozhraní API .NET.

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) Microsoft.aspnetcore.all ([zdroj](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)) popisuje sadu knihoven, které definují (částečně) jednu nebo více verzí rozhraní .NET Standard.

Objekt zadaný komponenty, jako jsou `System.Runtime`, popisuje:

- Součást .NET Standard (pouze jeho oboru).
- Několik verzí .NET Standard, pro tento obor.

Odvozená díla artefakty jsou k dispozici, povolte čtení pohodlnější a povolení určitých scénářích pro vývojáře (například pomocí kompilátoru).

- [Rozhraní API seznamu v markdownu](https://github.com/dotnet/standard/tree/master/docs/versions)
- Odkazovat na sestavení, distribuuje jako [balíčky NuGet](../core/packages.md) a odkazuje [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) Microsoft.aspnetcore.all.

### <a name="package-representation"></a>Reprezentace balíčku

Primární distribuce prostředkem pro .NET Standard referenční sestavení je [balíčky NuGet](../core/packages.md). Implementace se doručují různými způsoby, které jsou vhodné pro každou implementaci rozhraní .NET.

Balíčky NuGet cílit na jeden nebo více [architektury](frameworks.md). Balíčky .NET Standard cílit na rozhraní ".NET Standard". Můžete cílit na .NET Standard framework pomocí `netstandard` [compact TFM](frameworks.md) (například `netstandard1.4`). Cílem tohoto rozhraní by měl knihovny, které jsou určeny ke spuštění ve více modulů – runtime. Si nejširší škálu rozhraní API cílit `netstandard2.0` vzhledem k tomu, že počet dostupných rozhraní API více než dvojnásobný až .NET Standard 1.6 2.0.

[ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library/) Microsoft.aspnetcore.all odkazuje na kompletní sadu balíčků NuGet, které definují .NET Standard.  Nejběžnější způsob, jak cílové `netstandard` je pomocí odkazu na toto Microsoft.aspnetcore.all. Popisuje a poskytuje přístup k přibližně 40 knihovny .NET a přidružených rozhraní API, které definují .NET Standard. Můžete využít další balíčky, které se zaměřují `netstandard` získat přístup k další rozhraní API.

### <a name="versioning"></a>Správa verzí

Specifikace není jednotném čísle, ale postupně rozrůstá a lineárně označené verzí sady rozhraní API. První verze standard vytvoří sada standardních rozhraní API. Následné verze přidat rozhraní API a dědí definované v předchozích verzích rozhraní API. Neexistuje žádné zavedené zřizování pro odebrání standardní rozhraní API.

.NET standard, která není specifická pro žádné jedné implementace rozhraní .NET, ani neodpovídá schématu vytváření verzí kterékoli z těchto modulů runtime.

K některému z implementace (například rozhraní .NET Framework, .NET Core a Mono) přidali rozhraní API lze považovat za kandidáty pro přidání do specifikace, zejména v případě, že jsou považované za základní ze své podstaty. Nové [verzích .NET Standard](https://github.com/dotnet/standard/blob/master/docs/versions.md) jsou vytvořeny podle verze implementace .NET, můžete cílit na nová rozhraní API z .NET Standard PCL. Mechanismy správy verzí jsou popsány podrobněji [správy verzí rozhraní .NET Core](../core/versions/index.md).

Je důležité pro použití .NET standard správy verzí. Zadaná .NET Standard verze, můžete použít knihovny cílené na tuto verzi stejné nebo nižší. Následující postup popisuje pracovní postup pro použití .NET Standard PCLs specifické pro cílení na .NET Standard.

- Vyberte verzi .NET Standard pro vaše PCL.
- Použití knihovny, které jsou závislé na stejné verzi .NET Standard nebo nižší.
- Pokud narazíte na knihovnu, která závisí na vyšší verzi rozhraní .NET Standard, buď musíte přijmout stejnou verzi nebo rozhodnot nepoužívat této knihovny.

## <a name="targeting-net-standard"></a>Cílení na .NET Standard

Je možné [vytvářet knihovny .NET Standard](../core/tutorials/libraries.md) pomocí kombinace `netstandard` rozhraní framework a Microsoft.aspnetcore.all NETStandard.Library. Můžete zobrazit příklady [cílí na .NET Standard s nástroji .NET Core](../core/packages.md).

## <a name="net-framework-compatibility-mode"></a>Režim kompatibility rozhraní .NET framework

Počínaje rozhraním .NET Standard 2.0, byla zavedena režimu kompatibility rozhraní .NET Framework. Tento režim kompatibility umožňuje projekty .NET Standard teď k odkazování knihoven .NET Framework, jako kdyby byly zkompilovány pro .NET Standard. Odkazování na knihovny rozhraní .NET Framework nefunguje pro všechny projekty, jako jsou knihovny, které používají Windows Presentation Foundation (WPF) rozhraní API.

Další informace najdete v tématu [režim kompatibility rozhraní .NET Framework](../core/porting/third-party-deps.md#net-framework-compatibility-mode).

## <a name="net-standard-libraries-and-visual-studio"></a>Knihovny .NET standard a sady Visual Studio

Aby bylo možné vytvářet knihovny .NET Standard v sadě Visual Studio, ujistěte se, že máte [Visual Studio 2017 verze 15.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) nebo novější verzi Windows, nebo [Visual Studio pro Mac verze 7.1](https://visualstudio.microsoft.com/vs/visual-studio-mac/) nebo novější verzi macOS.

Pokud potřebujete pouze knihoven .NET Standard 2.0 ve svých projektech, můžete provést také, která v sadě Visual Studio 2015. Ale musíte NuGet nainstalovat klienta 3.6 nebo novější. Můžete stáhnout klienta NuGet pro Visual Studio 2015 z [stáhne NuGet](https://www.nuget.org/downloads) stránky.

## <a name="comparison-to-portable-class-libraries"></a>Porovnání pro přenosné knihovny tříd

.NET standard je náhradou [přenosné knihovny tříd (PCL)](./cross-platform/cross-platform-development-with-the-portable-class-library.md). .NET Standard zlepšuje prostředí tak, že správa standardní BCL a zřízení větší uniformita napříč implementace .NET v důsledku vytvoření přenosných knihoven. Knihovnu, která cílí na .NET Standard je PCL nebo ".NET Standard-based PCL". Existující PCLs jsou "na základě profilu PCLs".

Profily .NET standard a PCL bylo vytvořeno za účelem podobné, ale klíčovými způsoby se také liší.

Podobnosti:

- Definice rozhraní API, která slouží ke sdílení binárního kódu.

Rozdíly:

- .NET standard je kurátorovanou sadu rozhraní API, zatímco PCL profily, které jsou definovány pomocí průniky existujícími platformami.
- .NET standard lineárně verze, zatímco PCL profily tomu tak není.
- Profily PCL představuje platformy Microsoft .NET Standard je nezávislý na platformě.

### <a name="pcl-compatibility"></a>Kompatibilita PCL

.NET standard je kompatibilní s použitím podmnožiny PCL profily. Rozhraní .NET standard 1.0, 1.1 a 1.2 Každý překrytí sadu PCL profily. Toto překrývání bylo vytvořeno za dva důvody:

- Povolte .NET Standard na základě PCLs tak, aby odkazovaly na základě profilu PCLs.
- Povolte na základě profilu PCLs chcete mít podobu balíčku .NET Standard na základě PCLs.

Je poskytován na základě profilu PCL kompatibility [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) balíček NuGet. Při odkazování na balíčky NuGet, které obsahují PCLs na základě profilu je potřeba tuto závislost.

Na základě profilu PCLs lze zabalit jako `netstandard` usnadňuje využívání než obvykle zabalené PCLs na základě profilu. `netstandard` balení je kompatibilní se stávajícím uživatelům.

Můžete vidět sadu PCL profily, které jsou kompatibilní s .NET Standard:

| Profilem PCL | .NET Standard | PCL platformy
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profile7    | 1.1           | .NET Framework 4.5, Windows 8
| Profile31   | 1.0           | Windows 8.1, Windows Phone Silverlight 8.1
| Profile32   | 1.2           | Windows 8.1, Windows Phone 8.1
| Profile44   | 1.2           | Rozhraní .NET framework 4.5.1, Windows 8.1
| Profile49   | 1.0           | Rozhraní .NET framework 4.5, Windows Phone Silverlight 8
| Profile78   | 1.0           | Rozhraní .NET framework 4.5, Windows 8, Windows Phone Silverlight 8
| Profile84   | 1.0           | Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile111  | 1.1           | Rozhraní .NET framework 4.5, Windows 8, Windows Phone 8.1
| Profile151  | 1.2           | .NET Framework 4.5.1, Windows 8.1, Windows Phone 8.1
| Profile157  | 1.0           | Windows 8.1, Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile259  | 1.0           | Rozhraní .NET framework 4.5, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8

## <a name="see-also"></a>Viz také:

- [Verze rozhraní .NET standard](https://github.com/dotnet/standard/blob/master/docs/versions.md)
