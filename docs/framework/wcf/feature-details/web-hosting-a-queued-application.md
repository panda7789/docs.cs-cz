---
title: Webhosting frontové aplikace
ms.date: 03/30/2017
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
ms.openlocfilehash: aa50b3b66230930f9553d6f0238b0a5f9178f7a5
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297410"
---
# <a name="web-hosting-a-queued-application"></a>Webhosting frontové aplikace
Služby Aktivace procesu Windows (WAS) spravuje aktivace a dobu života pracovních procesů, které obsahují tento hostitel služby Windows Communication Foundation (WCF) aplikace. Model zpracování služby WAS zobecňuje [!INCLUDE[iis601](../../../../includes/iis601-md.md)] model procesu pro server HTTP odebráním závislosti na protokolu HTTP. To umožňuje službám WCF pomocí protokolu HTTP a jiných protokolů než HTTP, jako je například net.msmq a msmq.formatname v hostitelském prostředí, který podporuje aktivaci založenou na zprávách a nabízí schopnost hostovat velký počet aplikací v daném počítači.  
  
 BYL zahrnuje služba Aktivace řízení front zpráv (MSMQ), která aktivuje frontové aplikace, když jeden nebo více zpráv jsou umístěné v jednom z fronty v aplikaci použít. Aktivační služba MSMQ je služba NT se automaticky spustí ve výchozím nastavení.  
  
 Další informace o WAS a jeho výhodách najdete v tématu [hostování v aktivační službě procesů Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md). Další informace o MSMQ najdete v tématu [fronty – přehled](../../../../docs/framework/wcf/feature-details/queues-overview.md).
  
## <a name="queue-addressing-in-was"></a>Fronty adresování ve WAS  
 BYLO, že aplikace k dispozici identifikátor URI (Uniform Resource) adres. Aplikace adresy mít dvě části: základní identifikátor URI předponu a specifické pro aplikaci, relativní adresa (cesta). Tyto dvě části zadejte externí adresu aplikace, když propojeny. Základní identifikátor URI předponu je vytvořen z vazby webu a používá se pro všechny aplikace v rámci webu, například "net.msmq://localhost", "msmq.formatname://localhost" nebo "NET.TCP://localhost". Aplikace adresy jsou pak vytvořeny pomocí fragmentů cesty specifické pro aplikaci (například "/ applicationOne") a připojení k základní identifikátor URI předponu můžete přejít na úplný identifikátor URI aplikace, například "net.msmq://localhost/applicationOne".  
  
 Aktivační služba MSMQ používá identifikátor URI aplikace tak, aby odpovídaly frontě aktivační služba MSMQ musí sledovat pro zprávy. Při zahájení aktivace služby MSMQ, vypíše všechny veřejné a privátní fronty v počítači je nakonfigurovaný pro příjem z a monitoruje jejich zprávy. Každých 10 minut, aktivace služby MSMQ aktualizuje seznam front pro monitorování. Po nalezení zprávu ve frontě aktivační služby odpovídá názvu fronty na nejdelší odpovídající identifikátor URI aplikace pro vazbu net.msmq a aktivuje aplikace.  
  
> [!NOTE]
>  Aplikace aktivované musí odpovídat předponu názvu fronty (nejdelší shody).  
  
 Například je název fronty: msmqWebHost/orderProcessing/service.svc. Pokud má aplikace 1 /msmqWebHost/orderProcessing virtuální adresář s service.svc pod ním a 2 aplikace má /msmqWebHost virtuálního adresáře pomocí orderProcessing.svc pod ním, se aktivuje aplikace 1. Pokud se odstraní aplikace 1, 2 aplikace se aktivuje.  
  
> [!NOTE]
>  Když se do fronty, všechny zprávy odeslané do ní neaktivovat aplikaci až do aktivace služby MSMQ aktualizuje seznam front, což je maximálně 10 minut od okamžiku vytvoření fronty. Restartuje se služba Aktivace aktualizuje seznamu fronty.  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a>Efekt privátní a veřejné fronty adresování  
 Aktivační služba MSMQ nerozlišuje mezi monitorování privátní a veřejné fronty. V důsledku toho nemůže mít veřejné a soukromé fronty se stejným názvem. Pokud tak učiníte, může aplikace hostované webové aktivovat pomocí kteréhokoli z fronty pro čtení.  
  
### <a name="queue-configuration-for-activation"></a>Konfigurace fronty pro aktivaci  
 Aktivační služba MSMQ spouští jako síťová služba. Je služba, která monitoruje fronty k aktivaci aplikací. Pro ni k aktivaci aplikací z fronty musíte zadat fronty NETWORK SERVICE přístup ke prohlížet zprávy ve svém seznamu řízení přístupu (ACL).  
  
### <a name="poison-messaging"></a>Zacházení s nezpracovatelnými zasílání zpráv  
 Nezpracovatelná zpráva byla zpracování ve službě WCF zařizuje služba kanál, který nejen zjistí, že zprávy je poškozen, ale vybere dispozice v závislosti na konfiguraci uživatele. Ve frontě je proto do jedné zprávy. Hostované webové aplikace zruší po sobě jdoucích časy a zpráva bude přesunuta do fronty zkuste to znovu. V okamžiku, závisí zpoždění opakování cyklu zpráva bude přesunuta z fronty opakování do hlavní fronty a akci opakujte. Ale to vyžaduje, aby kanálu ve frontě jako aktivní. Pokud aplikace je recyklovány WAS, pak zpráva zůstane ve frontě opakovat až do další zpráva dorazí do hlavní fronty k aktivaci frontové aplikace. Alternativním řešením je v tomto případě přesuňte zprávu ručně z fronty opakování zpět do hlavní fronty se znovu aktivovat aplikace.  
  
### <a name="subqueue-and-system-queue-caveat"></a>Dílčí fronty a systému fronty výstrahou  
 Aplikace hostovaná služba WAS nejde aktivovat na základě zpráv ve frontě systému, jako jsou fronty nedoručených zpráv pro celý systém nebo dílčí fronty, jako jsou poškozené dílčí fronty. Jedná se o omezení pro tuto verzi produktu.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [Koncové body služby a adresování front](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
