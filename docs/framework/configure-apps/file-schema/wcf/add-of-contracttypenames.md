---
title: '&lt;add&gt; – &lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 79972eaea6918b3fe923c963b6a219fd8f972516
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145611"
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="78ec1-102">&lt;add&gt; – &lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="78ec1-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="78ec1-103">Konfigurace element, který určuje název kontraktu služby vyhledaly a kritéria obvykle používá při vyhledávání pro službu.</span><span class="sxs-lookup"><span data-stu-id="78ec1-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="78ec1-104">Pokud je zadán více než jeden název smlouvy, jenom koncové body služby odpovídající všechny kontrakty odpovíte.</span><span class="sxs-lookup"><span data-stu-id="78ec1-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="78ec1-105">Všimněte si, že ve Windows Communication Foundation (WCF), koncový bod podporuje pouze jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="78ec1-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="78ec1-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="78ec1-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="78ec1-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="78ec1-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78ec1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78ec1-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78ec1-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="78ec1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="78ec1-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="78ec1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78ec1-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="78ec1-111">Attributes</span></span>  
  
|<span data-ttu-id="78ec1-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="78ec1-112">Attribute</span></span>|<span data-ttu-id="78ec1-113">Popis</span><span class="sxs-lookup"><span data-stu-id="78ec1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78ec1-114">name</span><span class="sxs-lookup"><span data-stu-id="78ec1-114">name</span></span>|<span data-ttu-id="78ec1-115">Řetězec určující název typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="78ec1-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="78ec1-116">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="78ec1-116">namespace</span></span>|<span data-ttu-id="78ec1-117">Řetězec, který určuje obor názvů typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="78ec1-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78ec1-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="78ec1-118">Child Elements</span></span>  
 <span data-ttu-id="78ec1-119">Žádná</span><span class="sxs-lookup"><span data-stu-id="78ec1-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78ec1-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="78ec1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="78ec1-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="78ec1-121">Element</span></span>|<span data-ttu-id="78ec1-122">Popis</span><span class="sxs-lookup"><span data-stu-id="78ec1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78ec1-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="78ec1-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="78ec1-124">Kolekce názvů typů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="78ec1-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78ec1-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="78ec1-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
