---
title: .NET Framework & verze operačních systémů Windows
description: Seznamte se s klíčovými funkcemi v každé verzi .NET Framework, včetně základních verzí CLR a verzí nainstalovaných operačním systémem Windows.
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: df44786dfd0a384ae2498a94d14b029612450fee
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475473"
---
# <a name="net-framework-versions-and-dependencies"></a>.NET Framework verze a závislosti

Každá verze .NET Framework obsahuje modul CLR (Common Language Runtime), knihovny základních tříd a další spravované knihovny. Tento článek popisuje klíčové funkce .NET Framework podle verze, poskytuje informace o základních verzích CLR a přidružených vývojových prostředích a identifikuje verze, které jsou nainstalovány v operačním systému Windows (OS).

Každá nová verze .NET Framework přidává nové funkce, ale zachovává funkce z předchozích verzí.

Modul CLR je identifikován vlastním číslem verze. Číslo verze .NET Framework se zvýší v každé vydané verzi, ale verze CLR se vždy nezvýší. Například .NET Framework 4, 4,5 a novější verze zahrnují modul CLR 4, ale .NET Framework 2,0, 3,0 a 3,5 zahrnují 2,0 CLR. (Verze 3 CLR neexistovala.)

> [!TIP]
>
> - Úplný seznam podporovaných operačních systémů najdete v tématu požadavky na [systém](../get-started/system-requirements.md).
> - Informace ke stažení najdete v tématu [instalace .NET Framework pro vývojáře](../install/guide-for-developers.md).
> - Informace o určení, které verze .NET Framework jsou nainstalovány v počítači, naleznete v tématu [jak určit, které verze .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md).

## <a name="version-information"></a>Informace o verzi

Následující tabulky shrnují .NET Framework historii verzí a korelují jednotlivé verze se sadou Visual Studio, Windows a Windows serverem. Visual Studio podporuje cílení na více verzí, takže nejste omezeni na verzi .NET Framework, která je uvedena v seznamu.

- Ikona značky zaškrtnutí ✔️ označuje verze operačního systému, na kterých je .NET Framework nainstalované, ale musí být povolené [v Ovládacích panelech](../install/dotnet-35-windows-10.md) (pro Windows) nebo prostřednictvím Správce serveru (pro Windows Server).
- Ikona znaménka plus ➕ označuje verze operačního systému, na kterých .NET Framework instalovat, ale mohou být nainstalovány.

| | |
| - | - |
| [.NET Framework 4,8](#net-framework-48) | [.NET Framework 4.7.2](#net-framework-472) | [.NET Framework 4.7.1](#net-framework-471) | [.NET Framework 4,7](#net-framework-47) |
| [.NET Framework 4.6.2](#net-framework-462) | [.NET Framework 4.6.1](#net-framework-461) | [.NET Framework 4.6](#net-framework-46) | [.NET Framework 4.5.2](#net-framework-452) |
| [.NET Framework 4.5.1](#net-framework-451) | [.NET Framework 4.5](#net-framework-45) | [.NET Framework 4](#net-framework-4) | [.NET Framework 3.5](#net-framework-35) |
| [.NET Framework 3.0](#net-framework-30) | [.NET Framework 2,0](#net-framework-20) | [.NET Framework 1.1](#net-framework-11) | [.NET Framework 1.0](#net-framework-10) |

### <a name="net-framework-48"></a> .NET Framework 4.8

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-48)
- [Novinka v přístupnosti](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)
- [Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Verze systému Windows**|Aktualizace ✔️ 10 května 2019<br/>➕ 10. října 2018 Update (verze 1809)<br/>➕ 10. dubna 2018 Update (verze 1803)<br/>Aktualizace Creators v ➕ 10 (verze 1709)<br/>Aktualizace ➕ 10 Creators Update (verze 1703)<br/>➕ 10 – aktualizace pro výročí (verze 1607)<br/>➕ 8,1<br/>➕ 7|
|**Verze Windows serveru**|➕ Windows Server 2019<br/>➕ Windows Server verze 1809<br/>➕ Windows Server verze 1803<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Určení nainstalované verze rozhraní .NET**|Použít `Release` DWORD:<br/>-528040 (aktualizace z Windows 10 se dá 2019)<br/>-528049 (všechny ostatní verze operačního systému)<br/>(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-472"></a> .NET Framework 4.7.2

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-472)
- [Novinka v přístupnosti](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)
- [Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Zahrnuto ve verzi sady Visual Studio**|2019<sup>1</sup>|
|**Verze systému Windows**|✔️ 10. října 2018 Update (verze 1809)<br/>✔️ 10. dubna 2018 Update (verze 1803)<br/>Aktualizace Creators v ➕ 10 (verze 1709)<br/>Aktualizace ➕ 10 Creators Update (verze 1703)<br/>➕ 10 – aktualizace pro výročí (verze 1607)<br/>➕ 8,1<br/>➕ 7|
|**Verze Windows serveru**|✔️ Windows Server 2019<br/>✔️ Windows Server verze 1809<br/>✔️ Windows Server verze 1803<br/>➕ Windows Server verze 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Určení nainstalované verze rozhraní .NET**|Použít `Release` DWORD:<br/>-461814 (aktualizace Windows 10 říjen 2018)<br/>-461808 (aktualizace Windows 10 z dubna 2018 a Windows Server, verze 1803)<br/>-461814 (všechny ostatní verze operačního systému)<br/>(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

<sup>1</sup> vyžaduje instalaci vývoj **desktopových**aplikací pro .NET, **ASP.NET a vývoje webů**, vývoj pro **Azure**, **vývoj pro Office/SharePoint**, vývoj **mobilních aplikací pomocí .NET**nebo **.NET Core pro vývoj pro různé platformy** .

### <a name="net-framework-471"></a>.NET Framework 4.7.1

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-471)
- [Novinka v přístupnosti](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)
- [Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Verze systému Windows**|Aktualizace Creators v ✔️ 10 (verze 1709)<br/>Aktualizace ➕ 10 Creators Update (verze 1703)<br/>➕ 10 – aktualizace pro výročí (verze 1607)<br/>➕ 8,1<br/>➕ 7|
|**Verze Windows serveru**|➕ Windows Server verze 1803<br/>✔️ Windows Server verze 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Určení nainstalované verze rozhraní .NET**|Použít `Release` DWORD:<br/>-461308 (Windows 10 Creators Update a Windows Server, verze 1709)<br/>-461310 (všechny ostatní verze operačního systému)<br/>(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-47"></a> .NET Framework 4.7

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-47)
- [Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Verze systému Windows**|Aktualizace ✔️ 10 Creators Update (verze 1703)<br/>➕ 10 – aktualizace pro výročí (verze 1607)<br/>➕ 8,1<br/>➕ 7|
|**Verze Windows serveru**|➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Určení nainstalované verze rozhraní .NET**|Použít `Release` DWORD:<br/>-460798 (Windows 10 Creators Update)<br/>-460805 (všechny ostatní verze operačního systému)<br/>(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-462"></a>.NET Framework 4.6.2

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-462)
- [Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Verze systému Windows**|✔️ 10 – aktualizace pro výročí (verze 1607)<br/>➕ 10 listopadu Update (verze 1511)<br/>➕ 10<br/>➕ 8,1<br />➕ 7|
|**Verze Windows serveru**|✔️ 2016<br /><br/>➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1|
|**Určení nainstalované verze rozhraní .NET**|Použít `Release` DWORD:<br /><br/>-394802 (aktualizace pro Windows 10 – výročí a Windows Server 2016)<br/>-394806 (všechny ostatní verze operačního systému)<br /><br/>(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-461"></a>.NET Framework 4.6.1

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-461)
- [Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Zahrnuto ve verzi sady Visual Studio**|2017<sup>1</sup>|
|**Verze systému Windows**|✔️ 10 listopadu Update (verze 1511)<br/>➕ 10<br />➕ 8,1<br />➕ 8<br />➕ 7|
|**Verze Windows serveru**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1|
|**Určení nainstalované verze rozhraní .NET**|Použít `Release` DWORD:<br /><br/>-394254 (aktualizace Windows 10 listopadu)<br />-394271 (všechny ostatní verze operačního systému)<br /><br/>(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

<sup>1</sup> vyžaduje instalaci vývoj **desktopových**aplikací pro .NET, **ASP.NET a vývoje webů**, vývoj pro **Azure**, **vývoj pro Office/SharePoint**, vývoj **mobilních aplikací pomocí .NET**nebo **.NET Core pro vývoj pro různé platformy** .

### <a name="net-framework-46"></a>.NET Framework 4.6

- [Nové funkce](../whats-new/index.md#whats-new-in-net-2015)
- [Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Zahrnuto ve verzi sady Visual Studio**|2015|
|**Verze systému Windows**|✔️ 10<br /><br />➕ 8,1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Verze Windows serveru**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Určení nainstalované verze rozhraní .NET**|Použít `Release` DWORD:<br /><br />-393295 (Windows 10)<br />-393297 (všechny ostatní verze operačního systému)<br /><br />(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-452"></a>.NET Framework 4.5.2

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-452)
- [Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Verze systému Windows**|➕ 8,1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Verze Windows serveru**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Určení nainstalované verze rozhraní .NET**|Použijte `Release` DWORD 379893<br /><br />(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-451"></a>.NET Framework 4.5.1

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-451)
- [Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Zahrnuto ve verzi sady Visual Studio**|2013|
|**Verze systému Windows**|✔️ 8,1<br /><br />➕ 8<br />➕ 7<br />➕ Vista|
|**Verze Windows serveru**|✔️ 2012 R2<br /><br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Určení nainstalované verze rozhraní .NET**|Použít `Release` DWORD:<br /><br />-378675 (Windows 8.1)<br />-378758 (vše ostatní)<br /><br />(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-45"></a>.NET Framework 4.5

- [Nové funkce](../whats-new/index.md#whats-new-in-net-framework-45)
- [Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)

|||
|-|-|
|**Verze CLR**|4|
|**Zahrnuto ve verzi sady Visual Studio**|2012|
|**Verze systému Windows**|✔️ 8<br />➕ 7<br />➕ Vista|
|**Verze Windows serveru**|✔️ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Určení nainstalované verze rozhraní .NET**|Použijte `Release` DWORD 378389<br /><br />(Viz [pokyny](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-4"></a>.NET Framework 4

[Nové funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms171868(v=vs.100))

|||
|-|-|
|**Verze CLR**|4|
|**Zahrnuto ve verzi sady Visual Studio**|2010|
|**Verze systému Windows**|➕ 7<br />➕ Vista|
|**Verze Windows serveru**|➕ 2008 R2 SP1<br />➕ 2008 SP2<br />➕ 2003|
|**Určení nainstalované verze rozhraní .NET**|Zobrazit [pokyny](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-35"></a>.NET Framework 3.5

[Nové funkce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\)):

- LINQ
- Stromy výrazů
- Vylepšená podpora ASP.NET pro vývoj v AJAX
- Kolekce HashSet –
- DateTimeOffset
- Integrace WCF a WF
- Sítě peer-to-peer
- Doplňky pro rozšiřitelnost

|||
|-|-|
|**Verze CLR**|2.0|
|**Zahrnuto ve verzi sady Visual Studio**|2008|
|**Verze systému Windows**|✔️ 10\*<br/>✔️ 8,1\*<br />✔️ 8\*<br />✔️ 7<br /><br />➕ Vista|
|**Verze Windows serveru**|➕ Windows Server verze 1803\*<br/>➕ Windows Server verze 1709\*<br/>➕ 2016\*<br/>➕ 2012 R2\*<br />➕ 2012\*<br /><br />✔️ 2008 R2 SP1\*<br /><br/>➕ 2008 SP2<br />➕ 2003|
|**Určení nainstalované verze rozhraní .NET**|Zobrazit [pokyny](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-30"></a>.NET Framework 3.0

[Nové funkce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb822048(v=vs.90)):

- Windows Presentation Foundation
- Windows Communication Foundation
- Windows Workflow Foundation
- Služba Windows CardSpace

|||
|-|-|
|**Verze CLR**|2.0|
|**Verze systému Windows**|✔️ Vista|
|**Verze Windows serveru**|✔️ 2008 R2 SP1 *<br />✔️ 2008 SP2\*<br /><br />➕ 2003|
|**Určení nainstalované verze rozhraní .NET**|Viz [pokyny](how-to-determine-which-versions-are-installed.md).|

### <a name="net-framework-20"></a>.NET Framework 2,0

[Nové funkce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t357fb32%28v%3dvs.90%29):

- Obecné typy
- Upravit a pokračovat ladicímu programu
- Zlepšení škálovatelnosti a výkonu
- ClickOnce – nasazení
- V ASP.NET 2,0 nové ovládací prvky a podpora pro širokou škálu prohlížečů
- podpora 64bitových technologií

|||
|-|-|
|**Verze CLR**|2.0|
|**Zahrnuto ve verzi sady Visual Studio**|2005|
|**Verze systému Windows**|–|
|**Verze Windows serveru**|✔️ 2008 R2 SP1<br />✔️ 2008 SP2<br />✔️ 2003|
|**Určení nainstalované verze rozhraní .NET**|Zobrazit [pokyny](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-11"></a>.NET Framework 1.1

[Nové funkce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/h88tthh0%28v%3dvs.90%29):

- ASP.NET mobilní ovládací prvky
- Souběžné spouštění
- Podpora protokolu IPv6

|||
|-|-|
|**Verze CLR**|1.1|
|**Zahrnuto ve verzi sady Visual Studio**|2003|
|**Verze systému Windows**|–|
|**Verze Windows serveru**|✔️ 2003|
|**Určení nainstalované verze rozhraní .NET**|Zobrazit [pokyny](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-10"></a>.NET Framework 1.0

|||
|-|-|
|**Verze CLR**|1.0|
|**Zahrnuto ve verzi sady Visual Studio**|Visual Studio .NET|
|**Verze systému Windows**|–|
|**Verze Windows serveru**|–|
|**Určení nainstalované verze rozhraní .NET**|Zobrazit [pokyny](how-to-determine-which-versions-are-installed.md)|

> [!NOTE]
>
> - V tomto operačním systému .NET Framework musí být povolená přes [Ovládací panely (pro Windows) nebo správce serveru (pro Windows Server)](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel).
> - Obecně platí, že byste neměli odinstalovat žádné verze .NET Framework nainstalované na vašem počítači, protože na konkrétní verzi může záviset aplikace, kterou používáte, a v případě, že se tato verze odebere, může dojít k přerušení. V jednom počítači můžete najednou načíst několik verzí .NET Framework. To znamená, že můžete nainstalovat .NET Framework bez nutnosti odinstalování předchozích verzí. Další informace najdete v tématu [Začínáme](../get-started/index.md).

## <a name="remarks-for-version-45-and-later"></a>Poznámky pro verzi 4,5 a novější

.NET Framework 4,5 je místní aktualizace, která nahrazuje .NET Framework 4 ve vašem počítači a podobně .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 a 4,8 jsou místní aktualizace .NET Framework 4,5. Místní aktualizace znamená, že používají stejnou verzi modulu runtime, ale aktualizované verze sestavení a zahrnují nové typy a členy. Po instalaci jedné z těchto aktualizací by se .NET Framework 4, .NET Framework 4,5, .NET Framework 4,6 nebo .NET Framework 4,7, aby aplikace běžely i bez nutnosti opětovné kompilace. Opačně to však neplatí. Nedoporučujeme spouštět aplikace, které cílí na novější verzi .NET Framework v dřívější verzi. Například nedoporučujeme spouštět aplikaci cíle .NET Framework 4,6 na .NET Framework 4,5.

Platí následující pokyny:

- V sadě Visual Studio můžete zvolit .NET Framework 4,5 jako cílovou architekturu projektu (tím se nastaví <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType> vlastnost) pro zkompilování projektu jako sestavení .NET Framework 4,5 nebo spustitelného souboru. Toto sestavení nebo spustitelný soubor je pak možné použít na jakémkoli počítači s nainstalovanou .NET Framework 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 nebo 4,8.

- V aplikaci Visual Studio můžete zvolit .NET Framework 4.5.1 jako cílovou architekturu projektu, aby byla zkompilována jako sestavení .NET Framework 4.5.1 nebo spustitelný soubor. Toto sestavení nebo spustitelný soubor spouštějte pouze v počítačích, ve kterých je nainstalována .NET Framework 4.5.1 nebo novější. Pro spustitelný soubor, který cílí na .NET Framework 4.5.1, se zablokuje spuštění v počítači, který má jenom starší verzi .NET Framework, jako je třeba .NET Framework 4,5. Uživateli se zobrazí výzva k instalaci .NET Framework 4.5.1. Kromě toho .NET Framework 4.5.1 sestavení nesmí být voláno z aplikace, která cílí na starší verzi .NET Framework, jako je například .NET Framework 4,5.

  > [!NOTE]
  > .NET Framework 4.5.1 a .NET Framework 4,5 se tady používají jenom jako příklady. Popsaná zásada platí pro všechny aplikace, které cílí na novější verzi .NET Framework než ta, která je nainstalovaná v systému, ve kterém je spuštěná.

Některé změny v .NET Framework mohou vyžadovat změny kódu vaší aplikace. než začnete používat stávající aplikace s .NET Framework 4,5 nebo novějšími verzemi, podívejte se na [kompatibilitu aplikací](application-compatibility.md) . Další informace o instalaci aktuální verze najdete v tématu [instalace .NET Framework pro vývojáře](../install/guide-for-developers.md). Informace o podpoře pro .NET Framework najdete v tématu [.NET Framework oficiální zásady podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) na webu .NET.

## <a name="remarks-for-older-versions"></a>Poznámky pro starší verze

.NET Framework verze 2,0, 3,0 a 3,5 jsou sestavené se stejnou verzí modulu CLR (CLR 2,0). Tyto verze představují sousední vrstvy jedné instalace. Každá verze je postupně sestavena nad předchozí verzí. Na počítači není možné spouštět verze 2,0, 3,0 a 3,5 vedle sebe. Při instalaci verze 3.5 automaticky získáte vrstvy 2.0 a 3.0 a aplikace, které byly vytvořeny pro verze 2.0, 3.0 a 3.5, lze spustit na verzi 3.5. .NET Framework 4 ale tento přístup k vrstvení a novější verze (.NET Framework 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 a 4,8) také reprezentují po sobě jdoucí vrstvy jedné instalace. Počínaje .NET Framework 4 můžete použít vnitroprocesové hostování vedle sebe, aby se spouštělo více verzí modulu CLR v jednom procesu. Další informace naleznete v tématu [sestavení a souběžné spouštění](../../standard/assembly/side-by-side-execution.md).

Kromě toho, pokud vaše aplikace cílí na verzi 2,0, 3,0 nebo 3,5, mohou uživatelé vyžadovat .NET Framework 3,5 na počítači se systémem Windows 8, Windows 8.1 nebo Windows 10 předtím, než budou moct aplikaci spustit. Další informace najdete v tématu [instalace .NET Framework 3,5 ve Windows 10, Windows 8.1 a Windows 8](../install/dotnet-35-windows-10.md).

## <a name="next-steps"></a>Další kroky

- Pokud s .NET Framework začínáte, přečtěte si [Přehled](../get-started/overview.md) úvodních konceptů a funkcí.

- Nové funkce a vylepšení .NET Framework 4,5 a jejich vydání najdete v tématu [co je nového v .NET Framework](../whats-new/index.md).

- Informace o migraci aplikace na novější verzi .NET Framework najdete v [Průvodci migrací](index.md).

- Informace o určení, které verze nebo aktualizace jsou nainstalovány v počítači, naleznete v tématu [Postupy: určení, které verze .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md) a [Postupy: určení, které .NET Framework aktualizace jsou nainstalovány](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="see-also"></a>Viz také

- [Kompatibilita verzí](version-compatibility.md) 
|  [.NET Framework oficiálních zásad podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
