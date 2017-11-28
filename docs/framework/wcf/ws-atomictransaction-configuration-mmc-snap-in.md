---
title: Modul snap-in konzoly MMC WS-AtomicTransaction Configuration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 622a8b488a97041800d626566923095a770412f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>Modul snap-in konzoly MMC WS-AtomicTransaction Configuration
Modul Snap-in konzoly MMC WS-AtomicTransaction Configuration slouží ke konfiguraci hodnot nastavení, WS-AtomicTransaction na místních i vzdálených počítačích.  
  
## <a name="remarks"></a>Poznámky  
 Pokud používáte [!INCLUDE[wxp](../../../includes/wxp-md.md)] nebo [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], modul snap-in konzoly MMC naleznete přechodem na **součást Tools panelech řízení služby nebo**, klikněte pravým tlačítkem na **Můj počítač**, a Výběr **vlastnosti**. Toto je stejné umístění, kde můžete nakonfigurovat služby MS DTC. Možnosti, které jsou k dispozici ke konfiguraci jsou seskupené v rámci **WS-AT** kartě.  
  
 Pokud používáte systém Windows Vista nebo [!INCLUDE[lserver](../../../includes/lserver-md.md)], modul snap-in konzoly MMC naleznete kliknutím **spustit** tlačítko a zadáním příkazu v `dcomcnfg.exe` v **vyhledávání** pole. Po otevření konzoly MMC, přejděte na **Moje Computer\Distributed transakce Coordinator\Local DTC** uzel, klikněte pravým tlačítkem a vyberte **vlastnosti**. Možnosti, které jsou k dispozici ke konfiguraci jsou seskupené v rámci **WS-AT** kartě.  
  
 Předchozí kroky jsou použitý ke spuštění modulu snap-in pro konfiguraci místního počítače. Pokud chcete nakonfigurovat vzdálený počítač, byste měli vyhledat název vzdáleného počítače v **součást Tools panelech řízení služby nebo**a proveďte podobným způsobem, pokud používáte [!INCLUDE[wxp](../../../includes/wxp-md.md)] nebo [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Pokud používáte systém Windows Vista nebo [!INCLUDE[lserver](../../../includes/lserver-md.md)], postupujte podle předchozích kroků pro Vista a [!INCLUDE[lserver](../../../includes/lserver-md.md)], ale použít **Distribuovaných transakcí Coordinator\Local** uzlu pod uzlem vzdáleného počítače.  
  
 Chcete-li použít uživatelské rozhraní, poskytuje nástroje, budete muset zaregistrovat WsatUI.dll souboru, který se nachází v následující cestě,  
  
 **%ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 Registrace lze provést pomocí následujícího příkazu.  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 Tento nástroj můžete upravit nastavení základního WS-AtomicTransaction. Například můžete povolit a zakázat podpory protokolu WS-AtomicTransaction, nakonfigurovat porty HTTP pro WS-AT, vazby certifikátu SSL pro HTTP port, konfigurace certifikátů zadáním názvy předmětu certifikátu, vybrat režim trasování a nastavení výchozí a maximální počet časových limitů.  
  
 Pokud nakonfigurujete musí podpory protokolu WS-AtomicTransaction pouze v místním počítači, můžete použít příkaz verze tohoto nástroje. [!INCLUDE[crabout](../../../includes/crabout-md.md)]nástroje příkazového řádku najdete v článku [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md) tématu.  
  
 Je třeba si uvědomit, že jak modul Snap-in konzoly MMC a nástroje příkazového řádku nepodporují nastavení WS-AT. Tato nastavení lze upravit pouze pomocí úpravy registru přímo. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Tato nastavení registru najdete v části [konfigurace podpory WS-Atomic Transactions](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
### <a name="user-interface-description"></a>Popis rozhraní uživatele  
 **Povolit podporu sítě WS-Atomic Transactions**:  
  
 Přepnutím toto políčko povolí nebo zakáže všechny součásti grafické uživatelské rozhraní modulu snap-in.  
  
 Předtím, než toto políčko zaškrtnete, měli byste si ověřit, povolení síťového přístupu s příchozí nebo odchozí komunikace, nebo obojí. Tuto hodnotu můžete ověřit v **zabezpečení** kartě modul snap-in služby MS DTC.  
  
#### <a name="network-group-box"></a>Pole skupiny v síti  
 Ve skupině sítě můžete zadat HTTPS port a další bezpečnostní nastavení, jako například šifrování SSL. Tuto skupinu je zakázaná (šedě) Pokud není povoleno síťových transakcí koordinátoru DTC.  
  
 **HTTPS Port**  
  
 Toto je hodnota portu HTTPS používá pro WS-AT. Hodnota musí být číslo v rozsahu 1 – 65 535 (představoval platný port). Změna HTTP Port upraví konfiguraci služby protokolu HTTP, to znamená, že vydání použitých adresu služby WS-AT a nová adresa služby WS-AT je zaregistrována na základě na nový port. Kromě toho nově vybraný port je šifrován aktuálně vybraný certifikát pro šifrování SSL.  
  
> [!NOTE]
>  Pokud jste povolili již bránu firewall před spuštěním tohoto nástroje, port se automaticky registruje v seznamu výjimek. Pokud brána firewall je zakázáno před spuštěním tohoto nástroje, žádné další je nakonfigurován týkající se brány firewall.  
  
 Pokud povolíte bránu firewall po dokončení konfigurace služby WS-AT, je nutné spustit tento nástroj znovu a zadejte číslo portu pomocí tohoto parametru. Pokud zakážete po dokončení konfigurace brány firewall, WS-AT i nadále fungovat bez další vstup.  
  
 **Certifikát koncového bodu**  
  
 Kliknutím **vyberte** tlačítko zobrazí seznam aktuálně k dispozici certifikáty v místním počítači, které uživateli umožňují vyberte certifikát, který lze použít pro šifrování SSL. Certifikáty, musí mít privátní klíč. Jinak obdržíte chybovou zprávu.  
  
> [!NOTE]
>  Když nastavíte certifikát protokolu SSL pro vybraný port, můžete přepsat původní certifikát SSL přidružený tento port, pokud existuje.  
  
 **Autorizovaných účtů**  
  
 Kliknutím **vyberte** tlačítko vyvolá editor seznamu řízení přístupu Windows, kde můžete určit uživatele nebo skupinu, které mohou být zahrnuty v WS-Atomic transakce kontrolou **povolit** nebo **Odepřít** pole **účast** skupině oprávnění.  
  
 **Autorizovaný certifikáty**  
  
 Kliknutím **vyberte** tlačítko zobrazí seznam aktuálně dostupných certifikátů na LocalMachine. Pak můžete vybrat, která certifikát identity jsou povoleny zapojit se do protokolu WS-Atomic transakce.  
  
#### <a name="timeout-group-box"></a>Časový limit skupinový rámeček  
 **Časový limit** skupinový rámeček umožňuje zadat výchozí a maximální časový limit pro WS-Atomic Transactions. Platná hodnota pro odchozí časový limit je mezi 1 a 3600. Platná hodnota pro příchozí časový limit je mezi 0 a 3600.  
  
#### <a name="tracing-and-logging-group-box"></a>Trasování a protokolování skupinový rámeček  
 **Trasování a protokolování** skupiny pole umožňuje nakonfigurovat požadované trasování a úroveň protokolování.  
  
 Kliknutím **možnosti** tlačítko vyvolá stránky, kde můžete určit další nastavení.  
  
 **Úroveň trasování** kombinace pole umožňuje výběr z jakékoli platná hodnota <xref:System.Diagnostics.TraceLevel> výčtu. Zaškrtávací políčka můžete také použít k určení, zda chcete provést trasování aktivit, rozšíření aktivity nebo shromažďovat osobní identifikovatelné údaje.  
  
 Můžete také zadat protokolování relací v **protokolování relace** skupinový rámeček.  
  
> [!NOTE]
>  Pokud jiný příjemce trasování používá zprostředkovatel trasování WS-AT, nelze vytvořit novou relaci protokolování pro trasování událostí. Pokusy o konfiguraci protokolování během této doby výsledků v chybové zprávě "se nepodařilo povolit zprostředkovatele. Kód chyby: 1".  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]trasování a protokolování, najdete v části [Správa a Diagnostika](../../../docs/framework/wcf/diagnostics/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace podpory protokolu WS-Atomic Transactions](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)  
 [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)  
 [Správa a Diagnostika](../../../docs/framework/wcf/diagnostics/index.md)
