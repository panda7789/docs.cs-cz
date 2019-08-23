---
title: <add> z <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 24f1478b99aef909ae93f87a70be257e9ba10d7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926740"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="22d08-102">\<add> of \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="22d08-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="22d08-103">Prvek konfigurace, který určuje název kontraktu prohledávaných služeb a kritéria, která se obvykle používají při hledání služby.</span><span class="sxs-lookup"><span data-stu-id="22d08-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="22d08-104">Pokud je zadán více než jeden název kontraktu, odpoví pouze koncové body služby, které odpovídají všem smlouvám.</span><span class="sxs-lookup"><span data-stu-id="22d08-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="22d08-105">Všimněte si, že v Windows Communication Foundation (WCF) může koncový bod podporovat jenom jednu kontrakt.</span><span class="sxs-lookup"><span data-stu-id="22d08-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="22d08-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="22d08-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="22d08-107">\<Oddílu StandardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="22d08-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d08-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22d08-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22d08-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="22d08-109">Attributes and Elements</span></span>  
 <span data-ttu-id="22d08-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="22d08-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22d08-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="22d08-111">Attributes</span></span>  
  
|<span data-ttu-id="22d08-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="22d08-112">Attribute</span></span>|<span data-ttu-id="22d08-113">Popis</span><span class="sxs-lookup"><span data-stu-id="22d08-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22d08-114">name</span><span class="sxs-lookup"><span data-stu-id="22d08-114">name</span></span>|<span data-ttu-id="22d08-115">Řetězec, který určuje název typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="22d08-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="22d08-116">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="22d08-116">namespace</span></span>|<span data-ttu-id="22d08-117">Řetězec, který určuje obor názvů typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="22d08-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22d08-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="22d08-118">Child Elements</span></span>  
 <span data-ttu-id="22d08-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="22d08-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22d08-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="22d08-120">Parent Elements</span></span>  
  
|<span data-ttu-id="22d08-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="22d08-121">Element</span></span>|<span data-ttu-id="22d08-122">Popis</span><span class="sxs-lookup"><span data-stu-id="22d08-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22d08-123">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="22d08-123">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="22d08-124">Kolekce názvů typů kontraktů.</span><span class="sxs-lookup"><span data-stu-id="22d08-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22d08-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22d08-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
