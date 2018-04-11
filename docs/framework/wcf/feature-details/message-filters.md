---
title: Filtry zpráv
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
caps.latest.revision: 8
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bd5019668e865d2fea835b450d992d45b5273ed7
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="message-filters"></a>Filtry zpráv
Implementace založená na obsahu směrování, služba Směrování používá <xref:System.ServiceModel.Dispatcher.MessageFilter> implementací, které kontrola určité části zprávy, jako je například adresu, název koncového bodu nebo konkrétní příkaz XPath. Pokud žádné filtry zpráv s [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] vašim požadavkům, můžete vytvořit vlastní filtr tak, že vytvoříte novou implementací základu <xref:System.ServiceModel.Dispatcher.MessageFilter> třídy.  
  
 Při konfiguraci služby směrování, je nutné zadat filtr elementy (<xref:System.ServiceModel.Routing.Configuration.FilterElement> objekty) popisují typ **MessageFilter** a všechny podpůrné data potřebná k vytvoření filtru rozhraní, jako je například hodnoty konkrétní řetězec pro vyhledávání pro v rámci zprávy. Všimněte si, že vytváření prvků filtr definuje pouze filtry jednotlivých zpráv; použít filtry k vyhodnocení a směrování zpráv, které je třeba definovat tabulku filtru (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).  
  
 Každý záznam v tabulce filtr odkazuje na element filtru a určuje klienta koncového bodu, který zprávu budou směrované na, pokud zpráva odpovídá filtru. Položky tabulky filtru taky umožňují určit kolekci zálohování koncových bodů (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), která definuje seznam koncových bodů, které zprávy budou předány v případě selhání přenosu při odesílání na primární koncový bod. Tyto koncové body se pokusila v pořadí určeném, dokud jeden neuspěje.  
  
## <a name="message-filters"></a>Filtry zpráv  
 Filtry zpráv, používá služba Směrování zadejte běžné funkce Výběr zpráv, například vyhodnocení název koncového bodu, který zpráva byla odeslána na akce SOAP nebo adresu nebo předponu adresy, který vám byl zaslán zprávy. Filtry lze také připojit se `AND` podmínek, takže zprávy budou směrované jenom na koncový bod, pokud zpráva odpovídá oba filtry. Můžete také vytvořit vlastní filtry tak, že vytvoříte vlastní implementaci <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 Následující tabulka uvádí <xref:System.ServiceModel.Routing.Configuration.FilterType> používaný službou Směrování třídu, která implementuje filtr konkrétní zpráv a požadované <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parametry.  
  
|Typ filtru|Popis|Filtrování dat význam|Příklad filtru|  
|------------------|-----------------|-------------------------|--------------------|  
|Akce|Používá <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> třídy tak, aby odpovídaly zprávy obsahující určité akce.|Akce při filtrování.|\<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation" />|  
|EndpointAddress|Používá <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> třída, s <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` tak, aby odpovídaly zprávy obsahující konkrétní adresu.|Adresa pro filtrování po (v hlavičce na).|\<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b"  />|  
|EndpointAddressPrefix|Používá <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> třída, s <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` tak, aby odpovídaly zprávy obsahující předponu konkrétní adresu.|Adresa pro filtrování při porovnáváním nejdelší předpon.|\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" />|  
|A|Používá <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> třídu, která vždy vyhodnotí splněny obě podmínky před vrácením.|fulltextových dat filtru se nepoužívá; Místo toho Filtr1 a Filtr2 mají názvy odpovídající filtry zpráv (také v tabulce), které by měl být **a**ed společně.|\<filter name="and1" filterType="And" filter1="address1" filter2="action1" />|  
|Vlastní|Uživatelem definovaný typ, který rozšiřuje <xref:System.ServiceModel.Dispatcher.MessageFilter> třídy a má konstruktor trvá řetězec.|Atribut customType je typ plně kvalifikovaný název třídy Vytvoření; fulltextových dat filtru je řetězec, které mají být předána do konstruktoru, při vytváření filtru.|\<filter name="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Custom Data" />|  
|EndpointName|Používá <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> třídy tak, aby odpovídaly zprávy na základě názvu koncového bodu služby se dostali na.|Název koncového bodu služby, například: "serviceEndpoint1".  To by měl být jeden z koncových bodů zveřejněný ve službě Směrování.|\<Název filtru = "stock1" filterType = fulltextových dat filtru "Koncový bod" = "SvcEndpoint" / >|  
|MatchAll|Používá <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> třídy. Tento filtr odpovídá všechny příchozí zprávy.|fulltextových dat filtru se nepoužije. Tento filtr bude vždy odpovídat všechny zprávy.|\<Název filtru = "matchAll1" filterType = "MatchAll" / >|  
|XPath|Používá <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> třídy tak, aby odpovídaly konkrétní dotazů XPath v rámci zprávy.|Dotaz XPath pro použití při kontrole shody zprávy.|\<filter name="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 V následujícím příkladu definuje filtr položky, které používají filtry XPath EndpointName a PrefixEndpointAddress zpráv. Tento příklad také ukazuje pomocí vlastního filtru pro RoundRobinFilter1 a RoundRobinFilter2 položky.  
  
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
>  Jednoduše definice filtru nezpůsobí zprávy, které má být porovnán s filtru. Filtr musí být přidaný do filtru tabulky a který je pak přidružené koncový bod služby, které jsou vystavené směrovací služby.  
  
### <a name="namespace-table"></a>Namespace tabulky  
 Pokud používáte filtr XPath, se může stát velmi velký kvůli použití technologie oborů názvů filtru data, která obsahuje dotaz XPath. Ke zmírnění tohoto problému směrovací služby umožňuje definovat vlastní předpony oboru názvů pomocí tabulky oboru názvů.  
  
 Obor názvů tabulka je kolekce <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> objekty, které definuje předpony oboru názvů pro běžné obory názvů, který lze použít v XPath. Níže jsou uvedeny výchozí obory názvů a obor názvů předpon, které jsou obsaženy v tabulce oboru názvů.  
  
|Předpona|Obor názvů|  
|------------|---------------|  
|s11|http://schemas.xmlsoap.org/soap/envelope|  
|s12|http://www.w3.org/2003/05/soap-envelope|  
|wsaAugust2004|http://schemas.xmlsoap.org/ws/2004/08/addressing|  
|wsa10|http://www.w3.org/2005/08/addressing|  
|sm|http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions|  
|tempuri|http://tempuri.org|  
|Pož|http://schemas.microsoft.com/2003/10/Serialization|  
  
 Když víte, že budete používat konkrétní obor názvů v dotazech XPath, můžete ho přidat do oboru názvů tabulky společně s jedinečný obor názvů a použijte předponu v jakékoli dotaz XPath místo úplné obor názvů. V následujícím příkladu definuje předponu "vlastní" obor "http://my.custom.namespace", která je pak použita v dotazu XPath obsažené v fulltextových dat filtru.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Filtr tabulky  
 Když každý prvek filtr definuje logické porovnání, které lze použít pro zprávu, tabulka filtru obsahuje přidružení mezi element filtru a koncový bod cílového klienta. Tabulka Filtr je pojmenovaná kolekce <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> objekty, které definují přidružení mezi filtr, koncový bod primární cílové a seznam koncových bodů alternativní zálohování. Položky filtru tabulky lze také určit volitelné prioritu pro každou podmínku filtrování. V následujícím příkladu definuje dva filtry a pak definuje filtr tabulku, která přidruží koncový bod cílové každého filtru.  
  
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
  
### <a name="filter-evaluation-priority"></a>Priorita vyhodnocování filtru  
 Ve výchozím nastavení všechny položky v tabulce filtru se vyhodnocují současně a zpráva vyhodnocovaný směrována na koncové spojené s každou položku odpovídající filtru. Pokud více filtrů vyhodnocení `true`a zpráva je jednosměrný nebo duplexní, zprávy vícesměrového vysílání do koncových bodů pro všechny filtry odpovídající. Zprávy požadavku a odpovědi nemůže být vícesměrového vysílání, protože pouze jednu odpověď může být vrácen do klienta.  
  
 Složitější logikou, směrování lze provést zadáním úrovně priority pro každý filtr; Směrovací služby nejprve vyhodnotí všechny filtry na nejvyšší úroveň priority. Pokud zpráva odpovídá filtru této úrovně, jsou zpracovávány žádné filtry s nižší prioritou. Jednosměrný příchozí zprávy je třeba nejprve porovnán s všechny filtry s prioritou 2. Zpráva neodpovídá libovolný filtr na této úrovni s prioritou, takže teď že se zpráva s prioritou 1 porovná filtry. Dva filtry priority 1 odpovídající zprávu, a protože je jednosměrný zpráva se směruje na obou cílové koncové body.  Vzhledem k tomu, že byla nalezena shoda mezi filtry priority 1, jsou vyhodnoceny žádné filtry s prioritou 0.  
  
> [!NOTE]
>  Pokud je zadána žádná priorita, se používá výchozí s prioritou 0.  
  
 V následujícím příkladu definuje filtr tabulku, která určuje priority 2, 1 a 0 pro filtry odkazuje v tabulce.  
  
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
  
 V předchozím příkladu Pokud zpráva odpovídá Třída XPathFilter, bude směrována roundingCalcEndpoint a žádné další filtry v tabulce bude vyhodnoceno, protože všechny ostatní filtry jsou s nižší prioritou. Ale pokud zpráva neodpovídá Třída XPathFilter ho se pak vyhodnotí proti všechny filtry další s nižší prioritou, EndpointNameFilter a PrefixAddressFilter.  
  
> [!NOTE]
>  Pokud je to možné, používejte výhradní filtry místo zadání priority, protože vyhodnocení priority může způsobit snížení výkonu.  
  
### <a name="backup-lists"></a>Zálohování seznamy  
 Každý filtr ve filtru tabulky Volitelně můžete zadat seznam zálohování, což je pojmenovaná kolekce koncových bodů (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>). Tato kolekce obsahuje seřazený seznam koncových bodů, které zprávy budou předány v případě systému <xref:System.ServiceModel.CommunicationException> při odesílání na primární koncový bod uvedený v <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>. V následujícím příkladu definuje seznam zálohování s názvem "backupServiceEndpoints", který obsahuje dva koncové body.  
  
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
  
 V předchozím příkladu, bude-li odeslat na primární koncový bod "Cílové" selže, směrovací služby pokusí odesílání na každý koncový bod v uvedeném pořadí, první odesílání backupServiceQueue a následně odesílání do alternateServiceQueue, pokud poslat backupServiceQueue selže. Pokud selžou všechny koncové body zálohování, se vrátí chybu.
