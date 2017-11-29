---
title: '&lt;contractTypeNames&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 95be974404fdd845ee3a24bb194e9ba5e890147d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcontracttypenamesgt"></a><span data-ttu-id="0444c-102">&lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="0444c-102">&lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="0444c-103">Konfigurační oddíl, který určuje seznam názvy typů smlouvy, které jsou názvy kontraktu služby se hledají, a kritéria pro službu obvykle používaných při hledání.</span><span class="sxs-lookup"><span data-stu-id="0444c-103">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="0444c-104">Pokud je zadán více než jeden název kontraktu, bude odpověď pouze koncové body služby odpovídající všechny smlouvy.</span><span class="sxs-lookup"><span data-stu-id="0444c-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="0444c-105">Všimněte si, že v [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], koncový bod podporuje pouze jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="0444c-105">Note that in [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="0444c-106">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0444c-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="0444c-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0444c-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0444c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0444c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0444c-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0444c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0444c-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0444c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0444c-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="0444c-111">Attributes</span></span>  
 <span data-ttu-id="0444c-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="0444c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0444c-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0444c-113">Child Elements</span></span>  
  
|<span data-ttu-id="0444c-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="0444c-114">Element</span></span>|<span data-ttu-id="0444c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="0444c-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0444c-116">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="0444c-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="0444c-117">Název typu kontraktu je vlastnost, která odkazuje na sadu kritérií, na které se obvykle používá při vyhledávání pro službu.</span><span class="sxs-lookup"><span data-stu-id="0444c-117">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0444c-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0444c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0444c-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="0444c-119">Element</span></span>|<span data-ttu-id="0444c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="0444c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0444c-121">\<kritéria hledání ></span><span class="sxs-lookup"><span data-stu-id="0444c-121">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="0444c-122">Konfigurace element, který poskytuje sadu kritérií používané klientskou aplikaci pro vyhledávání pro službu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="0444c-122">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="0444c-123">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a najděte ukončení kritéria (jak dlouho by měl poslední hledání).</span><span class="sxs-lookup"><span data-stu-id="0444c-123">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0444c-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="0444c-124">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
