---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 5c2f0ef7ad509eb5d6c686802c3fe5a75ea1a258
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075517"
---
# <a name="servicetimeouts"></a><span data-ttu-id="9f592-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="9f592-101">\<serviceTimeouts></span></span>
<span data-ttu-id="9f592-102">Určuje časový limit pro službu.</span><span class="sxs-lookup"><span data-stu-id="9f592-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="9f592-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9f592-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9f592-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9f592-104">\<behaviors></span></span>  
<span data-ttu-id="9f592-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9f592-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="9f592-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9f592-106">\<behavior></span></span>  
<span data-ttu-id="9f592-107">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="9f592-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f592-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f592-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="9f592-109">Type</span><span class="sxs-lookup"><span data-stu-id="9f592-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f592-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9f592-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9f592-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9f592-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f592-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="9f592-112">Attributes</span></span>  
  
|<span data-ttu-id="9f592-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="9f592-113">Attribute</span></span>|<span data-ttu-id="9f592-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9f592-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="9f592-115">A <xref:System.TimeSpan> hodnota, která určuje dobu toku transakce z klienta na server.</span><span class="sxs-lookup"><span data-stu-id="9f592-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="9f592-116">Výchozí hodnota je "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="9f592-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f592-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9f592-117">Child Elements</span></span>  
 <span data-ttu-id="9f592-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="9f592-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f592-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9f592-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9f592-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="9f592-120">Element</span></span>|<span data-ttu-id="9f592-121">Popis</span><span class="sxs-lookup"><span data-stu-id="9f592-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f592-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9f592-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="9f592-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="9f592-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f592-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f592-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
