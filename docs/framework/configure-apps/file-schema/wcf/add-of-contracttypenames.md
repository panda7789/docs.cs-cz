---
title: <add> z <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 696752470aa39c2bcc66a1337f84119031742ae9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850534"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="ba1cf-102">\<add> z \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="ba1cf-102">\<add> of \<contractTypeNames></span></span>
<span data-ttu-id="ba1cf-103">Prvek konfigurace, který určuje název kontraktu prohledávaných služeb a kritéria, která se obvykle používají při hledání služby.</span><span class="sxs-lookup"><span data-stu-id="ba1cf-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="ba1cf-104">Pokud je zadán více než jeden název kontraktu, odpoví pouze koncové body služby, které odpovídají všem smlouvám.</span><span class="sxs-lookup"><span data-stu-id="ba1cf-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="ba1cf-105">Všimněte si, že v Windows Communication Foundation (WCF) může koncový bod podporovat jenom jednu kontrakt.</span><span class="sxs-lookup"><span data-stu-id="ba1cf-105">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ba1cf-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba1cf-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba1cf-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ba1cf-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ba1cf-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ba1cf-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba1cf-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="ba1cf-109">Attributes</span></span>  
  
|<span data-ttu-id="ba1cf-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="ba1cf-110">Attribute</span></span>|<span data-ttu-id="ba1cf-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ba1cf-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba1cf-112">name</span><span class="sxs-lookup"><span data-stu-id="ba1cf-112">name</span></span>|<span data-ttu-id="ba1cf-113">Řetězec, který určuje název typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ba1cf-113">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="ba1cf-114">namespace</span><span class="sxs-lookup"><span data-stu-id="ba1cf-114">namespace</span></span>|<span data-ttu-id="ba1cf-115">Řetězec, který určuje obor názvů typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ba1cf-115">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba1cf-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ba1cf-116">Child Elements</span></span>  
 <span data-ttu-id="ba1cf-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="ba1cf-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba1cf-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ba1cf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ba1cf-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="ba1cf-119">Element</span></span>|<span data-ttu-id="ba1cf-120">Description</span><span class="sxs-lookup"><span data-stu-id="ba1cf-120">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="ba1cf-121">Kolekce názvů typů kontraktů.</span><span class="sxs-lookup"><span data-stu-id="ba1cf-121">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba1cf-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba1cf-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
