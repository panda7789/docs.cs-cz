---
title: "Postupy: zjištění nainstalovaných verzí rozhraní .NET Framework"
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
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
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83de6036a9b86478546cdb8356ce132ef32e6be2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework
Uživatelé můžou instalovat a spuštění několika verzí rozhraní .NET Framework na svých počítačích. Při vývoji nebo nasazení aplikace, může být potřeba vědět, jaké verze rozhraní .NET Framework, které jsou nainstalovány v počítači uživatele. Všimněte si, že rozhraní .NET Framework obsahuje dvě hlavní komponenty, které jsou samostatně verzí:  
  
-   Sadu sestavení, která jsou kolekce typů a prostředky, které poskytují funkce pro vaše aplikace. Rozhraní .NET Framework a sestavení sdílet stejné číslo verze.  
  
-   Modul CLR (CLR), který spravuje a spouští kód aplikace. Modul CLR je určený podle čísla svou vlastní verzi (viz [verze a závislosti](~/docs/framework/migration-guide/versions-and-dependencies.md)).  
  
 Chcete-li získat přesné seznam verze rozhraní .NET Framework nainstalované v počítači, můžete zobrazit registru nebo v registru v kódu:  
  
 [Zobrazení registru (verze 1-4)](#net_a)  
 [Zobrazení registru (verze 4.5 nebo novější)](#net_b)  
 [Pomocí kódu v registru (verze 1-4)](#net_c)  
 [Pomocí kódu v registru (verze 4.5 nebo novější)](#net_d)  
 [Pomocí prostředí PowerShell v registru (verze 4.5 nebo novější)](#ps_a)  
  
 K vyhledání verze CLR, můžete použít nástroj nebo kódu:  
  
 [Pomocí nástroje Clrver](#clr_a)  
 [Pomocí kódu k dotazování System.Environment – třída](#clr_b)  
  
 Informace o zjišťování nainstalovaných aktualizací pro každou verzi rozhraní .NET Framework najdete v tématu [postupy: určení rozhraní .NET Framework aktualizace jsou nainstalované](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md). Informace o instalaci rozhraní .NET Framework najdete v tématu [instalaci rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md).  
  
<a name="net_a"></a>   
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a>Najít rozhraní .NET Framework verze zobrazením registru (rozhraní .NET Framework 1 – 4)  
  
1.  Na **spustit** nabídce zvolte **spustit**.  
  
2.  V **otevřete** zadejte **regedit.exe**.  
  
     Ke spuštění souboru regedit.exe musíte mít oprávnění správce.  
  
3.  V editoru registru otevřete následující podklíč:  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     Nainstalované verze jsou uvedeny v podklíči NDP. Číslo verze je uložené v **verze** položku. Pro [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] **verze** položka je v rámci klienta nebo úplné podklíčem (v NRP), nebo v obou podklíče.  
  

    > [!NOTE]
    > Složka „NET Framework Setup“ v registru nezačíná tečkou.

<a name="net_b"></a> 
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a>Najít rozhraní .NET Framework verze zobrazením registru (rozhraní .NET Framework 4.5 nebo novější)

1. Na **spustit** nabídce zvolte **spustit**.

2. V **otevřete** zadejte **regedit.exe**.

     Ke spuštění souboru regedit.exe musíte mít oprávnění správce.

3. V editoru registru otevřete následující podklíč:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     Všimněte si, že cesta k `Full` podklíč obsahuje podklíč `Net Framework` místo `.NET Framework`.

    > [!NOTE]
    > Pokud `Full` podklíč není k dispozici, pak nemají rozhraní .NET Framework 4.5 nebo novější.

     Zkontrolujte hodnotu DWORD s názvem `Release`. Existenci `Release` DWORD znamená, že [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější byl na tomto počítači nainstalován.

     ![Položky registru pro rozhraní .NET Framework 4.5. ] (../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")

     Hodnota `Release` DWORD označuje, která verze rozhraní .NET Framework je nainstalovaná.

    |Hodnota DWORD verze|Version|
    |--------------------------------|-------------|
    |378389|.NET Framework 4.5|
    |378675|Rozhraní .NET framework 4.5.1 nainstalované s Windows 8.1 nebo Windows Server 2012 R2|
    |378758|Rozhraní .NET framework 4.5.1 nainstalovaný na Windows 8, Windows 7 SP1 nebo Windows Vista SP2|
    |379893|.NET Framework 4.5.2|
    |V systémech Windows 10: 393295<br /><br /> Na všech ostatních verzí operačního systému: 393297|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |V systémech Windows 10 listopadu Update: 394254<br /><br /> Na všech ostatních verzí operačního systému: 394271|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |Na Windows 10 Anniversary aktualizace: 394802<br /><br /> Na všech ostatních verzí operačního systému: 394806|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |Na Windows 10 Creators aktualizace: 460798<br/><br/> Na všech ostatních verzí operačního systému: 460805 | Rozhraní .NET framework 4.7 |
    |V systému Windows 10 spadají Creators aktualizace: 461308<br/><br/> Na všech ostatních verzí operačního systému: 461310 | Rozhraní .NET framework 4.7.1 |
<a name="net_c"></a> 
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a>Vyhledání verze rozhraní .NET Framework podle v registru v kódu (rozhraní .NET Framework 1 – 4)

- Použití <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> třídy pro přístup k Software\Microsoft\NET Framework Setup\NDP\ podklíčem v HKEY_LOCAL_MACHINE v registru systému Windows.

     Následující kód ukazuje příklad tohoto dotazu.

    > [!NOTE]
    > Tento kód nezobrazuje k zjištění [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější. Zkontrolujte `Release` DWORD ke zjištění těchto verzí, jak je popsáno v předchozí části. Pro kód, který zjistí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější verze, najdete v další části v tomto článku.

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     Vzorové postupy budou mít výstup podobný následujícímu:

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a>Vyhledání verze rozhraní .NET Framework podle v registru v kódu (rozhraní .NET Framework 4.5 nebo novější)

1. Existenci `Release` DWORD označuje, zda na počítači byla nainstalována rozhraní .NET Framework 4.5 nebo novější. Hodnota klíčového slova označuje, že nainstalovaná verze. Chcete-li zkontrolovat toto klíčové slovo, použijte <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> a <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metody <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> třídy pro přístup k Software\Microsoft\NET Framework Setup\NDP\v4\Full podklíčem v HKEY_LOCAL_MACHINE v registru systému Windows.

2. Zkontrolujte hodnotu `Release` – klíčové slovo určení nainstalované verze. Chcete-li být dopřednou, můžete zkontrolovat na hodnotu větší než nebo rovna hodnotě hodnoty uvedené v tabulce. Tady jsou verze rozhraní .NET Framework a přidružených `Release` klíčová slova.

    |Version|Hodnota DWORD verze|
    |-------------|--------------------------------|
    |.NET Framework 4.5|378389|
    |Rozhraní .NET framework 4.5.1 nainstalované s Windows 8.1|378675|
    |Rozhraní .NET framework 4.5.1 nainstalovaný na Windows 8, Windows 7 SP1 nebo Windows Vista SP2|378758|
    |.NET Framework 4.5.2|379893|
    |Rozhraní .NET framework 4.6 nainstalovaná se systémem Windows 10|393295|
    |Rozhraní .NET framework 4.6 nainstalované na všech ostatních verzí operačního systému Windows|393297|
    |Rozhraní .NET framework 4.6.1 nainstalována ve Windows 10|394254|
    |Rozhraní .NET framework 4.6.1, které jsou nainstalované na všech ostatních verzí operačního systému Windows|394271|
    |Rozhraní .NET framework 4.6.2 nainstalovaný na Windows 10 Anniversary aktualizace|394802|
    |Rozhraní .NET framework 4.6.2 nainstalované na všech ostatních verzí operačního systému Windows|394806|
    |Rozhraní .NET framework 4.7 nainstalovaný na Windows 10 Creators Update|460798|
    |4.7 rozhraní .NET framework nainstalované na všech ostatních verzí operačního systému Windows|460805|
    |Rozhraní .NET framework 4.7.1 nainstalovaný na Windows 10 patří Creators aktualizace|461308|
    |Rozhraní .NET framework 4.7.1 nainstalované na všech ostatních verzí operačního systému Windows|461310|

     Následující příklad kontroly `Release` hodnotu v registru na určit, zda [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo je nainstalovaná novější verze rozhraní .NET Framework.

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     Tento příklad dodržuje doporučený postup pro kontrolu verzí:

    - Zkontroluje, zda hodnota `Release` položka je *větší než nebo rovna hodnotě* hodnotu klíče známé verze.

    - Zkontroluje, aby nejstarší verze z nejnovější verze.

<a name="ps_a"></a> 
#### <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a>Hledání minimální požadovaná verze rozhraní .NET Framework v registru v prostředí PowerShell (rozhraní .NET Framework 4.5 nebo novější)

- Následující příklad kontroluje hodnotu `Release` – klíčové slovo k určení zda rozhraní .NET Framework 4.6.2 nebo vyšší není nainstalovaná, bez ohledu na to verze operačního systému Windows (vrácení `True` Pokud je a `False` jinak).

    ```PowerShell
    Get-ChildItem "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | ForEach-Object { $_ -ge 394802 } 
    ```

    Můžete nahradit `394802` v předchozím příkladu s jinou hodnotou z zkontrolujte pro jinou verzi rozhraní .NET Framework minimální požadovaná v následující tabulce.
  
    |Version|Minimální hodnota DWORD verze|
    |-------------|--------------------------------|
    |.NET Framework 4.5|378389|
    |.NET Framework 4.5.1|378675|
    |.NET Framework 4.5.2|379893|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|393295|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|394254|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|394802|
    |Rozhraní .NET framework 4.7|460798|
    |Rozhraní .NET framework 4.7.1|461308|
    
<a name="clr_a"></a> 
#### <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a>Pomocí nástroje Clrver najít aktuální verzi modulu runtime

- Chcete-li zjistit, jaké verze Common Language Runtime jsou nainstalovány v počítači, použijte nástroj CLR Version Tool (Clrver.exe).

     Z Visual Studio příkazovém řádku zadejte `clrver`. Tento příkaz vytváří výstup podobný následujícímu:

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     Další informace o použití tohoto nástroje najdete v tématu [Clrver.exe (nástroj verze CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).

<a name="clr_b"></a> 
#### <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a>Vyhledání aktuální verze modulu runtime pomocí dotazu na třídu prostředí v kódu

- Dotaz <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnosti načíst <xref:System.Version> objekt, který určuje verzi modulu runtime, který je aktuálně zpracovávaných kód. Můžete použít <xref:System.Version.Major%2A?displayProperty=nameWithType> vlastnost k získání identifikátor hlavní verzi (například "4" pro verzi 4.0), <xref:System.Version.Minor%2A?displayProperty=nameWithType> vlastnost k získání identifikátor dílčí verzi (například "0" pro verzi 4.0), nebo <xref:System.Object.ToString%2A?displayProperty=nameWithType> získat pro celou verzi – metoda řetězec (například "4.0.30319.18010", jak je znázorněno v následujícím kódu). Tato vlastnost vrátí jednu hodnotu, která odpovídá verzi modulu runtime, který momentálně spouští kód; nevrací se verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.

     Pro rozhraní .NET Framework verze 4, 4.5, 4.5.1 a 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost vrátí <xref:System.Version> objekt, jehož řetězcovou reprezentaci má tvar `4.0.30319.xxxxx`. Pro rozhraní .NET Framework 4.6 a novější, je formulář `4.0.30319.42000`.

    > [!IMPORTANT]
    > Pro [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a novější, nedoporučujeme pomocí <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost zjistit verzi modulu runtime. Místo toho doporučujeme zadat dotaz registru, jak je popsáno v [vyhledání verze rozhraní .NET Framework podle v registru v kódu (rozhraní .NET Framework 4.5 nebo novější)](#net_d) dříve v tomto článku.

     Tady je příklad dotazu <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost pro informace o verzi modulu runtime:

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     Vzorové postupy budou mít výstup podobný následujícímu:

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a>Viz také
 [Postupy: Zjištění nainstalovaných aktualizací rozhraní .NET Framework](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
 [Nainstalujte rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md)  
 [Verze a závislosti](~/docs/framework/migration-guide/versions-and-dependencies.md)
