---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: b67ea137e6c116d00a8a098b9c0df99430114dc5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267284"
---
# <a name="servicetimeouts"></a><span data-ttu-id="93ca8-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="93ca8-101">\<serviceTimeouts></span></span>
<span data-ttu-id="93ca8-102">Určuje časový limit pro službu.</span><span class="sxs-lookup"><span data-stu-id="93ca8-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="93ca8-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="93ca8-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="93ca8-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="93ca8-104">\<behaviors></span></span>  
<span data-ttu-id="93ca8-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="93ca8-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="93ca8-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="93ca8-106">\<behavior></span></span>  
<span data-ttu-id="93ca8-107">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="93ca8-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93ca8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93ca8-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="93ca8-109">Typ</span><span class="sxs-lookup"><span data-stu-id="93ca8-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93ca8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="93ca8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="93ca8-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="93ca8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93ca8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="93ca8-112">Attributes</span></span>  
  
|<span data-ttu-id="93ca8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="93ca8-113">Attribute</span></span>|<span data-ttu-id="93ca8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="93ca8-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="93ca8-115">A <xref:System.TimeSpan> hodnota, která určuje dobu toku transakce z klienta na server.</span><span class="sxs-lookup"><span data-stu-id="93ca8-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="93ca8-116">Výchozí hodnota je "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="93ca8-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93ca8-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="93ca8-117">Child Elements</span></span>  
 <span data-ttu-id="93ca8-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="93ca8-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93ca8-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="93ca8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="93ca8-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="93ca8-120">Element</span></span>|<span data-ttu-id="93ca8-121">Popis</span><span class="sxs-lookup"><span data-stu-id="93ca8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93ca8-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="93ca8-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="93ca8-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="93ca8-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93ca8-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93ca8-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
