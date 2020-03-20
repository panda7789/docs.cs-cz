---
title: Zjištění nainstalovaných verzí rozhraní .NET Framework
description: Pomocí kódu regedit.exe nebo prostředí PowerShell zjistíte, které verze rozhraní .NET Framework jsou v počítači nainstalovány dotazováním na registr systému Windows.
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: 8469f977c6ed9691c81a2a8354935557b5c27171
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77093825"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Postup: Určení nainstalovaných verzí rozhraní .NET Framework

Uživatelé mohou ve svých počítačích [instalovat](../install/index.md) a spouštět více verzí rozhraní .NET Framework. Při vývoji nebo nasazení aplikace možná budete potřebovat vědět, které verze rozhraní .NET Framework jsou nainstalovány v počítači uživatele. Registr obsahuje seznam verzí rozhraní .NET Framework nainstalovaných v počítači.

Rozhraní .NET Framework se skládá ze dvou hlavních součástí, které jsou verzí samostatně:

- Sada sestavení, které jsou kolekce typů a prostředků, které poskytují funkce pro vaše aplikace. Rozhraní .NET Framework a sestavení sdílejí stejné číslo verze. Například verze rozhraní .NET Framework zahrnují 4.5, 4.6.1 a 4.7.2.

- Běžný jazyk runtime (CLR), který spravuje a spouští kód vaší aplikace. Jedna verze CLR obvykle podporuje více verzí rozhraní .NET Framework. Například CLR verze 4.0.30319. *xxxxx* kde *xxxxx* je menší než 42000, podporuje rozhraní .NET Framework verze 4 až 4.5.2. Verze CLR větší nebo rovna 4.0.30319.42000 podporuje verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.6.

K dispozici jsou nástroje spravované komunitou, které pomáhají zjistit, které verze rozhraní .NET Framework jsou nainstalovány:

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  Nástroj příkazového řádku .NET 2.0.

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  Modul Prostředí PowerShell 2.0.

Informace o zjišťování nainstalovaných aktualizací pro každou verzi rozhraní .NET Framework naleznete v tématu [Postup: Určení, které aktualizace rozhraní .NET Framework jsou nainstalovány](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="detect-net-framework-45-and-later-versions"></a>Detekce rozhraní .NET Framework 4.5 a novějších verzí

Verze rozhraní .NET Framework (4.5 a novější) nainstalovaná v počítači je uvedena v registru na **adrese\\HKEY_LOCAL_MACHINE SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**. Pokud chybí **úplný** podklíč, není nainstalována rozhraní .NET Framework 4.5 nebo vyšší.

> [!NOTE]
> Podklíč **nastavení rozhraní NET Framework** v cestě registru *nezačíná* tečkou.

Hodnota **release** REG_DWORD v registru představuje nainstalovanou verzi rozhraní .NET Framework.

<a name="version_table"></a>

| Verze rozhraní .NET Framework | Hodnota **uvolnění** |
| ---------------------- | -------------------------- |
| .NET Framework 4.5     | Všechny operační systémy Windows: 378389 |
| .NET Framework 4.5.1   | Ve Windows 8.1 a Windows Server 2012 R2: 378675<br />Ve všech ostatních operačních systémech Windows: 378758 |
| .NET Framework 4.5.2   | Všechny operační systémy Windows: 379893 |
| .NET Framework 4.6     | Ve Windows 10: 393295<br />Ve všech ostatních operačních systémech Windows: 393297 |
| .NET Framework 4.6.1   | V systému Windows 10 Listopad aktualizace systémy: 394254<br />Ve všech ostatních operačních systémech Windows (včetně Windows 10): 394271 |
| .NET Framework 4.6.2   | Ve Windows 10 Anniversary Update a Windows Server 2016: 394802<br />Ve všech ostatních operačních systémech Windows (včetně ostatních operačních systémů Windows 10): 394806 |
| Rozhraní .NET Framework 4.7     | V aktualizaci Windows 10 Creators: 460798<br />Ve všech ostatních operačních systémech Windows (včetně ostatních operačních systémů Windows 10): 460805 |
| Rozhraní .NET 4.7.1   | V systému Windows 10 Fall Creators Update a Windows Server, verze 1709: 461308<br/>Ve všech ostatních operačních systémech Windows (včetně ostatních operačních systémů Windows 10): 461310 |
|  .NET Framework 4.7.2   | Ve Windows 10 duben 2018 Update a Windows Server verze 1803: 461808<br/>Ve všech operačních systémech Windows jiných než Windows 10 Duben 2018 Update a Windows Server verze 1803: 461814 |
|  .NET Framework 4.8     | V systému Windows 10 Květen 2019 Update a Windows 10 listopad 2019 Aktualizace: 528040<br/>Ve Windows 10 a Windows Serveru verze 1909: 528209<br/>Na všech ostatních operačních systémech Windows (včetně ostatních operačních systémů Windows 10): 528049 |

### <a name="minimum-version"></a>Minimální verze

Chcete-li zjistit, zda je k dispozici *minimální* verze rozhraní .NET Framework, použijte nejmenší hodnotu **release** REG_DWORD pro tuto verzi z předchozí tabulky.

Například pokud vaše aplikace běží pod rozhraní mj **REG_DWORD.** *greater than or equal to*

| Verze rozhraní .NET Framework | Minimální hodnota |
| ---------------------- | ------------- |
| .NET Framework 4.5     | 378389 |
| .NET Framework 4.5.1   | 378675 |
| .NET Framework 4.5.2   | 379893 |
| .NET Framework 4.6     | 393295 |
| .NET Framework 4.6.1   | 394254 |
| .NET Framework 4.6.2   | 394802 |
| Rozhraní .NET Framework 4.7     | 460798 |
| Rozhraní .NET 4.7.1   | 461308 |
|  .NET Framework 4.7.2   | 461808 |
|  .NET Framework 4.8     | 528040 |

### <a name="use-registry-editor"></a>Použít Editor registru

01. V nabídce **Start** zvolte **Spustit**, zadejte *regedit*a pak vyberte **OK**.

    Chcete-li spustit regedit, musíte mít pověření pro správu.

01. V Editoru registru otevřete následující podklíč: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\\\NDP v4\\Full**. Pokud není k dispozici **úplný** podklíč, nemáte nainstalovanou rozhraní .NET Framework 4.5 nebo novější.

01. Zkontrolujte položku REG_DWORD s názvem **Uvolnit**. Pokud existuje, máte nainstalovaný rozhraní .NET Framework 4.5 nebo novější. Jeho hodnota odpovídá konkrétní verzi rozhraní .NET Framework. Na následujícím obrázku je například hodnota položky **release** 528040, což je klíč verze pro rozhraní .NET Framework 4.8.

    ![Položka registru pro rozhraní .NET Framework 4.5](./media/clr-installdir.png "Položka registru pro rozhraní .NET Framework 4.5")

### <a name="use-powershell-to-check-for-a-minimum-version"></a>Kontrola minimální verze pomocí PowerShellu

Pomocí příkazů prostředí PowerShell zkontrolujte hodnotu položky **vydání** úplného podklíče **\\HKEY_LOCAL_MACHINE SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4.\\**

Následující příklady zkontrolujte hodnotu položky **release** a zjistěte, zda je nainstalována rozhraní .NET Framework 4.6.2 nebo novější. Tento kód `True` vrátí, pokud `False` je nainstalován a jinak.

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a>Dotaz na registr pomocí kódu

01. Pomocí <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> metod <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> a můžete získat přístup k **úplnému podklíči\\HKEY_LOCAL_MACHINE software\\Microsoft\\NET Framework Setup\\NDP\\v4\\** v registru systému Windows.

    > [!IMPORTANT]
    > Pokud je spuštěná aplikace 32bitová a spuštěná v 64bitovém systému Windows, budou cesty registru jiné, než bylo uvedeno dříve. 64bitový registr je k dispozici v podklíči **\\HKEY_LOCAL_MACHINE SOFTWARE\\Wow6432Node.\\ ** Podklíč registru pro rozhraní .NET Framework 4.5 je například **\\HKEY_LOCAL_MACHINE\\\\SOFTWARE\\Wow6432Node Microsoft NET Framework Setup\\\\NDP v4\\Full**.

01. Zkontrolujte hodnotu **release** REG_DWORD a určete nainstalovanou verzi. Chcete-li být dopředné kompatibilní, zkontrolujte hodnotu větší nebo rovnou hodnotě uvedené v [tabulce verzí rozhraní .NET Framework](#version_table).

Následující příklad zkontroluje hodnotu položky **release** v registru a vyhledá nainstalovanou verzi rozhraní .NET Framework 4.5 a novějších verzí:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Tento příklad se řídí doporučeným postupem pro kontrolu verzí:

- Zkontroluje, zda je hodnota položky **Release** *větší nebo rovna* hodnotě známých klíčů vydání.
- Kontroluje v pořadí od nejnovější verze k nejstarší verzi.

## <a name="detect-net-framework-10-through-40"></a>Rozpoznat rozhraní .NET Framework 1.0 až 4.0

Každá verze rozhraní .NET Framework od 1.1 do 4.0 je uvedena jako podklíč k **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**. V následující tabulce je uvedena cesta ke každé verzi rozhraní .NET Framework. U většiny verzí je k **Install** dispozici hodnota `1` Instalace REG_DWORD, která označuje, že je nainstalována tato verze. V těchto podklíčích je také **hodnota Version** REG_SZ, která obsahuje řetězec verze.

> [!NOTE]
> Podklíč **nastavení rozhraní NET Framework** v cestě registru *nezačíná* tečkou.

| Verze architektury  | Podklíč registru | Hodnota |
| ------------------ | --------------- | ----- |
| 1.0                | **HKLM\\\\Software\\Microsoft . NETFramework\\\\Politika v1.0\\3705**     | **Instalace** REG_SZ rovná se`1` |
| 1.1                | **HKLM\\\\Software\\Microsoft\\NET\\Framework Instalační ndp v1.1.4322**   | **Instalace** REG_DWORD rovná se`1` |
| 2.0                | **HKLM\\\\Software\\Microsoft\\NET\\Framework Instalační ndp v2.0.50727**  | **Instalace** REG_DWORD rovná se`1` |
| 3.0                | **HKLM\\\\Software\\Microsoft\\NET\\Framework Instalační\\ndp v3.0 Instalace** | **InstallSuccess** REG_DWORD rovná se`1` |
| 3,5                | **HKLM\\\\Software\\Microsoft\\NET\\Framework Instalace NDP v3.5**        | **Instalace** REG_DWORD rovná se`1` |
| 4.0 Profil klienta | **HKLM\\\\Software\\Microsoft\\NET\\Framework\\Instalační ndp v4 klienta**  | **Instalace** REG_DWORD rovná se`1` |
| 4.0 Úplný profil   | **HKLM\\\\Software\\Microsoft\\NET\\Framework\\Instalace NDP v4 Úplné**    | **Instalace** REG_DWORD rovná se`1` |

> [!IMPORTANT]
> Pokud je spuštěná aplikace 32bitová a spuštěná v 64bitovém systému Windows, budou cesty registru jiné, než bylo uvedeno dříve. 64bitový registr je k dispozici v podklíči **\\HKEY_LOCAL_MACHINE SOFTWARE\\Wow6432Node.\\ ** Podklíč registru pro rozhraní .NET Framework 3.5 je například **\\HKEY_LOCAL_MACHINE\\\\SOFTWARE\\Wow6432Node Microsoft NET Framework Setup\\\\NDP verze 3.5**.

Všimněte si, že cesta registru k podklíči rozhraní .NET Framework 1.0 se liší od ostatních.

### <a name="use-registry-editor-older-framework-versions"></a>Použití Editoru registru (starší verze architektury)

01. V nabídce **Start** zvolte **Spustit**, zadejte *regedit*a pak vyberte **OK**.

    Chcete-li spustit regedit, musíte mít pověření pro správu.

01. Otevřete podklíč, který odpovídá verzi, kterou chcete zkontrolovat. Použijte tabulku v části [Rozpoznat rozhraní .NET Framework 1.0 až 4.0.](#detect-net-framework-10-through-40)

    Následující obrázek znázorňuje podklíč a jeho hodnotu **Version** pro rozhraní .NET Framework 3.5.

    ![Položka registru pro rozhraní .NET Framework 3.5.](./media/net-4-and-earlier.png "Rozhraní .NET Framework 3.5 a starší verze")

### <a name="query-the-registry-using-code-older-framework-versions"></a>Dotaz registru pomocí kódu (starší verze architektury)

Třídu <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> použijte pro přístup k **podklíči\\NDP HKEY_LOCAL_MACHINE SOFTWARE\\Microsoft\\NET Framework v\\** registru systému Windows.

> [!IMPORTANT]
> Pokud je spuštěná aplikace 32bitová a spuštěná v 64bitovém systému Windows, budou cesty registru jiné, než bylo uvedeno dříve. 64bitový registr je k dispozici v podklíči **\\HKEY_LOCAL_MACHINE SOFTWARE\\Wow6432Node.\\ ** Podklíč registru pro rozhraní .NET Framework 3.5 je například **\\HKEY_LOCAL_MACHINE\\\\SOFTWARE\\Wow6432Node Microsoft NET Framework Setup\\\\NDP verze 3.5**.

Následující příklad vyhledá nainstalované verze rozhraní .NET Framework 1 až 4:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>Najít verze CLR

Rozhraní CLR rozhraní .NET Framework nainstalované s rozhraním .NET Framework je verzí samostatně. Existují dva způsoby, jak zjistit verzi rozhraní CLR rozhraní .NET Framework:

- **Nástroj Clrver.exe**

  Pomocí [nástroje CLR Version (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) určete, které verze clr jsou nainstalovány v počítači. Otevřete [příkazový řádek pro vývojáře pro Visual Studio](../tools/developer-command-prompt-for-vs.md) a zadejte `clrver`.

  Ukázkový výstup:

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- **Třída `Environment`**

  > [!IMPORTANT]
  > Pro rozhraní .NET Framework 4.5 a novější <xref:System.Environment.Version%2A?displayProperty=nameWithType> verze nepoužívejte vlastnost ke zjištění verze CLR. Místo toho dotaz registru, jak je popsáno v [detect .NET Framework 4.5 a novější verze](#detect-net-framework-45-and-later-versions).
  
  01. Dotaz <xref:System.Environment.Version?displayProperty=nameWithType> vlastnost načíst <xref:System.Version> objekt.
  
      Vrácený `System.Version` objekt identifikuje verzi modulu runtime, který aktuálně provádí kód. Nevrací verze sestavení nebo jiné verze runtime, které mohly být nainstalovány v počítači.
  
      Pro rozhraní .NET Framework verze 4, 4.5, 4.5.1 a 4.5.2 má řetězcová reprezentace vráceného <xref:System.Version> objektu formulář 4.0.30319. *xxxxx*, kde *xxxxx* je menší než 42000. Pro rozhraní .NET Framework 4.6 a novější verze má formulář 4.0.30319.42000.
  
  01. Po verzi **objektu,** dotaz ovat následujícím způsobem:
  
      - Pro hlavní identifikátor verze (například *4* pro verzi <xref:System.Version.Major%2A?displayProperty=nameWithType> 4.0) použijte vlastnost.
  
      - Pro identifikátor dílčí verze (například *0* pro verzi <xref:System.Version.Minor%2A?displayProperty=nameWithType> 4.0) použijte vlastnost.
  
      - Pro celý řetězec verze (například *4.0.30319.18010*) použijte metodu. <xref:System.Version.ToString%2A?displayProperty=nameWithType> Tato metoda vrátí jednu hodnotu, která odráží verzi modulu runtime, který je provádění kódu. Nevrací verze sestavení nebo jiné verze runtime, které mohou být nainstalovány v počítači.

  Následující příklad používá <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost k načtení informací o verzi CLR:
  
  [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
  [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Viz také

- [Postup: Určení nainstalovaných aktualizací rozhraní .NET Framework](how-to-determine-which-net-framework-updates-are-installed.md)
- [Instalace rozhraní .NET Framework pro vývojáře](../install/guide-for-developers.md)
- [Verze a závislosti rozhraní .NET Framework](versions-and-dependencies.md)
