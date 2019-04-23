---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 5c2f0ef7ad509eb5d6c686802c3fe5a75ea1a258
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075517"
---
# <a name="servicetimeouts"></a><span data-ttu-id="c58e4-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="c58e4-101">\<serviceTimeouts></span></span>
<span data-ttu-id="c58e4-102">Určuje časový limit pro službu.</span><span class="sxs-lookup"><span data-stu-id="c58e4-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="c58e4-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c58e4-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c58e4-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c58e4-104">\<behaviors></span></span>  
<span data-ttu-id="c58e4-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c58e4-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="c58e4-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c58e4-106">\<behavior></span></span>  
<span data-ttu-id="c58e4-107">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="c58e4-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c58e4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c58e4-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="c58e4-109">Type</span><span class="sxs-lookup"><span data-stu-id="c58e4-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c58e4-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c58e4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c58e4-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c58e4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c58e4-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c58e4-112">Attributes</span></span>  
  
|<span data-ttu-id="c58e4-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c58e4-113">Attribute</span></span>|<span data-ttu-id="c58e4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c58e4-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="c58e4-115">A <xref:System.TimeSpan> hodnota, která určuje dobu toku transakce z klienta na server.</span><span class="sxs-lookup"><span data-stu-id="c58e4-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="c58e4-116">Výchozí hodnota je "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="c58e4-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c58e4-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c58e4-117">Child Elements</span></span>  
 <span data-ttu-id="c58e4-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="c58e4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c58e4-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c58e4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c58e4-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="c58e4-120">Element</span></span>|<span data-ttu-id="c58e4-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c58e4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c58e4-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c58e4-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="c58e4-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="c58e4-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c58e4-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c58e4-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
