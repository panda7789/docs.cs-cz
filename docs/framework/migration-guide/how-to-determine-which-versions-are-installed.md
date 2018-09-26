---
title: 'Postupy: zjištění nainstalovaných verzí rozhraní .NET Framework'
ms.date: 04/10/2018
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
ms.openlocfilehash: 1874d5512f04f22b9c53bdc9e92d0c96e45d21c8
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199709"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Postupy: zjištění nainstalovaných verzí rozhraní .NET Framework

Mohou uživatelé nainstalovat a spustit více verzí rozhraní .NET Framework na svých počítačích. Při vývoji nebo nasazení vaší aplikace, můžete potřebovat vědět, jaké verze rozhraní .NET Framework jsou nainstalovány v počítači uživatele. Všimněte si, že rozhraní .NET Framework obsahuje dvě hlavní součásti, které mají samostatné verze:  
  
-   Sadu sestavení, která jsou kolekce typů a prostředků, které poskytují funkce pro vaše aplikace. Rozhraní .NET Framework a sestavení sdílejí stejné číslo verze.  
  
-   Modul CLR (CLR), jež spravuje a spouští kód vaší aplikace. CLR je identifikováno svým vlastním číslem verze (viz [verze a závislosti](~/docs/framework/migration-guide/versions-and-dependencies.md)).  
  
 Pokud chcete získat přesné seznam verzí rozhraní .NET Framework nainstalované na počítači, můžete zobrazit registru nebo dotazovat na registr v kódu:  
  
 [Zobrazení registru (verze 1 – 4)](#net_a)  
 [Zobrazení registru (verze 4.5 a novější)](#net_b)  
 [Použití kódu k registru (verze 1 – 4)](#net_c)  
 [Použití kódu k registru (verze 4.5 a novější)](#net_d)  
 [Použití Powershellu k registru (verze 4.5 a novější)](#ps_a)  
  
 Pokud chcete zjistit verzi modulu CLR, můžete použít nástroj nebo kódu:  
  
 [Pomocí nástroje Clrver](#clr_a)  
 [Dotaz na třídu System.Environment pomocí kódu](#clr_b)  
  
 Informace o zjišťování nainstalovaných aktualizací pro každou verzi rozhraní .NET Framework najdete v tématu [postupy: určení Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md). Informace o instalaci rozhraní .NET Framework najdete v tématu [nainstalovat rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md).  
  
<a name="net_a"></a>   
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a>K vyhledání verze rozhraní .NET Framework zobrazením registru (.NET Framework 1 – 4)  
  
1.  Na **Start** nabídce zvolte **spustit**.  
  
2.  V **otevřít** zadejte **regedit.exe**.  
  
     Ke spuštění souboru regedit.exe musíte mít oprávnění správce.  
  
3.  V editoru registru otevřete následující podklíč:  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     Nainstalované verze jsou uvedeny v podklíči NDP. Číslo verze je uloženo v **verze** položka. Pro [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] **verze** položka je pod klientem nebo úplným podklíčem (pod NDP) nebo pod oběma podklíči.  
  

    > [!NOTE]
    > Složka „NET Framework Setup“ v registru nezačíná tečkou.

<a name="net_b"></a> 
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a>K vyhledání verze rozhraní .NET Framework zobrazením registru (.NET Framework 4.5 nebo novější)

1. Na **Start** nabídce zvolte **spustit**.

2. V **otevřít** zadejte **regedit.exe**.

     Ke spuštění souboru regedit.exe musíte mít oprávnění správce.

3. V editoru registru otevřete následující podklíč:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     Všimněte si, že cesta k `Full` podklíč zahrnuje podklíče `Net Framework` spíše než `.NET Framework`.

    > [!NOTE]
    > Pokud `Full` podklíč není k dispozici a není nutné rozhraní .NET Framework 4.5 nebo novější.

     Vyhledejte hodnotu DWORD s názvem `Release`. Existence `Release` DWORD označuje, že [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější je nainstalovaný na tomto počítači.

     ![Položky registru pro rozhraní .NET Framework 4.5. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")

     Hodnota `Release` DWORD označuje, která verze rozhraní .NET Framework je nainstalována.

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |Hodnota DWORD verze|Version|
    |--------------------------------|-------------|
    |378389|.NET Framework 4.5|
    |378675|Rozhraní .NET framework 4.5.1 nainstalovaná s Windows 8.1 nebo Windows Server 2012 R2|
    |378758|Rozhraní .NET framework 4.5.1 nainstalované ve Windows 8, Windows 7 SP1 nebo Windows Vista SP2|
    |379893|.NET Framework 4.5.2|
    |Pouze v systémech Windows 10: 393295<br /><br /> Na všech ostatních verzí operačního systému: 393297|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |Pouze v systémech Windows 10. listopadu Update: 394254<br /><br /> Na všech ostatních verzí operačního systému: 394271|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |V systému Windows 10 Anniversary Update a Windows Server 2016:394802<br /><br /> Na všech ostatních verzí operačního systému: 394806|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |Jenom na Windows 10 Creators Update: 460798<br/><br/> Na všech ostatních verzí operačního systému: 460805 | Rozhraní .NET framework 4.7 |
    |Na Windows 10 Fall Creators Update pouze: 461308<br/><br/> Na všech ostatních verzí operačního systému: 461310 | Rozhraní .NET framework 4.7.1 |
    |Ve Windows 10. dubna 2018 Update pouze: 461808<br/><br/> Na všech ostatních verzí operačního systému: 461814| Rozhraní .NET framework 4.7.2 |
    
<a name="net_c"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a>K vyhledání verze rozhraní .NET Framework dotazem na registr v kódu (.NET Framework 1 – 4)

- Použití <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> pro přístup k podklíči Software\Microsoft\NET Framework setup\ndp\ pod klíčem HKEY_LOCAL_MACHINE v registru Windows.

     Následující kód ukazuje příklad tohoto dotazu.

    > [!NOTE]
    > Tento kód neukazuje, jak detekovat [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější. Zkontrolujte, `Release` DWORD a VYHLEDEJTE tyto verze, jak je popsáno v předchozí části. Pro kód, který zjistí, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo novější verze, najdete v další části v tomto článku.

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
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a>K vyhledání verze rozhraní .NET Framework dotazem na registr v kódu (.NET Framework 4.5 nebo novější)

1. Existence `Release` DWORD označuje, zda v počítači byla nainstalována rozhraní .NET Framework 4.5 nebo novější. Hodnota klíčového slova označuje nainstalovanou verzi. Chcete-li zkontrolovat toto klíčové slovo, použijte <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> a <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metody <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> pro přístup k podklíči Software\Microsoft\NET Framework Setup\NDP\v4\Full podklíče pod klíčem HKEY_LOCAL_MACHINE v registru Windows.

2. Zkontrolujte hodnotu `Release` – klíčové slovo k určení Instalovatelné verze. Aby dopřednou můžete vyhledat hodnotu větší než nebo rovna hodnotě jsou hodnoty uvedené v tabulce. Zde jsou verze rozhraní .NET Framework a přidružených `Release` klíčová slova.

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |Version|Hodnota DWORD verze|
    |-------------|--------------------------------|
    |.NET Framework 4.5|378389|
    |Rozhraní .NET framework 4.5.1 nainstalovaná s Windows 8.1|378675|
    |Rozhraní .NET framework 4.5.1 nainstalované ve Windows 8, Windows 7 SP1 nebo Windows Vista SP2|378758|
    |.NET Framework 4.5.2|379893|
    |Rozhraní .NET framework 4.6 nainstalovaná se systémem Windows 10|393295|
    |Rozhraní .NET framework 4.6 nainstalovaný na všech ostatních verzí operačního systému Windows|393297|
    |Rozhraní .NET framework 4.6.1, které jsou nainstalované ve Windows 10|394254|
    |Rozhraní .NET framework 4.6.1, které jsou nainstalované na všech ostatních verzí operačního systému Windows|394271|
    |Rozhraní .NET framework 4.6.2 nainstalovaný na Windows serveru 2016 a Windows 10 Anniversary Update|394802|
    |Rozhraní .NET framework 4.6.2 nainstalovaný na všech ostatních verzí operačního systému Windows|394806|
    |Rozhraní .NET framework 4.7 nainstalované ve Windows 10 Creators Update|460798|
    |Rozhraní .NET framework 4.7 nainstalovaný na všech ostatních verzí operačního systému Windows|460805|
    |Rozhraní .NET framework 4.7.1 nainstalovat na Windows 10 Fall Creators Update|461308|
    |Rozhraní .NET framework 4.7.1 nainstalovat na všechny ostatní verze operačního systému Windows|461310|
    |Rozhraní .NET framework 4.7.2 nainstalované ve Windows 10. dubna 2018 aktualizovat|461808|
    |Rozhraní .NET framework 4.7.2 nainstalovaný na všech ostatních verzí operačního systému Windows|461814|
    
     Následující příklad kontroly `Release` hodnoty v registru k určení, zda [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo je nainstalovaná novější verze rozhraní .NET Framework.

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     V tomto příkladu následuje doporučený postup pro kontrolu verzí:

    - Zkontroluje, zda hodnota `Release` položka je *větší než nebo rovna hodnotě* hodnotu klíče známé verze.

    - Zkontroluje, aby nejstarší verzi z nejnovější verze.

<a name="ps_a"></a> 
## <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a>Chcete-li zkontrolovat minimální požadovaná verze rozhraní .NET Framework dotazem na registr v prostředí PowerShell (.NET Framework 4.5 nebo novější)

- Následující příklad zkontroluje hodnotu vlastnosti `Release` – klíčové slovo k určení, zda rozhraní .NET Framework 4.6.2 nebo novější je nainstalovaný, bez ohledu na verzi operačního systému Windows (vrácení `True` Pokud se jedná a `False` jinak).

    ```PowerShell
    Get-ChildItem "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | ForEach-Object { $_ -ge 394802 } 
    ```

    Můžete nahradit `394802` v předchozím příkladu s jinou hodnotou z následující tabulky pro kontrolu pro jinou verzi rozhraní .NET Framework minimální požadovaná.
  
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
    |Rozhraní .NET framework 4.7.2|461808|

<a name="clr_a"></a> 
## <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a>Vyhledání aktuální verze modulu runtime s použitím nástroje Clrver

- Chcete-li zjistit, jaké verze Common Language Runtime jsou nainstalovány v počítači, použijte nástroj CLR Version Tool (Clrver.exe).

     Z příkazového řádku aplikace Visual Studio, zadejte `clrver`. Tento příkaz vytváří výstup podobný následujícímu:

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     Další informace o použití tohoto nástroje najdete v tématu [Clrver.exe (nástroj verze CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).

<a name="clr_b"></a> 
## <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a>Vyhledání aktuální verze modulu runtime pomocí dotazu na třídu prostředí v kódu

- Dotaz <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost pro načtení <xref:System.Version> objekt, který určuje verzi modulu runtime, který aktuálně spouští kód. Můžete použít <xref:System.Version.Major%2A?displayProperty=nameWithType> vlastnost k získání hlavního identifikátoru verze (například "4" pro verzi 4.0), <xref:System.Version.Minor%2A?displayProperty=nameWithType> vlastnost k získání identifikátoru verze (například "0" pro verzi 4.0), nebo <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodu k získání celého verze řetězec (například "4.0.30319.18010", jak je znázorněno v následujícím kódu). Tato vlastnost vrátí jednu hodnotu, která odpovídá verzi modulu runtime, který momentálně spouští kód; nevrací se verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.

     Pro rozhraní .NET Framework verze 4, 4.5, 4.5.1 a 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> vrátí vlastnost <xref:System.Version> objekt, jehož řetězcové vyjádření má tvar `4.0.30319.xxxxx`. Pro rozhraní .NET Framework 4.6 nebo novější, má tvar `4.0.30319.42000`.

    > [!IMPORTANT]
    > Pro [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a později, nedoporučujeme používat <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost zjistit verzi modulu runtime. Namísto toho doporučujeme dotazování registru, jak je popsáno v [k vyhledání verze rozhraní .NET Framework dotazem na registr v kódu (.NET Framework 4.5 nebo novější)](#net_d) dříve v tomto článku.

     Tady je příklad dotazování <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost pro informace o verzi modulu runtime:

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     Vzorové postupy budou mít výstup podobný následujícímu:

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a>Viz také:

[Postupy: Zjištění nainstalovaných aktualizací rozhraní .NET Framework](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
[Instalace rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md)  
[Verze a závislosti](~/docs/framework/migration-guide/versions-and-dependencies.md)  
