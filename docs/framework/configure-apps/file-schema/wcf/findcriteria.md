---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 44e068ee205bc5e04382164e7ab00716b2c07dcf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855163"
---
# \<findCriteria>
Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování. Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            </contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|doba trvání|Hodnota TimeSpan, která určuje maximální dobu čekání na odpovědi ze služeb v síti. Výchozí doba trvání je 20 sekund.|  
|maxResults|Celé číslo určující maximální počet odpovědí, na které se má čekat, ze služeb v síti nebo Internetu. Pokud jsou přijaty maximální odpovědi před hodnotou zadanou v `duration` atributu, operace Find skončí.|  
|scopeMatchBy|Identifikátor URI, který určuje odpovídající algoritmus, který se má použít při porovnání oborů v rámci zprávy sondy s bodem koncového bodu.<br /><br /> Existuje pět podporovaných pravidel pro porovnání oboru. Pokud neurčíte pravidlo pro porovnání s oborem, `ScopeMatchByPrefix` použije se. Další informace o tomto naleznete v tématu <xref:System.ServiceModel.Discovery.FindCriteria>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|Kolekce elementů konfigurace, které obsahují názvy typů kontraktů služby pracovního postupu.|  
|\<extensions> z \<findCriteria>|Kolekce objektů XML elementů, které poskytují rozšíření.|  
|[\<scopes>](scopes.md)|Kolekce objektů, které obsahují absolutní identifikátory URI, které jsou použity během operace Find k vyhledání konkrétní služby nebo služeb.<br /><br /> Pokud je nalezena konkrétní služba, byla provedena úspěšná shoda mezi identifikátorem URI služby a identifikátorem URI oboru, někdy s použitím pravidel oboru, které zpracovávají komplikace při porovnávání.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Obsahuje nastavení, která aplikace potřebuje k účasti v procesu zjišťování služby jako klient.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
