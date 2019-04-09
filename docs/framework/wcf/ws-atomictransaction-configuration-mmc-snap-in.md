---
title: Modul snap-in konzoly MMC WS-AtomicTransaction Configuration
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: b1d86fa57b31d1f9be12f76c28f9d042e7e28e24
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138201"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>Modul snap-in konzoly MMC WS-AtomicTransaction Configuration
Modul Snap-in konzoly MMC WS-AtomicTransaction konfigurace slouží ke konfiguraci část nastavení WS-AtomicTransaction na místních i vzdálených počítačích.  
  
## <a name="remarks"></a>Poznámky  
 Pokud používáte [!INCLUDE[wxp](../../../includes/wxp-md.md)] nebo [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], modul snap-in konzoly MMC najdete tak, že přejdete na **ovládací panely/pro správu nástroje/Component Services /**, pravým tlačítkem myši **tento počítač**, a Výběr **vlastnosti**. Toto je na stejném umístění, kde můžete konfigurovat příkaz MSDTC. Možnosti pro konfiguraci k dispozici jsou seskupené podle **WS-AT** kartu.  
  
 Pokud používáte systém Windows Vista nebo [!INCLUDE[lserver](../../../includes/lserver-md.md)], modul snap-in konzoly MMC najdete po kliknutí **Start** tlačítko a zadejte text `dcomcnfg.exe` v **hledání** pole. Při otevření konzoly MMC, přejděte **Moje Computer\Distributed transakce Coordinator\Local DTC** uzel, klikněte pravým tlačítkem myši a vyberte **vlastnosti**. Možnosti pro konfiguraci k dispozici jsou seskupené podle **WS-AT** kartu.  
  
 Spusťte modul snap-in pro konfiguraci místního počítače se používají v předchozích krocích. Pokud chcete konfigurovat vzdálený počítač, byste měli vyhledat název vzdáleného počítače v **ovládací panely/pro správu nástroje/Component Services /** a provedení podobných kroků, pokud používáte [!INCLUDE[wxp](../../../includes/wxp-md.md)] nebo [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Pokud používáte systém Windows Vista nebo [!INCLUDE[lserver](../../../includes/lserver-md.md)], postupujte podle předchozích kroků pro Vista a [!INCLUDE[lserver](../../../includes/lserver-md.md)], ale použít **Distribuovaných transakcí Coordinator\Local** uzel pod uzlem vzdáleného počítače.  
  
 Použití uživatelského rozhraní pomocí nástroje, je nutné provést registraci WsatUI.dll soubor, který je umístěný v následující cestě,  
  
 **%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 Registraci můžete provést pomocí následujícího příkazu.  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 Tento nástroj můžete použít k úpravě základního WS-AtomicTransaction nastavení. Například můžete povolit a zakázat podporu protokolu WS-AtomicTransaction, konfigurace portů HTTP pro WS-AT, vytvoření vazby certifikátu SSL na HTTP port, konfigurace certifikátů tak, že zadáte názvy předmětu certifikátů, vyberte režim trasování a nastavit výchozí a maximální časový limit.  
  
 Pokud podpora WS-AtomicTransaction musíte nakonfigurovat na místním počítači, můžete použít příkazový řádek verzi tohoto nástroje. Další informace o nástroj příkazového řádku, najdete v článku [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md) tématu.  
  
 Byste měli vědět, jak modul Snap-in konzoly MMC a nástroje příkazového řádku nepodporují všechna WS-AT nastavení konfigurace. Tato nastavení lze upravit pouze pomocí úpravy registru přímo. Další informace o těchto nastaveních registru najdete v tématu [konfigurace WS-Atomic podpora transakcí](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
### <a name="user-interface-description"></a>Popis uživatelské rozhraní  
 **Povolit podporu sítě WS-Atomic Transactions**:  
  
 Při přepínání toto zaškrtávací políčko povolí nebo zakáže všechny součásti grafické uživatelské rozhraní modulu snap-in.  
  
 Než toto políčko zaškrtnete, by se ujistěte, že je povolen přístup pomocí koordinátoru DTC sítě s příchozí nebo odchozí komunikace, nebo obojí. Tato hodnota se dá ověřit v **zabezpečení** kartu modulu snap-in služby MSDTC.  
  
#### <a name="network-group-box"></a>Network Group Box  
 Ve skupině sítě můžete zadat HTTPS port a nastavení dalšího ověření zabezpečení, jako je šifrování pomocí protokolu SSL. Tato skupina je zakázaný (šedě) Pokud transakcí koordinátoru DTC sítě nejsou povoleny.  
  
 **HTTPS Port**  
  
 Jedná se o hodnotu protokol HTTPS port používaný pro WS-AT. Hodnota musí být číslo v rozsahu 1-65535 (jde o představovat platný port). Změnit HTTP Port upraví konfiguraci služby HTTP, to znamená, že dříve použitých WS-AT služby Adresa se uvolní a nová adresa služby WS-AT zaregistrován v závislosti na nový port. Kromě toho nově vybraný port se šifrují pomocí aktuálně vybraného certifikátu pro šifrování SSL.  
  
> [!NOTE]
>  Pokud brána firewall povolíte už před spuštěním tohoto nástroje, port, který se automaticky registruje v seznamu výjimek. Pokud brána firewall je zakázaná před spuštěním tohoto nástroje, další není nic nakonfigurované týkající se brány firewall.  
  
 Pokud po nakonfigurování WS-AT povolíte bránu firewall, musíte tento nástroj znovu spustit a zadat číslo portu, který pomocí tohoto parametru. Pokud zakážete po dokončení konfigurace brány firewall, WS-AT i nadále fungovat bez další vstupy.  
  
 **Certifikát koncového bodu**  
  
 Kliknutím **vyberte** tlačítko zobrazuje seznam aktuálně dostupných certifikátů na místním počítači, které uživateli umožňují vybrat certifikát, který lze použít pro šifrování SSL. Certifikáty musí mít privátní klíč. V opačném případě se zobrazí chybová zpráva.  
  
> [!NOTE]
>  Při nastavení certifikátu SSL pro vybraný port přepsat původní certifikát SSL přidružený tento port, pokud existuje.  
  
 **Autorizovaných účtů**  
  
 Kliknutím **vyberte** tlačítko vyvolá editor seznamu řízení přístupu pro Windows, kde můžete určit uživatele nebo skupiny, které se mohou účastnit v WS-Atomic transactions kontrolou **povolit** nebo **Odepřít** pole **účast** oprávnění skupiny.  
  
 **Autorizované certifikáty**  
  
 Kliknutím **vyberte** tlačítku zobrazí seznam certifikátů, aktuálně k dispozici na mém. Pak můžete vybrat, které certifikát identity můžou účastnit WS-Atomic transactions.  
  
#### <a name="timeout-group-box"></a>Časový limit skupinový rámeček  
 **Vypršení časového limitu** skupinový rámeček umožňuje určit výchozí a maximální časový limit pro WS-Atomic Transactions. Platná hodnota pro odchozí časový limit je mezi 1 a 3600. Platná hodnota pro příchozí časový limit je mezi 0 a 3600.  
  
#### <a name="tracing-and-logging-group-box"></a>Trasování a protokolování skupinový rámeček  
 **Trasování a protokolování** skupiny pole umožňuje nakonfigurovat požadované trasování a úroveň protokolování.  
  
 Kliknutím **možnosti** tlačítko vyvolá stránku, kde můžete určit další nastavení.  
  
 **Úroveň trasování** kombinace pole umožňuje výběr z jakékoli platné hodnoty <xref:System.Diagnostics.TraceLevel> výčtu. Zaškrtávací políčka můžete také použít k určení, zda chcete provést trasování činnosti, šíření aktivity nebo shromažďovat osobní údaje.  
  
 Můžete také určit relace protokolování **protokolování relace** skupinovém rámečku.  
  
> [!NOTE]
>  Jestli používáte jiný příjemce trasování je zprostředkovatel trasování WS-AT, nelze vytvořit novou relaci protokolování pro trasování událostí. Jakýkoliv pokus o konfiguraci protokolování během této doby výsledkem chybová zpráva "Nepodařilo se povolit poskytovatele. Kód chyby: 1".  
  
 Další informace o trasování a protokolování, najdete v části [Správa a Diagnostika](../../../docs/framework/wcf/diagnostics/index.md).  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace podpory protokolu WS-AT (WS-Atomic Transactions)](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
- [Nástroj WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [Správa a diagnostika](../../../docs/framework/wcf/diagnostics/index.md)
