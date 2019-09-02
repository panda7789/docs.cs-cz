---
title: .NET Standard
description: Seznamte se s .NET Standard, jejími verzemi a implementacemi rozhraní .NET, které ho podporují.
author: mairaw
ms.author: mairaw
ms.date: 08/30/2019
ms.technology: dotnet-standard
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: f479bbec504a965fde08af6d000d4be75ca85f8d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205599"
---
# <a name="net-standard"></a>.NET Standard

[.NET Standard](https://github.com/dotnet/standard) je formální specifikace rozhraní API .NET, která jsou určená k dispozici pro všechny implementace .NET. Motivace za .NET Standard vytváří větší jednotnost v ekosystému .NET. [ECMA 335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) pokračuje v vytváření jednotnosti pro chování implementace rozhraní .NET, ale pro implementace knihovny .NET není k dispozici podobná specifikace pro knihovny tříd .NET Base (BCL).

.NET Standard umožňuje následující klíčové scénáře:

- Definuje jednotnou sadu rozhraní BCL API pro všechny implementace .NET, které se mají implementovat, nezávisle na úlohách.
- Umožňuje vývojářům vytvářet přenosné knihovny, které jsou použitelné napříč implementacemi rozhraní .NET, a to pomocí stejné sady rozhraní API.
- Snižuje nebo eliminuje podmíněnou kompilaci sdíleného zdroje v důsledku rozhraní API .NET, pouze pro rozhraní API operačního systému.

Různé implementace rozhraní .NET cílí na konkrétní verze .NET Standard. Každá verze implementace rozhraní .NET oznamuje nejvyšší .NET Standard verzi, kterou podporuje, příkaz, který znamená, že podporuje také předchozí verze. Například .NET Framework 4,6 implementuje .NET Standard 1,3, což znamená, že zveřejňuje všechna rozhraní API definovaná v .NET Standard verzích 1,0 až 1,3. Podobně .NET Framework 4.6.1 implementuje .NET Standard 1,4, zatímco .NET Core 1,0 implementuje .NET Standard 1,6.

## <a name="net-implementation-support"></a>Podpora implementace rozhraní .NET

V následující tabulce jsou uvedeny **minimální** verze platforem, které podporují jednotlivé verze .NET Standard. To znamená, že novější verze uvedené platformy také podporují odpovídající verzi .NET Standard. Například .NET Core 2,2 podporuje .NET Standard 2,0 a starší.

[!INCLUDE [net-standard-table](../../includes/net-standard-table.md)]

Pokud chcete najít nejvyšší verzi .NET Standard, na kterou můžete cílit, postupujte podle následujících kroků:

1. Vyhledejte řádek, který označuje implementaci rozhraní .NET, na které chcete spustit.
2. Vyhledá sloupec v tomto řádku, který indikuje, že vaše verze začíná zprava doleva.
3. Záhlaví sloupce označuje .NET Standard verzi, kterou váš cíl podporuje. Můžete také cílit na jakoukoli nižší .NET Standard verzi. Vyšší verze .NET Standard budou podporovat i vaši implementaci.
4. Tento postup opakujte pro každou platformu, kterou chcete cílit. Pokud máte více než jednu cílovou platformu, měli byste si z nich vybrat menší verzi. Například pokud chcete spustit v .NET Framework 4,5 a .NET Core 1,0, je nejvyšší .NET Standard verze, kterou můžete použít, .NET Standard 1,1.

### <a name="which-net-standard-version-to-target"></a>Která .NET Standard cílová verze

Při volbě .NET Standard verze byste měli vzít v úvahu tento obchod:

- Čím vyšší je verze, tím více rozhraní API máte k dispozici.
- Čím nižší verze, tím více platforem ji implementuje.

Obecně doporučujeme, abyste nacíleni na *nejnižší* možnou verzi .NET Standard. Takže po nalezení nejvyšší .NET Standard verze, kterou můžete cílit, postupujte podle těchto kroků:

1. Zaměřte se na další nižší verzi .NET Standard a sestavte svůj projekt.
2. Pokud se projekt úspěšně sestaví, opakujte krok 1. V opačném případě přecílíte na další vyšší verzi a na verzi, kterou byste měli použít.

Cílení nižší verze .NET Standard ale přináší řadu závislostí podpory. Pokud je váš projekt cílen .NET Standard 1. x, doporučujeme *také* cílit .NET Standard 2,0. Tím se zjednoduší graf závislosti pro uživatele vaší knihovny, které běží na kompatibilních architekturách .NET Standard 2,0, a snižuje počet balíčků, které potřebují ke stažení.

### <a name="net-standard-versioning-rules"></a>Pravidla správy verzí .NET Standard

Existují dvě pravidla primárních verzí:

- Doplňková: verze .NET Standard jsou logicky soustředné kroužky: vyšší verze obsahují všechna rozhraní API z předchozích verzí. Mezi verzemi nejsou žádné průlomové změny.
- Neměnné Po odeslání .NET Standard verze se zmrazují. Nová rozhraní API jsou nejprve k dispozici v konkrétních implementacích .NET, jako je například .NET Core. Pokud .NET Standard šachovnici, že nová rozhraní API by měla být k dispozici pro všechny implementace .NET, přidají se v nové .NET Standard verzi.

## <a name="specification"></a>Specifikace

Specifikace .NET Standard je standardizovaná sada rozhraní API. Specifikace je udržována implementací rozhraní .NET, konkrétně Microsoft (zahrnuje .NET Framework, .NET Core a mono) a Unity. Proces veřejné zpětné vazby se používá jako součást vytváření nových .NET Standard verzí prostřednictvím [GitHubu](https://github.com/dotnet/standard).

### <a name="official-artifacts"></a>Oficiální artefakty

Oficiální specifikace je sada souborů. cs, které definují rozhraní API, která jsou součástí standardu. [Adresář ref](https://github.com/dotnet/standard/tree/master/src/netstandard/ref) v [úložišti dotnet/standard](https://github.com/dotnet/standard) definuje rozhraní .NET Standard API.

[NETStandard. Library](https://www.nuget.org/packages/NETStandard.Library) Metapackage ([zdroj](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)) popisuje sadu knihoven, které definují (částečně) jednu nebo více .NET Standard verzí.

Daná součást, `System.Runtime`například, popisuje:

- Součást .NET Standard (jenom její obor).
- Více verzí .NET Standard pro tento rozsah.

K dispozici jsou odvozené artefakty, které umožňují pohodlnější čtení a povolují některé vývojářské scénáře (například pomocí kompilátoru).

- [Seznam rozhraní API v Markdownu](https://github.com/dotnet/standard/tree/master/docs/versions)
- Referenční sestavení distribuovaná jako [balíčky NuGet](../core/packages.md) a odkazovaná pomocí [NETStandard. Library](https://www.nuget.org/packages/NETStandard.Library/) Metapackage.

### <a name="package-representation"></a>Reprezentace balíčku

Primární distribuční vozidlo pro .NET Standard referenční sestavení jsou [balíčky NuGet](../core/packages.md). Implementace jsou dodávány různými způsoby, které jsou vhodné pro každou implementaci rozhraní .NET.

Balíčky NuGet cílí na jednu nebo víc [platforem](frameworks.md). Balíčky .NET Standard cílí na architekturu ".NET Standard". .NET Standard rozhraní můžete cílit pomocí `netstandard` [kompaktního TFM](frameworks.md) `netstandard1.4`(například). Knihovny určené ke spuštění na více modulech runtime by měly cílit na toto rozhraní. Pro nejširší sadu rozhraní API cílíte `netstandard2.0` , protože počet dostupných rozhraní API je více než dvojnásobný mezi .NET Standard 1,6 a 2,0.

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library/) Metapackage odkazuje na úplnou sadu balíčků NuGet, které definují .NET Standard.  Nejběžnější způsob, jak se zaměřit `netstandard` , je odkazování na tento Metapackage. Popisuje a poskytuje přístup k knihovnám ~ 40 .NET a přidruženým rozhraním API, která definují .NET Standard. Na další balíčky, jejichž cílem `netstandard` je získat přístup k dalším rozhraním API, můžete odkazovat.

### <a name="versioning"></a>Správa verzí

Specifikace není v jednotném čísle, ale přírůstkově rostoucí a lineární verze sady rozhraní API. První verze standardu vytvoří základní sadu rozhraní API. Další verze přidávají rozhraní API a dědí rozhraní API definovaná předchozími verzemi. Neexistuje žádné zřízené zřízení pro odebrání rozhraní API ze standardu.

.NET Standard není specifické pro žádnou implementaci rozhraní .NET ani neodpovídá schématu správy verzí žádné z těchto modulů runtime.

Rozhraní API přidaná do kterékoli implementace (například .NET Framework, .NET Core a mono) je možné považovat za kandidáty na přidání do specifikace, zejména v případě, že jsou považovány za zásadní. Nové [verze .NET Standard](https://github.com/dotnet/standard/blob/master/docs/versions.md) jsou vytvořeny na základě verzí implementace rozhraní .NET a umožňují zacílit nová rozhraní api z .NET Standard PCL. Mechanismy správy verzí jsou podrobněji popsány v tématu [Správa verzí .NET Core](../core/versions/index.md).

Správa verzí .NET Standard je důležitá pro použití. Vzhledem k verzi .NET Standard můžete použít knihovny, které cílí na stejnou nebo nižší verzi. Následující postup popisuje pracovní postup pro použití .NET Standard PCLs, který je specifický pro .NET Standard cílení na.

- Vyberte verzi .NET Standard, kterou chcete použít pro PCL.
- Používejte knihovny, které jsou závislé na stejné nebo nižší verzi .NET Standard.
- Pokud najdete knihovnu, která závisí na vyšší verzi .NET Standard, musíte buď přijmout stejnou verzi, nebo se rozhodnout, že tuto knihovnu nebudete používat.

## <a name="targeting-net-standard"></a>Cílení na .NET Standard

[Knihovny .NET Standard lze vytvořit](../core/tutorials/libraries.md) pomocí kombinace `netstandard` rozhraní a Metapackage NETStandard. Library. Můžete si prohlédnout příklady [cílení .NET Standard pomocí nástrojů .NET Core](../core/packages.md).

## <a name="net-framework-compatibility-mode"></a>Režim kompatibility .NET Framework

Počínaje .NET Standard 2,0 byl zaveden režim kompatibility .NET Framework. Tento režim kompatibility umožňuje .NET Standard projektům odkazovat .NET Framework knihovny, jako kdyby byly zkompilovány pro .NET Standard. Odkazování na knihovny .NET Framework nefunguje pro všechny projekty, jako jsou knihovny, které používají rozhraní API Windows Presentation Foundation (WPF).

Další informace najdete v tématu [režim kompatibility .NET Framework](../core/porting/third-party-deps.md#net-framework-compatibility-mode).

## <a name="net-standard-libraries-and-visual-studio"></a>Knihovny .NET Standard a Visual Studio

Aby bylo možné sestavit knihovny .NET Standard v aplikaci Visual Studio, ujistěte se, že máte v systému Windows nainstalovanou [15,3 verzi sady Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) nebo novější, nebo [Visual Studio pro Mac verze 7,1](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) nebo novější, která je nainstalovaná v MacOS.

Pokud v projektech potřebujete pouze využívat knihovny .NET Standard 2,0, můžete to provést také v aplikaci Visual Studio 2015. Potřebujete však nainstalovaného klienta NuGet 3,6 nebo vyšší. Klienta NuGet pro Visual Studio 2015 si můžete stáhnout ze stránky [stažení NuGet](https://www.nuget.org/downloads) .

## <a name="comparison-to-portable-class-libraries"></a>Porovnání s přenosnou knihovnou tříd

.NET Standard je náhradou [přenosných knihoven tříd (PCL)](./cross-platform/cross-platform-development-with-the-portable-class-library.md). .NET Standard zlepšuje možnosti vytváření přenosných knihoven tím, že v důsledku toho dostanou standardní BCL a vytváří větší jednotnost u implementací rozhraní .NET. Knihovna, která cílí na .NET Standard, je PCL nebo ".NET Standard PCL". Stávající PCLs jsou "PCLs na základě profilu".

Profily .NET Standard a PCL byly vytvořeny pro podobné účely, ale také se liší v klíčových způsobech.

Podobnosti

- Definujte rozhraní API, která lze použít pro sdílení binárního kódu.

Rozdíly

- .NET Standard je podmnožinou rozhraní API, zatímco profily PCL jsou definovány průniky stávajících platforem.
- .NET Standard lineární verze, zatímco profily PCL ne.
- Profily PCL představují platformy Microsoftu, zatímco .NET Standard je Platform-nezávislá.

### <a name="pcl-compatibility"></a>Kompatibilita PCL

.NET Standard je kompatibilní s podmnožinou profilů PCL. .NET Standard 1,0, 1,1 a 1,2 se každá překrývají se sadou profilů PCL. Tento překryv byl vytvořen ze dvou důvodů:

- Povolte PCLs založené na .NET Standard pro odkazování na PCLs na základě profilu.
- Povolte zabalení PCLs založených na profilech .NET Standard jako PCLs na základě profilu.

Kompatibilita PCL založená na profilech je poskytována balíčkem NuGet [Microsoft. NETCore. Portable. Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) . Tato závislost se vyžaduje při odkazování na balíčky NuGet, které obsahují PCLs založené na profilech.

PCLS na základě profilu, jak `netstandard` je to snazší, než obvykle zabalíte PCLS založenou na profilech. `netstandard`balení je kompatibilní s existujícími uživateli.

Můžete zobrazit sadu profilů PCL, které jsou kompatibilní s .NET Standard:

| Profil PCL | .NET Standard | Platformy PCL
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profile7    | 1.1           | .NET Framework 4,5, Windows 8
| Profile31   | 1.0           | Windows 8.1 Windows Phone Silverlight 8,1
| Profile32   | 1.2           | Windows 8.1 Windows Phone 8,1
| Profile44   | 1.2           | .NET Framework 4.5.1, Windows 8.1
| Profile49   | 1.0           | .NET Framework 4,5, Windows Phone Silverlight 8
| Profile78   | 1.0           | .NET Framework 4,5, Windows 8, Windows Phone Silverlight 8
| Profile84   | 1.0           | Windows Phone 8,1, Windows Phone Silverlight 8,1
| Profile111  | 1.1           | .NET Framework 4,5, Windows 8, Windows Phone 8,1
| Profile151  | 1.2           | .NET Framework 4.5.1, Windows 8.1 Windows Phone 8,1
| Profile157  | 1.0           | Windows 8.1 Windows Phone 8,1 Windows Phone Silverlight 8,1
| Profile259  | 1.0           | .NET Framework 4,5, Windows 8, Windows Phone 8,1, Windows Phone Silverlight 8

## <a name="see-also"></a>Viz také:

- [Verze .NET Standard](https://github.com/dotnet/standard/blob/master/docs/versions.md)
