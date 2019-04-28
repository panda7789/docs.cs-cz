---
title: <add> z <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 856298cb0639cf19b941f326b5b9a25aa6663088
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701187"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="56837-102">\<add> of \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="56837-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="56837-103">Konfigurace element, který určuje název kontraktu služby vyhledaly a kritéria obvykle používá při vyhledávání pro službu.</span><span class="sxs-lookup"><span data-stu-id="56837-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="56837-104">Pokud je zadán více než jeden název smlouvy, jenom koncové body služby odpovídající všechny kontrakty odpovíte.</span><span class="sxs-lookup"><span data-stu-id="56837-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="56837-105">Všimněte si, že ve Windows Communication Foundation (WCF), koncový bod podporuje pouze jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="56837-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="56837-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="56837-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="56837-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="56837-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56837-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56837-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56837-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="56837-109">Attributes and Elements</span></span>  
 <span data-ttu-id="56837-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="56837-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56837-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="56837-111">Attributes</span></span>  
  
|<span data-ttu-id="56837-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="56837-112">Attribute</span></span>|<span data-ttu-id="56837-113">Popis</span><span class="sxs-lookup"><span data-stu-id="56837-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="56837-114">name</span><span class="sxs-lookup"><span data-stu-id="56837-114">name</span></span>|<span data-ttu-id="56837-115">Řetězec určující název typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="56837-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="56837-116">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="56837-116">namespace</span></span>|<span data-ttu-id="56837-117">Řetězec, který určuje obor názvů typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="56837-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56837-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="56837-118">Child Elements</span></span>  
 <span data-ttu-id="56837-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="56837-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56837-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="56837-120">Parent Elements</span></span>  
  
|<span data-ttu-id="56837-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="56837-121">Element</span></span>|<span data-ttu-id="56837-122">Popis</span><span class="sxs-lookup"><span data-stu-id="56837-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56837-123">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="56837-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="56837-124">Kolekce názvů typů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="56837-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56837-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56837-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
