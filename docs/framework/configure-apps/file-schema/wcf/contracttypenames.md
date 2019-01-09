---
title: '&lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 60647e6ec31e7228f09d084ff669a1829770ca14
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144713"
---
# <a name="ltcontracttypenamesgt"></a><span data-ttu-id="7478c-102">&lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="7478c-102">&lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="7478c-103">Konfigurační oddíl, který určuje seznam názvy typu smlouvy, které jsou názvy kontraktů služeb vyhledaly a kritéria obvykle používá při vyhledávání pro službu.</span><span class="sxs-lookup"><span data-stu-id="7478c-103">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="7478c-104">Pokud je zadán více než jeden název smlouvy, jenom koncové body služby odpovídající všechny kontrakty odpovíte.</span><span class="sxs-lookup"><span data-stu-id="7478c-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="7478c-105">Všimněte si, že ve Windows Communication Foundation (WCF), koncový bod podporuje pouze jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="7478c-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="7478c-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7478c-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="7478c-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="7478c-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7478c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7478c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7478c-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7478c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7478c-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7478c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7478c-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="7478c-111">Attributes</span></span>  
 <span data-ttu-id="7478c-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="7478c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7478c-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7478c-113">Child Elements</span></span>  
  
|<span data-ttu-id="7478c-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="7478c-114">Element</span></span>|<span data-ttu-id="7478c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="7478c-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7478c-116">\<add></span><span class="sxs-lookup"><span data-stu-id="7478c-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="7478c-117">Název typu kontraktu je vlastnost, která odkazuje na sadu kritérií, obvykle používá při vyhledávání pro službu.</span><span class="sxs-lookup"><span data-stu-id="7478c-117">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7478c-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7478c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7478c-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="7478c-119">Element</span></span>|<span data-ttu-id="7478c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="7478c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7478c-121">\<kritéria hledání ></span><span class="sxs-lookup"><span data-stu-id="7478c-121">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="7478c-122">Konfigurace element, který dodává sadu kritérií pro službu zjišťování používá klientská aplikace pro hledání.</span><span class="sxs-lookup"><span data-stu-id="7478c-122">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="7478c-123">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a nalézt ukončení kritéria (jak dlouho vyhledávání by měl trvat).</span><span class="sxs-lookup"><span data-stu-id="7478c-123">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7478c-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="7478c-124">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
