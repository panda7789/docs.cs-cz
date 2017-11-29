---
title: "&lt;kritéria hledání&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b428d1a95ec6f1f493c831f66223f52e4723990c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltfindcriteriagt"></a><span data-ttu-id="f891f-102">&lt;kritéria hledání&gt;</span><span class="sxs-lookup"><span data-stu-id="f891f-102">&lt;findCriteria&gt;</span></span>
<span data-ttu-id="f891f-103">Konfigurace element, který poskytuje sadu kritérií používané klientskou aplikaci pro vyhledávání pro službu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f891f-103">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="f891f-104">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a najděte ukončení kritéria (jak dlouho by měl poslední hledání).</span><span class="sxs-lookup"><span data-stu-id="f891f-104">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="f891f-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f891f-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f891f-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f891f-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f891f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f891f-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f891f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f891f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f891f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f891f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f891f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f891f-110">Attributes</span></span>  
  
|<span data-ttu-id="f891f-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f891f-111">Attribute</span></span>|<span data-ttu-id="f891f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f891f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f891f-113">doba trvání</span><span class="sxs-lookup"><span data-stu-id="f891f-113">duration</span></span>|<span data-ttu-id="f891f-114">Hodnota časového rozpětí, která určuje maximální dobu čekání na odpovědi od služby v síti.</span><span class="sxs-lookup"><span data-stu-id="f891f-114">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="f891f-115">Výchozí doba je 20 sekund...</span><span class="sxs-lookup"><span data-stu-id="f891f-115">The default duration is 20 seconds..</span></span>|  
|<span data-ttu-id="f891f-116">shluku</span><span class="sxs-lookup"><span data-stu-id="f891f-116">maxResults</span></span>|<span data-ttu-id="f891f-117">Celé číslo, které určuje maximální počet odpovědí čekat, služby v síti nebo Internetu.</span><span class="sxs-lookup"><span data-stu-id="f891f-117">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="f891f-118">Pokud jsou odpovědi maximální obdrženy předtím, než hodnota zadaná v `duration` atribut uplynul, skončení operace hledání.</span><span class="sxs-lookup"><span data-stu-id="f891f-118">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="f891f-119">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="f891f-119">scopeMatchBy</span></span>|<span data-ttu-id="f891f-120">Identifikátor URI, který zadejte odpovídající algoritmus použitý při odpovídající obory ve zprávě test s u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f891f-120">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="f891f-121">Existují pravidla pět odpovídající oboru podporované.</span><span class="sxs-lookup"><span data-stu-id="f891f-121">There are five supported scope-matching rules.</span></span> <span data-ttu-id="f891f-122">Pokud nezadáte oboru odpovídající pravidlo, `ScopeMatchByPrefix` se používá.</span><span class="sxs-lookup"><span data-stu-id="f891f-122">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="f891f-123">Další informace o tomto naleznete v tématu <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="f891f-123">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f891f-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f891f-124">Child Elements</span></span>  
  
|<span data-ttu-id="f891f-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="f891f-125">Element</span></span>|<span data-ttu-id="f891f-126">Popis</span><span class="sxs-lookup"><span data-stu-id="f891f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f891f-127">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="f891f-127">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="f891f-128">Kolekci elementů konfigurace, které obsahují názvy typů kontraktu služby pracovního postupu...</span><span class="sxs-lookup"><span data-stu-id="f891f-128">A collection of configuration elements that contain the names of workflow service contract types..</span></span>|  
|<span data-ttu-id="f891f-129">\<Rozšíření > z \<kritéria hledání ></span><span class="sxs-lookup"><span data-stu-id="f891f-129">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="f891f-130">Kolekce objektů elementu XML, které poskytují rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f891f-130">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="f891f-131">\<obory ></span><span class="sxs-lookup"><span data-stu-id="f891f-131">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="f891f-132">Kolekce objektů, které obsahují absolutní identifikátory URI, které se používají během operace hledání pro vyhledání konkrétní služby nebo služby.</span><span class="sxs-lookup"><span data-stu-id="f891f-132">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="f891f-133">Pokud je nalezen konkrétní službu, byl proveden úspěšně shody mezi URI služby a identifikátor URI oboru, někdy pomocí pravidel rozsahu, které zpracovávají komplikace odpovídajících.</span><span class="sxs-lookup"><span data-stu-id="f891f-133">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f891f-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f891f-134">Parent Elements</span></span>  
  
|<span data-ttu-id="f891f-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="f891f-135">Element</span></span>|<span data-ttu-id="f891f-136">Popis</span><span class="sxs-lookup"><span data-stu-id="f891f-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f891f-137">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f891f-137">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f891f-138">Obsahuje nastavení vyžadovaná aplikace k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="f891f-138">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f891f-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="f891f-139">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
