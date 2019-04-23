---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: eaa3998d3d0b1642c0c92380ec1228eea69d4da8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129548"
---
# <a name="findcriteria"></a><span data-ttu-id="b2962-101">\<kritéria hledání ></span><span class="sxs-lookup"><span data-stu-id="b2962-101">\<findCriteria></span></span>
<span data-ttu-id="b2962-102">Konfigurace element, který dodává sadu kritérií pro službu zjišťování používá klientská aplikace pro hledání.</span><span class="sxs-lookup"><span data-stu-id="b2962-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="b2962-103">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a nalézt ukončení kritéria (jak dlouho vyhledávání by měl trvat).</span><span class="sxs-lookup"><span data-stu-id="b2962-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="b2962-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b2962-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b2962-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="b2962-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2962-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2962-106">Syntax</span></span>  
  
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
            </contractTypeNames>
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2962-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b2962-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b2962-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b2962-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2962-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="b2962-109">Attributes</span></span>  
  
|<span data-ttu-id="b2962-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="b2962-110">Attribute</span></span>|<span data-ttu-id="b2962-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b2962-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2962-112">doba trvání</span><span class="sxs-lookup"><span data-stu-id="b2962-112">duration</span></span>|<span data-ttu-id="b2962-113">Časový interval hodnotu, která určuje maximální dobu čekání na odpovědi služby v síti.</span><span class="sxs-lookup"><span data-stu-id="b2962-113">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="b2962-114">Výchozí doba je 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="b2962-114">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="b2962-115">maxResults</span><span class="sxs-lookup"><span data-stu-id="b2962-115">maxResults</span></span>|<span data-ttu-id="b2962-116">Celé číslo určující maximální počet odpovědí čekat od služby v síti nebo Internetu.</span><span class="sxs-lookup"><span data-stu-id="b2962-116">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="b2962-117">Pokud se maximální odpovědi obdrženy předtím, než hodnota zadaná v `duration` atribut uplynul, skončí operace find.</span><span class="sxs-lookup"><span data-stu-id="b2962-117">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="b2962-118">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="b2962-118">scopeMatchBy</span></span>|<span data-ttu-id="b2962-119">Identifikátor URI určující porovnávací algoritmus, který bude použit při porovnání rozsahů průzkumné zprávy, která koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b2962-119">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="b2962-120">Existují pravidla pět oboru odpovídajícím podporované.</span><span class="sxs-lookup"><span data-stu-id="b2962-120">There are five supported scope-matching rules.</span></span> <span data-ttu-id="b2962-121">Pokud nezadáte pravidlo odpovídající oboru `ScopeMatchByPrefix` se používá.</span><span class="sxs-lookup"><span data-stu-id="b2962-121">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="b2962-122">Další informace o tomto naleznete v tématu <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="b2962-122">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2962-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b2962-123">Child Elements</span></span>  
  
|<span data-ttu-id="b2962-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="b2962-124">Element</span></span>|<span data-ttu-id="b2962-125">Popis</span><span class="sxs-lookup"><span data-stu-id="b2962-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2962-126">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="b2962-126">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="b2962-127">Kolekci elementů konfigurace, které obsahují názvy typů kontraktu služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b2962-127">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="b2962-128">\<Rozšíření > z \<kritéria hledání ></span><span class="sxs-lookup"><span data-stu-id="b2962-128">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="b2962-129">Kolekce objektů – element XML, které poskytují rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b2962-129">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="b2962-130">\<scopes></span><span class="sxs-lookup"><span data-stu-id="b2962-130">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="b2962-131">Kolekce objektů, které obsahují absolutní URI, které se používají během operace find k nalezení konkrétní služby nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="b2962-131">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="b2962-132">Pokud konkrétní služba nalezena, byl proveden úspěšná shoda mezi identifikátor URI služby a identifikátor URI oboru, někdy pomocí pravidel oboru, které zpracovávají komplikace párování.</span><span class="sxs-lookup"><span data-stu-id="b2962-132">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2962-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b2962-133">Parent Elements</span></span>  
  
|<span data-ttu-id="b2962-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="b2962-134">Element</span></span>|<span data-ttu-id="b2962-135">Popis</span><span class="sxs-lookup"><span data-stu-id="b2962-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2962-136">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="b2962-136">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="b2962-137">Obsahuje nastavení potřeby aplikací a součástí procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="b2962-137">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2962-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2962-138">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
