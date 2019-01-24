---
title: '&lt;findCriteria&gt;'
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: b90e6cab923075dbf750dc0d26a0eb1196cfde32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741236"
---
# <a name="ltfindcriteriagt"></a><span data-ttu-id="93444-102">&lt;findCriteria&gt;</span><span class="sxs-lookup"><span data-stu-id="93444-102">&lt;findCriteria&gt;</span></span>
<span data-ttu-id="93444-103">Konfigurace element, který dodává sadu kritérií pro službu zjišťování používá klientská aplikace pro hledání.</span><span class="sxs-lookup"><span data-stu-id="93444-103">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="93444-104">Kritéria mohou být seskupeny do kritéria vyhledávání (určení služby, kterou hledáte) a nalézt ukončení kritéria (jak dlouho vyhledávání by měl trvat).</span><span class="sxs-lookup"><span data-stu-id="93444-104">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="93444-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="93444-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="93444-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="93444-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93444-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93444-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93444-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="93444-108">Attributes and Elements</span></span>  
 <span data-ttu-id="93444-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="93444-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93444-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="93444-110">Attributes</span></span>  
  
|<span data-ttu-id="93444-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="93444-111">Attribute</span></span>|<span data-ttu-id="93444-112">Popis</span><span class="sxs-lookup"><span data-stu-id="93444-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93444-113">doba trvání</span><span class="sxs-lookup"><span data-stu-id="93444-113">duration</span></span>|<span data-ttu-id="93444-114">Časový interval hodnotu, která určuje maximální dobu čekání na odpovědi služby v síti.</span><span class="sxs-lookup"><span data-stu-id="93444-114">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="93444-115">Výchozí doba je 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="93444-115">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="93444-116">maxResults</span><span class="sxs-lookup"><span data-stu-id="93444-116">maxResults</span></span>|<span data-ttu-id="93444-117">Celé číslo určující maximální počet odpovědí čekat od služby v síti nebo Internetu.</span><span class="sxs-lookup"><span data-stu-id="93444-117">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="93444-118">Pokud se maximální odpovědi obdrženy předtím, než hodnota zadaná v `duration` atribut uplynul, skončí operace find.</span><span class="sxs-lookup"><span data-stu-id="93444-118">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="93444-119">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="93444-119">scopeMatchBy</span></span>|<span data-ttu-id="93444-120">Identifikátor URI určující porovnávací algoritmus, který bude použit při porovnání rozsahů průzkumné zprávy, která koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="93444-120">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="93444-121">Existují pravidla pět oboru odpovídajícím podporované.</span><span class="sxs-lookup"><span data-stu-id="93444-121">There are five supported scope-matching rules.</span></span> <span data-ttu-id="93444-122">Pokud nezadáte pravidlo odpovídající oboru `ScopeMatchByPrefix` se používá.</span><span class="sxs-lookup"><span data-stu-id="93444-122">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="93444-123">Další informace o tomto naleznete v tématu <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="93444-123">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93444-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="93444-124">Child Elements</span></span>  
  
|<span data-ttu-id="93444-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="93444-125">Element</span></span>|<span data-ttu-id="93444-126">Popis</span><span class="sxs-lookup"><span data-stu-id="93444-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93444-127">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="93444-127">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="93444-128">Kolekci elementů konfigurace, které obsahují názvy typů kontraktu služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="93444-128">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="93444-129">\<Rozšíření > z \<kritéria hledání ></span><span class="sxs-lookup"><span data-stu-id="93444-129">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="93444-130">Kolekce objektů – element XML, které poskytují rozšíření.</span><span class="sxs-lookup"><span data-stu-id="93444-130">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="93444-131">\<scopes></span><span class="sxs-lookup"><span data-stu-id="93444-131">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="93444-132">Kolekce objektů, které obsahují absolutní URI, které se používají během operace find k nalezení konkrétní služby nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="93444-132">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="93444-133">Pokud konkrétní služba nalezena, byl proveden úspěšná shoda mezi identifikátor URI služby a identifikátor URI oboru, někdy pomocí pravidel oboru, které zpracovávají komplikace párování.</span><span class="sxs-lookup"><span data-stu-id="93444-133">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93444-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="93444-134">Parent Elements</span></span>  
  
|<span data-ttu-id="93444-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="93444-135">Element</span></span>|<span data-ttu-id="93444-136">Popis</span><span class="sxs-lookup"><span data-stu-id="93444-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93444-137">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="93444-137">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="93444-138">Obsahuje nastavení potřeby aplikací a součástí procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="93444-138">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93444-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93444-139">See also</span></span>
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
