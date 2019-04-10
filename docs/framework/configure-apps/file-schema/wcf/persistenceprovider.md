---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: dc8dea0ddd1ea074c08952e3e2ebfef2d12f7183
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099284"
---
# <a name="persistenceprovider"></a><span data-ttu-id="76aee-101">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="76aee-101">\<persistenceProvider></span></span>
<span data-ttu-id="76aee-102">Určuje typ implementace poskytovatele trvalého použít, jakož i časový limit pro operace trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="76aee-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="76aee-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="76aee-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="76aee-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="76aee-104">\<behaviors></span></span>  
<span data-ttu-id="76aee-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="76aee-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="76aee-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="76aee-106">\<behavior></span></span>  
<span data-ttu-id="76aee-107">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="76aee-107">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76aee-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76aee-108">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76aee-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="76aee-109">Attributes and Elements</span></span>  
 <span data-ttu-id="76aee-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="76aee-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76aee-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="76aee-111">Attributes</span></span>  
  
|<span data-ttu-id="76aee-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="76aee-112">Attribute</span></span>|<span data-ttu-id="76aee-113">Popis</span><span class="sxs-lookup"><span data-stu-id="76aee-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76aee-114">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="76aee-114">persistenceOperationTimeout</span></span>|<span data-ttu-id="76aee-115">A <xref:System.TimeSpan> hodnota, která určuje časový limit pro operace trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="76aee-115">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="76aee-116">Výchozí hodnota je "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="76aee-116">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="76aee-117"> – typ</span><span class="sxs-lookup"><span data-stu-id="76aee-117">type</span></span>|<span data-ttu-id="76aee-118">Řetězec, který určuje typ továrny poskytovatele trvalosti používat.</span><span class="sxs-lookup"><span data-stu-id="76aee-118">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76aee-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="76aee-119">Child Elements</span></span>  
 <span data-ttu-id="76aee-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="76aee-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76aee-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="76aee-121">Parent Elements</span></span>  
  
|<span data-ttu-id="76aee-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="76aee-122">Element</span></span>|<span data-ttu-id="76aee-123">Popis</span><span class="sxs-lookup"><span data-stu-id="76aee-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76aee-124">\<chování ></span><span class="sxs-lookup"><span data-stu-id="76aee-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="76aee-125">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="76aee-125">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76aee-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76aee-126">Remarks</span></span>  
 <span data-ttu-id="76aee-127">Tento prvek určuje poskytovatele trvalého chování, který se má použít k serializaci stav služby WCF.</span><span class="sxs-lookup"><span data-stu-id="76aee-127">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="76aee-128">Mělo by se používat společně s `wsHttpContextBinding` které předává informace o stavu v hlavičkách protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="76aee-128">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76aee-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76aee-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
