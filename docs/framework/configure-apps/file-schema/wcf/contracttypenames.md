---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: c67e5b9e82b96e27ce73512680bd4236b26ef4dd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855448"
---
# <a name="contracttypenames"></a>\<contractTypeNames>
Konfigurační oddíl, který určuje seznam názvů typů kontraktů, což jsou názvy kontraktů prohledávaných služeb a kritéria, která se obvykle používají při hledání služby. Pokud je zadán více než jeden název kontraktu, odpoví pouze koncové body služby, které odpovídají všem smlouvám. Všimněte si, že v Windows Communication Foundation (WCF) může koncový bod podporovat jenom jednu kontrakt.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Standardendpoint definovanému >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Kritéria hledání >** ](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<contractTypeNames >**  
  
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
|[\<add>](contracttypenames.md)|Název typu kontraktu je vlastnost, která odkazuje na sadu kritérií typicky používaných při hledání služby.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<findCriteria>](findcriteria.md)|Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování. Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
