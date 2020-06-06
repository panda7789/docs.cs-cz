---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 44e068ee205bc5e04382164e7ab00716b2c07dcf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855163"
---
# \<findCriteria>
<span data-ttu-id="7cc94-101">Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování.</span><span class="sxs-lookup"><span data-stu-id="7cc94-101">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="7cc94-102">Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).</span><span class="sxs-lookup"><span data-stu-id="7cc94-102">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**  
  
## <a name="syntax"></a><span data-ttu-id="7cc94-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cc94-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cc94-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7cc94-104">Attributes and Elements</span></span>  
 <span data-ttu-id="7cc94-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7cc94-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cc94-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="7cc94-106">Attributes</span></span>  
  
|<span data-ttu-id="7cc94-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="7cc94-107">Attribute</span></span>|<span data-ttu-id="7cc94-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7cc94-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7cc94-109">doba trvání</span><span class="sxs-lookup"><span data-stu-id="7cc94-109">duration</span></span>|<span data-ttu-id="7cc94-110">Hodnota TimeSpan, která určuje maximální dobu čekání na odpovědi ze služeb v síti.</span><span class="sxs-lookup"><span data-stu-id="7cc94-110">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="7cc94-111">Výchozí doba trvání je 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="7cc94-111">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="7cc94-112">maxResults</span><span class="sxs-lookup"><span data-stu-id="7cc94-112">maxResults</span></span>|<span data-ttu-id="7cc94-113">Celé číslo určující maximální počet odpovědí, na které se má čekat, ze služeb v síti nebo Internetu.</span><span class="sxs-lookup"><span data-stu-id="7cc94-113">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="7cc94-114">Pokud jsou přijaty maximální odpovědi před hodnotou zadanou v `duration` atributu, operace Find skončí.</span><span class="sxs-lookup"><span data-stu-id="7cc94-114">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="7cc94-115">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="7cc94-115">scopeMatchBy</span></span>|<span data-ttu-id="7cc94-116">Identifikátor URI, který určuje odpovídající algoritmus, který se má použít při porovnání oborů v rámci zprávy sondy s bodem koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7cc94-116">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="7cc94-117">Existuje pět podporovaných pravidel pro porovnání oboru.</span><span class="sxs-lookup"><span data-stu-id="7cc94-117">There are five supported scope-matching rules.</span></span> <span data-ttu-id="7cc94-118">Pokud neurčíte pravidlo pro porovnání s oborem, `ScopeMatchByPrefix` použije se.</span><span class="sxs-lookup"><span data-stu-id="7cc94-118">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="7cc94-119">Další informace o tomto naleznete v tématu <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="7cc94-119">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7cc94-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7cc94-120">Child Elements</span></span>  
  
|<span data-ttu-id="7cc94-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="7cc94-121">Element</span></span>|<span data-ttu-id="7cc94-122">Description</span><span class="sxs-lookup"><span data-stu-id="7cc94-122">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="7cc94-123">Kolekce elementů konfigurace, které obsahují názvy typů kontraktů služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7cc94-123">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="7cc94-124">\<extensions> z \<findCriteria></span><span class="sxs-lookup"><span data-stu-id="7cc94-124">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="7cc94-125">Kolekce objektů XML elementů, které poskytují rozšíření.</span><span class="sxs-lookup"><span data-stu-id="7cc94-125">A collection of XML element objects that provide extensions.</span></span>|  
|[\<scopes>](scopes.md)|<span data-ttu-id="7cc94-126">Kolekce objektů, které obsahují absolutní identifikátory URI, které jsou použity během operace Find k vyhledání konkrétní služby nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="7cc94-126">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="7cc94-127">Pokud je nalezena konkrétní služba, byla provedena úspěšná shoda mezi identifikátorem URI služby a identifikátorem URI oboru, někdy s použitím pravidel oboru, které zpracovávají komplikace při porovnávání.</span><span class="sxs-lookup"><span data-stu-id="7cc94-127">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7cc94-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7cc94-128">Parent Elements</span></span>  
  
|<span data-ttu-id="7cc94-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="7cc94-129">Element</span></span>|<span data-ttu-id="7cc94-130">Description</span><span class="sxs-lookup"><span data-stu-id="7cc94-130">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="7cc94-131">Obsahuje nastavení, která aplikace potřebuje k účasti v procesu zjišťování služby jako klient.</span><span class="sxs-lookup"><span data-stu-id="7cc94-131">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7cc94-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cc94-132">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
