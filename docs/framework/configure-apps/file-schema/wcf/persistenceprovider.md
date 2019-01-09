---
title: '&lt;persistenceProvider&gt;'
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: ba02977a7df44931ae195040949e9a8eb0c141b5
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152018"
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="9f326-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="9f326-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="9f326-103">Určuje typ implementace poskytovatele trvalého použít, jakož i časový limit pro operace trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="9f326-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="9f326-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9f326-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9f326-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9f326-105">\<behaviors></span></span>  
<span data-ttu-id="9f326-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9f326-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9f326-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9f326-107">\<behavior></span></span>  
<span data-ttu-id="9f326-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="9f326-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f326-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f326-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f326-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9f326-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9f326-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9f326-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f326-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="9f326-112">Attributes</span></span>  
  
|<span data-ttu-id="9f326-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="9f326-113">Attribute</span></span>|<span data-ttu-id="9f326-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9f326-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f326-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="9f326-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="9f326-116">A <xref:System.TimeSpan> hodnota, která určuje časový limit pro operace trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="9f326-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="9f326-117">Výchozí hodnota je "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="9f326-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="9f326-118">– typ</span><span class="sxs-lookup"><span data-stu-id="9f326-118">type</span></span>|<span data-ttu-id="9f326-119">Řetězec, který určuje typ továrny poskytovatele trvalosti používat.</span><span class="sxs-lookup"><span data-stu-id="9f326-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f326-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9f326-120">Child Elements</span></span>  
 <span data-ttu-id="9f326-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="9f326-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f326-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9f326-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9f326-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="9f326-123">Element</span></span>|<span data-ttu-id="9f326-124">Popis</span><span class="sxs-lookup"><span data-stu-id="9f326-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f326-125">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9f326-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="9f326-126">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="9f326-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f326-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f326-127">Remarks</span></span>  
 <span data-ttu-id="9f326-128">Tento prvek určuje poskytovatele trvalého chování, který se má použít k serializaci stav služby WCF.</span><span class="sxs-lookup"><span data-stu-id="9f326-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="9f326-129">Mělo by se používat společně s `wsHttpContextBinding` které předává informace o stavu v hlavičkách protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="9f326-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f326-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f326-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
