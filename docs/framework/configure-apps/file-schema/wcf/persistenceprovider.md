---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 7c4d9ae29ca1e543217d444e05a661b48e2cbb62
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400067"
---
# <a name="persistenceprovider"></a><span data-ttu-id="22199-101">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="22199-101">\<persistenceProvider></span></span>
<span data-ttu-id="22199-102">Určuje typ používané implementace poskytovatele trvalosti a také časový limit pro operace trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="22199-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
<span data-ttu-id="22199-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="22199-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="22199-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="22199-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="22199-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="22199-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="22199-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="22199-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="22199-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="22199-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="22199-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<persistenceProvider >**</span><span class="sxs-lookup"><span data-stu-id="22199-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22199-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22199-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22199-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="22199-110">Attributes and Elements</span></span>  
 <span data-ttu-id="22199-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="22199-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22199-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="22199-112">Attributes</span></span>  
  
|<span data-ttu-id="22199-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="22199-113">Attribute</span></span>|<span data-ttu-id="22199-114">Popis</span><span class="sxs-lookup"><span data-stu-id="22199-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22199-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="22199-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="22199-116"><xref:System.TimeSpan> Hodnota, která určuje časový limit, který se používá pro operace trvalosti.</span><span class="sxs-lookup"><span data-stu-id="22199-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="22199-117">Výchozí hodnota je "00:00:30".</span><span class="sxs-lookup"><span data-stu-id="22199-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="22199-118">– typ</span><span class="sxs-lookup"><span data-stu-id="22199-118">type</span></span>|<span data-ttu-id="22199-119">Řetězec, který určuje typ továrny poskytovatele trvalosti, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="22199-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22199-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="22199-120">Child Elements</span></span>  
 <span data-ttu-id="22199-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="22199-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22199-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="22199-122">Parent Elements</span></span>  
  
|<span data-ttu-id="22199-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="22199-123">Element</span></span>|<span data-ttu-id="22199-124">Popis</span><span class="sxs-lookup"><span data-stu-id="22199-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22199-125">\<> chování</span><span class="sxs-lookup"><span data-stu-id="22199-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="22199-126">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="22199-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22199-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22199-127">Remarks</span></span>  
 <span data-ttu-id="22199-128">Tento prvek určuje poskytovatele trvalosti, který se použije k serializaci stavu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="22199-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="22199-129">Měl by se používat společně s tím `wsHttpContextBinding` , který předává informace o stavu v hlavičkách protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="22199-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22199-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22199-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
