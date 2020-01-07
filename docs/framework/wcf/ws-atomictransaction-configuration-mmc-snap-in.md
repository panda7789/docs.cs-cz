---
title: Modul snap-in konzoly MMC WS-AtomicTransaction Configuration
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: 04f9a014c3cb3ffd127ccc82fdda731e20136c52
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544643"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>Modul snap-in konzoly MMC WS-AtomicTransaction Configuration
Modul snap-in konzoly MMC pro konfiguraci WS-AtomicTransaction se používá ke konfiguraci části Nastavení WS-AtomicTransaction na místních i vzdálených počítačích.  
  
## <a name="remarks"></a>Poznámky  
 Pokud používáte [!INCLUDE[wxp](../../../includes/wxp-md.md)] nebo Windows Server 2003, modul snap-in konzoly MMC můžete najít tak, že přejdete na **Ovládací panely nebo nástroje pro správu/služby komponent/** , kliknete pravým tlačítkem na položku **Tento počítač**a vyberete **vlastnosti**. Toto je stejné umístění, kde můžete nakonfigurovat MSDTC. Možnosti, které jsou k dispozici pro konfiguraci, jsou seskupeny na kartě **WS-AT** .  
  
 Pokud používáte systém Windows Vista nebo Windows Server 2008, modul snap-in konzoly MMC lze najít kliknutím na tlačítko **Start** a zadáním `dcomcnfg.exe` do **vyhledávacího** pole. Po otevření konzoly MMC přejděte do uzlu **Computer\Distributed Transaction COORDINATOR\LOCAL DTC** , klikněte pravým tlačítkem a vyberte **vlastnosti**. Možnosti, které jsou k dispozici pro konfiguraci, jsou seskupeny na kartě **WS-AT** .  
  
 Pomocí předchozích kroků můžete spustit modul snap-in pro konfiguraci místního počítače. Pokud chcete nakonfigurovat vzdálený počítač, měli byste najít název vzdáleného počítače v **Ovládacích panelech/nástrojích pro správu/služby komponent/** a provést podobný postup, pokud používáte [!INCLUDE[wxp](../../../includes/wxp-md.md)] nebo Windows Server 2003. Pokud používáte systém Windows Vista nebo Windows Server 2008, postupujte podle předchozích kroků pro Vista a Windows Server 2008, ale použijte uzel **DTC (Distributed Transaction Coordinator\Local DTC** ) pod uzlem vzdáleného počítače.  
  
 Chcete-li použít uživatelské rozhraní poskytované nástrojem, je nutné zaregistrovat soubor WsatUI. dll, který je umístěn v následující cestě.  
  
 **%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 Registraci lze provést pomocí následujícího příkazu.  
  
```console
regasm.exe /codebase WsatUI.dll  
```  
  
 Pomocí tohoto nástroje můžete změnit základní nastavení WS-AtomicTransaction. Můžete například povolit a zakázat podporu protokolu WS-AtomicTransaction, nakonfigurovat porty HTTP pro protokol WS-AT, vytvořit propojení certifikátu SSL s portem HTTP, nakonfigurovat certifikáty zadáním názvů subjektů certifikátů, vybrat režim trasování a nastavit výchozí a maximální časové limity.  
  
 Pokud je nutné nakonfigurovat podporu WS-AtomicTransaction pouze v místním počítači, můžete použít verzi tohoto nástroje příkazového řádku. Další informace o nástroji příkazového řádku najdete v tématu věnovaném [nástroji pro konfiguraci WS-AtomicTransaction (WsatConfig. exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md) .  
  
 Měli byste si uvědomit, že modul snap-in konzoly MMC i nástroj příkazového řádku nepodporují konfiguraci všech nastavení WS-AT. Tato nastavení lze upravovat pouze úpravou registru přímo. Další informace o těchto nastaveních registru najdete v tématu [Konfigurace podpory transakcí WS-Atomic](./feature-details/configuring-ws-atomic-transaction-support.md).  
  
### <a name="user-interface-description"></a>Popis uživatelského rozhraní  
 **Povolit podporu sítě WS-Atomic Transaction Network**:  
  
 Přepnutím tohoto zaškrtávacího políčka povolíte nebo zakážete všechny součásti grafického uživatelského rozhraní tohoto modulu snap-in.  
  
 Než toto políčko zaškrtnete, měli byste se ujistit, že je povolen přístup k síti DTC pomocí příchozí nebo odchozí komunikace, nebo obojí. Tuto hodnotu lze ověřit na kartě **zabezpečení** v modulu snap-in MSDTC.  
  
#### <a name="network-group-box"></a>Pole Síťová skupina  
 V síťové skupině můžete zadat port HTTPS a další nastavení zabezpečení, například šifrování SSL. Tato skupina je zakázaná (šedá), pokud nejsou povolené síťové transakce DTC.  
  
 **Port HTTPS**  
  
 Toto je hodnota portu HTTPS používaného pro WS-AT. Hodnota musí být číslo v rozsahu 1-65535 (představující platný port). Změna portu HTTP změní konfiguraci služby HTTP, což znamená, že byla uvolněna dříve použitá adresa WS-AT a na základě nového portu je zaregistrována nová adresa služby WS-AT. Nově vybraný port je navíc zašifrovaný s aktuálně vybraným certifikátem pro šifrování SSL.  
  
> [!NOTE]
> Pokud jste už bránu firewall povolili před spuštěním tohoto nástroje, port se automaticky zaregistruje v seznamu výjimek. Je-li brána firewall před spuštěním tohoto nástroje zakázána, není pro bránu firewall konfigurována žádná další konfigurace.  
  
 Pokud bránu firewall povolíte po konfiguraci WS-AT, musíte znovu spustit tento nástroj a zadejte číslo portu pomocí tohoto parametru. Pokud bránu firewall po konfiguraci zakážete, bude WS-AT nadále fungovat bez dalšího vstupu.  
  
 **Certifikát koncového bodu**  
  
 Kliknutím na tlačítko **Vybrat** se zobrazí seznam s aktuálně dostupnými certifikáty v místním počítači, který uživateli umožňuje vybrat certifikát, který se dá použít pro šifrování SSL. Certifikáty musí mít privátní klíč. V opačném případě se zobrazí chybová zpráva.  
  
> [!NOTE]
> Když nastavíte certifikát SSL pro vybraný port, přepíšete původní certifikát SSL přidružený k tomuto portu, pokud existuje.  
  
 **Autorizované účty**  
  
 Kliknutím na tlačítko **Vybrat** vyvoláte editor seznamu Access Control Windows, kde můžete zadat uživatele nebo skupinu, které se mohou účastnit transakcí WS-Atomic zaškrtnutím políčka **Povolit** nebo **Odepřít** ve skupině oprávnění **účasti** .  
  
 **Autorizované certifikáty**  
  
 Kliknutím na tlačítko **Vybrat** se zobrazí seznam aktuálně dostupných certifikátů na LocalMachine. Pak můžete vybrat, které identity certifikátu se můžou zúčastnit v transakcích WS-Atomic.  
  
#### <a name="timeout-group-box"></a>Pole časový limit skupiny  
 Skupinový rámeček **časový limit** umožňuje zadat výchozí a maximální časový limit pro transakci WS-Atomic. Platná hodnota odchozího časového limitu je mezi 1 a 3600. Platná hodnota příchozího časového limitu je mezi 0 a 3600.  
  
#### <a name="tracing-and-logging-group-box"></a>Pole skupiny trasování a protokolování  
 Skupinový rámeček **trasování a protokolování** vám umožní nakonfigurovat požadované trasování a úroveň protokolování.  
  
 Kliknutím na tlačítko **Možnosti** aktivujete stránku, kde můžete zadat další nastavení.  
  
 Pole se kombinací **úrovně trasování** umožňuje vybrat libovolnou platnou hodnotu výčtu <xref:System.Diagnostics.TraceLevel>. Pomocí zaškrtávacích políček můžete také určit, jestli chcete provádět trasování aktivit, šíření aktivit nebo shromažďovat osobní údaje.  
  
 Můžete také zadat relace protokolování do pole Skupina **relace protokolování** .  
  
> [!NOTE]
> Když jiný příjemce trasování používá poskytovatele trasování WS-AT, nemůžete vytvořit novou relaci protokolování pro události trasování. Při každém pokusu o konfiguraci protokolování během této doby se zobrazí chybová zpráva s oznámením o povolení poskytovatele. Kód chyby: 1 ".  
  
 Další informace o trasování a protokolování najdete v tématu [Správa a diagnostika](./diagnostics/index.md).  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace podpory protokolu WS-AtomicTransaction](./feature-details/configuring-ws-atomic-transaction-support.md)
- [Nástroj pro konfiguraci WS-AtomicTransaction (wsatConfig.exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [Správa a diagnostika](./diagnostics/index.md)
