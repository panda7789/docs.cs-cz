---
title: .NET Standard
description: Informace o .NET Standard, jeho verze a implementace .NET, které ji podporují.
ms.date: 02/13/2020
ms.technology: dotnet-standard
ms.custom: updateeachrelease
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 34074b420547cff802f1835656540be7b8eb58b4
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607477"
---
# <a name="net-standard"></a>.NET Standard

[.NET Standard](https://github.com/dotnet/standard) je formální specifikace rozhraní API .NET, které mají být k dispozici ve všech implementacích rozhraní .NET. Motivací standardu .NET standard je vytvoření větší jednotnosti v ekosystému .NET. [ECMA 335](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) nadále vytvořit jednotnost pro chování implementace rozhraní .NET a zatímco ECMA 335 určuje malou sadu standardních knihoven, specifikace .NET Standard zahrnuje širší rozsah rozhraní API .NET.

Standard .NET umožňuje následující klíčové scénáře:

- Definuje jednotnou sadu rozhraní API BCL pro všechny implementace rozhraní .NET k implementaci, nezávisle na zatížení.
- Umožňuje vývojářům vytvářet přenosné knihovny, které jsou použitelné napříč implementacemi rozhraní .NET, pomocí stejné sady rozhraní API.
- Snižuje nebo dokonce eliminuje podmíněnou kompilaci sdíleného zdroje z důvodu rozhraní API .NET, pouze pro rozhraní API operačního systému.

Různé implementace rozhraní .NET cílí na konkrétní verze standardu .NET. Každá verze implementace rozhraní .NET inzeruje nejvyšší verzi .NET Standard, kterou podporuje, což znamená, že podporuje také předchozí verze. Například rozhraní .NET Framework 4.6 implementuje standard .NET Standard 1.3, což znamená, že zveřejňuje všechna rozhraní API definovaná ve standardních verzích .NET 1.0 až 1.3. Podobně rozhraní .NET Framework 4.6.1 implementuje standard .NET Standard 1.4, zatímco rozhraní .NET Core 1.0 implementuje standard .NET Standard 1.6.

## <a name="net-implementation-support"></a>Podpora implementace rozhraní .NET

V následující tabulce jsou uvedeny **minimální** verze platformy, které podporují každou verzi .NET Standard. To znamená, že novější verze uvedené platformy také podporují odpovídající verzi .NET Standard. Například .NET Core 2.2 podporuje standard .NET Standard 2.0 a starší.

[!INCLUDE [net-standard-table](../../includes/net-standard-table.md)]

Chcete-li najít nejvyšší verzi standardu .NET, na kterou můžete cílit, postupujte takto:

1. Vyhledejte řádek, který označuje implementaci rozhraní .NET, na které chcete spustit.
2. Najděte sloupec v tomto řádku, který označuje vaši verzi od zprava doleva.
3. Záhlaví sloupce označuje verzi .NET Standard, kterou váš cíl podporuje. Můžete také cílit na libovolnou nižší verzi .NET Standard. Vyšší verze .NET Standard budou také podporovat vaši implementaci.
4. Tento postup opakujte pro každou platformu, na kterou chcete cílit. Pokud máte více než jednu cílovou platformu, měli byste si vybrat menší verzi mezi nimi. Chcete-li například spustit rozhraní .NET Framework 4.5 a .NET Core 1.0, je nejvyšší verze .NET Standard, kterou můžete použít, standardem .NET Standard 1.1.

### <a name="which-net-standard-version-to-target"></a>Kterou verzi .NET Standard cílit

Při výběru verze .NET Standard byste měli zvážit tento kompromis:

- Čím vyšší je verze, tím více rozhraní API máte k dispozici.
- Čím nižší je verze, tím více platforem ji implementuje.

Obecně doporučujeme cílit na *nejnižší* možnou verzi standardu .NET. Takže po nalezení nejvyšší verze .NET Standard, na kterou můžete cílit, postupujte takto:

1. Zacilte na další nižší verzi standardu .NET a vytvořte projekt.
2. Pokud se projekt úspěšně sestaví, opakujte krok 1. V opačném případě retarget na další vyšší verzi a to je verze, kterou byste měli použít.

Cílení na nižší verze .NET Standard však zavádí řadu závislostí podpory. Pokud váš projekt cílí na rozhraní .NET Standard 1.x, doporučujeme také cílit *na* standard .NET Standard 2.0. To zjednodušuje graf závislostí pro uživatele knihovny, které běží na rozhraní kompatibilní s rozhraním .NET Standard 2.0 a snižuje počet balíčků, které je třeba stáhnout.

### <a name="net-standard-versioning-rules"></a>Pravidla správy verzí standardu .NET

Existují dvě primární pravidla správy verzí:

- Aditivní: Verze .NET Standard jsou logicky soustředné kruhy: vyšší verze obsahují všechna rozhraní API z předchozích verzí. Neexistují žádné změny mezi verzemi.
- Neměnné: Po odeslání jsou standardní verze .NET zmrazeny. Nová rozhraní API jsou nejprve k dispozici v konkrétních implementacích rozhraní .NET, jako je například .NET Core. Pokud se revizní komise .NET Standard domnívá, že nová rozhraní API by měla být k dispozici pro všechny implementace rozhraní .NET, budou přidána v nové verzi .NET Standard.

## <a name="specification"></a>Specifikace

Specifikace .NET Standard je standardizovaná sada rozhraní API. Specifikace je udržována implementátory .NET, konkrétně Microsoft (zahrnuje rozhraní .NET Framework, .NET Core a Mono) a Unity. Proces zpětné vazby veřejnosti se používá jako součást vytváření nových verzí .NET Standard prostřednictvím [GitHubu](https://github.com/dotnet/standard).

### <a name="official-artifacts"></a>Oficiální artefakty

Oficiální specifikace je sada souborů .cs, které definují api, které jsou součástí standardu. [Adresář ref](https://github.com/dotnet/standard/tree/master/src/netstandard/ref) v [úložišti dotnet/standard](https://github.com/dotnet/standard) definuje rozhraní API standardu .NET.

Metabalíček [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) ([zdroj)](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)popisuje sadu knihoven, které definují (částečně) jednu nebo více verzí .NET Standard.

Daná součást, `System.Runtime`například , popisuje:

- Část standardu .NET (pouze jeho rozsah).
- Více verzí rozhraní .NET Standard pro tento obor.

Odvozené artefakty jsou k dispozici k povolení pohodlnější čtení a povolit určité scénáře vývojáře (například pomocí kompilátoru).

- [Seznam rozhraní API v markdownu](https://github.com/dotnet/standard/tree/master/docs/versions)
- Referenční sestavení, distribuovaná jako [balíčky NuGet](../core/packages.md) a odkazovaná metabalíčkem [NETStandard.Library.](https://www.nuget.org/packages/NETStandard.Library/)

### <a name="package-representation"></a>Reprezentace balíčku

Primární distribuční vozidlo pro referenční sestavení .NET Standard je [Balíčky NuGet](../core/packages.md). Implementace jsou dodávány různými způsoby, vhodné pro každou implementaci .NET.

Balíčky NuGet cílí na jeden nebo více [architektur](frameworks.md). Balíčky .NET Standard cílí na rozhraní ".NET Standard". Můžete cílit na rozhraní .NET Standard framework `netstandard` pomocí `netstandard1.4`kompaktní [TFM](frameworks.md) (například). Knihovny, které jsou určeny ke spuštění na více runtimes by měl cílit na tento rámec. Pro nejširší sadu rozhraní API `netstandard2.0` cíl, protože počet dostupných rozhraní API více než zdvojnásobil mezi .NET Standard 1.6 a 2.0.

Metabalíček [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library/) odkazuje na úplnou sadu balíčků NuGet, které definují standard .NET.  Nejběžnější způsob, jak `netstandard` cílit, je odkazováním na tento metabalíček. Popisuje a poskytuje přístup ke knihovnám ~40 .NET a přidruženým rozhraním API, která definují standard .NET. Můžete odkazovat na `netstandard` další balíčky, které cílí získat přístup k dalším možnostem api.

### <a name="versioning"></a>Správa verzí

Specifikace není jednotné ho, ale postupně rostoucí a lineárně verzí sady API. První verze standardu vytváří základní sadu api. Následné verze přidávají api a dědí api definovaná předchozími verzemi. Neexistuje žádné zavedené ustanovení pro odstranění api ze standardu.

Standard .NET není specifický pro žádnou implementaci rozhraní .NET, ani neodpovídá schématu správy verzí žádného z těchto runtimes.

Rozhraní API přidané do některé z implementací (například .NET Framework, .NET Core a Mono) lze považovat za kandidáty přidat do specifikace, zejména v případě, že jsou považovány za zásadní povahy. Nové [verze standardu .NET](https://github.com/dotnet/standard/blob/master/docs/versions.md) Jsou vytvářeny na základě verzí implementace rozhraní .NET, což umožňuje cílit na nová rozhraní API z rozhraní .NET Standard PCL. Mechanika správy verzí je podrobněji popsána v [rozhraní .NET Core Versioning](../core/versions/index.md).

Správa verzí standardu .NET je důležitá pro použití. Vzhledem k tomu, .NET Standard verze, můžete použít knihovny, které se zaměřují na stejnou nebo nižší verzi. Následující postup popisuje pracovní postup pro použití rozhraní .NET Standard PCLs, specifické pro cílení .NET Standard.

- Vyberte verzi .NET Standard, která se má použít pro soubor PCL.
- Používejte knihovny, které jsou závislé na stejné verzi .NET Standard nebo nižší.
- Pokud najdete knihovnu, která závisí na vyšší verzi .NET Standard, musíte buď přijmout stejnou verzi, nebo se rozhodnout tuto knihovnu nepoužívat.

## <a name="target-net-standard"></a>Cílový standard .NET

Standardní [knihovny .NET](../core/tutorials/libraries.md) můžete vytvářet `netstandard` pomocí kombinace frameworku a metabalíčku NETStandard.Library. Můžete zobrazit příklady [cílení na standard .NET pomocí nástrojů .NET Core](../core/packages.md).

## <a name="net-framework-compatibility-mode"></a>Režim kompatibility rozhraní .NET Framework

Počínaje rozhraním .NET Standard 2.0 byl zaveden režim kompatibility rozhraní .NET Framework. Tento režim kompatibility umožňuje projektům .NET Standard odkazovat na knihovny rozhraní .NET Framework, jako by byly zkompilovány pro standard .NET. Odkazování na knihovny rozhraní .NET Framework nefunguje pro všechny projekty, jako jsou například knihovny, které používají rozhraní API Windows Presentation Foundation (WPF).

Další informace naleznete v [tématu .NET Framework compatibility mode](../core/porting/third-party-deps.md#net-framework-compatibility-mode).

## <a name="net-standard-libraries-and-visual-studio"></a>Knihovny .NET Standard a visual studio

Chcete-li ve Visual Studiu vytvářet knihovny .NET Standard, ujistěte se, že máte v systému Windows [nainstalovanou Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo Visual Studio 2017 verze 15.3 nebo novější nebo novější nebo [Visual Studio pro Mac verze 7.1](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) nebo novější.

Pokud potřebujete jenom využívat knihovny .NET Standard 2.0 ve vašich projektech, můžete to udělat také v sadě Visual Studio 2015. Však je třeba NuGet klienta 3.6 nebo vyšší nainstalován. Klienta NuGet pro Visual Studio 2015 si můžete stáhnout ze stránky [stažení NuGet.](https://www.nuget.org/downloads)

## <a name="comparison-to-portable-class-libraries"></a>Porovnání s přenosnými knihovnami tříd

.NET Standard je náhradou za [knihovny přenosných tříd (PCL).](./cross-platform/cross-platform-development-with-the-portable-class-library.md) .NET Standard vylepšuje prostředí vytváření přenosných knihoven tím, že vytváří standardní bcl a v důsledku toho vytváří větší jednotnost v implementacích rozhraní .NET. Knihovna, která cílí na standard .NET, je PCL nebo "PCL založený na standardu.NET". Stávající PCL s jsou "PCL založené na profilech".

Profily .NET Standard a PCL byly vytvořeny pro podobné účely, ale také se liší klíčovými způsoby.

Podobnosti:

- Definujte api, která lze použít pro sdílení binárního kódu.

Rozdíly:

- .NET Standard je kurátorská sada rozhraní API, zatímco profily PCL jsou definovány průsečíky existujících platforem.
- .NET Standardní lineárské verze, zatímco profily PCL nikoli.
- Profily PCL představují platformy společnosti Microsoft, zatímco rozhraní .NET Standard je nezávislá na platformě.

### <a name="pcl-compatibility"></a>Kompatibilita s PCL

Standard .NET je kompatibilní s podmnožinou profilů PCL. .NET Standard 1.0, 1.1 a 1.2 se překrývají se sadou profilů PCL. Toto překrytí bylo vytvořeno ze dvou důvodů:

- Povolte pcl s rozhraním .NET Standard na referenční soubory PCL založené na profilech.
- Povolte balíčky pcl založených na profilech jako soubory PCL založené na standardu .NET.

Kompatibilita pcl založené na profilu je poskytována balíčkem [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) NuGet. Tato závislost je vyžadována při odkazování na balíčky NuGet, které obsahují pcl založené na profilu.

Pcl založené na profilu `netstandard` jsou zabaleny tak, jak jsou snadněji spotřebovávat než obvykle balené pcl založené na profilu. `netstandard`balení je kompatibilní se stávajícími uživateli.

Můžete zobrazit sadu profilů PCL, které jsou kompatibilní se standardem .NET Standard:

| Profil PCL | .NET Standard | Platformy PCL
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profil7    | 1.1           | Rozhraní .NET Framework 4.5, Windows 8
| Profil31   | 1.0           | Windows 8.1, Windows Phone Silverlight 8.1
| Profil32   | 1.2           | Windows 8.1, Windows Phone 8.1
| Profil44   | 1.2           | Rozhraní .NET Framework 4.5.1, Windows 8.1
| Profil49   | 1.0           | Rozhraní .NET Framework 4.5, Windows Phone Silverlight 8
| Profil78   | 1.0           | .NET Framework 4.5, Windows 8, Windows Phone Silverlight 8
| Profil84   | 1.0           | Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profil111  | 1.1           | .NET Framework 4.5, Windows 8, Windows Phone 8.1
| Profil151  | 1.2           | Rozhraní .NET Framework 4.5.1, Windows 8.1, Windows Phone 8.1
| Profil157  | 1.0           | Windows 8.1, Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profil259  | 1.0           | .NET Framework 4.5, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8

## <a name="see-also"></a>Viz také

- [Standardní verze rozhraní .NET](https://github.com/dotnet/standard/blob/master/docs/versions.md)
- [Vytvoření knihovny .NET Standard](../core/tutorials/library-with-visual-studio.md)
- [Cílení na více platforem](./library-guidance/cross-platform-targeting.md)
