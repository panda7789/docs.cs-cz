---
title: '&lt;persistenceProvider&gt;'
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 3c7fd74a84184ddbf8cc8db90141174ed84e5774
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746654"
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="de125-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="de125-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="de125-103">Určuje typ implementace trvalost zprostředkovatele použít, jakož i časový limit používat pro operace trvalost.</span><span class="sxs-lookup"><span data-stu-id="de125-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="de125-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="de125-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="de125-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="de125-105">\<behaviors></span></span>  
<span data-ttu-id="de125-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="de125-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="de125-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="de125-107">\<behavior></span></span>  
<span data-ttu-id="de125-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="de125-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de125-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de125-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de125-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="de125-110">Attributes and Elements</span></span>  
 <span data-ttu-id="de125-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="de125-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de125-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="de125-112">Attributes</span></span>  
  
|<span data-ttu-id="de125-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="de125-113">Attribute</span></span>|<span data-ttu-id="de125-114">Popis</span><span class="sxs-lookup"><span data-stu-id="de125-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de125-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="de125-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="de125-116">A <xref:System.TimeSpan> hodnotu, která určuje časový limit používaných pro operace trvalost.</span><span class="sxs-lookup"><span data-stu-id="de125-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="de125-117">Výchozí hodnota je "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="de125-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="de125-118">– typ</span><span class="sxs-lookup"><span data-stu-id="de125-118">type</span></span>|<span data-ttu-id="de125-119">Řetězec, který určuje typ objektu pro vytváření zprostředkovatele trvalost používat.</span><span class="sxs-lookup"><span data-stu-id="de125-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de125-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="de125-120">Child Elements</span></span>  
 <span data-ttu-id="de125-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="de125-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de125-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="de125-122">Parent Elements</span></span>  
  
|<span data-ttu-id="de125-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="de125-123">Element</span></span>|<span data-ttu-id="de125-124">Popis</span><span class="sxs-lookup"><span data-stu-id="de125-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de125-125">\<chování ></span><span class="sxs-lookup"><span data-stu-id="de125-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="de125-126">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="de125-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de125-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de125-127">Remarks</span></span>  
 <span data-ttu-id="de125-128">Tento element určuje trvalost zprostředkovatele, který se má použít k serializaci stav služby WCF.</span><span class="sxs-lookup"><span data-stu-id="de125-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="de125-129">By být používána společně s `wsHttpContextBinding` který předává informace o stavu v hlavičkách protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="de125-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de125-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="de125-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
