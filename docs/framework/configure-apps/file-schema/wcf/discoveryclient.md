---
title: '&lt;objekty discoveryClient&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55c8b9a01eaf53105968e044aecb7e38ad691aac
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiscoveryclientgt"></a>&lt;objekty discoveryClient&gt;
Element konfigurace pro vytvoření vlastní vazby, která umožňuje klientskou aplikaci, aby automaticky vyhledat zjistitelný službu a najděte jeho adresa za běhu.  
  
\<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<objekty discoveryClient >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<discoveryClient discoveryEndpoint="String" >
  <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String" namespace="String" />
    <contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|discoveryEndpoint|Řetězec, který obsahuje název koncového bodu zjišťování, který umožňuje klientskou aplikaci, aby automaticky vyhledat zjistitelný službu a najděte jeho adresa za běhu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Konfigurace element, který poskytuje sadu kritérií používané klientskou aplikaci pro vyhledávání pro službu zjišťování. Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a najděte ukončení kritéria (jak dlouho by měl poslední hledání).|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
