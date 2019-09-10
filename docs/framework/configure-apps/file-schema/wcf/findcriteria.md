---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 44e068ee205bc5e04382164e7ab00716b2c07dcf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855163"
---
# <a name="findcriteria"></a><span data-ttu-id="e24d4-101">\<Kritéria hledání ></span><span class="sxs-lookup"><span data-stu-id="e24d4-101">\<findCriteria></span></span>
<span data-ttu-id="e24d4-102">Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování.</span><span class="sxs-lookup"><span data-stu-id="e24d4-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="e24d4-103">Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).</span><span class="sxs-lookup"><span data-stu-id="e24d4-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
<span data-ttu-id="e24d4-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e24d4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e24d4-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e24d4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e24d4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="e24d4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="e24d4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="e24d4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="e24d4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Standardendpoint definovanému >** </span><span class="sxs-lookup"><span data-stu-id="e24d4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="e24d4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="e24d4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="e24d4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Kritéria hledání >**</span><span class="sxs-lookup"><span data-stu-id="e24d4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e24d4-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e24d4-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e24d4-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e24d4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e24d4-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e24d4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e24d4-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="e24d4-114">Attributes</span></span>  
  
|<span data-ttu-id="e24d4-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="e24d4-115">Attribute</span></span>|<span data-ttu-id="e24d4-116">Popis</span><span class="sxs-lookup"><span data-stu-id="e24d4-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e24d4-117">doba trvání</span><span class="sxs-lookup"><span data-stu-id="e24d4-117">duration</span></span>|<span data-ttu-id="e24d4-118">Hodnota TimeSpan, která určuje maximální dobu čekání na odpovědi ze služeb v síti.</span><span class="sxs-lookup"><span data-stu-id="e24d4-118">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="e24d4-119">Výchozí doba trvání je 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="e24d4-119">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="e24d4-120">maxResults</span><span class="sxs-lookup"><span data-stu-id="e24d4-120">maxResults</span></span>|<span data-ttu-id="e24d4-121">Celé číslo určující maximální počet odpovědí, na které se má čekat, ze služeb v síti nebo Internetu.</span><span class="sxs-lookup"><span data-stu-id="e24d4-121">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="e24d4-122">Pokud jsou přijaty maximální odpovědi před hodnotou zadanou v `duration` atributu, operace Find skončí.</span><span class="sxs-lookup"><span data-stu-id="e24d4-122">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="e24d4-123">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="e24d4-123">scopeMatchBy</span></span>|<span data-ttu-id="e24d4-124">Identifikátor URI, který určuje odpovídající algoritmus, který se má použít při porovnání oborů v rámci zprávy sondy s bodem koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e24d4-124">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="e24d4-125">Existuje pět podporovaných pravidel pro porovnání oboru.</span><span class="sxs-lookup"><span data-stu-id="e24d4-125">There are five supported scope-matching rules.</span></span> <span data-ttu-id="e24d4-126">Pokud neurčíte pravidlo pro porovnání s oborem, `ScopeMatchByPrefix` použije se.</span><span class="sxs-lookup"><span data-stu-id="e24d4-126">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="e24d4-127">Další informace o tomto naleznete v tématu <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="e24d4-127">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e24d4-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e24d4-128">Child Elements</span></span>  
  
|<span data-ttu-id="e24d4-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="e24d4-129">Element</span></span>|<span data-ttu-id="e24d4-130">Popis</span><span class="sxs-lookup"><span data-stu-id="e24d4-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e24d4-131">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="e24d4-131">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="e24d4-132">Kolekce elementů konfigurace, které obsahují názvy typů kontraktů služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e24d4-132">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="e24d4-133">\<rozšíření > \<kritéria hledání ></span><span class="sxs-lookup"><span data-stu-id="e24d4-133">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="e24d4-134">Kolekce objektů XML elementů, které poskytují rozšíření.</span><span class="sxs-lookup"><span data-stu-id="e24d4-134">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="e24d4-135">\<> oborů</span><span class="sxs-lookup"><span data-stu-id="e24d4-135">\<scopes></span></span>](scopes.md)|<span data-ttu-id="e24d4-136">Kolekce objektů, které obsahují absolutní identifikátory URI, které jsou použity během operace Find k vyhledání konkrétní služby nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="e24d4-136">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="e24d4-137">Pokud je nalezena konkrétní služba, byla provedena úspěšná shoda mezi identifikátorem URI služby a identifikátorem URI oboru, někdy s použitím pravidel oboru, které zpracovávají komplikace při porovnávání.</span><span class="sxs-lookup"><span data-stu-id="e24d4-137">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e24d4-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e24d4-138">Parent Elements</span></span>  
  
|<span data-ttu-id="e24d4-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="e24d4-139">Element</span></span>|<span data-ttu-id="e24d4-140">Popis</span><span class="sxs-lookup"><span data-stu-id="e24d4-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e24d4-141">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e24d4-141">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="e24d4-142">Obsahuje nastavení, která aplikace potřebuje k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="e24d4-142">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e24d4-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e24d4-143">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
