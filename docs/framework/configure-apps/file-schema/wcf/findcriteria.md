---
title: "&lt;kritéria hledání&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b428d1a95ec6f1f493c831f66223f52e4723990c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltfindcriteriagt"></a>&lt;kritéria hledání&gt;
Konfigurace element, který poskytuje sadu kritérií používané klientskou aplikaci pro vyhledávání pro službu zjišťování. Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a najděte ukončení kritéria (jak dlouho by měl poslední hledání).  
  
 \<systém. ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
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
|doba trvání|Hodnota časového rozpětí, která určuje maximální dobu čekání na odpovědi od služby v síti. Výchozí doba je 20 sekund...|  
|shluku|Celé číslo, které určuje maximální počet odpovědí čekat, služby v síti nebo Internetu. Pokud jsou odpovědi maximální obdrženy předtím, než hodnota zadaná v `duration` atribut uplynul, skončení operace hledání.|  
|scopeMatchBy|Identifikátor URI, který zadejte odpovídající algoritmus použitý při odpovídající obory ve zprávě test s u koncového bodu.<br /><br /> Existují pravidla pět odpovídající oboru podporované. Pokud nezadáte oboru odpovídající pravidlo, `ScopeMatchByPrefix` se používá. Další informace o tomto naleznete v tématu <xref:System.ServiceModel.Discovery.FindCriteria>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<contractTypeNames >](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|Kolekci elementů konfigurace, které obsahují názvy typů kontraktu služby pracovního postupu...|  
|\<Rozšíření > z \<kritéria hledání >|Kolekce objektů elementu XML, které poskytují rozšíření.|  
|[\<obory >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Kolekce objektů, které obsahují absolutní identifikátory URI, které se používají během operace hledání pro vyhledání konkrétní služby nebo služby.<br /><br /> Pokud je nalezen konkrétní službu, byl proveden úspěšně shody mezi URI služby a identifikátor URI oboru, někdy pomocí pravidel rozsahu, které zpracovávají komplikace odpovídajících.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Obsahuje nastavení vyžadovaná aplikace k účasti v procesu zjišťování služby jako klient.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
