---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: b1cec9272a1de029ab72ea4d5f36c74630e5b93a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089494"
---
# <a name="contracttypenames"></a><span data-ttu-id="c7295-101">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="c7295-101">\<contractTypeNames></span></span>
<span data-ttu-id="c7295-102">Konfigurační oddíl, který určuje seznam názvy typu smlouvy, které jsou názvy kontraktů služeb vyhledaly a kritéria obvykle používá při vyhledávání pro službu.</span><span class="sxs-lookup"><span data-stu-id="c7295-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="c7295-103">Pokud je zadán více než jeden název smlouvy, jenom koncové body služby odpovídající všechny kontrakty odpovíte.</span><span class="sxs-lookup"><span data-stu-id="c7295-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="c7295-104">Všimněte si, že ve Windows Communication Foundation (WCF), koncový bod podporuje pouze jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="c7295-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="c7295-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c7295-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="c7295-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="c7295-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7295-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7295-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7295-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c7295-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c7295-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c7295-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7295-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c7295-110">Attributes</span></span>  
 <span data-ttu-id="c7295-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="c7295-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c7295-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c7295-112">Child Elements</span></span>  
  
|<span data-ttu-id="c7295-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="c7295-113">Element</span></span>|<span data-ttu-id="c7295-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c7295-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7295-115">\<add></span><span class="sxs-lookup"><span data-stu-id="c7295-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="c7295-116">Název typu kontraktu je vlastnost, která odkazuje na sadu kritérií, obvykle používá při vyhledávání pro službu.</span><span class="sxs-lookup"><span data-stu-id="c7295-116">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c7295-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c7295-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c7295-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="c7295-118">Element</span></span>|<span data-ttu-id="c7295-119">Popis</span><span class="sxs-lookup"><span data-stu-id="c7295-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7295-120">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="c7295-120">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="c7295-121">Konfigurace element, který dodává sadu kritérií pro službu zjišťování používá klientská aplikace pro hledání.</span><span class="sxs-lookup"><span data-stu-id="c7295-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="c7295-122">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a nalézt ukončení kritéria (jak dlouho vyhledávání by měl trvat).</span><span class="sxs-lookup"><span data-stu-id="c7295-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7295-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7295-123">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
