---
title: Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework
ms.date: 04/18/2019
ms.custom: updateeachrelease
helpviewer_keywords:
- .NET Framework, troubleshooting blocked installations
- blocked .NET Framework installations, troubleshooting
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
ms.openlocfilehash: d0f3d857a90aca763121595151a2193125b47c6c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975631"
---
# <a name="troubleshoot-blocked-net-framework-installations-and-uninstallations"></a>Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework

Pokud spustíte [webový nebo offline instalační program](guide-for-developers.md) pro .NET Framework 4,5 nebo novější verze, může dojít k problému, který brání nebo blokuje instalaci .NET Framework. Následující tabulka uvádí možné blokující problémy a obsahuje odkazy na informace o odstraňování potíží.

V systému Windows 8 nebo novějším je .NET Framework součástí operačního systému a nelze ji nezávisle odinstalovat. Aktualizace .NET Framework se zobrazí na kartě **nainstalované aktualizace** v nabídce aplikace **a funkce** v Ovládacích panelech. U operačních systémů, ve kterých není předinstalována .NET Framework, se .NET Framework zobrazí na kartě **Odinstalovat nebo změnit program** (nebo na kartě **Přidat nebo odebrat programy** ) aplikace **a funkce** v Ovládacích panelech. Informace o verzích Windows, na kterých je předinstalované .NET Framework, najdete v tématu [požadavky na systém](../get-started/system-requirements.md).

> [!IMPORTANT]
> Vzhledem k tomu, že verze .NET Framework 4. x jsou místní aktualizace, nemůžete nainstalovat starší verzi .NET Framework 4. x v systému, ve kterém už je nainstalovaná novější verze. Například v systému s Windows 10 se aktualizace Creators Update nedají nainstalovat .NET Framework 4.6.2, protože .NET Framework 4.7.1 je předinstalované s operačním systémem.

Můžete určit, které verze .NET Framework jsou nainstalovány v systému. Další informace najdete v tématu [Postupy: určení, které verze .NET Framework jsou nainstalovány](../migration-guide/how-to-determine-which-versions-are-installed.md) .

V této tabulce odkazuje 4.5 na .NET Framework 4,5 a jejich verze, 4.5.1 a 4.5.2, 4.6. x odkazuje na .NET Framework 4,6 a jejich verze, 4.6.1 a 4.6.2, 4.7. x odkazuje na .NET Framework 4,7 a jejich verze, 4.7.1 a 4.7.2. a 4,8 odkazuje na .NET Framework 4,8.

|Zpráva blokování|Další informace nebo řešení problému|  
|----------------------|--------------------------------------------------|  
|Odinstalování rozhraní Microsoft .NET Framework může způsobit, že některé aplikace přestanou fungovat.|Obecně platí, že byste neměli odinstalovávat verze rozhraní .NET Framework nainstalované na vašem počítači, protože na konkrétní verzi rozhraní .NET Framework může záviset aplikace, kterou používáte. Další informace najdete v tématu [.NET Framework pro uživatele](../get-started/index.md#ForUsers) v příručce *Začínáme* .|  
|V tomto počítači je již nainstalováno .NET Framework 4.5. x/4.6. x/4.7. x (CSY) nebo novější verze.|Žádná akce není nutná.<br /><br /> Chcete-li zjistit, které verze .NET Framework jsou nainstalovány v systému, přečtěte si téma [How to: Určete, které verze .NET Framework jsou nainstalovány](../migration-guide/how-to-determine-which-versions-are-installed.md).|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 (*jazyk*) vyžaduje .NET Framework 4.5. x/4.6. x/4,8. Nainstalujte prosím .NET Framework 4.5. x/4.6. x/4.7. x/4.8 ze služby Stažení softwaru a spusťte instalaci znovu.|Před instalací jazykové sady je třeba nainstalovat anglickou verzi zadaného .NET Framework Release. Další informace najdete v části [Instalace jazykových sad](guide-for-developers.md#to-install-language-packs) v instalační příručce.|  
|Nelze nainstalovat .NET Framework 4.5. x/4.6. x/4.7. x/4.8. V počítači jsou aplikace, které s tímto programem nejsou kompatibilní.<br /><br /> -nebo-<br /><br /> V počítači jsou aplikace, které s tímto programem nejsou kompatibilní.|Nejpravděpodobnější příčinou této zprávy je, že byla nainstalována verze Preview nebo RC rozhraní .NET Framework. Odinstalujte verzi Preview nebo RC a spusťte instalační program znovu.|  
|.NET Framework 4.5. x/4.6. x/4.7 nelze odinstalovat pomocí tohoto balíčku. Pokud chcete odinstalovat .NET Framework 4.5. x/4.6. x/4,8. x/4.8 z počítače, klikněte na **Ovládací panely**, zvolte **programy a funkce**, zvolte **Zobrazit nainstalované aktualizace**, vyberte aktualizace pro Microsoft Windows (KB2828152) a pak zvolte  **Odinstalujte**.|Balíček, který instalujete, neodinstaluje verze Preview nebo RC .NET Framework.<br /><br /> Odinstalujte verzi Preview nebo RC z ovládacích panelů.|  
|Nelze odinstalovat .NET Framework 4.5. x/4.6. x/4.7. x/4.8. Na tomto programu závisí další aplikace v počítači.|Obecně platí, že byste neměli odinstalovat žádné verze .NET Framework z počítače, protože na konkrétní verzi .NET Framework může záviset aplikace, kterou používáte. Další informace najdete v tématu [.NET Framework pro uživatele](../get-started/index.md#ForUsers) v příručce *Začínáme* .|  
|V tomto operačním systému se nevztahují na tento operační systém: .NET Framework 4.5. x/4.6. x/4.8 Redistributable. Stáhněte si prosím z webu Microsoft Download Center .NET Framework 4.5. x/4.6. x/4.7. x/4.8 pro váš operační systém.|Pravděpodobně se pokoušíte nainstalovat .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 nebo 4,8 na platformě, která není podporována, nebo jste vybrali instalační balíček, který neobsahuje komponenty pro všechny podporované operační systémy. Spusťte instalaci znovu pomocí instalačního programu offline ([pro 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=309493), pro [4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397706), pro [4,6](https://go.microsoft.com/fwlink/p/?LinkId=528233) [, pro](https://go.microsoft.com/fwlink/p/?LinkId=671744) [4.6.2](https://go.microsoft.com/fwlink/p/?LinkId=780604) [4,7](https://go.microsoft.com/fwlink/p/?LinkId=825306), pro [4.7.1](https://go.microsoft.com/fwlink/p/?LinkId=852090), pro 4.7.2, pro [](https://go.microsoft.com/fwlink/p/?LinkId=863265)nebo pro [4,8](https://go.microsoft.com/fwlink/?linkid=2088631). Další informace najdete v příručce pro [instalaci](guide-for-developers.md) a na [požadavcích na systém](../get-started/system-requirements.md) pro podporované operační systémy.|  
|Než budete moct tento produkt nainstalovat, musí být nainstalovaná aktualizace odpovídající KB\<*číslo*>.|Instalace .NET Framework vyžaduje, abyste před instalací .NET Framework nainstalovali aktualizaci KB. Nainstalujte aktualizaci a pak znovu spusťte instalaci .NET Framework.<br /><br /> Například instalace aktualizovaných verzí .NET Framework v Windows 8.1, Windows RT 8,1 a Windows Server 2012 R2 vyžaduje instalaci aktualizace odpovídající [KB 2919355](https://support.microsoft.com/kb/2919355) .|  
|Ve vašem počítači je nainstalováno serverové jádro operačního systému Windows Server 2008. .NET Framework 4.5. x vyžaduje novější verzi operačního systému. Nainstalujte prosím Windows Server 2008 R2 SP1 nebo novější a znovu spusťte instalační program .NET Framework 4.5. x.|.NET Framework 4.5.1 a 4.5.2 jsou podporované v roli jádro serveru s Windows Serverem 2008 R2 SP1 nebo novějším. Viz [požadavky na systém](../get-started/system-requirements.md).|  
|Nemáte dostatečná oprávnění, abyste tuto operaci mohli dokončit pro všechny uživatele počítače. Přihlaste se jako správce a znovu spusťte **instalační program**.|Pokud chcete instalovat rozhraní .NET Framework, musíte být správcem počítače.|  
|Instalační program nemůže pokračovat, protože předchozí instalace vyžaduje, aby byl počítač restartován. Restartujte počítač a spusťte instalační program znovu.|K úplnému dokončení instalace je někdy nutný Restart. Postupujte podle pokynů a restartujte počítač a spusťte instalační program znovu.<br /><br /> Ve výjimečných případech se může zobrazit výzva k restartování systému více než jednou, pokud systém Windows zjistil počet chybějících aktualizací a restartuje instalaci další aktualizace ve frontě.|  
|Rozhraní .NET Framework nelze spouštět v režimu kompatibility programů.|Viz část [problémy s kompatibilitou programu](#compat) dále v tomto článku.|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 nebylo nainstalováno, protože úložiště součástí je poškozeno.|Další informace najdete v tématu [Oprava chyb web Windows Update pomocí nástroje DISM nebo nástroje Readiness Update Readiness Tool](https://support.microsoft.com/kb/947821) .|  
|Instalační program nelze spustit, protože v počítači není k dispozici Instalační služba systému Windows.|V tématu ["Instalační služba systému Windows službě nelze přistupovat" při pokusu o instalaci programu v systému Windows 7 nebo Windows Vista](https://support.microsoft.com/help/2642495/the-windows-installer-service-could-not-be-accessed-error-when-you-try) na webu Podpora Microsoftu.|  
|Je možné, že instalační program nebude správně fungovat, protože v počítači není k dispozici Instalační služba systému Windows.|Počítač může být nakonfigurován tak, aby používal služby Windows Server Update Services (WSUS) namísto Microsoft Windows Update. Další informace najdete v části týkající se kódu chyby chyby 0x800F0906 v [.NET Framework 3,5 Chyba instalace: chyby 0x800F0906, 0x800F081F, 0x800f0907](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906-0x800f081f-0x800f0907).<br /><br /> Viz také [aktualizace agenta web Windows Update na nejnovější verzi](https://support.microsoft.com/help/949104/how-to-update-the-windows-update-agent-to-the-latest-version) na webu Podpora Microsoftu.|  
|Je možné, že instalační program nebude správně fungovat, protože v počítači není k dispozici Služba inteligentního přenosu na pozadí (BITS).|K [dispozici je aktualizace pro opravu chyby Background Intelligent Transfer Service (BITS) v počítači se systémem Windows Vista](https://support.microsoft.com/help/940520/an-update-is-available-to-fix-a-background-intelligent-transfer-servic) na webu Podpora Microsoftu.|  
|Je možné, že instalační program nebude správně fungovat, protože v systému Windows Update došlo k chybě a zobrazil se kód chyby 0x80070643 nebo 0x643.|Viz [Chyba instalace .NET Framework aktualizace: "0x80070643" nebo "0x643"](https://support.microsoft.com/kb/976982) na webu Podpora Microsoftu.|  
|V tomto operačním systému je již součástí tohoto operačního systému .NET Framework 4.5. x/4.6. x/4.7. x/4.8. Nemusíte instalovat .NET Framework 4.5. x/4.6. ×/4.7. x/4.8 Redistributable.|Žádná akce.<br /><br /> Chcete-li zjistit, které verze .NET Framework jsou nainstalovány v systému, přečtěte si téma [How to: Určete, které verze .NET Framework jsou nainstalovány](../migration-guide/how-to-determine-which-versions-are-installed.md). Podporované operační systémy najdete v tématu [požadavky na systém](../get-started/system-requirements.md) .|  
|V tomto operačním systému není podporován .NET Framework 4.5. x/4.6. x/4.7. x/4.8.|Podporované operační systémy najdete v tématu [požadavky na systém](../get-started/system-requirements.md) .<br /><br /> U neúspěšných instalací .NET Framework ve Windows 7 se tato zpráva obvykle označuje, že není nainstalovaná verze Windows 7 SP1. V systémech Windows 7 .NET Framework vyžaduje systém Windows 7 SP1. Pokud jste v systému Windows 7 a ještě jste nenainstalovali aktualizaci Service Pack 1, budete ji muset provést před instalací .NET Framework. Informace o instalaci systému Windows 7 SP1 najdete v tématu [informace o instalaci systému Windows 7 s aktualizací Service Pack 1 (SP1)](https://windows.microsoft.com/windows7/install-windows-7-service-pack-1).|  
|Ve vašem počítači právě běží instalace Server Core pro operační systém Windows Server 2008. .NET Framework 4.5. x vyžaduje plnou verzi operačního systému nebo Server Core 2008 R2 SP1. Nainstalujte prosím plnou verzi Windows serveru 2008 SP2 nebo Windows Server 2008 R2 SP1 nebo Server Core 2008 R2 SP1 a znovu spusťte instalační program .NET Framework 4.5. x.|Rozhraní .NET Framework je podporováno v roli Server Core v systému Windows Server 2008 R2 SP1 nebo novějším. Viz [požadavky na systém](../get-started/system-requirements.md).|  
|.NET Framework 4.5. x Už je součástí tohoto operačního systému, ale je momentálně vypnutý (jenom[!INCLUDE[winserver8](../../../includes/winserver8-md.md)]).| Pomocí **Možnosti zapnout nebo vypnout funkce systému Windows** v **Ovládacích panelech** zapněte .NET Framework 4.5. x. |  
|Tento instalační program vyžaduje počítač s architekturou x86. Nelze jej instalovat do počítače s architekturou x64 nebo IA64.|Viz [požadavky na systém](../get-started/system-requirements.md).|  
|Tento instalační program vyžaduje počítač s architekturou x64 nebo x86. Nelze jej instalovat na počítačích s architekturou IA64.|Viz [požadavky na systém](../get-started/system-requirements.md).|  

<a name="compat"></a>
### <a name="program-compatibility-issues"></a>Problémy s kompatibilitou programů

Instalace .NET Framework 4,5 nebo jeho vydání se nezdařila s kódem chyby 1603 nebo bloky, pokud jsou spuštěny v režimu kompatibility programů systému Windows. **Pomocník s kompatibilitou programů** indikuje, že .NET Framework pravděpodobně není správně nainstalován, a zobrazí výzvu k jejímu přeinstalaci pomocí doporučeného nastavení (režim kompatibility programů). Režim kompatibility programů mohl nastavit také Průvodce kompatibilitou programu během dřívějšího neúspěšného nebo zrušeného pokusu o spuštění instalačního programu rozhraní .NET Framework.

Instalační program rozhraní .NET Framework nelze spouštět v režimu kompatibility programů. Chcete-li tento blokující problém vyřešit, je nutné použít Editor registru, aby se zajistilo, že nastavení režimu kompatibility není povoleno v rámci systému:

1. Klikněte na tlačítko **Start** a poté zvolte možnost **Spustit**.

1. V dialogovém okně **Spustit** zadejte příkaz regedit a klikněte na **tlačítko OK**.

1. V Editoru registru vyhledejte následující podklíče:

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Compatibility Assistant\Persisted

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers

1. Ve sloupci Název vyhledejte .NET Framework 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1 nebo 4.7.2 jména stahování, podle toho, kterou verzi instalujete, a odstraňte tyto položky. Názvy ke stažení najdete v článku [instalace .NET Framework pro vývojáře](guide-for-developers.md) .

1. Spusťte znovu instalační program .NET Framework pro verzi 4,5, 4.5.1, 4.5.2 nebo 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1 nebo 4.7.2.

## <a name="see-also"></a>Viz také:

- [Instalace .NET Framework pro vývojáře](guide-for-developers.md)
- [Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework](../migration-guide/how-to-determine-which-versions-are-installed.md)
- [Verze a závislosti](../migration-guide/versions-and-dependencies.md)
