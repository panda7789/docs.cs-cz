---
title: Zjištění nainstalovaných verzí rozhraní .NET Framework
description: Pomocí kódu, regedit.exe nebo PowerShellu zjistíte, které verze .NET Framework jsou nainstalovány na počítači pomocí dotazování registru systému Windows.
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: 122441e9238fd91199aed255b0125f69081c0a8c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990147"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Postupy: určení, které verze .NET Framework jsou nainstalovány

Uživatelé mohou na svých počítačích [instalovat](../install/index.md) a spouštět více verzí .NET Framework. Když vyvíjíte nebo nasazujete aplikaci, možná budete potřebovat informace o tom, které verze .NET Framework jsou nainstalovány v počítači uživatele. Registr obsahuje seznam verzí .NET Framework nainstalovaných v počítači.

.NET Framework se skládá ze dvou hlavních součástí, které jsou ve verzi samostatně:

- Sada sestavení, což jsou kolekce typů a prostředků, které poskytují funkce pro vaše aplikace. .NET Framework a sestavení sdílejí stejné číslo verze. Například verze .NET Framework zahrnují 4,5, 4.6.1 a 4.7.2.

- Modul CLR (Common Language Runtime), který spravuje a spouští kód vaší aplikace. Jedna verze modulu CLR obvykle podporuje více .NET Framework verzí. Například CLR verze 4.0.30319. *xxxxx* , kde *xxxxx* je nižší než 42000, podporuje .NET Framework verze 4 až 4.5.2. Verze CLR větší než nebo rovna 4.0.30319.42000 podporuje .NET Framework verze počínaje .NET Framework 4,6.

K dispozici jsou nástroje pro údržbu komunity, které vám pomůžou zjistit, které verze .NET Framework jsou nainstalované:

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  Nástroj příkazového řádku .NET 2,0.

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  Modul PowerShell 2,0.

Informace o zjišťování nainstalovaných aktualizací pro každou verzi .NET Framework najdete v tématu [How to: Určete, které .NET Framework aktualizace se mají nainstalovat](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="detect-net-framework-45-and-later-versions"></a>Zjistit .NET Framework 4,5 a novější verze

Verze .NET Framework (4,5 a novější) nainstalovaná na počítači je uvedená v registru v **HKEY_LOCAL_MACHINE \\ software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full**. Pokud chybí **úplný** podklíč, pak .NET Framework 4,5 nebo vyšší není nainstalováno.

> [!NOTE]
> Podklíč **instalace rozhraní .NET Framework** v cestě registru *nezačíná tečkou* .

Hodnota REG_DWORD **verze** v registru představuje verzi .NET Framework, která je nainstalovaná.

<a name="version_table"></a>

| Verze rozhraní .NET Framework | Hodnota **verze** |
| ---------------------- | -------------------------- |
| .NET Framework 4.5     | Všechny operační systémy Windows: 378389 |
| .NET Framework 4.5.1   | V Windows 8.1 a Windows Server 2012 R2:378675<br />Ve všech ostatních operačních systémech Windows: 378758 |
| .NET Framework 4.5.2   | Všechny operační systémy Windows: 379893 |
| .NET Framework 4.6     | Ve Windows 10:393295<br />Ve všech ostatních operačních systémech Windows: 393297 |
| .NET Framework 4.6.1   | V systémech Windows 10 listopad Update: 394254<br />Ve všech ostatních operačních systémech Windows (včetně Windows 10): 394271 |
| .NET Framework 4.6.2   | Ve Windows 10 – aktualizace pro výročí a Windows Server 2016:394802<br />Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 394806 |
|  .NET Framework 4.7     | Ve Windows 10 Creators Update: 460798<br />Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 460805 |
| .NET Framework 4.7.1   | V systému Windows 10 patří mezi tvůrci aktualizace a Windows Server verze 1709:461308<br/>Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 461310 |
|  .NET Framework 4.7.2   | Ve Windows 10. dubna 2018 Update a Windows Server verze 1803:461808<br/>Ve všech operačních systémech Windows s výjimkou Windows 10 dubna 2018 Update a Windows Server verze 1803:461814 |
|  .NET Framework 4.8     | Ve Windows 10 května 2019 Update a Windows 10 listopadu 2019 Update: 528040<br/>Ve Windows 10 Květen 2020 Update: 528372<br/>Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 528049 |

### <a name="minimum-version"></a>Minimální verze

Chcete-li určit, zda je k dispozici *minimální* verze .NET Framework, použijte nejnižší hodnotu **verze REG_DWORD pro** tuto verzi z předchozí tabulky.

Například pokud vaše aplikace běží pod .NET Framework 4,8 nebo novější verzí, otestuje REG_DWORD hodnotu **verze** , která je *větší nebo rovna* 528040.

| Verze rozhraní .NET Framework | Minimální hodnota |
| ---------------------- | ------------- |
| .NET Framework 4.5     | 378389 |
| .NET Framework 4.5.1   | 378675 |
| .NET Framework 4.5.2   | 379893 |
| .NET Framework 4.6     | 393295 |
| .NET Framework 4.6.1   | 394254 |
| .NET Framework 4.6.2   | 394802 |
|  .NET Framework 4.7     | 460798 |
| .NET Framework 4.7.1   | 461308 |
|  .NET Framework 4.7.2   | 461808 |
|  .NET Framework 4.8     | 528040 |

### <a name="use-registry-editor"></a>Použití Editoru registru

01. V nabídce **Start** klikněte na příkaz **Spustit**, zadejte *příkaz regedit*a pak vyberte **OK**.

    Chcete-li spustit nástroj Regedit, musíte mít pověření správce.

01. V editoru registru otevřete následující podklíč: **HKEY_LOCAL_MACHINE \\ software \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v4 \\ Full**. Pokud není přítomen **úplný** podklíč, nemáte nainstalovanou .NET Framework 4,5 nebo novější.

01. Vyhledejte položku REG_DWORD s názvem **release**. Pokud existuje, budete mít nainstalované .NET Framework 4,5 nebo novější. Jeho hodnota odpovídá konkrétní verzi .NET Framework. Na následujícím obrázku je například hodnota položky **release** 528040, což je klíč verze .NET Framework 4,8.

    ![Položka registru pro .NET Framework 4,5](./media/clr-installdir.png "Položka registru pro .NET Framework 4,5")

### <a name="use-powershell-to-check-for-a-minimum-version"></a>Použití PowerShellu k vyhledání minimální verze

Použijte příkazy prostředí PowerShell ke kontrole hodnoty položky **Release** **HKEY_LOCAL_MACHINE \\ softwaru \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v4 \\ Full** podklíč.

Následující příklady kontrolují hodnotu položky **verze** , abyste zjistili, jestli je nainstalovaná .NET Framework 4.6.2 nebo novější. Tento kód `True` se vrátí, pokud je nainstalován, a `False` jinak.

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a>Dotazování registru pomocí kódu

01. Použijte <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> metody a <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> pro přístup k **HKEY_LOCAL_MACHINE \\ softwaru \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v4 \\ Full** podklíč v registru Windows.

    > [!IMPORTANT]
    > Pokud aplikace, kterou používáte, je 32 a běží v 64 bitovém systému Windows, cesty registru se budou lišit od dříve uvedených. 64 registr je k dispozici v podklíči **HKEY_LOCAL_MACHINE \\ software \\ Wow6432Node \\ ** . Například podklíč registru pro .NET Framework 4,5 je **HKEY_LOCAL_MACHINE \\ software \\ Wow6432Node \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v4 \\ Full**.

01. Pokud chcete zjistit nainstalovanou verzi, zkontrolujte hodnotu REG_DWORD **verze** . Chcete-li být kompatibilní s přesměrováním, vyhledejte hodnotu větší nebo rovnou hodnotě uvedené v [tabulce verze .NET Framework](#version_table).

Následující příklad zkontroluje hodnotu položky **release** v registru, aby bylo možné najít .NET Framework 4,5 a novější verze, které jsou nainstalovány:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Tento příklad se skládá z doporučené praxe pro kontrolu verzí:

- Kontroluje, zda je hodnota položky **verze** *větší než nebo rovna* hodnotě známých klíčů pro vydání.
- Kontroluje v pořadí od nejnovější verze k nejstarší verzi.

## <a name="detect-net-framework-10-through-40"></a>Detekovat .NET Framework 1,0 až 4,0

Každá verze .NET Framework od 1,1 do 4,0 je uvedena jako podklíč v **HKEY_LOCAL_MACHINE \\ softwaru \\ Microsoft \\ .NET Framework Setup \\ NDP**. Následující tabulka uvádí cestu ke každé verzi .NET Framework. Pro většinu verzí je k dispozici REG_DWORD hodnota pro **instalaci** , `1` která označuje, že je tato verze nainstalovaná. V těchto podklíčích je také REG_SZ hodnota **verze** , která obsahuje řetězec verze.

> [!NOTE]
> Podklíč **instalace rozhraní .NET Framework** v cestě registru *nezačíná tečkou* .

| Verze frameworku  | Podklíč registru | Hodnota |
| ------------------ | --------------- | ----- |
| 1.0                | **HKLM \\ software \\ Microsoft \\ . \\Zásady NETFramework \\ v 1.0 \\ 3705**     | **Nainstalovat** REG_SZ se rovná`1` |
| 1.1                | **HKLM \\ software \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v 1.1.4322**   | **Nainstalovat** REG_DWORD se rovná`1` |
| 2.0                | **HKLM \\ software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 2.0.50727**  | **Nainstalovat** REG_DWORD se rovná`1` |
| 3.0                | **HKLM \\ software \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v 3.0 – \\ instalace** | **InstallSuccess** REG_DWORD se rovná`1` |
| 3,5                | **HKLM \\ software \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v 3.5**        | **Nainstalovat** REG_DWORD se rovná`1` |
| Profil klienta 4,0 | **HKLM \\ software \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v4 \\ Client**  | **Nainstalovat** REG_DWORD se rovná`1` |
| úplný profil 4,0   | **HKLM \\ software \\ Microsoft \\ .NET Framework Setup \\ NDP \\ v4 \\ Full**    | **Nainstalovat** REG_DWORD se rovná`1` |

> [!IMPORTANT]
> Pokud aplikace, kterou používáte, je 32 a běží v 64 bitovém systému Windows, cesty registru se budou lišit od dříve uvedených. 64 registr je k dispozici v podklíči **HKEY_LOCAL_MACHINE \\ software \\ Wow6432Node \\ ** . Například podklíč registru pro .NET Framework 3,5 je **HKEY_LOCAL_MACHINE \\ software \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**.

Všimněte si, že cesta k registru pro podklíč .NET Framework 1,0 se liší od ostatních.

### <a name="use-registry-editor-older-framework-versions"></a>Použití Editoru registru (starší verze rozhraní)

01. V nabídce **Start** klikněte na příkaz **Spustit**, zadejte *příkaz regedit*a pak vyberte **OK**.

    Chcete-li spustit nástroj Regedit, musíte mít pověření správce.

01. Otevřete podklíč, který odpovídá verzi, kterou chcete ověřit. Použijte tabulku v části [Detect .NET Framework 1,0 až 4,0](#detect-net-framework-10-through-40) .

    Následující obrázek ukazuje podklíč a hodnotu jeho **verze** .NET Framework 3,5.

    ![Položka registru pro .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 a starší verze")

### <a name="query-the-registry-using-code-older-framework-versions"></a>Dotazování registru pomocí kódu (starší verze rozhraní)

Použijte <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> třídu pro přístup k podklíči **HKEY_LOCAL_MACHINE \\ softwaru \\ Microsoft \\ .NET Framework Setup \\ NDP** v registru systému Windows.

> [!IMPORTANT]
> Pokud aplikace, kterou používáte, je 32 a běží v 64 bitovém systému Windows, cesty registru se budou lišit od dříve uvedených. 64 registr je k dispozici v podklíči **HKEY_LOCAL_MACHINE \\ software \\ Wow6432Node \\ ** . Například podklíč registru pro .NET Framework 3,5 je **HKEY_LOCAL_MACHINE \\ software \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**.

Následující příklad vyhledá .NET Framework 1 až 4 verze, které jsou nainstalovány:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>Najít verze CLR

Modul CLR .NET Framework nainstalovaný s .NET Framework má samostatnou verzi. Existují dva způsoby, jak zjistit verzi .NET Framework CLR:

- **Nástroj Clrver.exe**

  K určení, které verze modulu CLR jsou nainstalovány v počítači, použijte [Nástroj verze CLR (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) . Otevřete [Developer Command Prompt pro Visual Studio](../tools/developer-command-prompt-for-vs.md) a zadejte `clrver` .

  Ukázkový výstup:

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- **`Environment`Třída**

  > [!IMPORTANT]
  > U .NET Framework 4,5 a novějších verzí Nepoužívejte <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost k detekci verze modulu CLR. Místo toho proveďte dotaz na registr, jak je popsáno v tématu [detekce .NET Framework 4,5 a novějších verzí](#detect-net-framework-45-and-later-versions).
  
  01. Dotaz na <xref:System.Environment.Version?displayProperty=nameWithType> vlastnost pro načtení <xref:System.Version> objektu.
  
      Vrácený `System.Version` objekt identifikuje verzi modulu runtime, který aktuálně spouští kód. Nevrací verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.
  
      Pro .NET Framework verze 4, 4,5, 4.5.1 a 4.5.2 má řetězcová reprezentace vráceného <xref:System.Version> objektu formu 4.0.30319.* xxxxx*, kde *xxxxx* je menší než 42000. U .NET Framework 4,6 a novějších verzí má formulář 4.0.30319.42000.
  
  01. Jakmile budete mít objekt **verze** , proveďte dotazování následujícím způsobem:
  
      - Pro hlavní identifikátor vydaných verzí (například *4* pro verzi 4,0) použijte <xref:System.Version.Major%2A?displayProperty=nameWithType> vlastnost.
  
      - V případě identifikátoru podverze (například *0* pro verzi 4,0) použijte <xref:System.Version.Minor%2A?displayProperty=nameWithType> vlastnost.
  
      - Pro celý řetězec verze (například *4.0.30319.18010*) použijte <xref:System.Version.ToString%2A?displayProperty=nameWithType> metodu. Tato metoda vrátí jednu hodnotu, která odráží verzi modulu runtime, který spouští kód. Nevrací verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.

  Následující příklad používá <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost k načtení informací o verzi CLR:
  
  [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
  [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Viz také

- [Postupy: určení nainstalovaných aktualizací .NET Framework](how-to-determine-which-net-framework-updates-are-installed.md)
- [Instalace .NET Framework pro vývojáře](../install/guide-for-developers.md)
- [.NET Framework verze a závislosti](versions-and-dependencies.md)
