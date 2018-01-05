---
title: "Směrovací služba"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
caps.latest.revision: "13"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7214a14b11ae1f91906c8d2140bc82836988390
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="routing-service"></a>Směrovací služba
Služba Směrování je obecný prostředník SOAP, který funguje jako směrovač zpráv. Základní funkce služby směrování je umožňuje směrovat zprávy na základě obsahu zprávy, která umožňuje zprávu, která se předají do koncového bodu klienta na základě hodnoty v rámci samotné, zprávy v záhlaví nebo textu zprávy.  
  
 <xref:System.ServiceModel.Routing.RoutingService> Je implementovaný jako [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby v <xref:System.ServiceModel.Routing> oboru názvů. Směrovací služby vystavuje jeden nebo více koncových bodů služby které přijímají zprávy a pak trasy každou zprávu na jeden nebo více koncových bodů klienta na základě obsahu zprávy. Služba poskytuje následující funkce:  
  
-   Na základě obsahu směrování  
  
    -   Služby agregace  
  
    -   Správa verzí služeb  
  
    -   Směrování s prioritou  
  
    -   Dynamické konfigurace  
  
-   Protokol přemostění  
  
-   Zpracování protokolu SOAP  
  
-   Pokročilé zpracování chyb  
  
-   Zálohování koncové body  
  
 I když je možné vytvořit zprostředkující služby, který má jeden nebo více těchto cílů, často takové implementace je vázaný na konkrétní scénář nebo řešení a nelze snadno použít pro nové aplikace.  
  
 Služba směrování poskytuje obecné, dynamicky Konfigurovatelný a modulární zprostředkovatel SOAP, který je kompatibilní s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby a kanál modelů a umožňuje provádět na základě obsahu směrování založený na protokolu SOAP zprávy.  
  
> [!NOTE]
>  Služba Směrování nepodporuje aktuálně směrování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby REST.  Ke směrování volání REST, zvažte použití <xref:System.Web.Routing> nebo [směrování žádostí na aplikace](http://go.microsoft.com/fwlink/?LinkId=164589) (http://go.microsoft.com/fwlink/?LinkId=164589).  
  
## <a name="content-based-routing"></a>Na základě obsahu směrování  
 Umožňuje směrovat zprávy založené na jednu nebo více hodnot, které jsou součástí zprávy je založená na obsahu směrování. Směrovací služby kontroluje každou zprávu a trasy ho do cílového koncového bodu na základě obsah zprávy a směrování logiku, které vytvoříte. Na základě obsahu směrování poskytuje základ pro služby agregace, Správa verzí služeb a s prioritou směrování.  
  
 Implementace založená na obsahu směrování, směrovací služby závisí na <xref:System.ServiceModel.Dispatcher.MessageFilter> implementace, které se používají tak, aby odpovídaly konkrétní hodnoty v rámci zpráv směrování. Pokud **MessageFilter** odpovídá zprávu, zpráva se směruje na cílový koncový bod přidružené **MessageFilter**.  Filtry zpráv se seskupují do filtru tabulky (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) k vytvoření komplexní logiku směrování. Tabulku filtru může například obsahovat pět filtry vzájemně se vylučuje zpráv, které způsobí zpráv k odeslání do pouze jeden z pěti cílové koncové body.  
  
 Směrovací služby umožňuje konfigurovat logiku, která se používá k provedení na základě obsahu směrování, jakož i dynamicky aktualizovat směrování logiku za běhu.  
  
 Prostřednictvím seskupení filtry zpráv do filtru tabulky směrování logiku lze sestavit umožňující zpracování více směrování scénářů, jako například:  
  
-   Služby agregace  
  
-   Správa verzí služeb  
  
-   Směrování s prioritou  
  
-   Dynamické konfigurace  
  
 Další informace o filtry zpráv a filtru tabulky najdete v tématu [směrování ÚVOD](../../../../docs/framework/wcf/feature-details/routing-introduction.md) a [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
### <a name="service-aggregation"></a>Služby agregace  
 Pomocí směrování na základě obsahu můžete vystavit jeden koncový bod, který přijímá zprávy od externích klientských aplikací a pak směruje každou zprávu do příslušné založená na hodnotě v rámci zpráva Vnitřní koncový bod. To je užitečné nabízet jeden konkrétní koncový bod pro celou řadu back-end aplikace a také k dispozici jeden koncový bod aplikace při řešení vaší aplikace do řady služeb zákazníkům.  
  
### <a name="service-versioning"></a>Verze služby  
 Při migraci na novou verzi vašeho řešení, možná budete muset zachovat předchozí verzi paralelně pro existující zákazníků. Často to vyžaduje, aby klienti připojení na novější verzi, musíte použít jinou adresu při komunikaci s řešením. Směrovací služby umožňuje vystavit jeden koncový bod služby, který obsluhuje obě verze vašeho řešení pomocí směrování zpráv do příslušné řešení podle specifické pro verzi informací obsažených ve zprávě. Příkladem takových implementace naleznete v části [postupy: Správa verzí služeb](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
### <a name="priority-routing"></a>Směrování s prioritou  
 Při poskytování služby pro více klientů, mohou mít smlouvu o úrovni služeb (SLA) s někteří partneři, které vyžaduje všechna data z těchto partnerů mají být zpracovány odděleně od jiných klientů. Pomocí filtru, který vyhledá informace o zákazníkovi, které jsou součástí zprávy je možné snadno směrovat zprávy z konkrétní partnery pro koncový bod, který byl vytvořen splnění jejich SLA.  
  
## <a name="dynamic-configuration"></a>Dynamické konfigurace  
 Pro podporu důležité systémy, kde zprávy musí být zpracována bez žádné přerušení služby, je důležité, že nebudete moct změnit konfiguraci součásti v rámci systému za běhu. Pro podporu tohoto požadavku, nabízí směrovací služby <xref:System.ServiceModel.IExtension%601> implementace <xref:System.ServiceModel.Routing.RoutingExtension>, což umožňuje dynamické aktualizaci konfigurace směrování služby za běhu.  
  
 Další informace o dynamické konfigurace služby směrování najdete v tématu [směrování ÚVOD](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="protocol-bridging"></a>Protokol přemostění  
 Jedním z problémů v zprostředkující scénáře je, že vnitřních koncových bodů může mít různé přenosové nebo požadavky na verzi protokolu SOAP než koncového bodu, který na jsou přijaty zprávy. Pro podporu tohoto scénáře, můžete službu Směrování přemostění protokoly, včetně zpracování zprávu protokolu SOAP, která se <xref:System.ServiceModel.Channels.MessageVersion> vyžadovanou koncové cílové. Tímto způsobem jeden protokol slouží pro interní komunikaci, zatímco jiné lze použít pro externí komunikaci.  
  
 Pro podporu směrování zpráv mezi koncovými body s jinou přenosy, používá služba Směrování vazby poskytované systémem, které umožňují službě přemostění odlišné protokoly. K tomu dojde automaticky při koncový bod služby, které jsou vystavené směrovací služby používá jiný protokol než koncové body klientů, které jsou směrovány zprávy.  
  
## <a name="soap-processing"></a>Zpracování protokolu SOAP  
 Běžné směrování požadavek je umožňuje směrovat zprávy mezi koncovými body s odlišnými požadavky protokolu SOAP. Pro podporu tento požadavek, poskytuje službu Směrování <xref:System.ServiceModel.Routing.SoapProcessingBehavior> , automaticky vytvoří nový **verze MessageVersion** , která splňuje požadavky na cílového koncového bodu předtím, než je zpráva směrována na ni. Toto chování také vytvoří novou **verze MessageVersion** pro jakékoli zprávy odpovědi před jeho vrácením aplikace vznášející požadavek klienta, abyste ověřili, že **verze MessageVersion** odpovědi se shoduje s původní žádost.  
  
 Další informace o protokolu SOAP zpracování najdete v tématu [směrování ÚVOD](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="error-handling"></a>Zpracování chyb  
 V systému, který se skládá z distribuované služby, které jsou závislé na síťové komunikace je důležité zajistit, že komunikace v rámci vašeho systému, které jsou odolné vůči selhání přechodný síťový.  Směrovací služby implementuje zpracování chyb, které umožňuje zpracovat mnoha scénářích selhání komunikace, které jinak může dojít k výpadku služby.  
  
 Pokud zaznamená službu Směrování <xref:System.ServiceModel.CommunicationException> při pokusu o odeslání zprávy, bude zpracování chyb probíhat.  Tyto výjimky typicky značí, že došlo k potížím při pokusu o komunikaci s koncového bodu definovaného klienta, například <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, nebo <xref:System.ServiceModel.CommunicationObjectFaultedException>.  Kód pro ošetření chyb rovněž catch a pokus opakujte při odesílání **TimeoutException** dojde, což je další běžné výjimku, který není odvozen od **communicationexception –**.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Chyba při zpracování úloh, naleznete v [směrování ÚVOD](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="backup-endpoints"></a>Zálohování koncové body  
 Kromě cílové koncové body klientů spojené s každou definici filtru ve filtru tabulky můžete také vytvořit seznam zálohování koncových bodů, které se zpráva bude směrovat na selhání přenosu. Pokud dojde k chybě a seznam zálohování je definován pro položku filtru, směrovací služby se pokusí odeslat zprávu na první koncový bod definované v seznamu. Pokud tento přenos pokus selže, služby zkuste další koncový bod a tento proces pokračovat, dokud se pokus o přenos úspěšně, vrátí že chybu související jiný přenos nebo všechny koncové body v záložním seznamu, aby vrátil chybu přenosu.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]zálohování koncové body, najdete v části [směrování ÚVOD](../../../../docs/framework/wcf/feature-details/routing-introduction.md) a [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
## <a name="streaming"></a>streamování  
 Služba směrování může úspěšně stream zpráv, pokud jste nastavili vazby pro podporu streamování.  Existují však některé podmínky, za kterých zprávy muset uložená do vyrovnávací paměti:  
  
-   Vícesměrové vysílání (vyrovnávací paměti k vytvoření kopie další zpráva)  
  
-   Převzetí služeb při selhání (vyrovnávací paměti v případě, kdy musí zpráva k odeslání do zálohy)  
  
-   System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly hodnotu false (vyrovnávací paměť k dispozici MessageFilterTable pomocí něho třídu MessageBuffer tak, aby filtry můžete prohlédnout text)  
  
-   Dynamické konfigurace  
  
## <a name="see-also"></a>Viz také  
 [Úvod do směrování](../../../../docs/framework/wcf/feature-details/routing-introduction.md)  
 [Kontrakty pro směrování](../../../../docs/framework/wcf/feature-details/routing-contracts.md)  
 [Filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md)
