---
title: Filtry zpráv
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: fc4656a76894eb3a844bc9f2187847fd9eff0ffe
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780450"
---
# <a name="message-filters"></a>Filtry zpráv
K implementaci, směrování na základě obsahu, směrovací služba používá <xref:System.ServiceModel.Dispatcher.MessageFilter> implementace, které kontrolovat určité části zprávy, jako je například adresu, název koncového bodu nebo konkrétní příkaz XPath. Pokud žádné filtry zpráv součástí [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] vašim potřebám, můžete vytvořit vlastní filtr tak, že vytvoříte novou implementaci základní třídy <xref:System.ServiceModel.Dispatcher.MessageFilter> třídy.  
  
 Při konfiguraci služby směrování, je nutné definovat prvků filtru (<xref:System.ServiceModel.Routing.Configuration.FilterElement> objekty), které popisují typ **MessageFilter** a všechny podpůrné data požadovaná k vytvoření filtru, například konkrétní řetězec hodnoty pro hledání pro v rámci zprávy. Všimněte si, že vytváření prvků filtr definuje pouze filtry jednotlivých zpráv; použití filtrů k vyhodnocení a směrování zpráv, musíte také definovat tabulku filtru (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).  
  
 Každý záznam v tabulce filtrů odkazuje na element filtr a Určuje koncový bod klienta, který zpráva bude směrován do zpráva odpovídá filtru. Filtrovat položky tabulky také umožňují zadat kolekce zálohování koncových bodů (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), která definuje seznam koncových bodů, které zprávy budou předány v případě selhání přenosu při odesílání na primární koncový bod. Tyto koncové body, vyzkouší se v uvedeném pořadí, dokud jeden neuspěje.  
  
## <a name="message-filters"></a>Filtry zpráv  
 Filtry zpráv používá služba Směrování poskytují společné funkce výběru zprávy, například vyhodnocení názvu koncového bodu, který na akce SOAP, nebo adresu nebo předponu adresy, která byla zaslána zpráva byla odeslána zpráva. Filtry lze také připojit se `AND` podmínky tak, aby se zprávy budou směrovány pouze na koncový bod, pokud zpráva odpovídá oba filtry. Můžete také vytvořit vlastní filtry tak, že vytvoříte vlastní implementace <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 Následující tabulce jsou uvedeny <xref:System.ServiceModel.Routing.Configuration.FilterType> využívané ve službě Směrování třídy, která implementuje konkrétní zprávu filtr a požadované <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parametry.  
  
|Typ filtru|Popis|Filtrovat podle Data|Příklad filtru|  
|------------------|-----------------|-------------------------|--------------------|  
|Akce|Používá <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> třídy tak, aby odpovídaly zpráv obsahujících určité akce.|Akce, který se má filtrovat.|\<Název filtru = filterType "action1" = "Action" fulltextových dat filtru = "http://namespace/contract/operation" / >|  
|EndpointAddress|Používá <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> třídy s <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` tak, aby odpovídaly zprávy obsahující konkrétní adresu.|Adresa chcete filtrovat (v záhlaví Komu).|\<Název filtru = "adresa1" filterType = fulltextových dat filtru "EndpointAddress" = "http://host/vdir/s.svc/b" / >|  
|EndpointAddressPrefix|Používá <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> třídy s <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` tak, aby odpovídaly zprávy obsahující předponu konkrétní adresu.|Adresa pro filtrování při použití nejdelší odpovídající předpona.|\<Název filtru = "prefix1" filterType = fulltextových dat filtru "EndpointAddressPrefix" = "http://host/" / >|  
|a|Používá <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> třídu, která se vždycky vyhodnotí jako obě podmínky před vrácením.|fulltextových dat filtru se nepoužívá; Místo toho Filtr1 a Filtr2 mají názvy odpovídající filtry zpráv (také v tabulce), které by měly být **a**ed společně.|\<Název filtru = filterType "and1" = "A" Filtr1 = Filtr2 "adresa1" = "action1" / >|  
|Vlastní|Uživatelem definovaný typ, který rozšiřuje <xref:System.ServiceModel.Dispatcher.MessageFilter> třídy a má konstruktor, který přebírá řetězec.|Název plně kvalifikovaný typ třídy k vytvoření; je customtype – atribut fulltextových dat filtru je řetězec, který má předat konstruktoru při vytváření filtru.|\<Název filtru = filterType "vlastní1" = "Vlastní" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" fulltextových dat filtru = "Vlastní Data" / >|  
|EndpointName|Používá <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> třídy tak, aby odpovídaly zprávy na základě názvu koncového bodu služby se dostali na.|Název koncového bodu služby, například: "serviceEndpoint1".  To by měl být jeden z koncových bodů zveřejněné na směrovací služba.|\<Název filtru = "stock1" filterType = fulltextových dat filtru "Koncového bodu" = "SvcEndpoint" / >|  
|MatchAll|Používá <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> třídy. Tento filtr odpovídá všechny příchozí zprávy.|fulltextových dat filtru se nepoužívá. Tento filtr bude vždy odpovídat všechny zprávy.|\<Název filtru = filterType "matchAll1" = "MatchAll" / >|  
|XPath|Používá <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> třídy tak, aby odpovídaly určité dotazy XPath v něm.|Dotaz XPath, který se má použít při přiřazování zpráv.|\<Název filtru = "XPath1" filterType = fulltextových dat filtru "Cesta XPath" = "//ns:element" / >|  
  
 Následující příklad definuje filtr položky, které používají filtry XPath, Název_koncového_bodu a PrefixEndpointAddress zpráv. Tento příklad také znázorňuje použití vlastního filtru pro RoundRobinFilter1 a RoundRobinFilter2 položky.  
  
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
>  Jednoduše definuje filtr nezpůsobí zprávy má být porovnán s filtru. Filtr musí být přidané do tabulky filtru, který je přidružený k koncový bod služby, vystavený službou směrování.  
  
### <a name="namespace-table"></a>Namespace tabulky  
 Pokud používáte filtr XPath, může být příliš velké vzhledem k použití oborů názvů filtrování dat, která obsahuje dotaz XPath. Ke zmírnění tohoto problému směrovací služby umožňuje definovat vlastní předpony oboru názvů pomocí oboru názvů tabulek.  
  
 Obor názvů tabulky je kolekce <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> objekty, které definuje předpony oboru názvů pro běžné obory názvů, který lze použít v XPath. Toto jsou výchozí obory názvů a obor názvů předpony, které jsou obsaženy v tabulce oboru názvů.  
  
|Předpona|Obor názvů|  
|------------|---------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|s12|`http://www.w3.org/2003/05/soap-envelope`|  
|wsaAugust2004|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|wsa10|`http://www.w3.org/2005/08/addressing`|  
|SM|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|tempuri|`http://tempuri.org`|  
|ser|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 Pokud víte, že budete používat konkrétní obor názvů v dotazech XPath, můžete ho přidat do oboru názvů tabulek spolu s předponu oboru názvů jedinečný a použijte předponu každého dotazu XPath místo úplné oboru názvů. Následující příklad definuje předponu "vlastní" pro obor názvů `"http://my.custom.namespace"`, které se pak použije obsažená v fulltextových dat filtru dotazu XPath.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Filtr tabulky  
 Zatímco každý prvek filtr definuje logické porovnání, který lze použít na zprávu, tabulky filtru poskytuje přidružení mezi prvkem filtr a cílový koncový bod klienta. Filtr tabulky je soubor s názvem <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> objekty, které definují přidružení mezi filtr koncovým bodem v cílové primární a seznam alternativní koncové body záloh. Filtrovat položky tabulky také umožňují určit volitelné prioritu pro každou podmínku filtru. Následující příklad definuje dva filtry a pak definuje filtr tabulku, která se přidruží koncový bod cílové každého filtru.  
  
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
 Ve výchozím nastavení všechny položky v tabulce filtrů jsou vyhodnoceny současně a zpráva právě vyhodnocuje se směruje do koncových bodů spojené s každou položku odpovídající filtr. Pokud mají více filtrů `true`a zpráva je jednosměrné nebo obousměrné je zprávy vícesměrového vysílání do koncových bodů pro všechny odpovídající filtry. Zprávy požadavek odpověď nemůže být vícesměrového vysílání, protože pouze jednu odpověď může být vrácen do klienta.  
  
 Složitější logiku směrování lze provést zadáním úrovně priority u každého filtru. Směrovací služba nejdřív vyhodnotí všechny filtry na úrovni nejvyšší prioritou. Pokud zpráva odpovídá filtru této úrovně, se zpracovávají žádné filtry s nižší prioritou. Například jednosměrný příchozí zprávy nejprve vyhodnotí oproti všechny filtry s prioritou 2. Zprávy se neshoduje s libovolný filtr na této úrovni prioritu, proto vám teď že zprávy se porovná s filtry s prioritou 1. Dva filtry priority 1 odpovídat zprávu, a protože je jednosměrná zpráva se směruje do obou cílové koncové body.  Protože byla nalezena shoda mezi filtry priority 1, jsou vyhodnocovány žádné filtry prioritu 0.  
  
> [!NOTE]
>  Pokud není zadána žádná priorita, použije se výchozí prioritu 0.  
  
 Následující příklad definuje filtr tabulku, která určuje priority 2 a 1, 0 pro filtry odkazuje v tabulce.  
  
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
  
 V předchozím příkladu Pokud zpráva odpovídá Třída XPathFilter, bude směrována roundingCalcEndpoint a žádné další filtry. v tabulce se vyhodnotit, protože se všemi ostatními filtry s nižší prioritou. Ale pokud zprávy neodpovídá Třída XPathFilter ho pak se vyhodnotí pro všechny filtry další nižší prioritou EndpointNameFilter a PrefixAddressFilter.  
  
> [!NOTE]
>  Pokud je to možné, používejte filtry exkluzivní místo určení prioritu, protože vyhodnocení priority může způsobit snížení výkonu.  
  
### <a name="backup-lists"></a>Zálohování seznamy  
 Každý filtr v tabulce filtrů můžete volitelně zadat záložní seznam, který je pojmenovaná kolekce koncových bodů (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>). Tato kolekce obsahuje uspořádaný seznam koncových bodů, které zprávy se dá přenést k v <xref:System.ServiceModel.CommunicationException> při odesílání do primárního koncového bodu určeného v <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>. Následující příklad definuje záložní seznam s názvem "backupServiceEndpoints", který obsahuje dva koncové body.  
  
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
  
 V předchozím příkladu, pokud se nepodaří odeslat na primární koncový bod "Cíl", směrovací služba zkusí odesílání do každého koncového bodu v pořadí, v jakém jsou uvedeny, první odesílání backupServiceQueue a následně odesláním do alternateServiceQueue, pokud Odeslat backupServiceQueue selže. Pokud selžou i všechny koncové body pro zálohování, je vrácena chyba.
