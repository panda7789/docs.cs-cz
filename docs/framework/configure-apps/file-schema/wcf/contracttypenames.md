---
title: '&lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 2c3f501f44d9e3c601e654041eb9d5a7de8a0a07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626768"
---
# <a name="ltcontracttypenamesgt"></a>&lt;contractTypeNames&gt;
Konfigurační oddíl, který určuje seznam názvy typu smlouvy, které jsou názvy kontraktů služeb vyhledaly a kritéria obvykle používá při vyhledávání pro službu. Pokud je zadán více než jeden název smlouvy, jenom koncové body služby odpovídající všechny kontrakty odpovíte. Všimněte si, že ve Windows Communication Foundation (WCF), koncový bod podporuje pouze jeden kontrakt.  
  
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
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|Název typu kontraktu je vlastnost, která odkazuje na sadu kritérií, obvykle používá při vyhledávání pro službu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<findCriteria>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|Konfigurace element, který dodává sadu kritérií pro službu zjišťování používá klientská aplikace pro hledání. Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a nalézt ukončení kritéria (jak dlouho vyhledávání by měl trvat).|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
