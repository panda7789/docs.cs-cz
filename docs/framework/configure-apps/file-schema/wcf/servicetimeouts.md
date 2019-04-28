---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 5c2f0ef7ad509eb5d6c686802c3fe5a75ea1a258
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758090"
---
# <a name="servicetimeouts"></a><span data-ttu-id="19e73-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="19e73-101">\<serviceTimeouts></span></span>
<span data-ttu-id="19e73-102">Určuje časový limit pro službu.</span><span class="sxs-lookup"><span data-stu-id="19e73-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="19e73-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="19e73-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="19e73-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="19e73-104">\<behaviors></span></span>  
<span data-ttu-id="19e73-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="19e73-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="19e73-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="19e73-106">\<behavior></span></span>  
<span data-ttu-id="19e73-107">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="19e73-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19e73-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19e73-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="19e73-109">Type</span><span class="sxs-lookup"><span data-stu-id="19e73-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19e73-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="19e73-110">Attributes and Elements</span></span>  
 <span data-ttu-id="19e73-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="19e73-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19e73-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="19e73-112">Attributes</span></span>  
  
|<span data-ttu-id="19e73-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="19e73-113">Attribute</span></span>|<span data-ttu-id="19e73-114">Popis</span><span class="sxs-lookup"><span data-stu-id="19e73-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="19e73-115">A <xref:System.TimeSpan> hodnota, která určuje dobu toku transakce z klienta na server.</span><span class="sxs-lookup"><span data-stu-id="19e73-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="19e73-116">Výchozí hodnota je "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="19e73-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19e73-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="19e73-117">Child Elements</span></span>  
 <span data-ttu-id="19e73-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="19e73-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19e73-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="19e73-119">Parent Elements</span></span>  
  
|<span data-ttu-id="19e73-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="19e73-120">Element</span></span>|<span data-ttu-id="19e73-121">Popis</span><span class="sxs-lookup"><span data-stu-id="19e73-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19e73-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="19e73-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="19e73-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="19e73-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19e73-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19e73-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
