---
title: <add> of <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 856298cb0639cf19b941f326b5b9a25aa6663088
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091314"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="4720a-102">\<add> of \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="4720a-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="4720a-103">Konfigurace element, který určuje název kontraktu služby vyhledaly a kritéria obvykle používá při vyhledávání pro službu.</span><span class="sxs-lookup"><span data-stu-id="4720a-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="4720a-104">Pokud je zadán více než jeden název smlouvy, jenom koncové body služby odpovídající všechny kontrakty odpovíte.</span><span class="sxs-lookup"><span data-stu-id="4720a-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="4720a-105">Všimněte si, že ve Windows Communication Foundation (WCF), koncový bod podporuje pouze jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="4720a-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="4720a-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4720a-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="4720a-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="4720a-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4720a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4720a-108">Syntax</span></span>  
  
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
              <add name="String" namespace="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4720a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4720a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4720a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4720a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4720a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4720a-111">Attributes</span></span>  
  
|<span data-ttu-id="4720a-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="4720a-112">Attribute</span></span>|<span data-ttu-id="4720a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4720a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4720a-114">name</span><span class="sxs-lookup"><span data-stu-id="4720a-114">name</span></span>|<span data-ttu-id="4720a-115">Řetězec určující název typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4720a-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="4720a-116">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="4720a-116">namespace</span></span>|<span data-ttu-id="4720a-117">Řetězec, který určuje obor názvů typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4720a-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4720a-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4720a-118">Child Elements</span></span>  
 <span data-ttu-id="4720a-119">Žádný</span><span class="sxs-lookup"><span data-stu-id="4720a-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4720a-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4720a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4720a-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="4720a-121">Element</span></span>|<span data-ttu-id="4720a-122">Popis</span><span class="sxs-lookup"><span data-stu-id="4720a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4720a-123">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="4720a-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="4720a-124">Kolekce názvů typů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4720a-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4720a-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4720a-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
