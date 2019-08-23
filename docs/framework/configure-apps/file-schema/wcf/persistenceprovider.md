---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 4fc9e1332effc51e183a84cf2d3653357277d2ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934142"
---
# <a name="persistenceprovider"></a><span data-ttu-id="63798-101">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="63798-101">\<persistenceProvider></span></span>
<span data-ttu-id="63798-102">Určuje typ používané implementace poskytovatele trvalosti a také časový limit pro operace trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="63798-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="63798-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="63798-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="63798-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="63798-104">\<behaviors></span></span>  
<span data-ttu-id="63798-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="63798-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="63798-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="63798-106">\<behavior></span></span>  
<span data-ttu-id="63798-107">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="63798-107">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63798-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63798-108">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63798-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="63798-109">Attributes and Elements</span></span>  
 <span data-ttu-id="63798-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="63798-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63798-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="63798-111">Attributes</span></span>  
  
|<span data-ttu-id="63798-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="63798-112">Attribute</span></span>|<span data-ttu-id="63798-113">Popis</span><span class="sxs-lookup"><span data-stu-id="63798-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="63798-114">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="63798-114">persistenceOperationTimeout</span></span>|<span data-ttu-id="63798-115"><xref:System.TimeSpan> Hodnota, která určuje časový limit, který se používá pro operace trvalosti.</span><span class="sxs-lookup"><span data-stu-id="63798-115">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="63798-116">Výchozí hodnota je "00:00:30".</span><span class="sxs-lookup"><span data-stu-id="63798-116">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="63798-117">– typ</span><span class="sxs-lookup"><span data-stu-id="63798-117">type</span></span>|<span data-ttu-id="63798-118">Řetězec, který určuje typ továrny poskytovatele trvalosti, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="63798-118">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63798-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="63798-119">Child Elements</span></span>  
 <span data-ttu-id="63798-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="63798-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63798-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="63798-121">Parent Elements</span></span>  
  
|<span data-ttu-id="63798-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="63798-122">Element</span></span>|<span data-ttu-id="63798-123">Popis</span><span class="sxs-lookup"><span data-stu-id="63798-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63798-124">\<> chování</span><span class="sxs-lookup"><span data-stu-id="63798-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="63798-125">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="63798-125">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63798-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63798-126">Remarks</span></span>  
 <span data-ttu-id="63798-127">Tento prvek určuje poskytovatele trvalosti, který se použije k serializaci stavu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="63798-127">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="63798-128">Měl by se používat společně s tím `wsHttpContextBinding` , který předává informace o stavu v hlavičkách protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="63798-128">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63798-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63798-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
