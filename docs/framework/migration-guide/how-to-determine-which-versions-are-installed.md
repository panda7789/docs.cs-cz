---
title: Určit, které verze .NET Framework jsou nainstalovány
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: b860aac01780acb67c53e822eff478b78198996b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738186"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Postupy: určení, které verze .NET Framework jsou nainstalovány

Uživatelé mohou na svých počítačích [instalovat](../install/index.md) a spouštět více verzí .NET Framework. Když vyvíjíte nebo nasazujete aplikaci, možná budete potřebovat informace o tom, které verze .NET Framework jsou nainstalovány v počítači uživatele.

.NET Framework se skládá ze dvou hlavních součástí, které jsou ve verzi samostatně:

- Sada sestavení, což jsou kolekce typů a prostředků, které poskytují funkce pro vaše aplikace. .NET Framework a sestavení sdílejí stejné číslo verze.

- Modul CLR (Common Language Runtime), který spravuje a spouští kód vaší aplikace. Modul CLR je identifikován vlastním číslem verze (viz [verze a závislosti](versions-and-dependencies.md)).

> [!NOTE]
> Každá nová verze rozhraní .NET Framework zachovává funkce předchozích verzí a přidává nové funkce. V jednom počítači můžete načíst několik verzí .NET Framework současně, což znamená, že můžete nainstalovat .NET Framework bez nutnosti odinstalování předchozích verzí. Obecně platí, že byste neměli odinstalovat předchozí verze .NET Framework, protože na konkrétní verzi může záviset aplikace, kterou používáte, a v případě, že je tato verze odebrána, může dojít k přerušení.
>
> Existuje rozdíl mezi verzí .NET Framework a verzí CLR:
>
> - Verze .NET Framework je založena na sadě sestavení, které tvoří knihovnu tříd .NET Framework. Například verze .NET Framework zahrnují 4,5, 4.6.1 a 4.7.2.
> - Verze CLR je založená na modulu runtime, ve kterém se .NET Framework aplikace spouštějí. Jedna verze modulu CLR obvykle podporuje více .NET Framework verzí. Například CLR verze 4.0.30319. *xxxxx* podporuje .NET Framework verze 4 až 4.5.2, kde *xxxxx* je méně než 42000 a CLR verze 4.0.30319.42000 podporuje .NET Framework verze počínaje .NET Framework 4,6.
>
> Další informace o verzích najdete v tématu [.NET Framework verze a závislosti](versions-and-dependencies.md).

Registr obsahuje seznam verzí .NET Framework nainstalovaných v počítači. Můžete použít Editor registru k zobrazení registru nebo k jeho dotazování s kódem:

- Najít novější verze .NET Framework (4,5 a novější):

  - [Vyhledání verzí .NET Framework pomocí Editoru registru](#net_b)
  - [Použití kódu k dotazování registru pro .NET Framework verze](#net_d)
  - [Použití PowerShellu k dotazování registru pro .NET Framework verze](#ps_a)

- Najít starší verze .NET Framework (1 až 4):

  - [Vyhledání verzí .NET Framework pomocí Editoru registru](#net_a)
  - [Použití kódu k dotazování registru pro .NET Framework verze](#net_c)

Chcete-li získat seznam verzí modulu CLR nainstalovaných v počítači, použijte nástroj nebo kód:

- [Použití nástroje Clrver](#clr_a)
- [Použití kódu pro dotazování třídy prostředí](#clr_b)

Informace o zjišťování nainstalovaných aktualizací pro každou verzi .NET Framework najdete v tématu [How to: Určete, které .NET Framework aktualizace se mají nainstalovat](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="find-newer-net-framework-versions-45-and-later"></a>Najít novější verze .NET Framework (4,5 a novější)

Editor registru můžete použít k vyhledání informací o verzi v registru nebo k zaregistrování registru prostřednictvím kódu programu.

<a name="net_b"></a>

### <a name="use-registry-editor"></a>Použití Editoru registru

1. V nabídce **Start** klikněte na příkaz **Spustit**, zadejte *příkaz regedit*a pak vyberte **OK**.

     Chcete-li spustit nástroj Regedit, musíte mít pověření správce.

2. V editoru registru otevřete následující podklíč: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**. Pokud není přítomen **úplný** podklíč, nemáte nainstalovanou .NET Framework 4,5 nebo novější.

    > [!NOTE]
    > Složka pro **instalaci rozhraní .NET Framework** v registru *nezačíná tečkou* .

3. Vyhledejte položku DWORD s názvem **release**. Pokud existuje, budete mít nainstalované .NET Framework 4,5 nebo novější. Jeho hodnota je klíč verze, který odpovídá konkrétní verzi .NET Framework. Na následujícím obrázku je například hodnota položky **release** 378389, což je klíč verze .NET Framework 4,5.

   ![Položka registru pro .NET Framework 4,5](./media/clr-installdir.png "Položka registru pro .NET Framework 4,5")

V následující tabulce je uvedena hodnota DWORD **verze** v jednotlivých operačních systémech .NET Framework 4,5 a novějších verzích.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|Verze rozhraní .NET Framework|Hodnota DWORD verze|
|--------------------------------|-------------|
|.NET Framework 4.5|Všechny operační systémy Windows: 378389|
|.NET Framework 4.5.1|V Windows 8.1 a Windows Server 2012 R2:378675<br />Ve všech ostatních operačních systémech Windows: 378758|
|.NET Framework 4.5.2|Všechny operační systémy Windows: 379893|
|.NET Framework 4.6|Ve Windows 10:393295<br />Ve všech ostatních operačních systémech Windows: 393297|
|.NET Framework 4.6.1|V systémech Windows 10 listopad Update: 394254<br />Ve všech ostatních operačních systémech Windows (včetně Windows 10): 394271|
|.NET Framework 4.6.2|Ve Windows 10 – aktualizace pro výročí a Windows Server 2016:394802<br />Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 394806|
|.NET Framework 4,7|Ve Windows 10 Creators Update: 460798<br />Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 460805|
|.NET Framework 4.7.1|V systému Windows 10 patří mezi tvůrci aktualizace a Windows Server verze 1709:461308<br/>Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 461310|
|.NET Framework 4.7.2|Ve Windows 10. dubna 2018 Update a Windows Server verze 1803:461808<br/>Ve všech operačních systémech Windows s výjimkou Windows 10 dubna 2018 Update a Windows Server verze 1803:461814|
|.NET Framework 4,8|Ve Windows 10 května 2019 Update a Windows 10 listopadu 2019 Update: 528040<br/>Ve všech ostatních operačních systémech Windows (včetně dalších operačních systémů Windows 10): 528049|

#### <a name="specific-version"></a>Specific version (Konkrétní verze)

Chcete-li zjistit, zda je v konkrétní verzi operačního systému Windows nainstalována *konkrétní* verze .NET Framework, proveďte test, zda je hodnota DWORD **verze** *shodná s* hodnotou uvedenou v tabulce. Chcete-li například zjistit, zda je v systému Windows 10 .NET Framework 4,6, proveďte test na hodnotu **verze** , která se *rovná* 393295.

#### <a name="minimum-version"></a>Minimální verze

Chcete-li určit, zda je k dispozici *minimální* verze .NET Framework, použijte **hodnotu DWORD nejnižší verze pro** tuto verzi z předchozí tabulky. (Pro usnadnění práce jsou uvedeny také minimální hodnoty v tabulce, která následuje.)

Například pokud vaše aplikace běží pod .NET Framework 4,8 nebo novější verzí, otestujte hodnotu DWORD **verze** , která je *větší nebo rovna* 528040.

|Verze rozhraní .NET Framework|Minimální hodnota pro DWORD verze|
|--------------------------------|-------------|
|.NET Framework 4.5|378389|
|.NET Framework 4.5.1|378675|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.6|393295|
|.NET Framework 4.6.1|394254|
|.NET Framework 4.6.2|394802|
|.NET Framework 4,7|460798|
|.NET Framework 4.7.1|461308|
|.NET Framework 4.7.2|461808|
|.NET Framework 4,8|528040|

#### <a name="multiple-versions"></a>Více verzí

Chcete-li otestovat více verzí, začněte testováním na hodnotu, která je *větší nebo rovna* menší hodnotě DWORD pro nejnovější verzi .NET Framework, a pak porovnejte hodnotu s menší hodnotou DWORD pro každou následnou dřívější verzi. Například pokud vaše aplikace vyžaduje .NET Framework 4,7 nebo novější a chcete určit konkrétní verzi .NET Framework přítomná, začněte testováním hodnoty DWORD **verze** , která je *větší nebo rovna* 461808 (menší hodnota DWORD hodnota pro .NET Framework 4.7.2). Pak porovnejte hodnotu DWORD **verze** s menší hodnotou pro každou pozdější .NET Framework verzi.

<a name="net_d"></a>

### <a name="query-the-registry-using-code"></a>Dotazování registru pomocí kódu

1. Použijte metody <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> a <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> pro přístup k podklíči **Setup\NDP\v4\Full rozhraní HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework** v registru systému Windows.

   Existence položky DWORD **verze** v podklíči **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** označuje, že v počítači je nainstalována .NET Framework 4,5 nebo novější verze.

2. Zkontrolujte hodnotu položky **release** a určete nainstalovanou verzi. Chcete-li být kompatibilní s přesměrováním, vyhledejte hodnotu větší nebo rovnou hodnotě uvedené v [tabulce verze .NET Framework](#version_table).

Následující příklad zkontroluje hodnotu položky **release** v registru, aby bylo možné najít .NET Framework 4,5 a novější verze, které jsou nainstalovány:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Tento příklad se skládá z doporučené praxe pro kontrolu verzí:

- Kontroluje, zda je hodnota položky **verze** *větší než nebo rovna* hodnotě známých klíčů pro vydání.

- Kontroluje v pořadí od nejnovější verze k nejstarší verzi.

<a name="ps_a"></a>

### <a name="use-powershell-to-check-for-a-minimum-required-version"></a>Použití PowerShellu k vyhledání minimální požadované verze

Pomocí příkazů PowerShellu zkontrolujete hodnotu položky **release** podklíče **Setup\NDP\v4\Full HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework** .

Následující příklady kontrolují hodnotu položky **verze** , abyste zjistili, jestli je nainstalovaná .NET Framework 4.6.2 nebo novější. Tento kód vrátí `True`, pokud je nainstalován, a `False` jinak.

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

Chcete-li vyhledat jinou minimální požadovanou verzi .NET Framework, nahraďte `394802` v příkladu hodnotou z [tabulky verze .NET Framework](#version_table). Použijte nejnižší hodnotu zobrazenou pro tuto verzi.

## <a name="find-older-net-framework-versions-1-through-4"></a>Najít starší verze .NET Framework (1 až 4)

<a name="net_a"></a>

### <a name="use-registry-editor-older-framework-versions"></a>Použití Editoru registru (starší verze rozhraní)

1. V nabídce **Start** klikněte na příkaz **Spustit**, zadejte *příkaz regedit*a pak vyberte **OK**.

    Chcete-li spustit nástroj Regedit, musíte mít pověření správce.

2. V editoru registru otevřete následující podklíč: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:

    - Pro .NET Framework verze 1,1 až 3,5 je každá nainstalovaná verze uvedena jako podklíč v podklíči **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** . Například **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**. Číslo verze je uloženo jako hodnota v položce **verze** podklíče verze.

    - V případě .NET Framework 4 je položka **verze** pod podklíčem **Setup\NDP\v4.0\Client rozhraní HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework** , **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** podklíče nebo pod oběma podklíči.

    > [!NOTE]
    > Složka pro **instalaci rozhraní .NET Framework** v registru nezačíná tečkou.

    Následující obrázek ukazuje podklíč a jeho položku **verze** pro .NET Framework 3,5.

    ![Položka registru pro .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 a starší verze")

<a name="net_c"></a>

### <a name="query-the-registry-using-code-older-framework-versions"></a>Dotazování registru pomocí kódu (starší verze rozhraní)

Použijte třídu <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> pro přístup k podklíči **Setup\NDP rozhraní HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework** v registru systému Windows.

Následující příklad vyhledá .NET Framework 1 až 4 verze, které jsou nainstalovány:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>Najít verze CLR

<a name="clr_a"></a>

### <a name="use-clrverexe"></a>Použití Clrver. exe

K určení, které verze modulu CLR jsou nainstalovány v počítači, použijte [Nástroj verze CLR (Clrver. exe)](../tools/clrver-exe-clr-version-tool.md) :

- Z [Developer Command Prompt pro Visual Studio](../tools/developer-command-prompt-for-vs.md)zadejte `clrver`.

    Ukázkový výstup:

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="use-the-environment-class"></a>Použití třídy Environment

> [!IMPORTANT]
> U .NET Framework 4,5 a novějších verzí nepoužívejte vlastnost <xref:System.Environment.Version%2A?displayProperty=nameWithType> k detekci verze modulu CLR. Místo toho proveďte dotaz na registr, jak je popsáno v části [Find .NET Framework verze 4,5 a novější s kódem](#net_d).

1. Pomocí dotazu na vlastnost <xref:System.Environment.Version?displayProperty=nameWithType> načtěte objekt <xref:System.Version>.

    Vrácený objekt `System.Version` identifikuje verzi modulu runtime, který aktuálně spouští kód. Nevrací verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.

    Pro .NET Framework verze 4, 4,5, 4.5.1 a 4.5.2 má řetězcová reprezentace vráceného objektu <xref:System.Version> formu 4.0.30319. *xxxxx*, kde *xxxxx* je menší než 42000. U .NET Framework 4,6 a novějších verzí má formulář 4.0.30319.42000.

2. Až budete mít objekt `Version`, proveďte dotazování následujícím způsobem:

   - Pro hlavní identifikátor vydaných verzí (například *4* pro verzi 4,0) použijte vlastnost <xref:System.Version.Major%2A?displayProperty=nameWithType>.

   - Pro dílčí identifikátor vydání (například *0* pro verzi 4,0) použijte vlastnost <xref:System.Version.Minor%2A?displayProperty=nameWithType>.

   - Pro celý řetězec verze (například *4.0.30319.18010*) použijte metodu <xref:System.Version.ToString%2A?displayProperty=nameWithType>. Tato metoda vrátí jednu hodnotu, která odráží verzi modulu runtime, který spouští kód. Nevrací verze sestavení ani jiné verze modulu runtime, které mohou být nainstalovány v počítači.

Následující příklad používá vlastnost <xref:System.Environment.Version%2A?displayProperty=nameWithType> pro načtení informací o verzi CLR:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Viz také:

- [Postupy: určení nainstalovaných aktualizací .NET Framework](how-to-determine-which-net-framework-updates-are-installed.md)
- [Instalace .NET Framework pro vývojáře](../install/guide-for-developers.md)
- [.NET Framework verze a závislosti](versions-and-dependencies.md)
