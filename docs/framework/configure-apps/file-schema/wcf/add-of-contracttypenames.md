---
title: <add> z <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 696752470aa39c2bcc66a1337f84119031742ae9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850534"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="5728f-102">\<add> of \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="5728f-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="5728f-103">Prvek konfigurace, který určuje název kontraktu prohledávaných služeb a kritéria, která se obvykle používají při hledání služby.</span><span class="sxs-lookup"><span data-stu-id="5728f-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="5728f-104">Pokud je zadán více než jeden název kontraktu, odpoví pouze koncové body služby, které odpovídají všem smlouvám.</span><span class="sxs-lookup"><span data-stu-id="5728f-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="5728f-105">Všimněte si, že v Windows Communication Foundation (WCF) může koncový bod podporovat jenom jednu kontrakt.</span><span class="sxs-lookup"><span data-stu-id="5728f-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
<span data-ttu-id="5728f-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5728f-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5728f-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5728f-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5728f-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="5728f-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="5728f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="5728f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="5728f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Standardendpoint definovanému >** </span><span class="sxs-lookup"><span data-stu-id="5728f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="5728f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="5728f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="5728f-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Kritéria hledání >** ](findcriteria.md)</span><span class="sxs-lookup"><span data-stu-id="5728f-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)</span></span>\
<span data-ttu-id="5728f-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<contractTypeNames >** ](contracttypenames.md)</span><span class="sxs-lookup"><span data-stu-id="5728f-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)</span></span>\
<span data-ttu-id="5728f-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="5728f-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5728f-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5728f-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5728f-116">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5728f-116">Attributes and Elements</span></span>  
 <span data-ttu-id="5728f-117">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5728f-117">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5728f-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="5728f-118">Attributes</span></span>  
  
|<span data-ttu-id="5728f-119">Atribut</span><span class="sxs-lookup"><span data-stu-id="5728f-119">Attribute</span></span>|<span data-ttu-id="5728f-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5728f-120">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5728f-121">name</span><span class="sxs-lookup"><span data-stu-id="5728f-121">name</span></span>|<span data-ttu-id="5728f-122">Řetězec, který určuje název typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="5728f-122">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="5728f-123">– obor názvů</span><span class="sxs-lookup"><span data-stu-id="5728f-123">namespace</span></span>|<span data-ttu-id="5728f-124">Řetězec, který určuje obor názvů typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="5728f-124">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5728f-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5728f-125">Child Elements</span></span>  
 <span data-ttu-id="5728f-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="5728f-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5728f-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5728f-127">Parent Elements</span></span>  
  
|<span data-ttu-id="5728f-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="5728f-128">Element</span></span>|<span data-ttu-id="5728f-129">Popis</span><span class="sxs-lookup"><span data-stu-id="5728f-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5728f-130">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="5728f-130">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="5728f-131">Kolekce názvů typů kontraktů.</span><span class="sxs-lookup"><span data-stu-id="5728f-131">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5728f-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5728f-132">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
