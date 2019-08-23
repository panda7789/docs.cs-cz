---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: a1792fec4f86c9ac31107c043b976cfafcfa4c13
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937098"
---
# <a name="servicetimeouts"></a><span data-ttu-id="e29d3-101">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="e29d3-101">\<serviceTimeouts></span></span>
<span data-ttu-id="e29d3-102">Určuje časový limit služby.</span><span class="sxs-lookup"><span data-stu-id="e29d3-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="e29d3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e29d3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e29d3-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e29d3-104">\<behaviors></span></span>  
<span data-ttu-id="e29d3-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e29d3-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="e29d3-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e29d3-106">\<behavior></span></span>  
<span data-ttu-id="e29d3-107">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="e29d3-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e29d3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e29d3-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="e29d3-109">type</span><span class="sxs-lookup"><span data-stu-id="e29d3-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e29d3-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e29d3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e29d3-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e29d3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e29d3-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="e29d3-112">Attributes</span></span>  
  
|<span data-ttu-id="e29d3-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="e29d3-113">Attribute</span></span>|<span data-ttu-id="e29d3-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e29d3-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="e29d3-115"><xref:System.TimeSpan> Hodnota, která určuje časový interval, po který musí transakce z klienta na server přesměrovat.</span><span class="sxs-lookup"><span data-stu-id="e29d3-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="e29d3-116">Výchozí hodnota je "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="e29d3-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e29d3-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e29d3-117">Child Elements</span></span>  
 <span data-ttu-id="e29d3-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="e29d3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e29d3-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e29d3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e29d3-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="e29d3-120">Element</span></span>|<span data-ttu-id="e29d3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="e29d3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e29d3-122">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e29d3-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e29d3-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="e29d3-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e29d3-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e29d3-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
