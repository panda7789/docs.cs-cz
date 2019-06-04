---
title: 'Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework'
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e6086772b807440570b94cfff268aa1d78fa048
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490001"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework

Uživatelé můžou [nainstalovat](https://docs.microsoft.com/dotnet/framework/install) a spuštění několika verzí rozhraní .NET Framework na svých počítačích. Při vývoji nebo nasazení vaší aplikace, můžete potřebovat vědět, jaké verze rozhraní .NET Framework jsou nainstalovány v počítači uživatele.

Rozhraní .NET Framework obsahuje dvě hlavní součásti, které mají samostatné verze:

- Sadu sestavení, která jsou kolekce typů a prostředků, které poskytují funkce pro vaše aplikace. Rozhraní .NET Framework a sestavení sdílejí stejné číslo verze.

- Modul CLR (CLR), jež spravuje a spouští kód vaší aplikace. CLR je identifikováno svým vlastním číslem verze (viz [verze a závislosti](~/docs/framework/migration-guide/versions-and-dependencies.md)).

> [!NOTE]
> Každá nová verze rozhraní .NET Framework zachovává funkce předchozích verzí a přidává nové funkce. Více verzí rozhraní .NET Framework v jednom počítači můžete načíst ve stejnou dobu, což znamená, že můžete nainstalovat rozhraní .NET Framework bez odinstalování předchozích verzí. Obecně platí že byste neměli odinstalovávat předchozích verzích rozhraní .NET Framework, protože na konkrétní verzi může záviset aplikace, které používáte a mohou přestat fungovat, pokud je verze odebrána.
>
> Existuje rozdíl mezi verzí rozhraní .NET Framework a verzi modulu CLR:
> - Verze rozhraní .NET Framework je založená na sadu sestavení, které tvoří knihovny tříd rozhraní .NET Framework. Například zahrnují verze rozhraní .NET Framework 4.5, 4.6.1 a 4.7.2.
>- Verze CLR je založená na modulu runtime, na kterém aplikace rozhraní .NET Framework jsou spouštěny. Jedna verze modulu CLR obvykle podporuje více verzí rozhraní .NET Framework. Například verze modulu CLR 4.0.30319. *xxxxx* podporuje rozhraní .NET Framework verze 4 až 4.5.2, kde *xxxxx* je menší než 42000 a CLR verze 4.0.30319.42000 podporuje verze rozhraní .NET Framework počínaje .NET Framework 4.6.
>
> Další informace o verzích, najdete v části [rozhraní .NET Framework verze a závislosti](versions-and-dependencies.md).

Pokud chcete získat seznam verzí rozhraní .NET Framework nainstalované na počítači, máte přístup k registru. Editor registru můžete použít buď k zobrazení registru nebo ji dotazovat s pomocí kódu:

- Najdete novější verze rozhraní .NET Framework (4.5 a novější):
  - [Pomocí Editoru registru vyhledejte verze rozhraní .NET Framework](#net_b)
  - [Použít kód k dotazování registru pro verze rozhraní .NET Framework](#net_d)
  - [Použití Powershellu k dotazování registru pro verze rozhraní .NET Framework](#ps_a)
- Najít starší verze rozhraní .NET Framework (1&#8211;4):
  - [Pomocí Editoru registru vyhledejte verze rozhraní .NET Framework](#net_a)
  - [Použít kód k dotazování registru pro verze rozhraní .NET Framework](#net_c)

Pokud chcete získat seznam verzí modulu CLR nainstalované v počítači, pomocí nástroje nebo kódu:

- [Použití nástroje Clrver](#clr_a)
- [Dotaz na třídu prostředí pomocí kódu](#clr_b)

Informace o zjišťování nainstalovaných aktualizací pro každou verzi rozhraní .NET Framework najdete v tématu [jak: Zjištění nainstalovaných aktualizací rozhraní .NET Framework](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="find-newer-net-framework-versions-45-and-later"></a>Najít novější verze rozhraní .NET Framework (4.5 a novější)

<a name="net_b"></a>

### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>Najít rozhraní .NET Framework verze 4.5 a vyšší v registru

1. Z **Start** nabídce zvolte **spustit**, zadejte *regedit*a pak vyberte **OK**.

     Musíte mít pověření správce, chcete-li spustit program regedit.

2. V editoru registru otevřete následující podklíč: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**. Pokud **úplné** podklíč není k dispozici a není k dispozici rozhraní .NET Framework 4.5 nebo novější.

    > [!NOTE]
    > **NET Framework Setup** složky v registru neodpovídá *není* nezačíná tečkou.

3. Vyhledejte položku DWORD s názvem **vydání**. Pokud existuje, pak je nutné rozhraní .NET Framework 4.5 nebo novější. Jeho hodnota je verze klíče, který odpovídá konkrétní verzi rozhraní .NET Framework. Na následujícím obrázku, například hodnoty **Release** položka je *378389*, což je verze klíč pro rozhraní .NET Framework 4.5.

     ![Položky registru pro rozhraní .NET Framework 4.5](media/clr-installdir.png "položky registru pro rozhraní .NET Framework 4.5")

V následující tabulce jsou uvedeny hodnoty **vydání** typu DWORD v jednotlivých operačních systémech pro rozhraní .NET Framework 4.5 a novější verze.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|Verze rozhraní .NET Framework|Hodnota DWORD verze|
|--------------------------------|-------------|
|.NET Framework 4.5|Všechny operační systémy Windows: 378389|
|.NET Framework 4.5.1|Na Windows 8.1 a Windows Server 2012 R2: 378675<br />Na všechny ostatní Windows operační systémy: 378758|
|.NET Framework 4.5.2|Všechny operační systémy Windows: 379893|
|.NET Framework 4.6|On Windows 10: 393295<br />Na všechny ostatní Windows operační systémy: 393297|
|.NET Framework 4.6.1|V systémech Windows 10. listopadu Update: 394254<br />Na všechny ostatní Windows operačních systémů (včetně Windows 10): 394271|
|.NET Framework 4.6.2|V systému Windows 10 Anniversary Update a Windows Server 2016: 394802<br />Na všechny ostatní Windows operačních systémů (včetně jiných operačních systémech Windows 10): 394806|
|Rozhraní .NET framework 4.7|Na Windows 10 Creators Update: 460798<br />Na všechny ostatní Windows operačních systémů (včetně jiných operačních systémech Windows 10): 460805|
|.NET Framework 4.7.1|V systému Windows Server verze 1709 a Windows 10 Fall Creators Update: 461308<br/>Na všechny ostatní Windows operačních systémů (včetně jiných operačních systémech Windows 10): 461310|
|.NET Framework 4.7.2|Ve Windows 10. dubna 2018 Update a Windows Server verze 1803: 461808<br/>Ve všech operačních systémech Windows než Windows 10. dubna 2018 Update a Windows Server verze 1803: 461814|
|.NET Framework 4.8|Při aktualizaci Windows 10. května 2019: 528040<br/>Na všechny ostatní operační systémy Windows (včetně jiných operačních systémech Windows 10): 528049|

Tyto hodnoty můžete použít takto:

- K určení, zda konkrétní verzi rozhraní .NET Framework je nainstalována na konkrétní verzi operačního systému Windows, otestovat, jestli **vydání** hodnotu DWORD *rovna* hodnota uvedená ve v tabulce. Například, pokud chcete zjistit, zda rozhraní .NET Framework 4.6 je k dispozici v systému Windows 10, test pro v **vydání** hodnotu *rovna* 393295.

- Chcete-li zjistit, zda je k dispozici minimální verzi rozhraní .NET Framework, použijte menší **vydání** hodnotu DWORD pro tuto verzi. Například pokud je aplikace spuštěná v rámci rozhraní .NET Framework 4.6 nebo novější verze, testování **vydání** hodnotu DWORD *větší než nebo rovna hodnotě* 393295. Pro tabulku, která obsahuje pouze minimální **vydání** hodnotu DWORD pro každou verzi rozhraní .NET Framework naleznete v tématu [minimální hodnoty DWORD verze rozhraní .NET Framework 4.5 a novější verze](minimum-release-dword.md).

- Pokud chcete testovat více verzí, začněte tím, že testování na hodnotu, která je *větší než nebo rovna hodnotě* na menší hodnotu DWORD pro nejnovější verzi rozhraní .NET Framework a pak porovnat hodnotu s menší hodnotu DWORD pro každou po sobě jdoucích starší verze. Například pokud vaše aplikace vyžaduje rozhraní .NET Framework 4.7 nebo novější a chcete zjistit, konkrétní verzi rozhraní .NET Framework, které jsou k dispozici, spusťte testováním **vydání** hodnotu DWORD *víc než nebo rovno*  k 461808 (menší hodnota DWORD pro rozhraní .NET Framework 4.7.2). Pak porovnat **vydání** hodnotu DWORD s menší hodnotu pro každou novější verzi rozhraní .NET Framework. Pro tabulku, která obsahuje pouze minimální **vydání** hodnotu DWORD pro každou verzi rozhraní .NET Framework naleznete v tématu [minimální hodnoty DWORD verze rozhraní .NET Framework 4.5 a novější verze](minimum-release-dword.md).

<a name="net_d"></a>

### <a name="find-net-framework-versions-45-and-later-with-code"></a>Najít rozhraní .NET Framework verze 4.5 a vyšší s kódem

1. Použití <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> a <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> metody pro přístup k **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** podklíčů v registru Windows.

    Existence **vydání** položku DWORD v **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** podklíč označuje, že je rozhraní .NET Framework 4.5 nebo novější verze počítači nainstalována.

2. Zkontrolujte hodnotu **vydání** položku k určení Instalovatelné verze. Aby dopřednou vyhledejte hodnotu větší než nebo rovno hodnota uvedená ve [tabulku verzí rozhraní .NET Framework](#version_table).

Následující příklad zkontroluje hodnotu vlastnosti **vydání** záznam v registru najít rozhraní .NET Framework 4.5 a novější verze, které jsou nainstalovány:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

V tomto příkladu následuje doporučený postup pro kontrolu verzí:

- Zkontroluje, zda hodnota **Release** položka je *větší než nebo rovna hodnotě* hodnotu klíče známé verze.

- Zkontroluje, aby nejstarší verzi z nejnovější verze.

<a name="ps_a"></a>

### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>Vyhledejte minimální požadovaná rozhraní .NET Framework verze (4.5 a novější) pomocí Powershellu

- Zkontrolovat hodnoty pomocí příkazů Powershellu **vydání** vstupu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** podklíči.

Následující příklady kontrolu hodnoty **vydání** položku k určení, zda rozhraní .NET Framework 4.6.2 nebo novější nainstalován. Tento kód vrátí `True` je-li nainstalován a `False` jinak.

```PowerShell
# PowerShell 5
 Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' |  Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 }
 ```

```PowerShell
# PowerShell 4
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

Vyhledat jinou verzi rozhraní .NET Framework minimální požadovaná, nahraďte *394802* v těchto příkladech se **vydání** hodnotu [tabulku verzí rozhraní .NET Framework](#version_table).

## <a name="find-older-net-framework-versions-182114"></a>Najít starší verze rozhraní .NET Framework (1&#8211;4)

<a name="net_a"></a>

### <a name="find-net-framework-versions-182114-in-the-registry"></a>Najít rozhraní .NET Framework verze 1&#8211;4 v registru

1. Z **Start** nabídce zvolte **spustit**, zadejte *regedit*a pak vyberte **OK**.

    Musíte mít pověření správce, chcete-li spustit program regedit.

2. V editoru registru otevřete následující podklíč: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:

    - Pro rozhraní .NET Framework verze 1.1 až 3.5, každý nainstalovaná verze je uveden jako podklíč **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** podklíči. Například **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**. Číslo verze je uloženo jako hodnota v podklíči verze **verze** položka.

    - Pro rozhraní .NET Framework 4 **verze** položka je v části **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** podklíči **HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\NET Framework Setup\NDP\v4.0\Full** podklíče, nebo pod oběma podklíči.

    > [!NOTE]
    > **NET Framework Setup** složky v registru nezačíná tečkou.

    Následující obrázek znázorňuje podklíče a jeho **verze** položku pro rozhraní .NET Framework 3.5.

    ![Položky registru pro rozhraní .NET Framework 3.5. ](media/net-4-and-earlier.png "Rozhraní .NET framework 3.5 a starší")

<a name="net_c"></a>

### <a name="find-net-framework-versions-182114-with-code"></a>Najít rozhraní .NET Framework verze 1&#8211;4 s kódem

- Použití <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> třídy k přístupu **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** podklíčů v registru Windows.

Následující příklad vyhledá rozhraní .NET Framework 1&#8211;4 verze, které jsou nainstalovány:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>Najít verze CLR

<a name="clr_a"></a>

### <a name="find-the-current-clr-version-with-clrverexe"></a>Vyhledání aktuální verze modulu CLR s Clrver.exe

Použití [nástroj CLR Version (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) k určení, jaké verze modulu CLR jsou nainstalovány v počítači:

- Z [Developer Command Prompt pro sadu Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), zadejte `clrver`.

    Ukázkový výstup:

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="find-the-current-clr-version-with-the-environment-class"></a>Vyhledání aktuální verze modulu CLR s třídou prostředí

> [!IMPORTANT]
> Pro rozhraní .NET Framework 4.5 a novější verze, nepoužívejte <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost zjistit verzi modulu CLR. Místo toho dotazu registru, jak je popsáno v [najít rozhraní .NET Framework verze 4.5 a vyšší s kódem](#net_d).

1. Dotaz <xref:System.Environment.Version?displayProperty=nameWithType> vlastnost pro načtení <xref:System.Version> objektu.

    Vrácený `System.Version` objekt určuje verzi modulu runtime, který aktuálně spouští kód. Nevrací se verze sestavení ani jiné verze modulu runtime, který byl nainstalován v počítači.

    Pro rozhraní .NET Framework verze 4, 4.5, 4.5.1 a 4.5.2, řetězcovou reprezentaci vráceného <xref:System.Version> objektu má tvar 4.0.30319. *xxxxx*, kde *xxxxx* je menší než 42000. Pro rozhraní .NET Framework 4.6 a novějším má formulář 4.0.30319.42000.

2. Až budete mít `Version` objektu, dotaz následujícím způsobem:

   - Pro hlavní verzi identifikátor (například *4* pro verzi 4.0), použijte <xref:System.Version.Major%2A?displayProperty=nameWithType> vlastnost.

   - Nezletilý release identifikátor (například *0* pro verzi 4.0), použijte <xref:System.Version.Minor%2A?displayProperty=nameWithType> vlastnost.

   - Pro celého řetězci verze (například *4.0.30319.18010*), použijte <xref:System.Version.ToString%2A?displayProperty=nameWithType> metody. Tato metoda vrátí jednu hodnotu, která odpovídá verzi modulu runtime, který se spouští kód. Nevrací se verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.

V následujícím příkladu <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost pro načtení informací o verzi modulu CLR:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Viz také:

- [Postupy: Zjištění nainstalovaných aktualizací rozhraní .NET Framework](how-to-determine-which-net-framework-updates-are-installed.md)
- [Instalace rozhraní .NET Framework pro vývojáře](../install/guide-for-developers.md)
- [Rozhraní .NET framework verze a závislosti](versions-and-dependencies.md)
