---
title: Filtry zpráv
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: b8de58b6935ee59fc8c787dfcf7445afcd0774b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912701"
---
# <a name="message-filters"></a>Filtry zpráv
K implementaci směrování na základě obsahu služba Směrování používá <xref:System.ServiceModel.Dispatcher.MessageFilter> implementace, které kontrolují určité části zprávy, jako je adresa, název koncového bodu nebo konkrétní příkaz XPath. Pokud žádný z filtrů zpráv není k dispozici pro [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] splnění vašich potřeb, můžete vytvořit vlastní filtr vytvořením nové implementace základní <xref:System.ServiceModel.Dispatcher.MessageFilter> třídy.  
  
 Při konfiguraci směrovací služby je nutné definovat prvky filtru (<xref:System.ServiceModel.Routing.Configuration.FilterElement> objekty), které popisují typ **MessageFilter** a veškerá podpůrná data potřebná k vytvoření filtru, například konkrétní řetězcové hodnoty, které se mají v rámci zprávy vyhledat. . Všimněte si, že vytváření elementů filtru definuje pouze jednotlivé filtry zpráv; Chcete-li použít filtry k vyhodnocení a směrování zpráv, musíte také definovat tabulku filtru (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).  
  
 Každá položka v tabulce filtru odkazuje na element Filter a určuje koncový bod klienta, na který bude směrována zpráva, pokud zpráva odpovídá filtru. Položky v tabulce filtru také umožňují zadat kolekci koncových bodů zálohy (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), která definuje seznam koncových bodů, do kterých se zpráva přenáší v případě selhání přenosu při odeslání do primárního koncového bodu. Tyto koncové body budou vyzkoušeny v uvedeném pořadí, dokud jeden neuspěje.  
  
## <a name="message-filters"></a>Filtry zpráv  
 Filtry zpráv používané směrovací službou poskytují běžné funkce výběru zpráv, jako je například vyhodnocení názvu koncového bodu, na který byla zpráva odeslána, akce protokolu SOAP nebo předpony adresy nebo adresy, na kterou byla zpráva odeslána. Filtry je také možné spojit s `AND` podmínkou, takže zprávy budou směrovány pouze do koncového bodu, pokud zpráva odpovídá oběma filtry. Můžete také vytvořit vlastní filtry vytvořením vlastní implementace <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 V následující tabulce je uveden <xref:System.ServiceModel.Routing.Configuration.FilterType> seznam používaný směrovací službou, třída, která implementuje určitý filtr zpráv, a požadované <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parametry.  
  
|Typ filtru|Popis|Filtrovat význam dat|Ukázkový filtr|  
|------------------|-----------------|-------------------------|--------------------|  
|Akce|<xref:System.ServiceModel.Dispatcher.ActionMessageFilter> Používá třídu k porovnávání zpráv obsahujících určitou akci.|Akce, která má být filtrována.|\<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation" />|  
|Parametry|<xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A> Používá třídu s ==  , abyodpovídalazprávám,kteréobsahujíkonkrétníadresu`true`. <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>|Adresa, na kterou se má filtr filtrovat (v hlavičce do).|\<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b"  />|  
|EndpointAddressPrefix|<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A> Používá třídu s ==  , abyodpovídalazprávámobsahujícímkonkrétní`true`předponuadresy. <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>|Adresa, která se má filtrovat při použití nejdelšího spárování předpon|\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" />|  
|A|<xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> Používá třídu, která před vrácením hodnot vždy vyhodnocuje obě podmínky.|fulltextových se nepoužívá; místo toho mají filter1 a filter2 názvy odpovídajících filtrů zpráv (také v tabulce), které by měly být **a**Ed společně.|\<filter name="and1" filterType="And" filter1="address1" filter2="action1" />|  
|Vlastní|Uživatelsky definovaný typ, který rozšiřuje <xref:System.ServiceModel.Dispatcher.MessageFilter> třídu a má konstruktor s řetězcem.|Atribut customType je plně kvalifikovaný název typu třídy, který se má vytvořit. fulltextových je řetězec, který má být předána konstruktoru při vytváření filtru.|\<filter name="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Custom Data" />|  
|EndpointName|<xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> Používá třídu k porovnávání zpráv na základě názvu koncového bodu služby, na který byly přijaty.|Název koncového bodu služby, například: "serviceEndpoint1".  Mělo by to být jeden z koncových bodů zveřejněných v směrovací službě.|\<filter name="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|MatchAll|<xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> Používá třídu. Tento filtr odpovídá všem doručeným zprávám.|fulltextových se nepoužívá. Tento filtr vždy bude odpovídat všem zprávám.|\<Filter name = "matchAll1" filterType = "MatchAll"/>|  
|XPath|<xref:System.ServiceModel.Dispatcher.XPathMessageFilter> Používá třídu ke spárování konkrétních dotazů XPath v rámci zprávy.|Dotaz XPath, který se má použít, pokud se shodují zprávy|\<filter name="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 Následující příklad definuje položky filtru, které používají filtry zpráv XPath, Endpoint a PrefixEndpointAddress. Tento příklad také ukazuje použití vlastního filtru pro položky RoundRobinFilter1 a RoundRobinFilter2.  
  
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
> Pouhým definováním filtru nezpůsobí vyhodnocení zpráv proti filtru. Filtr musí být přidán do tabulky filtrů, která je pak přidružena k koncovému bodu služby vystavenému směrovací službou.  
  
### <a name="namespace-table"></a>Tabulka oboru názvů  
 Při použití filtru XPath může být data filtru obsahující dotaz XPath v důsledku použití oborů názvů velmi velká. Aby bylo možné tento problém zmírnit, služba Směrování poskytuje možnost definovat vlastní předpony oboru názvů pomocí tabulky obor názvů.  
  
 Tabulka oboru názvů je kolekce <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> objektů, které definují předpony oboru názvů pro běžné obory názvů, které lze použít ve výrazu XPath. Níže jsou uvedené výchozí obory názvů a předpony oboru názvů, které jsou obsaženy v tabulce oboru názvů.  
  
|Směr|Obor názvů|  
|------------|---------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|s12|`http://www.w3.org/2003/05/soap-envelope`|  
|wsaAugust2004|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|wsa10|`http://www.w3.org/2005/08/addressing`|  
|sm|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|tempuri|`http://tempuri.org`|  
|Ser|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 Pokud víte, že budete v dotazech XPath používat konkrétní obor názvů, můžete ho přidat do tabulky oboru názvů spolu s jedinečnou předponou oboru názvů a místo úplného oboru názvů použít předponu v jakémkoli dotazu XPath. Následující příklad definuje předponu "Custom" pro obor názvů `"http://my.custom.namespace"`, který je pak použit v dotazu XPath obsaženém v fulltextových.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Filtrovat tabulky  
 Zatímco každý prvek filtru definuje logické porovnání, které lze použít na zprávu, tabulka filtru poskytuje přidružení mezi prvkem filtru a cílovým koncovým bodem klienta. Tabulka filtru je pojmenovaná kolekce <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> objektů, které definují přidružení mezi filtrem, primárním cílovým koncovým bodem a seznamem alternativních koncových bodů zálohování. Položky v tabulce filtru také umožňují určit volitelnou prioritu pro každou podmínku filtru. Následující příklad definuje dva filtry a definuje tabulku filtrů, která přidruží jednotlivé filtry k cílovému koncovému bodu.  
  
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
 Ve výchozím nastavení jsou všechny položky v tabulce filtru vyhodnocovány současně a vyhodnocená zpráva je směrována do koncových bodů přidružených ke každé odpovídající položce filtru. Pokud je vyhodnoceno `true`více filtrů a zpráva je jednosměrná nebo duplexní, je zpráva vícesměrového vysílání pro všechny vyhovující filtry. Zprávy požadavku a odpovědi nemohou být vícesměrové vysílání, protože klientovi může být vrácena pouze jedna odpověď.  
  
 Složitější logiku směrování lze implementovat zadáním úrovní priority pro každý filtr. Směrovací služba vyhodnocuje všechny filtry na nejvyšší úrovni priority jako první. Pokud zpráva odpovídá filtru této úrovně, nezpracují se žádné filtry s nižší prioritou. Například příchozí jednosměrná zpráva se nejprve vyhodnotí proti všem filtrům s prioritou 2. Zpráva neodpovídá žádnému filtru na této úrovni priority, takže další zpráva je porovnána s filtry s prioritou 1. Dvě filtry priority 1 odpovídají zprávě a protože se jedná o jednosměrnou zprávu, která je směrována do obou cílových koncových bodů.  Vzhledem k tomu, že byla nalezena shoda mezi filtry priority 1, nejsou vyhodnoceny žádné filtry priority 0.  
  
> [!NOTE]
> Pokud není zadána žádná priorita, je použita výchozí priorita 0.  
  
 Následující příklad definuje tabulku filtru, která určuje priority 2, 1 a 0 pro filtry odkazované v tabulce.  
  
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
  
 Pokud se v předchozím příkladu zpráva shoduje s Třída XPathFilter, bude směrována na roundingCalcEndpoint a žádné další filtry v tabulce nebudou vyhodnoceny, protože všechny ostatní filtry mají nižší prioritu. Pokud se však zpráva neshoduje s Třída XPathFilter, bude vyhodnocena proti všem filtrům další s nižší prioritou, EndpointNameFilter a PrefixAddressFilter.  
  
> [!NOTE]
> Pokud je to možné, používejte exkluzivní filtry namísto určení priority, protože hodnocení priority může způsobit snížení výkonu.  
  
### <a name="backup-lists"></a>Seznamy zálohování  
 Každý filtr v tabulce filtru může volitelně zadat seznam zálohování, který je pojmenovanou kolekcí koncových bodů (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>). Tato kolekce obsahuje seřazený seznam koncových bodů, na které se zpráva přenáší v případě <xref:System.ServiceModel.CommunicationException> , že se odesílá do primárního koncového bodu určeného v. <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A> Následující příklad definuje seznam zálohování s názvem "backupServiceEndpoints", který obsahuje dva koncové body.  
  
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
  
 Pokud v předchozím příkladu selže odeslání do primárního koncového bodu "cíl", směrovací služba se pokusí odeslat do každého koncového bodu v uvedeném pořadí, nejprve odešle do backupServiceQueue a následně odešle do alternateServiceQueue, pokud odeslání do backupServiceQueue se nezdařilo. Pokud se všechny koncové body zálohování nezdaří, vrátí se chyba.
