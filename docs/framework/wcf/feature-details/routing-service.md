---
title: Směrovací služba
ms.date: 03/30/2017
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
ms.openlocfilehash: 833c824e17d70a982a2f7bb13fe388b9b2b0dec1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590446"
---
# <a name="routing-service"></a>Směrovací služba

Směrovací služba je obecný prostředník SOAP, který funguje jako směrovač zpráv. Základní funkcí směrovací služby je schopnost směrovat zprávy na základě obsahu zpráv, což umožňuje přesměrovat zprávu na koncový bod klienta na základě hodnoty v samotné zprávě, a to buď v záhlaví, nebo v těle zprávy.

Rozhraní <xref:System.ServiceModel.Routing.RoutingService> je implementováno jako služba Windows Communication Foundation (WCF) v <xref:System.ServiceModel.Routing> oboru názvů. Směrovací služba zveřejňuje jeden nebo více koncových bodů služby, které obdrží zprávy, a pak každou zprávu přesměruje do jednoho nebo více koncových bodů klienta na základě obsahu zprávy. Služba poskytuje následující funkce:

- Směrování na základě obsahu

  - Agregace služeb

  - Správa verzí služeb

  - Směrování podle priority

  - Dynamická konfigurace

- Přemostění protokolů

- Zpracování SOAP

- Pokročilé zpracování chyb

- Koncové body zálohování

I když je možné vytvořit zprostředkující službu, která dosahuje jednoho nebo více těchto cílů, často taková implementace je svázána s konkrétním scénářem nebo řešením a nelze ji snadno použít pro nové aplikace.

Směrovací služba poskytuje obecnou, dynamicky konfigurovatelnou a připojitelná zprostředkující modul SOAP, který je kompatibilní se službou WCF a modely kanálů, a umožňuje provádět směrování zpráv založené na obsahu protokolu SOAP.

> [!NOTE]
> Směrovací služba v současné době nepodporuje směrování služeb WCF REST.  Pokud chcete směrovat volání REST, zvažte použití <xref:System.Web.Routing> nebo [Směrování žádostí o aplikace](https://go.microsoft.com/fwlink/?LinkId=164589).

## <a name="content-based-routing"></a>Směrování na základě obsahu

Směrování na základě obsahu je schopnost směrovat zprávu na základě jedné nebo více hodnot obsažených ve zprávě. Směrovací služba zkontroluje každou zprávu a směruje ji do cílového koncového bodu na základě obsahu zprávy a logiky směrování, kterou vytvoříte. Směrování na základě obsahu poskytuje základ pro agregaci služeb, správu verzí služeb a prioritní směrování.

K implementaci směrování založeného na obsahu se služba Směrování spoléhá na <xref:System.ServiceModel.Dispatcher.MessageFilter> implementace, které se používají k vyhledání konkrétních hodnot v rámci zpráv určených ke směrování. Pokud **MessageFilter** odpovídá zprávě, je zpráva směrována do cílového koncového bodu přidruženého k **MessageFilter**.  Filtry zpráv se seskupují do tabulek Filter ( <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection> ), aby se napracovala složitá logika směrování. Tabulka filtru může například obsahovat pět vzájemně vylučujících filtrů zpráv, které způsobují směrování zpráv pouze do jednoho z pěti cílových koncových bodů.

Směrovací služba umožňuje nakonfigurovat logiku, která se používá k provádění směrování založeného na obsahu, a také dynamicky aktualizovat logiku směrování za běhu.

Pomocí seskupení filtrů zpráv do tabulek filtrů můžete vytvořit logiku směrování, která umožňuje zpracovávat více scénářů směrování, například:

- Agregace služeb

- Správa verzí služeb

- Směrování podle priority

- Dynamická konfigurace

Další informace o filtrech zpráv a tabulkách filtru najdete v tématu [Úvod do směrování](routing-introduction.md) a [filtry zpráv](message-filters.md).

### <a name="service-aggregation"></a>Agregace služeb

Pomocí směrování založeného na obsahu můžete vystavit jeden koncový bod, který přijímá zprávy z externích klientských aplikací, a pak každou zprávu směrovat do příslušného interního koncového bodu na základě hodnoty ve zprávě. To je užitečné, pokud chcete nabízet jeden konkrétní koncový bod pro celou řadu back-endové aplikace a také k tomu, aby zákazníkům poskytovali jeden koncový bod aplikace a současně přidělil aplikaci do různých služeb.

### <a name="service-versioning"></a>Verze služby

Při migraci na novou verzi řešení je možné, že budete muset udržet starou verzi paralelně, aby sloužila stávajícím zákazníkům. To často vyžaduje, aby klienti připojující se k novější verzi používali při komunikaci s řešením jinou adresu. Směrovací služba umožňuje vystavit jeden koncový bod služby, který bude obsluhovat obě verze vašeho řešení, směrováním zpráv do příslušného řešení na základě informací, které jsou obsaženy ve zprávě. Příklad takové implementace naleznete v tématu [How to: Service Versioning](how-to-service-versioning.md).

### <a name="priority-routing"></a>Prioritní směrování

Když poskytujete službu pro více klientů, můžete mít smlouvu o úrovni služeb (SLA) s některými partnery, které vyžadují, aby se všechna data od těchto partnerů zpracovala odděleně od ostatních klientů. Pomocí filtru, který vyhledává informace specifické pro zákazníka obsažené ve zprávě, můžete snadno směrovat zprávy od konkrétních partnerů do koncového bodu, který byl vytvořen tak, aby splňoval požadavky smlouvy SLA.

## <a name="dynamic-configuration"></a>Dynamická konfigurace

Aby bylo možné podporovat klíčové systémy, ve kterých je nutné zpracovat zprávy bez přerušení služeb, je důležité, abyste v systému mohli v době běhu upravit konfiguraci součástí. Pro podporu této potřeby služba Směrování poskytuje <xref:System.ServiceModel.IExtension%601> implementaci, <xref:System.ServiceModel.Routing.RoutingExtension> která umožňuje dynamickou aktualizaci konfigurace směrovací služby v době běhu.

Další informace o dynamické konfiguraci směrovací služby najdete v tématu popisujícím [Úvod do směrování](routing-introduction.md).

## <a name="protocol-bridging"></a>Přemostění protokolů

Jedním z výzev v případě zprostředkovatelských scénářů je, že interní koncové body mohou mít různé požadavky na přenos nebo verzi SOAP než koncový bod, na kterém jsou zprávy přijímány. Pro podporu tohoto scénáře může směrovací služba Přemostění protokolů, včetně zpracování zprávy protokolu SOAP na <xref:System.ServiceModel.Channels.MessageVersion> požadované cílovým koncovým bodem (y). Tímto způsobem lze použít jeden protokol pro interní komunikaci, zatímco další lze použít pro externí komunikaci.

Pro podporu směrování zpráv mezi koncovými body pomocí různých přenosů služba Směrování používá vazby poskytované systémem, které službě umožňují přemostění podobných protokolů. K tomu dojde automaticky v případě, že koncový bod služby vystavený směrovací službou používá jiný protokol než koncové body klienta, na které jsou zprávy směrovány.

## <a name="soap-processing"></a>Zpracování SOAP

Běžným požadavkem na směrování je schopnost směrovat zprávy mezi koncovými body s odlišnými požadavky SOAP. Pro podporu tohoto požadavku služba Směrování poskytuje <xref:System.ServiceModel.Routing.SoapProcessingBehavior> , aby automaticky vytvořila novou **třídu MessageVersion** , která splňuje požadavky cílového koncového bodu před tím, než se do ní směruje zpráva. Toto chování také vytvoří novou **třídu MessageVersion** pro jakoukoli zprávu odpovědi, než ji vrátíte do žádající klientské aplikace, aby se zajistilo, že třída **MessageVersion** odpovědi odpovídá původní žádosti.

Další informace o zpracování protokolu SOAP najdete v tématu popisujícím [Úvod do směrování](routing-introduction.md).

## <a name="error-handling"></a>Zpracování chyb

V systému složeném z distribuovaných služeb, které využívají síťovou komunikaci, je důležité zajistit, aby komunikace v rámci systému byla odolná vůči přechodným chybám sítě.  Směrovací služba implementuje zpracování chyb, které vám umožní zvládnout mnoho scénářů selhání komunikace, které by jinak mohly způsobit výpadek služby.

Pokud směrovací služba <xref:System.ServiceModel.CommunicationException> při pokusu o odeslání zprávy narazí na chybu, bude provedeno zpracování chyb.  Tyto výjimky obvykle označují, že došlo k potížím při pokusu o komunikaci s definovaným koncovým bodem klienta, jako je například <xref:System.ServiceModel.EndpointNotFoundException> , <xref:System.ServiceModel.ServerTooBusyException> nebo <xref:System.ServiceModel.CommunicationObjectFaultedException> .  Kód pro zpracování chyb bude také zachytit a pokusí se o opakované odeslání, když dojde k **TimeoutException** , což je další běžná výjimka, která není odvozena od **CommunicationException**.

Další informace o zpracování chyb najdete v tématu popisujícím [Úvod do směrování](routing-introduction.md).

## <a name="backup-endpoints"></a>Koncové body zálohování

Kromě cílových koncových bodů klienta přidružených ke každé definici filtru v tabulce filtru můžete také vytvořit seznam koncových bodů zálohy, na které bude zpráva směrována v případě selhání přenosu. Pokud dojde k chybě a je definován seznam zálohování pro položku filtru, směrovací služba se pokusí odeslat zprávu do prvního koncového bodu definovaného v seznamu. Pokud tento pokus o přenos selže, služba zkusí další koncový bod a pokračuje v tomto procesu až do chvíle, kdy pokus o přenos proběhne úspěšně, vrátí chybu nesouvisející s přenosem nebo všechny koncové body v seznamu zálohování vrátily chybu přenosu.

Další informace o koncových bodech zálohování najdete v tématu [Úvod do směrování](routing-introduction.md) a [filtry zpráv](message-filters.md).

## <a name="streaming"></a>Streamování

Směrovací služba může úspěšně streamovat zprávy, pokud nastavíte vazbu na podporu streamování.  Existují však podmínky, za kterých mohou být zprávy nutné ukládat do vyrovnávací paměti:

- Vícesměrové vysílání (vyrovnávací paměť pro vytvoření dalších kopií zpráv)

- Převzetí služeb při selhání (vyrovnávací paměť pro případ, že je nutné odeslat zprávu do zálohy)

- System. ServiceModel. Routing. konfigurace RoutingConfiguration. hodnotami RouteOnHeadersOnly je false (vyrovnávací paměť pro zobrazení MessageFilterTable s třída MessageBuffer, aby filtry mohli kontrolovat tělo).

- Dynamická konfigurace

## <a name="see-also"></a>Viz také

- [Směrování – úvod](routing-introduction.md)
- [Kontrakty pro směrování](routing-contracts.md)
- [Filtry zpráv](message-filters.md)
