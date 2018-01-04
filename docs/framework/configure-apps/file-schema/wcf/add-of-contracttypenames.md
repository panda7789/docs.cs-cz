---
title: "&lt;add&gt; – &lt;contractTypeNames&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 191e3e221ae42e5c046f8df324989aae7ab0dc1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a>&lt;add&gt; – &lt;contractTypeNames&gt;
Konfigurace element, který určuje název kontraktu služby vyhledána a kritéria pro službu obvykle používaných při hledání. Pokud je zadán více než jeden název kontraktu, bude odpověď pouze koncové body služby odpovídající všechny smlouvy. Všimněte si, že v [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], koncový bod podporuje pouze jeden kontrakt.  
  
 \<systém. ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <dynamicEndpoint>           <standardEndpoint>             <discoveryClientSettings discoveryEndpoint="String" >               <findCriteria duration="TimeSpan"                  maxResults="Integer"                   scopeMatchBy="Uri" >                  <contractTypeNames>                     <add name="String" namespace="String" />                  <contractTypeNames>                  <extensions />                  <scopes>                    <add scope="URI"/>                  </scopes>               </findCriteria>             </discoveryClientSettings>          <standardEndpoint>       </dynamicEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Řetězec, který určuje název typu kontraktu.|  
|– obor názvů|Řetězec, který určuje obor názvů typu kontraktu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<contractTypeNames >](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|Kolekce názvy typů kontrakt.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
