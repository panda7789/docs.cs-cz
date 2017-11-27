---
title: '&lt;persistenceProvider&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b506b8ef14246ee954adb0a16102f4bb208106b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="87201-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="87201-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="87201-103">Určuje typ implementace trvalost zprostředkovatele použít, jakož i časový limit používat pro operace trvalost.</span><span class="sxs-lookup"><span data-stu-id="87201-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="87201-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="87201-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="87201-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="87201-105">\<behaviors></span></span>  
<span data-ttu-id="87201-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="87201-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="87201-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="87201-107">\<behavior></span></span>  
<span data-ttu-id="87201-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="87201-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87201-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87201-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87201-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="87201-110">Attributes and Elements</span></span>  
 <span data-ttu-id="87201-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="87201-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87201-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="87201-112">Attributes</span></span>  
  
|<span data-ttu-id="87201-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="87201-113">Attribute</span></span>|<span data-ttu-id="87201-114">Popis</span><span class="sxs-lookup"><span data-stu-id="87201-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87201-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="87201-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="87201-116">A <xref:System.TimeSpan> hodnotu, která určuje časový limit používaných pro operace trvalost.</span><span class="sxs-lookup"><span data-stu-id="87201-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="87201-117">Výchozí hodnota je "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="87201-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="87201-118">– typ</span><span class="sxs-lookup"><span data-stu-id="87201-118">type</span></span>|<span data-ttu-id="87201-119">Řetězec, který určuje typ objektu pro vytváření zprostředkovatele trvalost používat.</span><span class="sxs-lookup"><span data-stu-id="87201-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87201-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="87201-120">Child Elements</span></span>  
 <span data-ttu-id="87201-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="87201-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87201-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="87201-122">Parent Elements</span></span>  
  
|<span data-ttu-id="87201-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="87201-123">Element</span></span>|<span data-ttu-id="87201-124">Popis</span><span class="sxs-lookup"><span data-stu-id="87201-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87201-125">\<chování ></span><span class="sxs-lookup"><span data-stu-id="87201-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="87201-126">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="87201-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87201-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87201-127">Remarks</span></span>  
 <span data-ttu-id="87201-128">Tento element určuje trvalost zprostředkovatele, který se má použít k serializaci stav služby WCF.</span><span class="sxs-lookup"><span data-stu-id="87201-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="87201-129">By být používána společně s `wsHttpContextBinding` který předává informace o stavu v hlavičkách protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="87201-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87201-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="87201-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
