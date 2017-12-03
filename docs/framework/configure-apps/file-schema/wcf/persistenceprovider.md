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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d93a9ea8614f98c968d499c2f95dcd3962f0020
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="839fc-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="839fc-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="839fc-103">Určuje typ implementace trvalost zprostředkovatele použít, jakož i časový limit používat pro operace trvalost.</span><span class="sxs-lookup"><span data-stu-id="839fc-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="839fc-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="839fc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="839fc-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="839fc-105">\<behaviors></span></span>  
<span data-ttu-id="839fc-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="839fc-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="839fc-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="839fc-107">\<behavior></span></span>  
<span data-ttu-id="839fc-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="839fc-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="839fc-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="839fc-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="839fc-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="839fc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="839fc-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="839fc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="839fc-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="839fc-112">Attributes</span></span>  
  
|<span data-ttu-id="839fc-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="839fc-113">Attribute</span></span>|<span data-ttu-id="839fc-114">Popis</span><span class="sxs-lookup"><span data-stu-id="839fc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="839fc-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="839fc-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="839fc-116">A <xref:System.TimeSpan> hodnotu, která určuje časový limit používaných pro operace trvalost.</span><span class="sxs-lookup"><span data-stu-id="839fc-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="839fc-117">Výchozí hodnota je "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="839fc-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="839fc-118">– typ</span><span class="sxs-lookup"><span data-stu-id="839fc-118">type</span></span>|<span data-ttu-id="839fc-119">Řetězec, který určuje typ objektu pro vytváření zprostředkovatele trvalost používat.</span><span class="sxs-lookup"><span data-stu-id="839fc-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="839fc-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="839fc-120">Child Elements</span></span>  
 <span data-ttu-id="839fc-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="839fc-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="839fc-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="839fc-122">Parent Elements</span></span>  
  
|<span data-ttu-id="839fc-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="839fc-123">Element</span></span>|<span data-ttu-id="839fc-124">Popis</span><span class="sxs-lookup"><span data-stu-id="839fc-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="839fc-125">\<chování ></span><span class="sxs-lookup"><span data-stu-id="839fc-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="839fc-126">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="839fc-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="839fc-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="839fc-127">Remarks</span></span>  
 <span data-ttu-id="839fc-128">Tento element určuje trvalost zprostředkovatele, který se má použít k serializaci stav služby WCF.</span><span class="sxs-lookup"><span data-stu-id="839fc-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="839fc-129">By být používána společně s `wsHttpContextBinding` který předává informace o stavu v hlavičkách protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="839fc-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="839fc-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="839fc-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
