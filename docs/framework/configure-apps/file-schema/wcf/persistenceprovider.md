---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: dc8dea0ddd1ea074c08952e3e2ebfef2d12f7183
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099284"
---
# <a name="persistenceprovider"></a><span data-ttu-id="5dceb-101">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="5dceb-101">\<persistenceProvider></span></span>
<span data-ttu-id="5dceb-102">Určuje typ implementace poskytovatele trvalého použít, jakož i časový limit pro operace trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="5dceb-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="5dceb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5dceb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5dceb-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5dceb-104">\<behaviors></span></span>  
<span data-ttu-id="5dceb-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5dceb-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="5dceb-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5dceb-106">\<behavior></span></span>  
<span data-ttu-id="5dceb-107">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="5dceb-107">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dceb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5dceb-108">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5dceb-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5dceb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5dceb-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5dceb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5dceb-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="5dceb-111">Attributes</span></span>  
  
|<span data-ttu-id="5dceb-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="5dceb-112">Attribute</span></span>|<span data-ttu-id="5dceb-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5dceb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5dceb-114">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="5dceb-114">persistenceOperationTimeout</span></span>|<span data-ttu-id="5dceb-115">A <xref:System.TimeSpan> hodnota, která určuje časový limit pro operace trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="5dceb-115">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="5dceb-116">Výchozí hodnota je "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="5dceb-116">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="5dceb-117"> – typ</span><span class="sxs-lookup"><span data-stu-id="5dceb-117">type</span></span>|<span data-ttu-id="5dceb-118">Řetězec, který určuje typ továrny poskytovatele trvalosti používat.</span><span class="sxs-lookup"><span data-stu-id="5dceb-118">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5dceb-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5dceb-119">Child Elements</span></span>  
 <span data-ttu-id="5dceb-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="5dceb-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5dceb-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5dceb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5dceb-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="5dceb-122">Element</span></span>|<span data-ttu-id="5dceb-123">Popis</span><span class="sxs-lookup"><span data-stu-id="5dceb-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5dceb-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5dceb-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5dceb-125">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="5dceb-125">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dceb-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5dceb-126">Remarks</span></span>  
 <span data-ttu-id="5dceb-127">Tento prvek určuje poskytovatele trvalého chování, který se má použít k serializaci stav služby WCF.</span><span class="sxs-lookup"><span data-stu-id="5dceb-127">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="5dceb-128">Mělo by se používat společně s `wsHttpContextBinding` které předává informace o stavu v hlavičkách protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5dceb-128">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dceb-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5dceb-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
