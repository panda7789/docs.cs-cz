---
title: Řešení potíží s blokované rozhraní .NET Framework instalacemi a odinstalacemi
ms.date: 04/10/2018
ms.custom: updateeachrelease
helpviewer_keywords:
- .NET Framework, troubleshooting blocked installations
- blocked .NET Framework installations, troubleshooting
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cb33ffbbd735a015b58fe4fd6b9f7f70282cba1
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625311"
---
# <a name="troubleshoot-blocked-net-framework-installations-and-uninstallations"></a>Řešení potíží s blokované rozhraní .NET Framework instalacemi a odinstalacemi

Při spuštění [web nebo offline instalační program](../../../docs/framework/install/guide-for-developers.md) pro rozhraní .NET Framework 4.5 nebo novější verze, může dojít k problému, který brání nebo blokuje instalaci rozhraní .NET Framework. Následující tabulka uvádí možné blokující problémy a obsahuje odkazy na informace o odstraňování potíží.

V systému Windows 8 a novější verze rozhraní .NET Framework je součástí operačního systému a nedá se odinstalovat nezávisle na sobě. Aktualizace rozhraní .NET Framework jsou zobrazeny v **nainstalované aktualizace** kartu ovládacího panelu **programy a funkce** aplikace. Pro operační systémy, ve kterých není předinstalované rozhraní .NET Framework, rozhraní .NET Framework se zobrazí v **odinstalovat nebo změnit program** kartu (nebo **přidat nebo odebrat programy** kartu) z  **Programy a funkce** aplikace v Ovládacích panelech. Informace o verzích Windows, na kterých je předinstalován rozhraní .NET Framework najdete v tématu [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).

> [!IMPORTANT]
> Protože verze rozhraní .NET Framework 4.x jsou aktualizace na místě, nelze nainstalovat dřívější verzi rozhraní .NET Framework 4.x v systému, který již je nainstalovaná novější verze. Například v systému Windows 10 Fall Creators Update, nelze nainstalovat rozhraní .NET Framework 4.6.2, protože rozhraní .NET Framework 4.7.1 je předinstalován v operačním systému.

Můžete určit, jaké verze rozhraní .NET Framework jsou nainstalovány v systému. Zobrazit [jak: Determine Which .NET Framework verze Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) Další informace.

V této tabulce 4.5. *x* odkazuje na rozhraní .NET Framework 4.5 a jeho novější vydání, 4.5.1, 4.5.2, 4.6. *x* odkazuje na rozhraní .NET Framework 4.6 a jeho novější vydání, 4.6.1 a 4.6.2 a 4.7. *x* odkazuje na rozhraní .NET Framework 4.7 a jeho novější vydání, 4.7.1 a 4.7.2.

|Zpráva blokování|Další informace nebo řešení problému|  
|----------------------|--------------------------------------------------|  
|Odinstalování rozhraní Microsoft .NET Framework může způsobit, že některé aplikace přestanou fungovat.|Obecně platí, že byste neměli odinstalovávat verze rozhraní .NET Framework nainstalované na vašem počítači, protože na konkrétní verzi rozhraní .NET Framework může záviset aplikace, kterou používáte. Další informace najdete v tématu [rozhraní .NET Framework pro uživatele](../../../docs/framework/get-started/index.md#ForUsers) v *Začínáme* průvodce.|  
|Rozhraní .NET framework 4.5 *.x*/4.6 *.x*/4.7 *.x* (CSY) nebo na tomto počítači je již nainstalovaná novější verze.|Žádná akce není nutná.<br /><br /> Pokud chcete zjistit, jaké verze rozhraní .NET Framework jsou nainstalovány v systému, naleznete v tématu [jak: Determine Which .NET Framework verze Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).|  
|Rozhraní .NET Framework 4.5 *.x*/4.6 *.x*/4.7 *.x* (*jazyk*) vyžaduje rozhraní .NET Framework 4.5 *.x*/4.6 *.x*/4.7 *.x*. Nainstalujte prosím .NET Framework 4.5 *.x*/4.6 *.x*/4.7 *.x* z webu Download Center a spusťte instalaci znovu.|Je nutné nainstalovat anglickou verzi zadaná verze rozhraní .NET Framework před instalací jazykové sady. Další informace najdete v části na [instalace jazykových sad](../../../docs/framework/install/guide-for-developers.md#to-install-language-packs) v instalační příručce.|  
|Nelze nainstalovat rozhraní .NET Framework 4.5 *.x*/4.6 *.x*/4.7 *.x*. V počítači jsou aplikace, které s tímto programem nejsou kompatibilní.<br /><br /> -nebo-<br /><br /> V počítači jsou aplikace, které s tímto programem nejsou kompatibilní.|Nejpravděpodobnější příčinou této zprávy je, že byla nainstalována verze Preview nebo RC rozhraní .NET Framework. Odinstalujte verzi preview nebo RC a znovu spusťte instalační program.|  
|Rozhraní .NET framework 4.5 *.x*/4.6 *.x*/4.7 *.x* pomocí tohoto balíčku nedá odinstalovat. Chcete-li odinstalovat rozhraní .NET Framework 4.5 *.x*/4.6 *.x*/4.7 *.x* z vašeho počítače, přejděte na **ovládací panely**, zvolte  **Programy a funkce**, zvolte **zobrazit nainstalované aktualizace**, vyberte položku aktualizace pro Microsoft Windows (KB2828152) a klikněte na tlačítko **odinstalovat**.|Balíček, který instalujete neodinstaluje verzi preview nebo RC rozhraní .NET Framework.<br /><br /> Odinstalujte verzi preview nebo RC verze v Ovládacích panelech.|  
|Nelze odinstalovat rozhraní .NET Framework 4.5 *.x*/4.6 *.x*/4.7 *.x*. Na tomto programu závisí další aplikace v počítači.|Obecně byste neměli odinstalovávat verze rozhraní .NET Framework z vašeho počítače, protože na konkrétní verzi rozhraní .NET Framework může záviset aplikace, které používáte. Další informace najdete v tématu [rozhraní .NET Framework pro uživatele](../../../docs/framework/get-started/index.md#ForUsers) v *Začínáme* průvodce.|  
|Rozhraní .NET Framework 4.5 *.x*/4.6 *.x*/4.7 *.x* redistributable není vhodné pro tento operační systém. Stáhněte si prosím .NET Framework 4.5 *.x*/4.6 *.x*/4.7 *.x* pro váš operační systém z webu Microsoft Download Center.|Může se pokoušíte nainstalovat [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, nebo 4.7.2 na platformě, která není podporována nebo jste vybrali instalační balíček, který neobsahuje komponenty pro všechny podporované operační systémy. Spusťte instalaci znovu pomocí offline instalační program ([pro 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=309493), [pro 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397706), [pro 4.6](https://go.microsoft.com/fwlink/p/?LinkId=528233), [pro 4.6.1](https://go.microsoft.com/fwlink/p/?LinkId=671744), pro [ 4.6.2](https://go.microsoft.com/fwlink/p/?LinkId=780604), pro [4.7](https://go.microsoft.com/fwlink/p/?LinkId=825306)), pro [4.7.1](https://go.microsoft.com/fwlink/p/?LinkId=852090), nebo pro [4.7.2](https://go.microsoft.com/fwlink/p/?LinkId=863265). Další informace najdete v tématu [Průvodce instalací](../../../docs/framework/install/guide-for-developers.md) a [požadavky na systém](../../../docs/framework/get-started/system-requirements.md) pro podporované operační systémy.|  
|Aktualizace znalostní BÁZE odpovídající\<*číslo*> musí být nainstalovaný před instalací tohoto produktu.|Instalace rozhraní .NET Framework vyžaduje instalaci aktualizace KB před instalací rozhraní .NET Framework. Nainstalujte aktualizaci a znovu spusťte znovu instalaci rozhraní .NET Framework.<br /><br /> Například instalaci aktualizované verze rozhraní .NET Framework na Windows 8.1, Windows RT 8.1 a Windows Server 2012 R2 vyžaduje, aby aktualizace odpovídající [KB 2919355](https://support.microsoft.com/kb/2919355) nainstalovat.|  
|Ve vašem počítači je nainstalováno serverové jádro operačního systému Windows Server 2008. Rozhraní .NET Framework 4.5. *x* vyžaduje novější verzi operačního systému. Nainstalujte Windows Server 2008 R2 SP1 nebo novější a znovu spusťte rozhraní .NET Framework 4.5. *x* instalační program.|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] a 4.5.2 jsou podporovány v roli jádra serveru s Windows Server 2008 R2 SP1 nebo novější. Zobrazit [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).|  
|Nemáte dostatečná oprávnění, abyste tuto operaci mohli dokončit pro všechny uživatele počítače. Přihlaste se jako správce a spusťte znovu **nastavení**.|Pokud chcete instalovat rozhraní .NET Framework, musíte být správcem počítače.|  
|Instalační program nemůže pokračovat, protože předchozí instalace vyžaduje, aby byl počítač restartován. Restartujte počítač a spusťte instalační program znovu.|Je někdy plně dokončení instalace vyžadovat restartování. Postupujte podle pokynů a restartujte počítač a spusťte instalaci znovu.<br /><br /> Ve výjimečných případech může být vyzváni k restartování systému více než jednou, pokud Windows zjistil počet chybějících aktualizací a restartování nainstalovat další aktualizace ve frontě.|  
|Rozhraní .NET Framework nelze spouštět v režimu kompatibility programů.|Zobrazit [problémy s kompatibilitou programu](#compat) části dále v tomto článku.|  
|Rozhraní .NET framework 4.5 *.x*/4.6 *.x*/4.7 *.x* nebyl nainstalován z těchto důvodů je poškozeno úložiště součástí.|Zobrazit [chyby opravit aktualizací Windows pomocí nástroje DISM nebo připravenosti aktualizace systému](https://support.microsoft.com/en-us/kb/947821) Další informace.|  
|Instalační program nelze spustit, protože v počítači není k dispozici Instalační služba systému Windows.|Zobrazit [chyba Instalační služby Windows Installer při instalaci nebo aktualizaci programů](https://go.microsoft.com/fwlink/p/?LinkId=248684) na webu Microsoft Support.|  
|Je možné, že instalační program nebude správně fungovat, protože v počítači není k dispozici Instalační služba systému Windows.|Počítač může být nakonfigurován tak, aby používal služby Windows Server Update Services (WSUS) namísto Microsoft Windows Update. Další informace naleznete v části kód chyby 0x800F0906 v [kódy chyb při pokusu o instalaci rozhraní .NET Framework 3.5 v systému Windows 8 nebo Windows Server 2012](https://support.microsoft.com/kb/2734782).<br /><br /> Viz také [jak získat nejnovější verzi služby Agent webu Windows Update pro usnadnění správy aktualizací v počítači](https://go.microsoft.com/fwlink/p/?LinkId=248437) na webu Microsoft Support.|  
|Je možné, že instalační program nebude správně fungovat, protože v počítači není k dispozici Služba inteligentního přenosu na pozadí (BITS).|Zobrazit [aktualizace bránící zhroucení služby inteligentního přenosu na pozadí (BITS) na počítači se systémem Windows Vista](https://go.microsoft.com/fwlink/p/?LinkId=248680) na webu Microsoft Support.|  
|Instalační program nebude správně fungovat, protože Windows update došlo k chybě a zobrazí kód chyby: 0x80070643 nebo 0x643.|Zobrazit [chyby instalace aktualizace rozhraní .NET Framework: "0x80070643" nebo "0x643"](https://support.microsoft.com/kb/976982) na webu Microsoft Support.|  
|Rozhraní .NET Framework 4.5. *.x*/4.6 *.x*/4.7 *.x* je již součástí tohoto operačního systému. Není potřeba instalovat rozhraní .NET Framework 4.5 *.x*/4.6 *.x*/4.7 *.x* redistributable.|Žádná akce.<br /><br /> Pokud chcete zjistit, jaké verze rozhraní .NET Framework jsou nainstalovány v systému, naleznete v tématu [jak: Determine Which .NET Framework verze Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md). Zobrazit [požadavky na systém](../../../docs/framework/get-started/system-requirements.md) pro podporované operační systémy.|  
|Rozhraní .NET Framework 4.5 *.x*/4.6 *.x*/4.7 *.x* nepodporuje tento operační systém.|Zobrazit [požadavky na systém](../../../docs/framework/get-started/system-requirements.md) pro podporované operační systémy.<br /><br /> Týkajících se neúspěšných instalací rozhraní .NET Framework ve Windows 7 Tato zpráva obvykle znamená, že Windows 7 SP1 není nainstalována. Rozhraní .NET Framework vyžaduje v systémech Windows 7, Windows 7 SP1. Pokud jsou ve Windows 7 a aktualizací Service Pack 1 ještě nenainstalovali, musíte provést před instalací rozhraní .NET Framework. Informace o instalaci Windows 7 SP1, najdete v části [zjistěte, jak nainstalovat Windows 7 Service Pack 1 (SP1)](https://windows.microsoft.com/en-us/windows7/install-windows-7-service-pack-1).|  
|Ve vašem počítači právě běží instalace Server Core pro operační systém Windows Server 2008. Rozhraní .NET Framework 4.5. *x* vyžaduje plnou verzi operačního systému nebo Server Core 2008 R2 SP1. Nainstalujte plnou verzi systému Windows Server 2008 SP2 nebo Windows Server 2008 R2 SP1 nebo Server Core 2008 R2 SP1 a znovu spusťte rozhraní .NET Framework 4.5. *x* instalační program.|Rozhraní .NET Framework je podporováno v roli Server Core v systému Windows Server 2008 R2 SP1 nebo novějším. Zobrazit [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).|  
|Rozhraní .NET Framework 4.5. *x* je již součástí tohoto operačního systému, ale je aktuálně vypnuto ([!INCLUDE[winserver8](../../../includes/winserver8-md.md)] pouze).|Zobrazit [Windows zapnout nebo vypnout funkce](https://go.microsoft.com/fwlink/p/?LinkId=248438) na webu Windows.|  
|Tento instalační program vyžaduje počítač s architekturou x86. Nelze jej instalovat do počítače s architekturou x64 nebo IA64.|Zobrazit [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).|  
|Tento instalační program vyžaduje počítač s architekturou x64 nebo x86. Nelze jej instalovat na počítačích s architekturou IA64.|Zobrazit [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).|  

<a name="compat"></a>
### <a name="program-compatibility-issues"></a>Problémy s kompatibilitou programu

Instalace rozhraní .NET Framework 4.5 nebo jeho novější vydání selže s chybovým kódem 1603 nebo bloky při spuštění v režimu kompatibility programů Windows. **Pomocník s kompatibilitou programů** označuje, že rozhraní .NET Framework nemuselo být správně nainstalováno a vyzve k přeinstalování pomocí doporučeného nastavení (režim kompatibility programů). Režim kompatibility programů mohl nastavit také Průvodce kompatibilitou programu během dřívějšího neúspěšného nebo zrušeného pokusu o spuštění instalačního programu rozhraní .NET Framework.

Instalační program rozhraní .NET Framework nelze spouštět v režimu kompatibility programů. Pokud chcete vyřešit tento problém blokování, musíte v Editoru registru zajistit, aby nastavení režimu kompatibility nebylo povoleno v celém systému:

1. Zvolte **Start** tlačítko a pak zvolte **spustit**.

1. V **spustit** dialogové okno, zadejte "regedit" a klikněte na tlačítko **OK**.

1. V Editoru registru vyhledejte následující podklíče:

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Compatibility Assistant\Persisted

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers

1. Ve sloupci Název vyhledejte [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 nebo 4.7.2 staženého, v závislosti na kterou verzi instalujete a tyto položky odstraňte. Pokyny ke stažení názvů naleznete v tématu [nainstalovat rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md) článku.

1. Znovu spusťte instalační program rozhraní .NET Framework verze 4.5, 4.5.1, 4.5.2, nebo 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 nebo 4.7.2.

## <a name="see-also"></a>Viz také:

[Instalace rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md)   
[Postupy: zjištění nainstalovaných verzí rozhraní .NET Framework](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)   
[Verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md)
