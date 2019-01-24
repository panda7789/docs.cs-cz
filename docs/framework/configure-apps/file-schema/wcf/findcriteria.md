---
title: '&lt;findCriteria&gt;'
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: b90e6cab923075dbf750dc0d26a0eb1196cfde32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741236"
---
# <a name="ltfindcriteriagt"></a>&lt;findCriteria&gt;
Konfigurace element, který dodává sadu kritérií pro službu zjišťování používá klientská aplikace pro hledání. Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a nalézt ukončení kritéria (jak dlouho vyhledávání by měl trvat).  
  
 \<system.ServiceModel>  
\<standardEndpoints>  
  
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
|doba trvání|Časový interval hodnotu, která určuje maximální dobu čekání na odpovědi služby v síti. Výchozí doba je 20 sekund.|  
|maxResults|Celé číslo určující maximální počet odpovědí čekat od služby v síti nebo Internetu. Pokud se maximální odpovědi obdrženy předtím, než hodnota zadaná v `duration` atribut uplynul, skončí operace find.|  
|scopeMatchBy|Identifikátor URI určující porovnávací algoritmus, který bude použit při porovnání rozsahů průzkumné zprávy, která koncového bodu.<br /><br /> Existují pravidla pět oboru odpovídajícím podporované. Pokud nezadáte pravidlo odpovídající oboru `ScopeMatchByPrefix` se používá. Další informace o tomto naleznete v tématu <xref:System.ServiceModel.Discovery.FindCriteria>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<contractTypeNames>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|Kolekci elementů konfigurace, které obsahují názvy typů kontraktu služby pracovního postupu.|  
|\<Rozšíření > z \<kritéria hledání >|Kolekce objektů – element XML, které poskytují rozšíření.|  
|[\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Kolekce objektů, které obsahují absolutní URI, které se používají během operace find k nalezení konkrétní služby nebo služeb.<br /><br /> Pokud konkrétní služba nalezena, byl proveden úspěšná shoda mezi identifikátor URI služby a identifikátor URI oboru, někdy pomocí pravidel oboru, které zpracovávají komplikace párování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Obsahuje nastavení potřeby aplikací a součástí procesu zjišťování služby jako klient.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
