---
title: "Řešení potíží s blokované rozhraní .NET Framework a odinstalacemi"
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.custom: updateeachrelease
helpviewer_keywords:
- .NET Framework, troubleshooting blocked installations
- blocked .NET Framework installations, troubleshooting
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ccac79516966a6da51d2b590cd22409f0703576
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshoot-blocked-net-framework-installations-and-uninstallations"></a>Řešení potíží s blokované rozhraní .NET Framework a odinstalacemi

Při spuštění [web nebo offline instalačního programu](../../../docs/framework/install/guide-for-developers.md) pro rozhraní .NET Framework 4.5 nebo novější verze, můžete setkat problém, který brání nebo blokuje instalaci rozhraní .NET Framework. Následující tabulka uvádí možné blokující problémy a obsahuje odkazy na informace o odstraňování potíží.

V systému Windows 8 a novější verze rozhraní .NET Framework je součástí operačního systému a nelze ho odinstalovat samostatně. Aktualizace pro rozhraní .NET Framework se zobrazí v **nainstalované aktualizace** kartě ovládacího panelu **programy a funkce** aplikace. Pro operační systémy, ve kterých není předinstalována rozhraní .NET Framework, rozhraní .NET Framework se zobrazí v **odinstalovat nebo změnit program** karta (nebo **přidat nebo odebrat programy** kartě) z  **Programy a funkce** aplikace v Ovládacích panelech. Informace o verzích Windows, na kterých je předinstalován rozhraní .NET Framework, najdete v části [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).

> [!IMPORTANT]
> Protože verze rozhraní .NET Framework 4.x nejsou aktualizace na místě, nelze nainstalovat dřívější verzi rozhraní .NET Framework 4.x v systému to již nainstalována novější verze. Například v systému Windows 10 patří Creators aktualizaci, nelze nainstalovat rozhraní .NET Framework 4.6.2, jelikož je předinstalován rozhraní .NET Framework 4.7.1 s operačním systémem.

Můžete určit, jaké verze rozhraní .NET Framework, které jsou nainstalované v systému. V tématu [postupy: určení rozhraní .NET Framework verze jsou nainstalované](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) Další informace.

V této tabulce 4.5. *x* odkazuje na rozhraní .NET Framework 4.5 a jeho verze bodu 4.5.1 a 4.5.2, 4.6. *x* odkazuje na rozhraní .NET Framework 4.6 a jeho verze bodu 4.6.1 a 4.6.2 a 4.7. *x* odkazuje rozhraní .NET Framework 4.7 a její verze bodu 4.7.1.

|Zpráva blokování|Další informace nebo řešení problému|  
|----------------------|--------------------------------------------------|  
|Odinstalování rozhraní Microsoft .NET Framework může způsobit, že některé aplikace přestanou fungovat.|Obecně platí, že byste neměli odinstalovávat verze rozhraní .NET Framework nainstalované na vašem počítači, protože na konkrétní verzi rozhraní .NET Framework může záviset aplikace, kterou používáte. Další informace najdete v tématu [rozhraní .NET Framework pro uživatele](../../../docs/framework/get-started/index.md#ForUsers) v *Začínáme* průvodce.|  
|Rozhraní .NET framework 4.5*.x*/4.6*.x*  /je již v tomto počítači nainstalován 4.7 (CSY) nebo novější verze.|Žádná akce není nutná.<br /><br /> Chcete-li zjistit, jaké verze rozhraní .NET Framework, které jsou nainstalované v systému, přečtěte si téma [postupy: určení rozhraní .NET Framework verze jsou nainstalované](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).|  
|Rozhraní .NET Framework 4.5*.x*/4.6*.x*/4.7*.x* (*jazyk*) vyžaduje rozhraní .NET Framework 4.5*.x*/4.6*.x*/4.7*.x*. Nainstalujte rozhraní .NET Framework 4.5*.x*/4.6*.x*/4.7*.x* z webu Stažení softwaru a spusťte instalaci znovu.|Je nutné nainstalovat anglickou verzi zadaná verze rozhraní .NET Framework před instalací jazykové sady. Další informace najdete v části na [instalace jazykové sady](../../../docs/framework/install/guide-for-developers.md#to-install-language-packs) v instalační příručce.|  
|Nelze nainstalovat rozhraní .NET Framework 4.5*.x*/4.6*.x*/4.7*.x*. V počítači jsou aplikace, které s tímto programem nejsou kompatibilní.<br /><br /> -nebo-<br /><br /> V počítači jsou aplikace, které s tímto programem nejsou kompatibilní.|Nejpravděpodobnější příčinou této zprávy je, že byla nainstalována verze Preview nebo RC rozhraní .NET Framework. Odinstalujte preview nebo verzi RC a znovu spusťte instalační program.|  
|Rozhraní .NET framework 4.5*.x*/4.6*.x*  /4.7 nelze odinstalovat pomocí tohoto balíčku. Chcete-li odinstalovat rozhraní .NET Framework 4.5*.x*/4.6*.x* z vašeho počítače, přejděte na **ovládací panely**, zvolte **programy a funkce**, zvolte **Zobrazit nainstalované aktualizace**, vyberte aktualizace pro Microsoft Windows (KB2828152) a potom zvolte **odinstalovat**.|Balíček, který instalujete neodinstaluje preview nebo RC verzích rozhraní .NET Framework.<br /><br /> Odinstalujte preview nebo RC verze v Ovládacích panelech.|  
|Nelze odinstalovat, rozhraní .NET Framework 4.5*.x*/4.6*.x*/4.7*.x*. Na tomto programu závisí další aplikace v počítači.|Obecně platí by neměl odinstalovat všechny verze rozhraní .NET Framework z vašeho počítače, protože aplikaci, kterou používáte, může záviset na konkrétní verzi rozhraní .NET Framework. Další informace najdete v tématu [rozhraní .NET Framework pro uživatele](../../../docs/framework/get-started/index.md#ForUsers) v *Začínáme* průvodce.|  
|Rozhraní .NET Framework 4.5*.x*/4.6*.x*/4.7*.x* redistributable nevztahuje na tomto operačním systému. Stáhněte si prosím rozhraní .NET Framework 4.5*.x*/4.6*.x*/4.7*.x* operačního systému z webu Microsoft Download Center.|Pokoušíte nainstalovat [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, nebo 4.7.1 na platformě, která není podporována nebo jste vybrali instalační balíček, který neobsahuje součásti pro všechny podporované operační systémy. Spusťte instalaci znovu pomocí offline instalačního programu ([pro 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=309493), [pro 4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397706), [pro 4.6](http://go.microsoft.com/fwlink/p/?LinkId=528233), [pro 4.6.1](http://go.microsoft.com/fwlink/p/?LinkId=671744), pro [ 4.6.2](http://go.microsoft.com/fwlink/p/?LinkId=780604), pro [4.7](http://go.microsoft.com/fwlink/p/?LinkId=825306)), nebo pro [4.7.1](http://go.microsoft.com/fwlink/p/?LinkId=852090). Další informace najdete v tématu [Průvodce instalací](../../../docs/framework/install/guide-for-developers.md) a [požadavky na systém](../../../docs/framework/get-started/system-requirements.md) pro podporované operační systémy.|  
|Aktualizace odpovídající KB\<*číslo*> musí být nainstalovaný před instalací tohoto produktu.|Instalace rozhraní .NET Framework vyžaduje nainstalovanou aktualizaci KB před instalací rozhraní .NET Framework. Instalaci aktualizace a potom spusťte instalaci rozhraní .NET Framework.<br /><br /> Například instalaci aktualizované verze rozhraní .NET Framework na Windows 8.1, Windows RT 8.1 a Windows Server 2012 R2 vyžaduje, aby aktualizace odpovídající [aktualizaci KB 2919355](https://support.microsoft.com/kb/2919355) nainstalovat.|  
|Ve vašem počítači je nainstalováno serverové jádro operačního systému Windows Server 2008. Rozhraní .NET Framework 4.5. *x* vyžaduje novější verzi operačního systému. Nainstalujte Windows Server 2008 R2 SP1 nebo vyšší a znovu spusťte rozhraní .NET Framework 4.5. *x* instalační program.|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] a 4.5.2 jsou podporovány v roli jádro serveru s Windows Server 2008 R2 SP1 nebo novější. V tématu [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).|  
|Nemáte dostatečná oprávnění, abyste tuto operaci mohli dokončit pro všechny uživatele počítače. Přihlaste se jako správce a spusťte znovu **instalační program**.|Pokud chcete instalovat rozhraní .NET Framework, musíte být správcem počítače.|  
|Instalační program nemůže pokračovat, protože předchozí instalace vyžaduje, aby byl počítač restartován. Restartujte počítač a spusťte instalační program znovu.|Někdy je nutné restartovat plně dokončení instalace. Postupujte podle pokynů a restartujte počítač a spusťte instalaci znovu.<br /><br /> Ve výjimečných případech můžete být vyzváni k restartování systému více než jednou, pokud zjistil počet chybějící aktualizace systému Windows a je restartování nainstalovat další aktualizace ve frontě.|  
|Rozhraní .NET Framework nelze spouštět v režimu kompatibility programů.|Najdete v článku [Program kompatibility problémy](#compat) později v tomto článku.|  
|Rozhraní .NET framework 4.5*.x*/4.6*.x*/4.7*.x* nenainstaloval, protože úložiště součástí je poškozená.|V tématu [Windows Update opravit chyby pomocí nástroje DISM nebo připravenosti aktualizace systému](https://support.microsoft.com/en-us/kb/947821) Další informace.|  
|Instalační program nelze spustit, protože v počítači není k dispozici Instalační služba systému Windows.|V tématu [chyba Instalační služba systému Windows při instalaci nebo aktualizaci programy](http://go.microsoft.com/fwlink/p/?LinkId=248684) na webu Microsoft Support.|  
|Je možné, že instalační program nebude správně fungovat, protože v počítači není k dispozici Instalační služba systému Windows.|Počítač může být nakonfigurován tak, aby používal služby Windows Server Update Services (WSUS) namísto Microsoft Windows Update. Další informace najdete v části pro kód chyby 0x800F0906 v [kódy chyb při instalaci rozhraní .NET Framework 3.5 v systému Windows 8 nebo Windows Server 2012](http://support.microsoft.com/kb/2734782).<br /><br /> Viz také [jak získat nejnovější verzi aplikace Windows Update Agent ke správě aktualizací v počítači](http://go.microsoft.com/fwlink/p/?LinkId=248437) na webu Microsoft Support.|  
|Je možné, že instalační program nebude správně fungovat, protože v počítači není k dispozici Služba inteligentního přenosu na pozadí (BITS).|V tématu [aktualizaci, aby se zabránilo chybě služby inteligentního přenosu na pozadí (BITS) na počítači se systémem Windows Vista](http://go.microsoft.com/fwlink/p/?LinkId=248680) na webu Microsoft Support.|  
|Instalační program nebude správně fungovat, protože Windows update došlo k chybě a zobrazí kód chyby 0x80070643 nebo 0x643.|V tématu [chyby instalace aktualizace .NET Framework: "0x80070643" nebo "0x643"](https://support.microsoft.com/kb/976982) na webu Microsoft Support.|  
|Rozhraní .NET Framework 4.5. *.x*/4.6*.x*/4.7*.x* už je součástí tohoto operačního systému. Není potřeba nainstalovat rozhraní .NET Framework 4.5*.x*/4.6*.x*/4.7*.x* redistributable.|Žádná akce.<br /><br /> Chcete-li zjistit, jaké verze rozhraní .NET Framework, které jsou nainstalované v systému, přečtěte si téma [postupy: určení rozhraní .NET Framework verze jsou nainstalované](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md). V tématu [požadavky na systém](../../../docs/framework/get-started/system-requirements.md) pro podporované operační systémy.|  
|Rozhraní .NET Framework 4.5*.x*/4.6*.x*/4.7*.x* není podporován v tomto operačním systému.|V tématu [požadavky na systém](../../../docs/framework/get-started/system-requirements.md) pro podporované operační systémy.<br /><br /> Týkajících se neúspěšných instalací rozhraní .NET Framework na systému Windows 7 Tato zpráva obvykle znamená, že systém Windows 7 SP1 není nainstalována. V systémech Windows 7 se vyžaduje rozhraní .NET Framework Windows 7 SP1. Pokud jsou v systému Windows 7 a aktualizací Service Pack 1 ještě nenainstalovali, musíte provést před instalací rozhraní .NET Framework. Informace o instalaci systému Windows 7 SP1 najdete v tématu [zjistěte, jak nainstalovat Windows 7 Service Pack 1 (SP1)](http://windows.microsoft.com/en-us/windows7/install-windows-7-service-pack-1).|  
|Ve vašem počítači právě běží instalace Server Core pro operační systém Windows Server 2008. Rozhraní .NET Framework 4.5. *x* vyžaduje úplnou verzi operačního systému nebo Server Core 2008 R2 SP1. Nainstalujte plnou verzi systému Windows Server 2008 SP2 nebo Windows Server 2008 R2 SP1 nebo Server Core 2008 R2 SP1 a znovu spusťte rozhraní .NET Framework 4.5. *x* instalační program.|Rozhraní .NET Framework je podporováno v roli Server Core v systému Windows Server 2008 R2 SP1 nebo novějším. V tématu [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).|  
|Rozhraní .NET Framework 4.5. *x* už je součástí tohoto operačního systému, ale je aktuálně vypnutý ([!INCLUDE[winserver8](../../../includes/winserver8-md.md)] pouze).|V tématu [Windows zapnout nebo vypnout funkce](http://go.microsoft.com/fwlink/p/?LinkId=248438) na webu systému Windows.|  
|Tento instalační program vyžaduje počítač s architekturou x86. Nelze jej instalovat do počítače s architekturou x64 nebo IA64.|V tématu [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).|  
|Tento instalační program vyžaduje počítač s architekturou x64 nebo x86. Nelze jej instalovat na počítačích s architekturou IA64.|V tématu [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).|  

<a name="compat"></a>
### <a name="program-compatibility-issues"></a>Problémy s kompatibilitou programu

Instalace rozhraní .NET Framework 4.5 nebo jeho verze bodu selže s kód chyby 1603 nebo bloky při spuštění v režimu kompatibility programu systému Windows. **Pomocník s kompatibilitou** označuje, že rozhraní .NET Framework nebyly správně nainstalovány a vás vyzve, abyste znovu ji nainstalujte pomocí doporučené nastavení (režim kompatibility programů). Režim kompatibility programů mohl nastavit také Průvodce kompatibilitou programu během dřívějšího neúspěšného nebo zrušeného pokusu o spuštění instalačního programu rozhraní .NET Framework.

Instalační program rozhraní .NET Framework nelze spouštět v režimu kompatibility programů. Pokud chcete vyřešit tento problém blokování, musíte v Editoru registru zajistit, aby nastavení režimu kompatibility nebylo povoleno v celém systému:

1. Vyberte **spustit** tlačítko a potom vyberte **spustit**.

1. V **spustit** dialogové okno, zadejte "regedit" a zvolte **OK**.

1. V Editoru registru vyhledejte následující podklíče:

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Compatibility Assistant\Persisted

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers

1. Ve sloupci Název vyhledejte [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 nebo 4.7.1 stáhnout názvy, v závislosti na verzi, kterou instalujete a odstranit tyto položky. Názvy stahování, najdete v části [instalaci rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md) článku.

1. Znovu spusťte instalační program rozhraní .NET Framework verze 4.5, 4.5.1, 4.5.2, nebo 4.6, 4.6.1, 4.6.2, 4.7 nebo 4.7.1.

## <a name="see-also"></a>Viz také

[Nainstalujte rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md)   
[Postupy: zjištění nainstalovaných verzí rozhraní .NET Framework](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)   
[Verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md)
