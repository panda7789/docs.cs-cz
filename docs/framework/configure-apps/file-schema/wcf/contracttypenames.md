---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 12f9d4eca02ae3b306646826667c4eafef51a95c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919375"
---
# <a name="contracttypenames"></a><span data-ttu-id="28b19-101">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="28b19-101">\<contractTypeNames></span></span>
<span data-ttu-id="28b19-102">Konfigurační oddíl, který určuje seznam názvů typů kontraktů, což jsou názvy kontraktů prohledávaných služeb a kritéria, která se obvykle používají při hledání služby.</span><span class="sxs-lookup"><span data-stu-id="28b19-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="28b19-103">Pokud je zadán více než jeden název kontraktu, odpoví pouze koncové body služby, které odpovídají všem smlouvám.</span><span class="sxs-lookup"><span data-stu-id="28b19-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="28b19-104">Všimněte si, že v Windows Communication Foundation (WCF) může koncový bod podporovat jenom jednu kontrakt.</span><span class="sxs-lookup"><span data-stu-id="28b19-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="28b19-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="28b19-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="28b19-106">\<Oddílu StandardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="28b19-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28b19-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28b19-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28b19-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="28b19-108">Attributes and Elements</span></span>  
 <span data-ttu-id="28b19-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="28b19-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28b19-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="28b19-110">Attributes</span></span>  
 <span data-ttu-id="28b19-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="28b19-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="28b19-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="28b19-112">Child Elements</span></span>  
  
|<span data-ttu-id="28b19-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="28b19-113">Element</span></span>|<span data-ttu-id="28b19-114">Popis</span><span class="sxs-lookup"><span data-stu-id="28b19-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28b19-115">\<add></span><span class="sxs-lookup"><span data-stu-id="28b19-115">\<add></span></span>](contracttypenames.md)|<span data-ttu-id="28b19-116">Název typu kontraktu je vlastnost, která odkazuje na sadu kritérií typicky používaných při hledání služby.</span><span class="sxs-lookup"><span data-stu-id="28b19-116">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28b19-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="28b19-117">Parent Elements</span></span>  
  
|<span data-ttu-id="28b19-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="28b19-118">Element</span></span>|<span data-ttu-id="28b19-119">Popis</span><span class="sxs-lookup"><span data-stu-id="28b19-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28b19-120">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="28b19-120">\<findCriteria></span></span>](findcriteria.md)|<span data-ttu-id="28b19-121">Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování.</span><span class="sxs-lookup"><span data-stu-id="28b19-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="28b19-122">Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).</span><span class="sxs-lookup"><span data-stu-id="28b19-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28b19-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28b19-123">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
