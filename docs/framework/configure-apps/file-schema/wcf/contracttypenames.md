---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: c67e5b9e82b96e27ce73512680bd4236b26ef4dd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855448"
---
# \<contractTypeNames>
<span data-ttu-id="98d7d-101">Konfigurační oddíl, který určuje seznam názvů typů kontraktů, což jsou názvy kontraktů prohledávaných služeb a kritéria, která se obvykle používají při hledání služby.</span><span class="sxs-lookup"><span data-stu-id="98d7d-101">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="98d7d-102">Pokud je zadán více než jeden název kontraktu, odpoví pouze koncové body služby, které odpovídají všem smlouvám.</span><span class="sxs-lookup"><span data-stu-id="98d7d-102">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="98d7d-103">Všimněte si, že v Windows Communication Foundation (WCF) může koncový bod podporovat jenom jednu kontrakt.</span><span class="sxs-lookup"><span data-stu-id="98d7d-103">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<contractTypeNames>**  
  
## <a name="syntax"></a><span data-ttu-id="98d7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98d7d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98d7d-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="98d7d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="98d7d-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="98d7d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98d7d-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="98d7d-107">Attributes</span></span>  
 <span data-ttu-id="98d7d-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="98d7d-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="98d7d-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="98d7d-109">Child Elements</span></span>  
  
|<span data-ttu-id="98d7d-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="98d7d-110">Element</span></span>|<span data-ttu-id="98d7d-111">Description</span><span class="sxs-lookup"><span data-stu-id="98d7d-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](contracttypenames.md)|<span data-ttu-id="98d7d-112">Název typu kontraktu je vlastnost, která odkazuje na sadu kritérií typicky používaných při hledání služby.</span><span class="sxs-lookup"><span data-stu-id="98d7d-112">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="98d7d-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="98d7d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="98d7d-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="98d7d-114">Element</span></span>|<span data-ttu-id="98d7d-115">Description</span><span class="sxs-lookup"><span data-stu-id="98d7d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<findCriteria>](findcriteria.md)|<span data-ttu-id="98d7d-116">Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování.</span><span class="sxs-lookup"><span data-stu-id="98d7d-116">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="98d7d-117">Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).</span><span class="sxs-lookup"><span data-stu-id="98d7d-117">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98d7d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="98d7d-118">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
