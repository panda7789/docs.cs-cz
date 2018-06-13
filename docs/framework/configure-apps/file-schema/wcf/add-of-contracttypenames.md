---
title: '&lt;add&gt; – &lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 159ab5a40a69c075b648a0c161babe604d13377b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750190"
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="4dcf2-102">&lt;add&gt; – &lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="4dcf2-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="4dcf2-103">Konfigurace element, který určuje název kontraktu služby vyhledána a kritéria pro službu obvykle používaných při hledání.</span><span class="sxs-lookup"><span data-stu-id="4dcf2-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="4dcf2-104">Pokud je zadán více než jeden název kontraktu, bude odpověď pouze koncové body služby odpovídající všechny smlouvy.</span><span class="sxs-lookup"><span data-stu-id="4dcf2-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="4dcf2-105">Všimněte si, že ve Windows Communication Foundation (WCF), koncový bod podporuje pouze jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="4dcf2-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="4dcf2-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4dcf2-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="4dcf2-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="4dcf2-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dcf2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4dcf2-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <dynamicEndpoint>           <standardEndpoint>             <discoveryClientSettings discoveryEndpoint="String" >               <findCriteria duration="TimeSpan"                  maxResults="Integer"                   scopeMatchBy="Uri" >                  <contractTypeNames>                     <add name="String" namespace="String" />                  <contractTypeNames>                  <extensions />                  <scopes>                    <add scope="URI"/>                  </scopes>               </findCriteria>             </discoveryClientSettings>          <standardEndpoint>       </dynamicEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dcf2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4dcf2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4dcf2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4dcf2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dcf2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4dcf2-111">Attributes</span></span>  
  
|<span data-ttu-id="4dcf2-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="4dcf2-112">Attribute</span></span>|<span data-ttu-id="4dcf2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4dcf2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4dcf2-114">name</span><span class="sxs-lookup"><span data-stu-id="4dcf2-114">name</span></span>|<span data-ttu-id="4dcf2-115">Řetězec, který určuje název typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4dcf2-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="4dcf2-116">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="4dcf2-116">namespace</span></span>|<span data-ttu-id="4dcf2-117">Řetězec, který určuje obor názvů typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4dcf2-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4dcf2-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4dcf2-118">Child Elements</span></span>  
 <span data-ttu-id="4dcf2-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="4dcf2-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4dcf2-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4dcf2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4dcf2-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="4dcf2-121">Element</span></span>|<span data-ttu-id="4dcf2-122">Popis</span><span class="sxs-lookup"><span data-stu-id="4dcf2-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4dcf2-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="4dcf2-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="4dcf2-124">Kolekce názvy typů kontrakt.</span><span class="sxs-lookup"><span data-stu-id="4dcf2-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4dcf2-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="4dcf2-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
