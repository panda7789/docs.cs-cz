---
title: '&lt;serviceTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: a0f0725bffe0c3c83e412348dea97b16736ef3a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="d179c-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="d179c-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="d179c-103">Určuje časový limit pro službu.</span><span class="sxs-lookup"><span data-stu-id="d179c-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="d179c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d179c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d179c-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d179c-105">\<behaviors></span></span>  
<span data-ttu-id="d179c-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d179c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d179c-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d179c-107">\<behavior></span></span>  
<span data-ttu-id="d179c-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="d179c-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d179c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d179c-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="d179c-110">Typ</span><span class="sxs-lookup"><span data-stu-id="d179c-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d179c-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d179c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d179c-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d179c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d179c-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d179c-113">Attributes</span></span>  
  
|<span data-ttu-id="d179c-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="d179c-114">Attribute</span></span>|<span data-ttu-id="d179c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d179c-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="d179c-116">A <xref:System.TimeSpan> hodnotu, která určuje transakce musí procházet od klienta k serveru časový interval.</span><span class="sxs-lookup"><span data-stu-id="d179c-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="d179c-117">Výchozí hodnota je "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="d179c-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d179c-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d179c-118">Child Elements</span></span>  
 <span data-ttu-id="d179c-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="d179c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d179c-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d179c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d179c-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="d179c-121">Element</span></span>|<span data-ttu-id="d179c-122">Popis</span><span class="sxs-lookup"><span data-stu-id="d179c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d179c-123">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d179c-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d179c-124">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="d179c-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d179c-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="d179c-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
