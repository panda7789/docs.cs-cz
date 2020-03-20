---
title: Rozhraní .NET Framework & verze operačního systému Windows
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: 486b320ca30323684d301630ad29f8f4615764ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504056"
---
# <a name="net-framework-versions-and-dependencies"></a>Verze a závislosti rozhraní .NET Framework

Každá verze rozhraní .NET Framework obsahuje běžný jazyk runtime (CLR), knihovny základních tříd a další spravované knihovny. Tento článek popisuje klíčové funkce rozhraní .NET Framework podle verze, poskytuje informace o základních verzích CLR a přidružených vývojových prostředích a identifikuje verze nainstalované operačním systémem Windows (OS).

Každá nová verze rozhraní .NET Framework přidává nové funkce, ale zachovává funkce z předchozích verzí.

Modul CLR je identifikován vlastním číslem verze. Číslo verze rozhraní .NET Framework se v každé verzi zintátáže, ale verze CLR není vždy přírůstá. Například rozhraní .NET Framework 4, 4.5 a novější verze zahrnují CLR 4, ale rozhraní .NET Framework 2.0, 3.0 a 3.5 zahrnují CLR 2.0. (Verze 3 CLR neexistovala.)

> [!TIP]
>
> - Úplný seznam podporovaných operačních systémů naleznete v [tématu Systémové požadavky](../get-started/system-requirements.md).
> - Soubory ke stažení naleznete [v tématu Instalace rozhraní .NET Framework pro vývojáře](../install/guide-for-developers.md).
> - Informace o určení, které verze rozhraní .NET Framework jsou v počítači nainstalovány, naleznete v tématu [Určení, které verze rozhraní .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md).

## <a name="version-information"></a>Informace o verzi

Následující tabulky shrnují historii verzí rozhraní .NET Framework a korelují každou verzi se soubory Visual Studio, Windows a Windows Server. Visual Studio podporuje více cílení, takže nejste omezeni na verzi rozhraní .NET Framework, která je uvedena.

- Ikona zaškrtnutí ✔️ označuje verze operačního systému, ve kterých je nainstalována rozhraní .NET Framework, ale musí být [povolena v Ovládacích panelech](../install/dotnet-35-windows-10.md) (pro Windows) nebo prostřednictvím Správce serveru (pro Windows Server).
- Ikona znaménko plus ➕ označuje verze operačního systému, ve kterých není nainstalována rozhraní .NET Framework, ale lze ji nainstalovat.

| | |
| - | - |
| [Rozhraní .NET Framework 4.8](#net-framework-48) | [Rozhraní .NET 4.7.2](#net-framework-472) | [Rozhraní .NET 4.7.1](#net-framework-471) | [Rozhraní .NET Framework 4.7](#net-framework-47) |
| [.NET Framework 4.6.2](#net-framework-462) | [.NET Framework 4.6.1](#net-framework-461) | [.NET Framework 4.6](#net-framework-46) | [.NET Framework 4.5.2](#net-framework-452) |
| [.NET Framework 4.5.1](#net-framework-451) | [.NET Framework 4.5](#net-framework-45) | [.NET Framework 4](#net-framework-4) | [.NET Framework 3.5](#net-framework-35) |
| [.NET Framework 3.0](#net-framework-30) | [.NET Framework 2,0](#net-framework-20) | [.NET Framework 1.1](#net-framework-11) | [.NET Framework 1.0](#net-framework-10) |

### <a name="net-framework-48"></a> .NET Framework 4.8

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-48)
- [Novinka v přístupnosti](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)
- [Poznámky k verzi](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Verze systému Windows**|✔️ 10 května 2019 Aktualizace<br/>➕ 10 října 2018 (verze 1809)<br/>aktualizace ➕ 10. dubna 2018 (verze 1803)<br/>➕ 10 Fall Creators Update (verze 1709)<br/>➕ 10 Creators Update (verze 1703)<br/>aktualizace 10 ➕ Výročí (verze 1607)<br/>➕ 8.1<br/>➕7|
|**Verze systému Windows Server**|➕ Windows Server 2019<br/>➕ Windows Server, verze 1809<br/>➕ Windows Server, verze 1803<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Určení nainstalované verze rozhraní .NET**|Použití `Release` DWORD:<br/>- 528040 (Windows 10 Květen 2019 Update)<br/>- 528049 (všechny ostatní verze operačního systému)<br/>(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-472"></a> .NET Framework 4.7.2

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-472)
- [Novinka v přístupnosti](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)
- [Poznámky k verzi](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Součástí verze sady Visual Studio**|2019<sup>1</sup>|
|**Verze systému Windows**|✔️ 10 října 2018 (verze 1809)<br/>✔️ 10 duben 2018 Update (verze 1803)<br/>➕ 10 Fall Creators Update (verze 1709)<br/>➕ 10 Creators Update (verze 1703)<br/>aktualizace 10 ➕ Výročí (verze 1607)<br/>➕ 8.1<br/>➕7|
|**Verze systému Windows Server**|✔️ Windows Server 2019<br/>✔️ Windows Server, verze 1809<br/>✔️ Windows Server, verze 1803<br/>➕ Windows Server, verze 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Určení nainstalované verze rozhraní .NET**|Použití `Release` DWORD:<br/>- 461814 (Aktualizace Windows 10 z října 2018)<br/>- 461808 (Windows 10 duben 2018 Aktualizace a Windows Server, verze 1803)<br/>- 461814 (všechny ostatní verze operačního systému)<br/>(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

<sup>1</sup> Vyžaduje instalaci **úloh pro vývoj stolních počítačů .NET**, **ASP.NET a webových aplikací**, Vývoje **Azure**, **Vývoje Office/SharePointu**, **Mobilní vývoj s rozhraním .NET**nebo vývojové úlohy **.NET Core napříč platformami.**

### <a name="net-framework-471"></a>Rozhraní .NET 4.7.1

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-471)
- [Novinka v přístupnosti](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)
- [Poznámky k verzi](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Verze systému Windows**|✔️ 10 Fall Creators Update (verze 1709)<br/>➕ 10 Creators Update (verze 1703)<br/>aktualizace 10 ➕ Výročí (verze 1607)<br/>➕ 8.1<br/>➕7|
|**Verze systému Windows Server**|➕ Windows Server, verze 1803<br/>✔️ Windows Server, verze 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Určení nainstalované verze rozhraní .NET**|Použití `Release` DWORD:<br/>- 461308 (Windows 10 Creators Update a Windows Server, verze 1709)<br/>- 461310 (všechny ostatní verze operačního systému)<br/>(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-47"></a>Rozhraní .NET Framework 4.7

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-47)
- [Poznámky k verzi](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Verze systému Windows**|✔️ 10 Creators Update (verze 1703)<br/>aktualizace 10 ➕ Výročí (verze 1607)<br/>➕ 8.1<br/>➕7|
|**Verze systému Windows Server**|➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Určení nainstalované verze rozhraní .NET**|Použití `Release` DWORD:<br/>- 460798 (Windows 10 Creators Update)<br/>- 460805 (všechny ostatní verze operačního systému)<br/>(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-462"></a>.NET Framework 4.6.2

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-462)
- [Poznámky k verzi](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Verze systému Windows**|✔️ 10 Výročí Update (verze 1607)<br/>➕ 10 listopadová aktualizace (verze 1511)<br/>10. ➕<br/>➕ 8.1<br />7➕|
|**Verze systému Windows Server**|✔️ 2016<br /><br/>➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1|
|**Určení nainstalované verze rozhraní .NET**|Použití `Release` DWORD:<br /><br/>- 394802 (Windows 10 Výročí aktualizace a Windows Server 2016)<br/>- 394806 (všechny ostatní verze operačního systému)<br /><br/>(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-461"></a>.NET Framework 4.6.1

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-461)
- [Poznámky k verzi](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Součástí verze sady Visual Studio**|2017<sup>1</sup>|
|**Verze systému Windows**|✔️ 10 listopadu Update (verze 1511)<br/>10. ➕<br />➕ 8.1<br />➕ 8<br />7➕|
|**Verze systému Windows Server**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1|
|**Určení nainstalované verze rozhraní .NET**|Použití `Release` DWORD:<br /><br/>- 394254 (Windows 10 listopadová aktualizace)<br />- 394271 (všechny ostatní verze operačního systému)<br /><br/>(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

<sup>1</sup> Vyžaduje instalaci **úloh pro vývoj stolních počítačů .NET**, **ASP.NET a webových aplikací**, Vývoje **Azure**, **Vývoje Office/SharePointu**, **Mobilní vývoj s rozhraním .NET**nebo vývojové úlohy **.NET Core napříč platformami.**

### <a name="net-framework-46"></a>.NET Framework 4.6

- [Nové funkce](../whats-new/index.md#whats-new-in-net-2015)
- [Poznámky k verzi](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Součástí verze sady Visual Studio**|2015|
|**Verze systému Windows**|✔️ 10.<br /><br />➕ 8.1<br />➕ 8<br />7➕<br />➕ Vista|
|**Verze systému Windows Server**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Určení nainstalované verze rozhraní .NET**|Použití `Release` DWORD:<br /><br />- 393295 (Windows 10)<br />- 393297 (všechny ostatní verze operačního systému)<br /><br />(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-452"></a>.NET Framework 4.5.2

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-452)
- [Poznámky k verzi](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Verze systému Windows**|➕ 8.1<br />➕ 8<br />7➕<br />➕ Vista|
|**Verze systému Windows Server**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Určení nainstalované verze rozhraní .NET**|Použití `Release` DWORD 379893<br /><br />(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-451"></a>.NET Framework 4.5.1

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-451)
- [Poznámky k verzi](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Součástí verze sady Visual Studio**|2013|
|**Verze systému Windows**|✔️ 8.1<br /><br />➕ 8<br />7➕<br />➕ Vista|
|**Verze systému Windows Server**|✔️ 2012 R2<br /><br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Určení nainstalované verze rozhraní .NET**|Použití `Release` DWORD:<br /><br />- 378675 (Windows 8.1)<br />- 378758 (všechny ostatní)<br /><br />(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-45"></a>.NET Framework 4.5

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-45)
- [Poznámky k verzi](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Součástí verze sady Visual Studio**|2012|
|**Verze systému Windows**|✔️ 8<br />7➕<br />➕ Vista|
|**Verze systému Windows Server**|✔️ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Určení nainstalované verze rozhraní .NET**|Použití `Release` DWORD 378389<br /><br />(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-4"></a>.NET Framework 4

[Nové funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms171868(v=vs.100))

|||
|-|-|
|**Verze CLR**|4|
|**Součástí verze sady Visual Studio**|2010|
|**Verze systému Windows**|7➕<br />➕ Vista|
|**Verze systému Windows Server**|➕ 2008 R2 SP1<br />➕ 2008 SP2<br />➕ 2003|
|**Určení nainstalované verze rozhraní .NET**|Viz [pokyny](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-35"></a>.NET Framework 3.5

[Nové funkce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\)):

- LINQ
- Stromy výrazů
- Vylepšená podpora ASP.NET pro rozvoj AJAX
- Kolekce HashSet
- DateTimeOffset
- Integrace WCF a WF
- Sítě mezi dvěma účastníky
- Doplňky pro rozšiřitelnost

|||
|-|-|
|**Verze CLR**|2.0|
|**Součástí verze sady Visual Studio**|2008|
|**Verze systému Windows**|✔️ 10.\*<br/>✔️ 8.1\*<br />✔️ 8\*<br />7. ✔️<br /><br />➕ Vista|
|**Verze systému Windows Server**|➕ Windows Server, verze 1803\*<br/>➕ Windows Server, verze 1709\*<br/>➕ 2016\*<br/>➕ 2012 R2\*<br />➕ 2012\*<br /><br />✔️2008 R2 SP1\*<br /><br/>➕ 2008 SP2<br />➕ 2003|
|**Určení nainstalované verze rozhraní .NET**|Viz [pokyny](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-30"></a>.NET Framework 3.0

[Nové funkce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb822048(v=vs.90)):

- Windows Presentation Foundation
- Windows Communication Foundation
- Windows Workflow Foundation
- Windows CardSpace

|||
|-|-|
|**Verze CLR**|2.0|
|**Verze systému Windows**|✔️ Vista|
|**Verze systému Windows Server**|✔️ 2008 R2 SP1*<br />✔️ 2008 SP2\*<br /><br />➕ 2003|
|**Určení nainstalované verze rozhraní .NET**|Viz [pokyny](how-to-determine-which-versions-are-installed.md).|

### <a name="net-framework-20"></a>.NET Framework 2,0

[Nové funkce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t357fb32%28v%3dvs.90%29):

- Obecné typy
- Ladicí program upravit a pokračovat
- Lepší škálovatelnost a výkon
- ClickOnce – nasazení
- V ASP.NET 2.0, nové ovládací prvky a podpora pro širokou škálu prohlížečů
- podpora 64bitových technologií

|||
|-|-|
|**Verze CLR**|2.0|
|**Součástí verze sady Visual Studio**|2005|
|**Verze systému Windows**|Není dostupné.|
|**Verze systému Windows Server**|✔️ 2008 R2 SP1<br />✔️ 2008 SP2<br />✔️ 2003|
|**Určení nainstalované verze rozhraní .NET**|Viz [pokyny](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-11"></a>.NET Framework 1.1

[Nové funkce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/h88tthh0%28v%3dvs.90%29):

- ASP.NET mobilní ovládací prvky
- Souběžné spouštění
- Podpora protokolu IPv6

|||
|-|-|
|**Verze CLR**|1.1|
|**Součástí verze sady Visual Studio**|2003|
|**Verze systému Windows**|Není dostupné.|
|**Verze systému Windows Server**|✔️ 2003|
|**Určení nainstalované verze rozhraní .NET**|Viz [pokyny](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-10"></a>.NET Framework 1.0

|||
|-|-|
|**Verze CLR**|1.0|
|**Součástí verze sady Visual Studio**|Visual Studio .NET|
|**Verze systému Windows**|Není dostupné.|
|**Verze systému Windows Server**|Není dostupné.|
|**Určení nainstalované verze rozhraní .NET**|Viz [pokyny](how-to-determine-which-versions-are-installed.md)|

> [!NOTE]
>
> - Rozhraní .NET Framework musí být v tomto operačním systému povoleno prostřednictvím [Ovládacích panelů (pro Systém Windows) nebo Správce serveru (pro systém Windows Server).](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel)
> - Obecně byste neměli odinstalovat žádné verze rozhraní .NET Framework, které jsou nainstalovány v počítači, protože aplikace, kterou používáte, může záviset na konkrétní verzi a může přerušit, pokud je tato verze odebrána. V jednom počítači můžete načíst více verzí rozhraní .NET Framework současně. To znamená, že rozhraní .NET Framework můžete nainstalovat bez nutnosti odinstalovat předchozí verze. Další informace naleznete v [tématu Začínáme](../get-started/index.md).

## <a name="remarks-for-version-45-and-later"></a>Poznámky k verzi 4.5 a novější

Rozhraní .NET Framework 4.5 je aktuální aktualizace, která nahrazuje rozhraní .NET Framework 4 v počítači a podobně rozhraní .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 a 4.8 jsou aktuální aktualizace rozhraní .NET Framework 4.5. Aktualizace na místě znamená, že používají stejnou verzi za běhu, ale verze sestavení jsou aktualizovány a zahrnují nové typy a členy. Po instalaci jedné z těchto aktualizací by měly aplikace rozhraní .NET Framework 4, .NET Framework 4.5, .NET Framework 4.6 nebo .NET Framework 4.7 nadále spouštět bez nutnosti opětovné kompilace. Opačně to však neplatí. Nedoporučujeme spouštět aplikace, které cílí na novější verzi rozhraní .NET Framework v dřívější verzi. Například nedoporučujeme spouštět aplikaci cíle .NET Framework 4.6 na rozhraní .NET Framework 4.5.

Platí následující pokyny:

- V sadě Visual Studio můžete zvolit rozhraní .NET Framework 4.5 jako <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType> cílovou architekturu pro projekt (to nastaví vlastnost) pro kompilaci projektu jako sestavení rozhraní .NET Framework 4.5 nebo spustitelný soubor. Toto sestavení nebo spustitelný soubor lze pak použít v libovolném počítači, který má nainstalovaný rozhraní .NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 nebo 4.8.

- V sadě Visual Studio můžete zvolit rozhraní .NET Framework 4.5.1 jako cílovou architekturu pro projekt pro jeho kompilaci jako sestavení nebo spustitelný soubor .NET Framework 4.5.1. Toto sestavení nebo spustitelný soubor spusťte pouze v počítačích s nainstalovanou rozhraním .NET Framework 4.5.1 nebo novějším. Spustitelný soubor, který cílí na rozhraní .NET Framework 4.5.1, bude blokován v počítači, který má nainstalovanou pouze starší verzi rozhraní .NET Framework, například rozhraní .NET Framework 4.5. Uživatel bude vyzván k instalaci rozhraní .NET Framework 4.5.1. Kromě toho sestavení rozhraní .NET Framework 4.5.1 by neměla být volána z aplikace, která se zaměřuje na starší verzi rozhraní .NET Framework, například rozhraní .NET Framework 4.5.

  > [!NOTE]
  > Rozhraní .NET Framework 4.5.1 a .NET Framework 4.5 se zde používají pouze jako příklady. Popsaný princip platí pro všechny aplikace, které se zaměřují na novější verzi rozhraní .NET Framework, než je nainstalované v systému, ve kterém je spuštěna.

Některé změny v rozhraní .NET Framework mohou vyžadovat změny kódu aplikace. Viz [Kompatibilita aplikací](application-compatibility.md) před spuštěním existujících aplikací s rozhraním .NET Framework 4.5 nebo novějšími verzemi. Další informace o instalaci aktuální verze naleznete [v tématu Instalace rozhraní .NET Framework pro vývojáře](../install/guide-for-developers.md). Informace o podpoře rozhraní .NET Framework naleznete v tématu [zásady oficiální podpory rozhraní .NET Framework](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) na webu .NET.

## <a name="remarks-for-older-versions"></a>Poznámky pro starší verze

Rozhraní .NET Framework verze 2.0, 3.0 a 3.5 jsou vytvořeny se stejnou verzí CLR (CLR 2.0). Tyto verze představují sousední vrstvy jedné instalace. Každá verze je postupně sestavena nad předchozí verzí. Není možné spustit verze 2.0, 3.0 a 3.5 vedle sebe v počítači. Při instalaci verze 3.5 automaticky získáte vrstvy 2.0 a 3.0 a aplikace, které byly vytvořeny pro verze 2.0, 3.0 a 3.5, lze spustit na verzi 3.5. Rozhraní .NET Framework 4 však ukončí tento přístup vrstvení a ona a novější verze (.NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 a 4.8) také představují po sobě jdoucí vrstvy jedné instalace. Počínaje rozhraním .NET Framework 4 můžete použít hostování v procesu vedle sebe ke spuštění více verzí CLR v jednom procesu. Další informace naleznete v [tématu Sestavení a souběžné provádění](../../standard/assembly/side-by-side-execution.md).

Kromě toho, pokud vaše aplikace cílí na verzi 2.0, 3.0 nebo 3.5, mohou být uživatelé před spuštěním aplikace povolováni k povolení rozhraní .NET Framework 3.5 v počítači s Windows 8, Windows 8.1 nebo Windows 10. Další informace naleznete [v tématu Instalace rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8](../install/dotnet-35-windows-10.md).

## <a name="next-steps"></a>Další kroky

- Pokud s rozhraním .NET Framework tečujete, podívejte se na [přehled](../get-started/overview.md) úvodu ke klíčovým konceptům a funkcím.

- Nové funkce a vylepšení v rozhraní .NET Framework 4.5 a jeho bodové verze naleznete [v tématu Co je nového v rozhraní .NET Framework](../whats-new/index.md).

- Informace o migraci aplikace do novější verze rozhraní .NET Framework naleznete v [průvodci migrací](index.md).

- Informace o určení, které verze nebo aktualizace jsou v počítači nainstalovány, naleznete v tématu [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md) and How [to: Determine Which .NET Framework Updates Are Installed](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="see-also"></a>Viz také

- [Zásady](version-compatibility.md)
| oficiální podpory rozhraní[.NET Framework kompatibility](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) verzí
- [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
