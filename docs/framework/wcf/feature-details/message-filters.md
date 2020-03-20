---
title: Filtry zpráv
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: a953dea9224d75907c593d87f06a0b0888f0af2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184664"
---
# <a name="message-filters"></a>Filtry zpráv
K implementaci směrování založeného na <xref:System.ServiceModel.Dispatcher.MessageFilter> obsahu používá služba Směrování implementace, které kontrolují určité části zprávy, jako je adresa, název koncového bodu nebo konkrétní příkaz XPath. Pokud žádný z filtrů [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] zpráv dodaný s vašimi potřebami, můžete vytvořit <xref:System.ServiceModel.Dispatcher.MessageFilter> vlastní filtr vytvořením nové implementace základní třídy.  
  
 Při konfiguraci služby Směrování je nutné<xref:System.ServiceModel.Routing.Configuration.FilterElement> definovat prvky filtru (objekty), které popisují typ **filtru MessageFilter** a všechna podpůrná data potřebná k vytvoření filtru, například konkrétní hodnoty řetězců, které mají být ve zprávě vyhledány. Všimněte si, že vytvoření prvků filtru definuje pouze jednotlivé filtry zpráv; Chcete-li použít filtry k vyhodnocení a směrování<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>zpráv, musíte také definovat tabulku filtrů ( ).  
  
 Každá položka v tabulce filtrů odkazuje na prvek filtru a určuje koncový bod klienta, na který bude zpráva směrována, pokud zpráva odpovídá filtru. Položky tabulky filtrů také umožňují zadat kolekci<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>koncových bodů zálohování ( ), která definuje seznam koncových bodů, do kterých bude zpráva přenesena v případě selhání přenosu při odesílání do primárního koncového bodu. Tyto koncové body budou vyzkoušeny v uvedeném pořadí, dokud jeden úspěšný.  
  
## <a name="message-filters"></a>Filtry zpráv  
 Filtry zpráv používané službou Směrování poskytují běžné funkce výběru zpráv, jako je například vyhodnocení názvu koncového bodu, do kterého byla zpráva odeslána, akce SOAP nebo předpony adresy nebo adresy, na kterou byla zpráva odeslána. Filtry lze také `AND` spojit s podmínkou, takže zprávy budou směrovány do koncového bodu pouze v případě, že zpráva odpovídá oběma filtrům. Vlastní filtry můžete také vytvořit vytvořením vlastní implementace aplikace <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 V následující tabulce <xref:System.ServiceModel.Routing.Configuration.FilterType> jsou uvedeny používané službou Směrování, třída, která <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> implementuje filtr konkrétní zprávy a požadované parametry.  
  
|Typ filtru|Popis|Význam dat filtru|Ukázkový filtr|  
|------------------|-----------------|-------------------------|--------------------|  
|Akce|Používá <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> třídu k sladění zpráv obsahujících konkrétní akci.|Akce, na kterou chcete filtrovat.|\<název filtru="action1" filterType="Action" filterData="http://namespace/contract/operation"/>|  
|Endpointaddress|Používá <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> třídu, <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` s souřadit zprávy obsahující určitou adresu.|Adresa, na kterou chcete filtrovat (v záhlaví Do).|\<název filtru="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b/>|  
|EndpointAddressPrefix|Používá <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> třídu <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` s souřadných zpráv obsahujících předponu konkrétní adresy.|Adresa, která chcete filtrovat při použití nejdelší ho porovnání předpony.|\<název filtru="prefix1" filterType="EndpointAddressPrefix" filterData="http://host//>|  
|And|Používá <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> třídu, která vždy vyhodnotí obě podmínky před vrácením.|filterData se nepoužívá; místo filter1 a filter2 mají názvy odpovídající filtry zpráv (také v tabulce), které by měly být **and**ed společně.|\<název filtru="and1" filterType="A" filter1="address1" filter2="action1" />|  
|Vlastní|Uživatelem definovaný typ, který <xref:System.ServiceModel.Dispatcher.MessageFilter> rozšiřuje třídu a má konstruktor s řetězcem.|Atribut customType je plně kvalifikovaný název typu třídy, kterou chcete vytvořit; filterData je řetězec, který má být při vytváření filtru předáván konstruktoru.|\<název filtru="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Vlastní data" />|  
|Název koncového bodu|Používá <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> třídu k sladění zpráv na základě názvu koncového bodu služby, ke kterým byly doručeny.|Název koncového bodu služby, například "serviceEndpoint1".  To by měl být jeden z koncových bodů vystavených ve službě směrování.|\<název filtru="stock1" filterType="Koncový bod" filterData="SvcEndpoint" />|  
|MatchAll|Používá <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> třídu. Tento filtr odpovídá všem příchozím zprávám.|filterData se nepoužívá. Tento filtr bude vždy odpovídat všem zprávám.|\<název filtru="matchAll1" filterType="MatchAll" />|  
|XPath|Používá <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> třídu tak, aby odpovídala konkrétním dotazům XPath ve zprávě.|Dotaz XPath, který se má použít při porovnávání zpráv.|\<název filtru="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 Následující příklad definuje položky filtrů, které používají filtry zpráv XPath, EndpointName a PrefixEndpointAddress. Tento příklad také ukazuje použití vlastního filtru pro položky RoundRobinFilter1 a RoundRobinFilter2.  
  
```xml  
<filters>  
     <filter name="XPathFilter" filterType="XPath"
             filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
     <filter name="EndpointNameFilter" filterType="EndpointName"
             filterData="calculatorEndpoint"/>  
     <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"
             filterData="http://localhost/routingservice/router/rounding/"/>  
     <filter name="RoundRobinFilter1" filterType="Custom"
             customType="RoutingServiceFilters.RoundRobinMessageFilter,
             RoutingService" filterData="group1"/>  
     <filter name="RoundRobinFilter2" filterType="Custom"
             customType="RoutingServiceFilters.RoundRobinMessageFilter,
             RoutingService" filterData="group1"/>  
</filters>  
```  
  
> [!NOTE]
> Jednoduše definování filtru nezpůsobí, že zprávy, které mají být vyhodnoceny proti filtru. Filtr musí být přidán do tabulky filtrů, která je pak přidružena ke koncovému bodu služby vystaveného službou Směrování.  
  
### <a name="namespace-table"></a>Tabulka oboru názvů  
 Při použití filtru XPath mohou být data filtru obsahující dotaz XPath velmi velká z důvodu použití oborů názvů. Chcete-li tento problém zmírnit, služba Směrování poskytuje možnost definovat vlastní předpony oboru názvů pomocí tabulky oboru názvů.  
  
 Tabulka oboru názvů je <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> kolekce objektů, která definuje předpony oboru názvů pro běžné obory názvů, které lze použít v aplikaci XPath. Následují výchozí obory názvů a předpony oboru názvů, které jsou obsaženy v tabulce oboru názvů.  
  
|Předpona|Obor názvů|  
|------------|---------------|  
|S11|`http://schemas.xmlsoap.org/soap/envelope`|  
|s12|`http://www.w3.org/2003/05/soap-envelope`|  
|wsaSaSrpen2004|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|wsa10 řekl:|`http://www.w3.org/2005/08/addressing`|  
|sm|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|tempuri|`http://tempuri.org`|  
|Ser|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 Pokud víte, že budete v dotazech XPath používat určitý obor názvů, můžete jej přidat do tabulky oboru názvů spolu s jedinečnou předponou oboru názvů a použít předponu v libovolném dotazu XPath namísto celého oboru názvů. Následující příklad definuje předponu "custom" pro `"http://my.custom.namespace"`obor názvů , která se pak používá v dotazu XPath obsaženém v filterData.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Filtrovat tabulky  
 Zatímco každý prvek filtru definuje logické porovnání, které lze použít na zprávu, tabulka filtrů poskytuje přidružení mezi elementem filtru a cílovým koncovým bodem klienta. Tabulka filtrů je pojmenovaná kolekce <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> objektů, které definují přidružení mezi filtrem, primárním cílovým koncovým bodem a seznamem alternativních koncových bodů zálohování. Položky tabulky filtrů také umožňují určit volitelnou prioritu pro každou podmínku filtru. Následující příklad definuje dva filtry a pak definuje tabulku filtrů, která přidružuje každý filtr k cílovému koncovému bodu.  
  
```xml  
<routing>  
     <filters>  
       <filter name="AddAction" filterType="Action" filterData="Add" />  
       <filter name="SubtractAction" filterType="Action" filterData="Subtract" />  
     </filters>  
     <filterTables>  
       <table name="routingTable1">  
         <filters>  
           <add filterName="AddAction" endpointName="Addition" />  
           <add filterName="SubtractAction" endpointName="Subtraction" />  
         </filters>  
       </table>  
     </filterTables>
</routing>  
```  
  
### <a name="filter-evaluation-priority"></a>Priorita vyhodnocení filtru  
 Ve výchozím nastavení jsou všechny položky v tabulce filtrů vyhodnocovány současně a vyhodnocovaná zpráva je směrována do koncového bodu přidruženého ke každé odpovídající položce filtru. Pokud je více `true`filtrů vyhodnoceno do a zpráva je jednosměrná nebo duplexní, je zpráva vícesměrovým vysíláním koncovým bodům pro všechny odpovídající filtry. Zprávy požadavku a odpovědi nemohou být vícesměrové, protože klientovi lze vrátit pouze jednu odpověď.  
  
 Složitější logiku směrování lze implementovat zadáním úrovní priority pro každý filtr; Služba Směrování nejprve vyhodnotí všechny filtry na úrovni s nejvyšší prioritou. Pokud zpráva odpovídá filtru této úrovně, nebudou zpracovány žádné filtry s nižší prioritou. Například příchozí jednosměrná zpráva je nejprve vyhodnocena proti všem filtrům s prioritou 2. Zpráva neodpovídá žádnému filtru na této úrovni priority, takže další zpráva je porovnána s filtry s prioritou 1. Dvě priority 1 filtry odpovídají zprávě a protože se jedná o jednosměrnou zprávu je směrována do obou cílových koncových bodů.  Vzhledem k tomu, že byla nalezena shoda mezi filtry priority 1, nejsou vyhodnoceny žádné filtry s prioritou 0.  
  
> [!NOTE]
> Pokud není zadána žádná priorita, použije se výchozí priorita 0.  
  
 Následující příklad definuje tabulku filtrů, která určuje priority 2, 1 a 0 pro filtry uvedené v tabulce.  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="XPathFilter" endpointName="roundingCalcEndpoint"
               priority="2"/>  
          <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint"
               priority="1"/>  
          <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint"
               priority="1"/>  
          <add filterName="MatchAllMessageFilter" endpointName="defaultCalcEndpoint"
               priority="0"/>  
     </filterTable>  
</filterTables>  
```  
  
 V předchozím příkladu pokud zpráva odpovídá XPathFilter, bude směrována do zaokrouhleníCalcEndpoint a žádné další filtry v tabulce budou vyhodnoceny, protože všechny ostatní filtry mají nižší prioritu. Pokud však zpráva neodpovídá filtru XPathFilter, bude vyhodnocena proti všem filtrům s nižší prioritou EndpointNameFilter a PrefixAddressFilter.  
  
> [!NOTE]
> Pokud je to možné, použijte výhradní filtry namísto určení priority, protože vyhodnocení priority může mít za následek snížení výkonu.  
  
### <a name="backup-lists"></a>Seznamy záloh  
 Každý filtr v tabulce filtrů může volitelně určit záložní seznam,<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>což je pojmenovaná kolekce koncových bodů ( ). Tato kolekce obsahuje seřazený seznam koncových bodů, které <xref:System.ServiceModel.CommunicationException> zpráva bude odeslána v <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>případě při odesílání do primárního koncového bodu zadaného v . Následující příklad definuje seznam záloh s názvem "backupServiceEndpoints", který obsahuje dva koncové body.  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
 V předchozím příkladu, pokud se nezdaří odeslání primárního koncového bodu "Cíl", služba Směrování se pokusí odeslat do každého koncového bodu v pořadí, ve kterém jsou uvedeny, nejprve odeslat do backupServiceQueue a následně odeslat do alternateServiceQueue, pokud odeslání do programu backupServiceQueue se nezdaří. Pokud se nezdaří všechny koncové body zálohování, je vrácena chyba.
