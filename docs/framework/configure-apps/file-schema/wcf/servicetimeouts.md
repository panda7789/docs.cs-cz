---
title: '&lt;serviceTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: f7aa623ee387f67f3bbff32249d3695049359cde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524465"
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="2db92-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="2db92-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="2db92-103">Určuje časový limit pro službu.</span><span class="sxs-lookup"><span data-stu-id="2db92-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="2db92-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2db92-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2db92-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2db92-105">\<behaviors></span></span>  
<span data-ttu-id="2db92-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2db92-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="2db92-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2db92-107">\<behavior></span></span>  
<span data-ttu-id="2db92-108">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="2db92-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2db92-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2db92-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="2db92-110">Typ</span><span class="sxs-lookup"><span data-stu-id="2db92-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2db92-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2db92-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2db92-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2db92-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2db92-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="2db92-113">Attributes</span></span>  
  
|<span data-ttu-id="2db92-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="2db92-114">Attribute</span></span>|<span data-ttu-id="2db92-115">Popis</span><span class="sxs-lookup"><span data-stu-id="2db92-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="2db92-116">A <xref:System.TimeSpan> hodnota, která určuje dobu toku transakce z klienta na server.</span><span class="sxs-lookup"><span data-stu-id="2db92-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="2db92-117">Výchozí hodnota je "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="2db92-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2db92-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2db92-118">Child Elements</span></span>  
 <span data-ttu-id="2db92-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="2db92-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2db92-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2db92-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2db92-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="2db92-121">Element</span></span>|<span data-ttu-id="2db92-122">Popis</span><span class="sxs-lookup"><span data-stu-id="2db92-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2db92-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2db92-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2db92-124">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="2db92-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2db92-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2db92-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
