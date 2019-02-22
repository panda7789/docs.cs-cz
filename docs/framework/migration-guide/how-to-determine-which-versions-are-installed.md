---
title: 'Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework'
ms.date: 02/20/2019
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
ms.openlocfilehash: d7661b3ebaa8f29d6d3b2adbc56c405c8f0945f3
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584171"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework

Mohou uživatelé nainstalovat a spustit více verzí rozhraní .NET Framework na svých počítačích. Při vývoji nebo nasazení vaší aplikace, můžete potřebovat vědět, jaké verze rozhraní .NET Framework jsou nainstalovány v počítači uživatele. Všimněte si, že rozhraní .NET Framework obsahuje dvě hlavní součásti, které mají samostatné verze:  
  
- Sadu sestavení, která jsou kolekce typů a prostředků, které poskytují funkce pro vaše aplikace. Rozhraní .NET Framework a sestavení sdílejí stejné číslo verze.  
  
- Modul CLR (CLR), jež spravuje a spouští kód vaší aplikace. CLR je identifikováno svým vlastním číslem verze (viz [verze a závislosti](~/docs/framework/migration-guide/versions-and-dependencies.md)).  
  
Pokud chcete získat přesné seznam verzí rozhraní .NET Framework nainstalované na počítači, můžete zobrazit registru nebo dotazovat na registr v kódu:  
  
 [V registru najít rozhraní .NET Framework verze 1 – 4](#net_a)  
 [Najít rozhraní .NET Framework verze 4.5 a vyšší v registru)](#net_b)  
 [Použití kódu k registru (verze 1 – 4)](#net_c)  
 [Použití kódu k registru (verze 4.5 a novější)](#net_d)  
 [Použití Powershellu k registru (verze 4.5 a novější)](#ps_a)  

 Pokud chcete zjistit verzi modulu CLR, můžete použít nástroj nebo kódu:  
  
 [Pomocí nástroje Clrver](#clr_a)  
 [Dotaz na třídu System.Environment pomocí kódu](#clr_b)  

> [!NOTE]
> Existuje rozdíl mezi verzí rozhraní .NET Framework a společné jazykové verzi modulu runtime (CLR). Rozhraní .NET Framework se systémovou správou verzí podle sadu sestavení, které tvoří knihovny tříd rozhraní .NET Framework. Například zahrnují verze rozhraní .NET Framework 4.5, 4.6.1 a 4.7.2. Modul CLR se systémovou správou verzí podle modulu runtime, na které rozhraní .NET Framework aplikace jsou spouštěny a jedna verze modulu CLR obvykle podporuje více verzí rozhraní .NET Framework. Verze 4.30319 modulu CLR. *xxxxx* podporuje rozhraní .NET Framework verze 4 až 4.5.2; Modul CLR verze 4.30319.42000 podporuje verze rozhraní .NET Framework počínaje .NET Framework 4.6. Další informace najdete v tématu <xref:System.Environment.Version?displayProperty=nameWithType> vlastnost.

 Informace o zjišťování nainstalovaných aktualizací pro každou verzi rozhraní .NET Framework najdete v tématu [jak: Zjištění nainstalovaných aktualizací rozhraní .NET Framework](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md). Informace o instalaci rozhraní .NET Framework najdete v tématu [nainstalovat rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md).  
  
<a name="net_a"></a>   
## <a name="find-net-framework-versions-1-4-in-the-registry"></a>V registru najít rozhraní .NET Framework verze 1 – 4 
  
1.  Na **Start** nabídce zvolte **spustit**.  
  
2.  V **otevřít** zadejte **regedit.exe**.  
  
     Ke spuštění souboru regedit.exe musíte mít oprávnění správce.  
  
3.  V editoru registru otevřete následující podklíč:  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     Pro rozhraní .NET Framework verze 1.1 až 3.5, nainstalované verze jsou uvedeny jako podklíče pod `NDP` podklíči. Číslo verze je uloženo v podklíči verze **verze** položka. 
     
     Pro rozhraní .NET Framework 4 **verze** položka je v části `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` podklíči `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` podklíče, nebo pod oběma podklíči.

    > [!NOTE]
    > Složka „NET Framework Setup“ v registru nezačíná tečkou.

    Následující obrázek ukazuje, že podklíč pro rozhraní .NET Framework 3.5 spolu s jeho **verze** položka.

     ![Položky registru pro rozhraní .NET Framework 3.5. ](../../../docs/framework/migration-guide/media/net-4-and-earlier.png "Rozhraní .NET framework 4 a dřívějších verzích")

<a name="net_b"></a> 
## <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>Najít rozhraní .NET Framework verze 4.5 a vyšší v registru

1. Na **Start** nabídce zvolte **spustit**.

2. V **otevřít** zadejte **regedit.exe**.

     Ke spuštění souboru regedit.exe musíte mít oprávnění správce.

3. V editoru registru otevřete následující podklíč:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     Všimněte si, že cesta k `Full` podklíč zahrnuje podklíče `Net Framework` spíše než `.NET Framework`.

    > [!NOTE]
    > Pokud `Full` podklíč není k dispozici a není nutné rozhraní .NET Framework 4.5 nebo novější.

     Vyhledejte hodnotu DWORD s názvem `Release`. Existence `Release` DWORD označuje, že byla v počítači nainstalováno rozhraní .NET Framework 4.5 nebo novější. Jeho hodnota je verze klíče, který odpovídá konkrétní verzi rozhraní .NET Framework. Na následujícím obrázku, například hodnoty `Release` DWORD je 378389, což je verze klíč pro rozhraní .NET Framework 4.5. 

     ![Položky registru pro rozhraní .NET Framework 4.5. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")

V následující tabulce jsou uvedeny minimální hodnota `Release` DWORD pro každou verzi rozhraní .NET Framework. Tyto hodnoty můžete použít takto:

- Pokud chcete zjistit, zda je k dispozici minimální verze rozhraní .NET Framework, otestovat, zda `Release` v registru byla nalezena hodnota DWORD je *větší než nebo rovna hodnotě* hodnota uvedená v tabulce. Například pokud vaše aplikace vyžaduje rozhraní .NET Framework 4.7 nebo novější, byste testovali pro hodnotu klíče minimální verzi 460798.

- Pokud chcete otestovat více verzí, začněte s nejnovější verzí rozhraní .NET Framework a pak test pro každou po sobě jdoucích starší verzi.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|Verze rozhraní .NET framework|Hodnota DWORD verze|
|--------------------------------|-------------|
|.NET Framework 4.5|378389|
|.NET Framework 4.5.1|378675|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.6|393295|
|.NET Framework 4.6.1|394254|
|.NET Framework 4.6.2|394802|
|Rozhraní .NET framework 4.7|460798|
|.NET Framework 4.7.1|461308|
|.NET Framework 4.7.2|461808|

Kompletní tabulku verze klíče pro rozhraní .NET Framework pro konkrétní verze operačního systému Windows, naleznete v tématu [klíče rozhraní .NET Framework verze a verze operačního systému Windows](release-keys-and-os-versions.md).

<a name="net_c"></a> 
## <a name="find-net-framework-versions-1-4-with-code"></a>Najít rozhraní .NET Framework verze 1 – 4 s kódem

- Použití <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> třídy k přístupu `Software\Microsoft\NET Framework Setup\NDP\` podklíče pod `HKEY_LOCAL_MACHINE` větve v registru Windows.

     Následující kód ukazuje příklad tohoto dotazu.

    > [!NOTE]
    > Tento kód neukazuje k zjištění rozhraní .NET Framework 4.5 nebo novější. Zkontrolujte, `Release` DWORD a VYHLEDEJTE tyto verze, jak je popsáno v předchozí části. Kód, který zjistí rozhraní .NET Framework 4.5 nebo novější verze najdete v další části v tomto článku.

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

<a name="net_d"></a> 
## <a name="find-net-framework-versions-45-and-later-with-code"></a>Najít rozhraní .NET Framework verze 4.5 a vyšší s kódem

1. Existence `Release` typu DWORD v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíče označuje, že je na počítači nainstalované rozhraní .NET Framework 4.5 nebo novější. Hodnota klíčového slova označuje nainstalovanou verzi. Chcete-li zkontrolovat toto klíčové slovo, použijte <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> a <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> metody pro přístup k podklíči registru Windows.

2. Zkontrolujte hodnotu `Release` – klíčové slovo k určení Instalovatelné verze. Bude dopřednou, můžete zkontrolovat hodnotu větší než nebo rovna hodnotě uvedené v tabulce [najít rozhraní .NET Framework verze 4.5 a vyšší v registru](#net_b) oddílu.

Následující příklad kontroly `Release` hodnoty v registru k určení, jestli je nainstalované rozhraní .NET Framework 4.5 nebo novější.

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

V tomto příkladu následuje doporučený postup pro kontrolu verzí:

- Zkontroluje, zda hodnota `Release` položka je *větší než nebo rovna hodnotě* hodnotu klíče známé verze.

- Zkontroluje, aby nejstarší verzi z nejnovější verze.

<a name="ps_a"></a> 
## <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>Vyhledejte minimální požadované rozhraní .NET Framework verze (4.5 a novější) pomocí Powershellu

Následující příklad zkontroluje hodnotu vlastnosti `Release` – klíčové slovo k určení, zda rozhraní .NET Framework 4.6.2 nebo novější je nainstalována (vrácení `True` Pokud se jedná a `False` jinak).

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    You can replace `394802` in the previous example with another value from the following table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section to check for a different minimum required .NET Framework version.
  
<a name="clr_a"></a> 
## <a name="find-the-current-clr-version-with-clrverexe"></a>Vyhledání aktuální verze modulu CLR s Clrver.exe

Chcete-li zjistit, jaké verze Common Language Runtime jsou nainstalovány v počítači, použijte nástroj CLR Version Tool (Clrver.exe).

Z příkazový řádek vývojáře pro sadu Visual Studio, zadejte `clrver`. Tento příkaz vytváří výstup podobný následujícímu:

```console
Versions installed on the machine:
v2.0.50727
v4.0.30319
```

Další informace o použití tohoto nástroje najdete v tématu [Clrver.exe (nástroj verze CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).

<a name="clr_b"></a> 
## <a name="find-the-current-clr-version-with-the-environment-class"></a>Vyhledání aktuální verze modulu CLR s třídou prostředí

Můžete načíst hodnotu <xref:System.Environment.Version?displayProperty=nameWithType> vlastnost pro načtení <xref:System.Version> objekt, který určuje verzi modulu runtime, který aktuálně spouští kód. Tato vlastnost vrátí jednu hodnotu, která odpovídá verzi modulu runtime, který aktuálně spouští kód; nevrací se verze sestavení ani jiné verze modulu runtime, který byl nainstalován v počítači. Můžete použít <xref:System.Version.Major%2A?displayProperty=nameWithType> vlastnost k získání hlavního identifikátoru verze (například "4" pro verzi 4.0), <xref:System.Version.Minor%2A?displayProperty=nameWithType> vlastnost k získání identifikátoru verze (například "0" pro verzi 4.0), nebo <xref:System.Version.ToString%2A?displayProperty=nameWithType> metodu k získání celého verze řetězec (například "4.0.30319.18010", jak je znázorněno v následujícím kódu). 

Pro rozhraní .NET Framework verze 4, 4.5, 4.5.1 a 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> vrátí vlastnost <xref:System.Version> objekt, jehož řetězcové vyjádření má tvar `4.0.30319.xxxxx`. Pro rozhraní .NET Framework 4.6 nebo novější, má tvar `4.0.30319.42000`.

> [!IMPORTANT]
> Pro rozhraní .NET Framework 4.5 nebo novější, nedoporučujeme používat <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost zjistit verzi modulu runtime. Namísto toho doporučujeme dotazování registru, jak je popsáno v [k vyhledání verze rozhraní .NET Framework dotazem na registr v kódu (.NET Framework 4.5 nebo novější)](#net_d) dříve v tomto článku.

Následující příklad použitý <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost pro načtení informací o verzi modulu runtime:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Viz také:

- [Postupy: Zjištění nainstalovaných aktualizací rozhraní .NET Framework](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)
- [Instalace rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md)
- [Verze a závislosti](~/docs/framework/migration-guide/versions-and-dependencies.md)
