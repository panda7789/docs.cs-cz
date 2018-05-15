---
title: '&lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 99547967b65e5d7663ec11be98247e2018aaa34c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltcontracttypenamesgt"></a><span data-ttu-id="58f62-102">&lt;contractTypeNames&gt;</span><span class="sxs-lookup"><span data-stu-id="58f62-102">&lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="58f62-103">Konfigurační oddíl, který určuje seznam názvy typů smlouvy, které jsou názvy kontraktu služby se hledají, a kritéria pro službu obvykle používaných při hledání.</span><span class="sxs-lookup"><span data-stu-id="58f62-103">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="58f62-104">Pokud je zadán více než jeden název kontraktu, bude odpověď pouze koncové body služby odpovídající všechny smlouvy.</span><span class="sxs-lookup"><span data-stu-id="58f62-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="58f62-105">Všimněte si, že ve Windows Communication Foundation (WCF), koncový bod podporuje pouze jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="58f62-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="58f62-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="58f62-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="58f62-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="58f62-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58f62-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58f62-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58f62-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="58f62-109">Attributes and Elements</span></span>  
 <span data-ttu-id="58f62-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="58f62-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58f62-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="58f62-111">Attributes</span></span>  
 <span data-ttu-id="58f62-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="58f62-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="58f62-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="58f62-113">Child Elements</span></span>  
  
|<span data-ttu-id="58f62-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="58f62-114">Element</span></span>|<span data-ttu-id="58f62-115">Popis</span><span class="sxs-lookup"><span data-stu-id="58f62-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58f62-116">\<add></span><span class="sxs-lookup"><span data-stu-id="58f62-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="58f62-117">Název typu kontraktu je vlastnost, která odkazuje na sadu kritérií, na které se obvykle používá při vyhledávání pro službu.</span><span class="sxs-lookup"><span data-stu-id="58f62-117">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58f62-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="58f62-118">Parent Elements</span></span>  
  
|<span data-ttu-id="58f62-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="58f62-119">Element</span></span>|<span data-ttu-id="58f62-120">Popis</span><span class="sxs-lookup"><span data-stu-id="58f62-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58f62-121">\<kritéria hledání ></span><span class="sxs-lookup"><span data-stu-id="58f62-121">\<findCriteria></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|<span data-ttu-id="58f62-122">Konfigurace element, který poskytuje sadu kritérií používané klientskou aplikaci pro vyhledávání pro službu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="58f62-122">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="58f62-123">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a najděte ukončení kritéria (jak dlouho by měl poslední hledání).</span><span class="sxs-lookup"><span data-stu-id="58f62-123">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58f62-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="58f62-124">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
