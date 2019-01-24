---
title: Směrovací služba
ms.date: 03/30/2017
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
ms.openlocfilehash: b0d58e70d482532e3f148d3f4f92741f46221982
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495302"
---
# <a name="routing-service"></a>Směrovací služba
Směrovací služba je obecný zprostředkovatele protokolu SOAP, která funguje jako směrovač zprávy. Základní funkce služby směrování je schopnost trasy zpráv na základě obsahu zprávy, což umožní zprávy mají být předány koncový bod klienta na základě hodnoty v rámci samotné, zprávy v záhlaví nebo textu zprávy.  
  
 <xref:System.ServiceModel.Routing.RoutingService> Je implementovaný jako služba Windows Communication Foundation (WCF) v <xref:System.ServiceModel.Routing> oboru názvů. Směrovací služba zpřístupňuje jeden nebo více koncových bodů služby, které přijímají zprávy a poté trasy každou zprávu na jeden nebo více koncových bodů klienta na základě obsahu zprávy. Služba poskytuje následující funkce:  
  
-   Směrování na základě obsahu  
  
    -   Služby agregace  
  
    -   Správa verzí služby  
  
    -   Priorita směrování  
  
    -   Dynamickou konfiguraci  
  
-   Protokol přemostění  
  
-   Zpracování SOAP  
  
-   Pokročilé zpracování chyb  
  
-   Zálohování koncových bodů  
  
 I když je možné vytvořit zprostředkující služba, která provádí jeden nebo více těchto cílů, často takové implementace se váže na konkrétní scénář nebo řešení a nedá se použít snadno do nových aplikací.  
  
 Směrovací služba poskytuje obecné, dynamicky konfigurovat, modulární zprostředkovatel SOAP, který je kompatibilní s modely kanálu a služby WCF a je možné provádět, směrování na základě obsahu zpráv založený na protokolu SOAP.  
  
> [!NOTE]
>  Směrovací služba nepodporuje aktuálně směrování služeb WCF REST.  Směrování volání REST, zvažte použití <xref:System.Web.Routing> nebo [směrování žádostí na aplikace](https://go.microsoft.com/fwlink/?LinkId=164589).  
  
## <a name="content-based-routing"></a>Směrování na základě obsahu  
 Umožňuje směrovat zprávy na základě hodnot jednoho nebo více součástí zprávy směrování na základě obsahu je. Směrovací služba zkontroluje každou zprávu a přesměruje ho do cílového koncového bodu podle obsah zpráv a směrování logika, kterou vytvoříte. Směrování na základě obsahu poskytuje základ pro služby agregace, Správa verzí služby a Priorita směrování.  
  
 Pokud chcete implementovat, směrování na základě obsahu, směrovací služba závisí na <xref:System.ServiceModel.Dispatcher.MessageFilter> implementace, které se používají tak, aby odpovídaly konkrétní hodnoty v rámci zpráv bude směrovat. Pokud **MessageFilter** shody zprávu, zpráva se směruje na cílový koncový bod přidružený k **MessageFilter**.  Filtry zpráv jsou seskupeny do filtru tabulky (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) k vytvoření komplexní logiku směrování. Například filtr tabulky mohou obsahovat pět filtry vzájemně se vylučující zpráv, které způsobují zprávy má být směrována na pouze jeden z pěti cílové koncové body.  
  
 Směrovací služby umožňuje konfigurovat logiku, která se používá k provedení směrování na základě obsahu, stejně jako v době běhu dynamicky aktualizovat logiku směrování.  
  
 Prostřednictvím seskupování filtry zpráv do filtru tabulky směrování logiky lze sestavit, který umožňuje zpracovávat více scénáře, jako:  
  
-   Služby agregace  
  
-   Správa verzí služby  
  
-   Priorita směrování  
  
-   Dynamickou konfiguraci  
  
 Další informace o filtrech zpráv a filtr tabulky najdete v tématu [směrování ÚVOD](../../../../docs/framework/wcf/feature-details/routing-introduction.md) a [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
### <a name="service-aggregation"></a>Služby agregace  
 Pomocí směrování na základě obsahu, můžete zveřejnit jeden koncový bod, který přijímá zprávy z externích klientských aplikací a potom na příslušný interní koncový bod na základě hodnoty v něm přesměruje každou zprávu. To je užitečné nabízet jeden konkrétní koncový bod pro různé back endové aplikace a také k dispozici jeden koncový bod aplikace pro zákazníky, při které budou zohledňovat aplikace do celé řady služeb.  
  
### <a name="service-versioning"></a>Verze služby  
 Při migraci na novou verzi vašeho řešení, bude pravděpodobně nutné udržovat stará verze souběžně s existující zákazníků. Často vyžaduje, aby klienti připojení k novější verzi, musíte použít jinou adresu při komunikaci s řešením. Směrovací služba umožňuje vystavit jeden koncový bod služby, který slouží obě verze vašeho řešení pomocí směrování zpráv do příslušné řešení založené na konkrétní verzi informace obsažené ve zprávě. Příklad takové implementace naleznete v tématu [How To: Správa verzí služby](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
### <a name="priority-routing"></a>Priorita směrování  
 Při poskytování služeb pro víc klientů, které máte uzavřeny smlouvy o úrovni služeb (SLA) s někteří partneři, které vyžaduje všechna data od těchto partnerů se zpracovávají odděleně od jiných klientů. Když použijete filtr, který hledá zákaznické informace obsažené ve zprávě, snadno zprávy budete směrovat od partnerů pro konkrétní do koncového bodu, která byla vytvořená za účelem vyhovuje jejich požadavkům na smlouvu SLA.  
  
## <a name="dynamic-configuration"></a>Dynamickou konfiguraci  
 Pro podporu zásadně důležitých systémů, kde je potřeba zpracovat zprávy bez případná přerušení služeb, je důležité, že budete moci změnit konfiguraci komponenty v rámci systému v době běhu. Tyto potřeby, směrovací služba podporuje <xref:System.ServiceModel.IExtension%601> implementace, <xref:System.ServiceModel.Routing.RoutingExtension>, který umožňuje dynamické aktualizaci konfigurace služby směrování v době běhu.  
  
 Další informace o dynamické konfigurace služby směrování najdete v tématu [směrování ÚVOD](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="protocol-bridging"></a>Protokol přemostění  
 Jedním z problémů v zprostředkující scénáře je, že koncovým bodům s interním může mít různé přenosové nebo požadavky na verzi protokolu SOAP než koncového bodu, který jsou zprávy přijímány. Pro podporu tohoto scénáře, směrovací služba dokáže Přemostit protokolů, jako jsou třeba zpracování zprávy protokolu SOAP <xref:System.ServiceModel.Channels.MessageVersion> vyžaduje určení koncových bodů. Tímto způsobem jeden protokol. slouží pro interní komunikaci, zatímco jiné lze použít pro externí komunikaci.  
  
 Pro podporu směrování zpráv mezi koncovými body s jinou přenosy, používá služba Směrování vazeb poskytovaných systémem, které umožňují službě přemostění rozdílných protokolů. Automaticky dojde při používá jiný protokol než koncových bodů klienta, které zprávy jsou směrovány na koncový bod služby, vystavený službou směrování.  
  
## <a name="soap-processing"></a>Zpracování SOAP  
 Běžné požadavky směrování je schopnost směrování zpráv mezi koncovými body s různými požadavky na SOAP. Splnění tohoto požadavku, poskytuje službu Směrování <xref:System.ServiceModel.Routing.SoapProcessingBehavior> , který automaticky vytvoří nový **MessageVersion** , který splňuje požadavky na cílového koncového bodu předtím, než se zpráva směruje do něj. Toto chování také vytvoří nový **MessageVersion** pro všechny zprávy s odpovědí před jeho vrácením žádající klientské aplikaci, ujistěte se, že **MessageVersion** odpovědi odpovídá původní požadavek.  
  
 Další informace o zpracování SOAP, naleznete v tématu [směrování ÚVOD](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="error-handling"></a>Zpracování chyb  
 V systému tvořený distribuované služby, které spoléhají na síťovou komunikaci je důležité zajistit této komunikaci v rámci vašeho systému, které jsou odolné vůči selhání přechodné sítě.  Směrovací služba implementuje zpracování chyb, který umožňuje zpracovávat mnoho scénáře selhání komunikace, které jinak může vést k výpadku služeb.  
  
 Pokud zjistí služba Směrování <xref:System.ServiceModel.CommunicationException> při pokusu o odeslání zprávy, bude zpracování chyb proběhnout.  Tyto výjimky obvykle signalizují, že došlo k potížím při pokusu o komunikaci s koncovým bodem definované klienta, například <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, nebo <xref:System.ServiceModel.CommunicationObjectFaultedException>.  Kód pro zpracování chyb také zachytit a pokus opakujte při odesílání **TimeoutException** dojde, což je další běžné výjimku, která není odvozena od **communicationexception –**.  
  
 Další informace o zpracování chyb, naleznete v tématu [směrování ÚVOD](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="backup-endpoints"></a>Zálohování koncových bodů  
 Kromě cílové koncové body klientů spojené s každou definici filtru v tabulce filtrů můžete také vytvořit seznam zálohování koncových bodů, které zprávy se budou směrovat na selhání přenosu. Pokud dojde k chybě a zálohování seznamu je definován pro položku filtr, směrovací služba se pokusí odeslat zprávu do první koncový bod definovaný v seznamu. Pokud tento přenos pokus selže, služba se pokusí další koncový bod a tomto procesu pokračovat, dokud nebude úspěšný pokus o přenos, vrátí že chybu související bez přenosu a všechny koncové body v seznamu záloh mají Vrácená chyba přenosu.  
  
 Další informace o zálohování koncových bodech, najdete v části [směrování ÚVOD](../../../../docs/framework/wcf/feature-details/routing-introduction.md) a [filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
## <a name="streaming"></a>Streamování  
 Služba Směrování úspěšně proudy zprávy Pokud nastavíte vazby podporovat datový proud.  Existují však některé podmínky, za kterých možná muset ukládány do vyrovnávací paměti zpráv:  
  
-   Vícesměrové vysílání (vyrovnávací paměti k vytvoření kopie další zpráva)  
  
-   Převzetí služeb při selhání (v takovém případě je zprávu zapotřebí k odeslání do zálohy vyrovnávací paměti)  
  
-   System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly má hodnotu false (předložit MessageFilterTable se namísto něho třídu MessageBuffer tak, aby filtry můžete kontrolovat obsah vyrovnávací paměti)  
  
-   Dynamickou konfiguraci  
  
## <a name="see-also"></a>Viz také:
- [Úvod do směrování](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
- [Kontrakty pro směrování](../../../../docs/framework/wcf/feature-details/routing-contracts.md)
- [Filtry zpráv](../../../../docs/framework/wcf/feature-details/message-filters.md)
