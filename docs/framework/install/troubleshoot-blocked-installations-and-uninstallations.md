---
title: Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework
description: Poradce při potížích, se kterými se setkáte a které brání instalaci rozhraní .NET Framework. Informace k řešení problémů naleznete na stavových zprávách.
ms.date: 04/18/2019
ms.custom: updateeachrelease
helpviewer_keywords:
- .NET Framework, troubleshooting blocked installations
- blocked .NET Framework installations, troubleshooting
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
ms.openlocfilehash: 70cefb53d29c7a895a3e242776bae39b7636fd65
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506954"
---
# <a name="troubleshoot-blocked-net-framework-installations-and-uninstallations"></a>Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework

Při spuštění [webové nebo offline instalační program](guide-for-developers.md) pro rozhraní .NET Framework 4.5 nebo novější verze, může dojít k problému, který zabraňuje nebo blokuje instalaci rozhraní .NET Framework. Následující tabulka uvádí možné blokující problémy a obsahuje odkazy na informace o odstraňování potíží.

V systému Windows 8 a vyšší rozhraní .NET Framework je součást operačního systému a nelze ji nezávisle odinstalovat. Aktualizace rozhraní .NET Framework se zobrazí na kartě **Nainstalované aktualizace** v aplikaci **Programy a funkce** Ovládacích panelů. U operačních systémů, ve kterých není rozhraní .NET Framework předinstalováno, se rozhraní .NET Framework zobrazí na kartě **Odinstalovat nebo změnit** kartu Program (nebo kartu **Přidat nebo odebrat programy)** aplikace **Program a funkce** v Ovládacích panelech. Informace o verzích systému Windows, na kterých je předinstalována rozhraní .NET Framework, naleznete [v tématu Systémové požadavky](../get-started/system-requirements.md).

> [!IMPORTANT]
> Vzhledem k tomu, že verze rozhraní 4.x rozhraní .NET Framework jsou místní aktualizace, nelze nainstalovat starší verzi rozhraní .NET Framework 4.x do systému, který již má nainstalovanou novější verzi. Například v systému s aktualizací Windows 10 Fall Creators Update nelze nainstalovat rozhraní .NET Framework 4.6.2, protože rozhraní .NET Framework 4.7.1 je předinstalováno s operačním systémem.

Můžete určit, které verze rozhraní .NET Framework jsou nainstalovány v systému. Další informace naleznete [v tématu How to: Determine Which .NET Framework Versions Are Installed](../migration-guide/how-to-determine-which-versions-are-installed.md) for more information.

V této tabulce 4.5.x odkazuje na rozhraní .NET Framework 4.5 a jeho bodové verze, 4.5.1 a 4.5.2, 4.6.x odkazuje na rozhraní .NET Framework 4.6 a jeho bodové verze, 4.6.1 a 4.6.2, 4.7.x odkazuje na rozhraní .NET Framework 4.7 a jeho bodové verze, 4.7.1 a 4.7.2 , a 4.8 odkazuje na rozhraní .NET Framework 4.8.

|Zpráva blokování|Další informace nebo řešení problému|  
|----------------------|--------------------------------------------------|  
|Odinstalování rozhraní Microsoft .NET Framework může způsobit, že některé aplikace přestanou fungovat.|Obecně platí, že byste neměli odinstalovávat verze rozhraní .NET Framework nainstalované na vašem počítači, protože na konkrétní verzi rozhraní .NET Framework může záviset aplikace, kterou používáte. Další informace naleznete [v rozhraní .NET Framework pro uživatele](../get-started/index.md#ForUsers) v příručce *Začínáme.*|  
|Rozhraní .NET Framework 4.5.x/4.6.x/4.7.x (ENU) nebo novější verze je již v tomto počítači nainstalována.|Žádná akce není nutná.<br /><br /> Informace o tom, které verze rozhraní .NET Framework jsou v systému nainstalovány, naleznete v [tématu How to: Determine Which .NET Framework Versions Are Installed](../migration-guide/how-to-determine-which-versions-are-installed.md).|  
|Rozhraní .NET Framework 4.5.x/4.6.x/4.7.x/4.8 (*jazyk*) vyžaduje rozhraní .NET Framework 4.5.x/4.6.x/4.7.x/4.8. Nainstalujte rozhraní .NET Framework 4.5.x/4.6.x/4.7.x/4.8 ze služby Stažení softwaru a znovu spusťte instalační program.|Před instalací jazykové sady je nutné nainstalovat anglickou verzi zadané verze rozhraní .NET Framework. Další informace naleznete v části [Instalace jazykových sad](guide-for-developers.md#to-install-language-packs) v instalační příručce.|  
|Rozhraní .NET Framework 4.5.x/4.6.x/4.7.x/4.8 nelze nainstalovat. V počítači jsou aplikace, které s tímto programem nejsou kompatibilní.<br /><br /> -nebo-<br /><br /> V počítači jsou aplikace, které s tímto programem nejsou kompatibilní.|Nejpravděpodobnější příčinou této zprávy je, že byla nainstalována verze Preview nebo RC rozhraní .NET Framework. Odinstalujte verzi preview nebo RC a znovu spusťte instalační program.|  
|Rozhraní .NET Framework 4.5.x/4.6.x/4.7.x/4.8 nelze odinstalovat pomocí tohoto balíčku. Chcete-li odinstalovat rozhraní .NET Framework 4.5.x/4.6.x/4.7.x/4.8 z počítače, přejděte na **Ovládací panely**, zvolte **Programy a funkce**, zvolte Zobrazit **nainstalované aktualizace**, vyberte možnost Aktualizovat pro systém Microsoft Windows (KB2828152) a pak zvolte **Odinstalovat**.|Balíček, který instalujete, neodinstaluje náhled nebo RC verze rozhraní .NET Framework.<br /><br /> Odinstalujte náhled nebo rc verzi z Ovládacích panelů.|  
|Rozhraní .NET Framework 4.5.x/4.6.x/4.7.x/4.8 nelze odinstalovat. Na tomto programu závisí další aplikace v počítači.|Obecně byste neměli odinstalovat žádné verze rozhraní .NET Framework z počítače, protože aplikace, kterou používáte, může záviset na konkrétní verzi rozhraní .NET Framework. Další informace naleznete [v rozhraní .NET Framework pro uživatele](../get-started/index.md#ForUsers) v příručce *Začínáme.*|  
|Redistribuovatelné rozhraní .NET Framework 4.5.x/4.6.x/4.7.x/4.8 se na tento operační systém nevztahuje. Stáhněte si rozhraní .NET Framework 4.5.x/4.6.x/4.7.x/4.8 pro váš operační systém ze stránky ke stažení rozhraní .NET Framework.|Je možné, že se pokoušíte nainstalovat rozhraní .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 nebo 4.8 na platformě, která není podporována, nebo jste vybrali instalační balíček, který neobsahuje součásti pro všechny podporované operační systémy. Spusťte instalaci znovu pomocí instalátoru offline ([pro 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=309493), [pro 4.5.2](https://dotnet.microsoft.com/download/dotnet-framework/net452), [pro 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net46), pro [4.6.2](https://go.microsoft.com/fwlink/p/?LinkId=780604), pro [4.7](https://go.microsoft.com/fwlink/p/?LinkId=825306)), pro [4.7.1](https://go.microsoft.com/fwlink/p/?LinkId=852090), pro [4.7.2](https://dotnet.microsoft.com/download/dotnet-framework/net472)nebo pro [4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48). [for 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461) Další informace naleznete v [příručce k instalaci](guide-for-developers.md) a [v požadavcích na systém](../get-started/system-requirements.md) pro podporované operační systémy.|  
|Před instalací tohoto\<produktu je třeba nainstalovat aktualizaci odpovídající*číslu* KB>.|Instalace rozhraní .NET Framework vyžaduje, aby byla před instalací rozhraní .NET Framework nainstalována aktualizace KB. Nainstalujte aktualizaci a začněte instalaci rozhraní .NET Framework znovu.<br /><br /> Například instalace aktualizovaných verzí rozhraní .NET Framework v systémech Windows 8.1, Windows RT 8.1 a Windows Server 2012 R2 vyžaduje instalaci aktualizace odpovídající [kb 2919355.](https://support.microsoft.com/kb/2919355)|  
|Ve vašem počítači je nainstalováno serverové jádro operačního systému Windows Server 2008. Rozhraní .NET Framework 4.5.x vyžaduje novější verzi operačního systému. Nainstalujte systém Windows Server 2008 R2 SP1 nebo vyšší a znovu spusťte instalační program rozhraní .NET Framework 4.5.x.|Rozhraní .NET Framework 4.5.1 a 4.5.2 jsou podporovány v roli Jádra serveru se systémem Windows Server 2008 R2 SP1 nebo novějším. Viz [Systémové požadavky](../get-started/system-requirements.md).|  
|Nemáte dostatečná oprávnění, abyste tuto operaci mohli dokončit pro všechny uživatele počítače. Přihlaste se jako správce a znovu **spusťte instalační program**.|Pokud chcete instalovat rozhraní .NET Framework, musíte být správcem počítače.|  
|Instalační program nemůže pokračovat, protože předchozí instalace vyžaduje, aby byl počítač restartován. Restartujte počítač a spusťte instalační program znovu.|K úplnému dokončení instalace je někdy nutné restartovat počítač. Podle pokynů restartujte počítač a spusťte instalační program znovu.<br /><br /> Ve výjimečných případech můžete být vyzváni k restartování systému více než jednou, pokud systém Windows zjistil řadu chybějících aktualizací a restartuje instalaci další aktualizace do fronty.|  
|Rozhraní .NET Framework nelze spouštět v režimu kompatibility programů.|V tomto článku najdete část [Problémy s kompatibilitou programů](#compat) dále v tomto článku.|  
|Rozhraní .NET Framework 4.5.x/4.6.x/4.7.x/4.8 nebylo nainstalováno, protože úložiště součástí bylo poškozeno.|Další informace naleznete [v tématu Oprava chyb služby Windows Update pomocí nástroje Připravenost na služby DISM nebo Aktualizace systému.](https://support.microsoft.com/kb/947821)|  
|Instalační program nelze spustit, protože v počítači není k dispozici Instalační služba systému Windows.|Při [pokusu o instalaci programu v systému Windows 7 nebo Windows Vista](https://support.microsoft.com/help/2642495/the-windows-installer-service-could-not-be-accessed-error-when-you-try) na webu podpory společnosti Microsoft naleznete chybu "Instalační služba systému Windows nelze získat přístup k chybě".|  
|Je možné, že instalační program nebude správně fungovat, protože v počítači není k dispozici Instalační služba systému Windows.|Počítač může být nakonfigurován tak, aby používal služby Windows Server Update Services (WSUS) namísto Microsoft Windows Update. Další informace naleznete v části kód chyby 0x800F0906 v [rozhraní .NET Framework 3.5 chyba instalace: 0x800F0906, 0x800F081F, 0x800F0907](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906-0x800f081f-0x800f0907).<br /><br /> Viz Také [informace o tom, jak aktualizovat agenta služby Windows Update na nejnovější verzi](https://support.microsoft.com/help/949104/how-to-update-the-windows-update-agent-to-the-latest-version) na webu podpory společnosti Microsoft.|  
|Je možné, že instalační program nebude správně fungovat, protože v počítači není k dispozici Služba inteligentního přenosu na pozadí (BITS).|Informace o [opravě selhání služby BITS (Background Intelligent Transfer Service) na webu se systémem Windows Vista](https://support.microsoft.com/help/940520/an-update-is-available-to-fix-a-background-intelligent-transfer-servic) na webu podpory společnosti Microsoft naleznete v tématu Je k dispozici aktualizace.|  
|Instalační program nemusí pracovat správně, protože aktualizace systému Windows zjistila chybu a zobrazila kód chyby 0x80070643 nebo 0x643.|[Chyba instalace aktualizace rozhraní .NET Framework: "0x80070643" nebo "0x643"](https://support.microsoft.com/kb/976982) na webu podpory společnosti Microsoft.|  
|Rozhraní .NET Framework 4.5.x/4.6.x/4.7.x/4.8 je již součástí tohoto operačního systému. Rozhraní .NET Framework 4.5.x/4.6.x/4.7.x/4.8 redistributable není nutné instalovat.|Žádná akce.<br /><br /> Informace o tom, které verze rozhraní .NET Framework jsou v systému nainstalovány, naleznete v [tématu How to: Determine Which .NET Framework Versions Are Installed](../migration-guide/how-to-determine-which-versions-are-installed.md). Viz [Systémové požadavky](../get-started/system-requirements.md) pro podporované operační systémy.|  
|Rozhraní .NET Framework 4.5.x/4.6.x/4.7.x/4.8 není v tomto operačním systému podporováno.|Viz [Systémové požadavky](../get-started/system-requirements.md) pro podporované operační systémy.<br /><br /> U neúspěšných instalací rozhraní .NET Framework v systému Windows 7 tato zpráva obvykle označuje, že systém Windows 7 SP1 není nainstalován. V systémech Windows 7 vyžaduje rozhraní .NET Framework aktualizaci Windows 7 SP1. Pokud jste v systému Windows 7 a ještě jste nenainstalovali aktualizaci Service Pack 1, budete to muset učinit před instalací rozhraní .NET Framework. Informace o instalaci aktualizace Windows 7 SP1 naleznete v [tématu How to install Windows 7 Service Pack 1 (SP1)](https://windows.microsoft.com/windows7/install-windows-7-service-pack-1).|  
|Ve vašem počítači právě běží instalace Server Core pro operační systém Windows Server 2008. Rozhraní .NET Framework 4.5.x vyžaduje úplnou verzi operačního systému nebo servercore 2008 R2 SP1. Nainstalujte plnou verzi aktualizace Windows Server 2008 SP2 nebo Windows Server 2008 R2 SP1 nebo Server Core 2008 R2 SP1 a znovu spusťte instalační program rozhraní .NET Framework 4.5.x.|Rozhraní .NET Framework je podporováno v roli Server Core v systému Windows Server 2008 R2 SP1 nebo novějším. Viz [Systémové požadavky](../get-started/system-requirements.md).|  
|Rozhraní .NET Framework 4.5.x je již součástí tohoto operačního systému, ale je aktuálně vypnuto (pouze systém Windows Server 2012).| Pomocí **zapnutí nebo vypnutí funkcí systému Windows** v **Ovládacích panelech** zapněte rozhraní .NET Framework 4.5.x. |  
|Tento instalační program vyžaduje počítač s architekturou x86. Nelze jej instalovat do počítače s architekturou x64 nebo IA64.|Viz [Systémové požadavky](../get-started/system-requirements.md).|  
|Tento instalační program vyžaduje počítač s architekturou x64 nebo x86. Nelze jej instalovat na počítačích s architekturou IA64.|Viz [Systémové požadavky](../get-started/system-requirements.md).|  

<a name="compat"></a>
### <a name="program-compatibility-issues"></a>Problémy s kompatibilitou programů

Instalace rozhraní .NET Framework 4.5 nebo jejích bodových verzí se nezdaří s kódem chyby 1603 nebo bloky, pokud je spuštěna v režimu kompatibility programů systému Windows. **Pomocník s kompatibilitou programů** označuje, že rozhraní .NET Framework pravděpodobně nebylo správně nainstalováno, a zobrazí výzvu k jeho přeinstalaci pomocí doporučeného nastavení (režim kompatibility programů). Režim kompatibility programů mohl nastavit také Průvodce kompatibilitou programu během dřívějšího neúspěšného nebo zrušeného pokusu o spuštění instalačního programu rozhraní .NET Framework.

Instalační program rozhraní .NET Framework nelze spouštět v režimu kompatibility programů. Chcete-li tento problém s blokováním vyřešit, musíte pomocí Editoru registru zajistit, aby nastavení režimu kompatibility nebylo povoleno v celém systému:

1. Zvolte tlačítko **Start** a pak zvolte **Spustit**.

1. V dialogovém okně **Spustit** zadejte "regedit" a pak zvolte **OK**.

1. V Editoru registru vyhledejte následující podklíče:

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Compatibility Assistant\Persisted

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers

1. Ve sloupci Název vyhledejte soubory .NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 nebo 4.7.2 názvy ke stažení v závislosti na tom, kterou verzi instalujete, a odstraňte tyto položky. Názvy ke stažení naleznete [v článku Instalace rozhraní .NET Framework pro vývojáře.](guide-for-developers.md)

1. Spusťte instalační program rozhraní .NET Framework pro verze 4.5, 4.5.1, 4.5.2 nebo 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 nebo 4.7.2.

## <a name="see-also"></a>Viz také

- [Instalace rozhraní .NET Framework pro vývojáře](guide-for-developers.md)
- [Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework](../migration-guide/how-to-determine-which-versions-are-installed.md)
- [Verze a závislosti](../migration-guide/versions-and-dependencies.md)
