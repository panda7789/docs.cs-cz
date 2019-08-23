---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: eb8ff3905f7696f4c71a79e31db1b8f82c9f0d3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925582"
---
# <a name="findcriteria"></a><span data-ttu-id="f1760-101">\<Kritéria hledání ></span><span class="sxs-lookup"><span data-stu-id="f1760-101">\<findCriteria></span></span>
<span data-ttu-id="f1760-102">Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f1760-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="f1760-103">Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).</span><span class="sxs-lookup"><span data-stu-id="f1760-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="f1760-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f1760-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1760-105">\<Oddílu StandardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f1760-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1760-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1760-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1760-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f1760-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f1760-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f1760-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1760-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="f1760-109">Attributes</span></span>  
  
|<span data-ttu-id="f1760-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="f1760-110">Attribute</span></span>|<span data-ttu-id="f1760-111">Popis</span><span class="sxs-lookup"><span data-stu-id="f1760-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1760-112">doba trvání</span><span class="sxs-lookup"><span data-stu-id="f1760-112">duration</span></span>|<span data-ttu-id="f1760-113">Hodnota TimeSpan, která určuje maximální dobu čekání na odpovědi ze služeb v síti.</span><span class="sxs-lookup"><span data-stu-id="f1760-113">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="f1760-114">Výchozí doba trvání je 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="f1760-114">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="f1760-115">maxResults</span><span class="sxs-lookup"><span data-stu-id="f1760-115">maxResults</span></span>|<span data-ttu-id="f1760-116">Celé číslo určující maximální počet odpovědí, na které se má čekat, ze služeb v síti nebo Internetu.</span><span class="sxs-lookup"><span data-stu-id="f1760-116">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="f1760-117">Pokud jsou přijaty maximální odpovědi před hodnotou zadanou v `duration` atributu, operace Find skončí.</span><span class="sxs-lookup"><span data-stu-id="f1760-117">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="f1760-118">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="f1760-118">scopeMatchBy</span></span>|<span data-ttu-id="f1760-119">Identifikátor URI, který určuje odpovídající algoritmus, který se má použít při porovnání oborů v rámci zprávy sondy s bodem koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f1760-119">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="f1760-120">Existuje pět podporovaných pravidel pro porovnání oboru.</span><span class="sxs-lookup"><span data-stu-id="f1760-120">There are five supported scope-matching rules.</span></span> <span data-ttu-id="f1760-121">Pokud neurčíte pravidlo pro porovnání s oborem, `ScopeMatchByPrefix` použije se.</span><span class="sxs-lookup"><span data-stu-id="f1760-121">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="f1760-122">Další informace o tomto naleznete v tématu <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="f1760-122">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1760-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f1760-123">Child Elements</span></span>  
  
|<span data-ttu-id="f1760-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1760-124">Element</span></span>|<span data-ttu-id="f1760-125">Popis</span><span class="sxs-lookup"><span data-stu-id="f1760-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1760-126">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="f1760-126">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="f1760-127">Kolekce elementů konfigurace, které obsahují názvy typů kontraktů služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f1760-127">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="f1760-128">\<rozšíření > \<kritéria hledání ></span><span class="sxs-lookup"><span data-stu-id="f1760-128">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="f1760-129">Kolekce objektů XML elementů, které poskytují rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f1760-129">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="f1760-130">\<> oborů</span><span class="sxs-lookup"><span data-stu-id="f1760-130">\<scopes></span></span>](scopes.md)|<span data-ttu-id="f1760-131">Kolekce objektů, které obsahují absolutní identifikátory URI, které jsou použity během operace Find k vyhledání konkrétní služby nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="f1760-131">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="f1760-132">Pokud je nalezena konkrétní služba, byla provedena úspěšná shoda mezi identifikátorem URI služby a identifikátorem URI oboru, někdy s použitím pravidel oboru, které zpracovávají komplikace při porovnávání.</span><span class="sxs-lookup"><span data-stu-id="f1760-132">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1760-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f1760-133">Parent Elements</span></span>  
  
|<span data-ttu-id="f1760-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1760-134">Element</span></span>|<span data-ttu-id="f1760-135">Popis</span><span class="sxs-lookup"><span data-stu-id="f1760-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1760-136">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="f1760-136">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="f1760-137">Obsahuje nastavení, která aplikace potřebuje k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="f1760-137">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1760-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1760-138">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
