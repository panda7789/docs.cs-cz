---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: c67e5b9e82b96e27ce73512680bd4236b26ef4dd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855448"
---
# <a name="contracttypenames"></a><span data-ttu-id="3be08-101">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="3be08-101">\<contractTypeNames></span></span>
<span data-ttu-id="3be08-102">Konfigurační oddíl, který určuje seznam názvů typů kontraktů, což jsou názvy kontraktů prohledávaných služeb a kritéria, která se obvykle používají při hledání služby.</span><span class="sxs-lookup"><span data-stu-id="3be08-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="3be08-103">Pokud je zadán více než jeden název kontraktu, odpoví pouze koncové body služby, které odpovídají všem smlouvám.</span><span class="sxs-lookup"><span data-stu-id="3be08-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="3be08-104">Všimněte si, že v Windows Communication Foundation (WCF) může koncový bod podporovat jenom jednu kontrakt.</span><span class="sxs-lookup"><span data-stu-id="3be08-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
<span data-ttu-id="3be08-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3be08-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3be08-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3be08-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3be08-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="3be08-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="3be08-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="3be08-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="3be08-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Standardendpoint definovanému >** </span><span class="sxs-lookup"><span data-stu-id="3be08-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="3be08-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="3be08-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="3be08-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Kritéria hledání >** ](findcriteria.md)</span><span class="sxs-lookup"><span data-stu-id="3be08-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)</span></span>\
<span data-ttu-id="3be08-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<contractTypeNames >**</span><span class="sxs-lookup"><span data-stu-id="3be08-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<contractTypeNames>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3be08-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3be08-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3be08-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3be08-114">Attributes and Elements</span></span>  
 <span data-ttu-id="3be08-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3be08-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3be08-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="3be08-116">Attributes</span></span>  
 <span data-ttu-id="3be08-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="3be08-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3be08-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3be08-118">Child Elements</span></span>  
  
|<span data-ttu-id="3be08-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="3be08-119">Element</span></span>|<span data-ttu-id="3be08-120">Popis</span><span class="sxs-lookup"><span data-stu-id="3be08-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3be08-121">\<add></span><span class="sxs-lookup"><span data-stu-id="3be08-121">\<add></span></span>](contracttypenames.md)|<span data-ttu-id="3be08-122">Název typu kontraktu je vlastnost, která odkazuje na sadu kritérií typicky používaných při hledání služby.</span><span class="sxs-lookup"><span data-stu-id="3be08-122">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3be08-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3be08-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3be08-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3be08-124">Element</span></span>|<span data-ttu-id="3be08-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3be08-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3be08-126">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="3be08-126">\<findCriteria></span></span>](findcriteria.md)|<span data-ttu-id="3be08-127">Prvek konfigurace, který poskytuje sadu kritérií používaných klientskou aplikací pro hledání služby zjišťování.</span><span class="sxs-lookup"><span data-stu-id="3be08-127">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="3be08-128">Kritéria se dají seskupit do vyhledávacích kritérií (určení služeb, které hledáte), a najít kritéria ukončení (jak dlouho má hledání trvat).</span><span class="sxs-lookup"><span data-stu-id="3be08-128">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3be08-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3be08-129">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
