---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: d57a888a19e684ac13632c1ab2476e304667c3e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919668"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="fd00c-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="fd00c-101">\<callbackTimeouts></span></span>
<span data-ttu-id="fd00c-102">Určuje hodnotu časového limitu při toku transakcí ze serveru tak, aby client.in scénář kontraktu pro oboustranný zpětný pokus.</span><span class="sxs-lookup"><span data-stu-id="fd00c-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="fd00c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fd00c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="fd00c-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="fd00c-104">\<behaviors></span></span>  
<span data-ttu-id="fd00c-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="fd00c-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="fd00c-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="fd00c-106">\<behavior></span></span>  
<span data-ttu-id="fd00c-107">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="fd00c-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd00c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd00c-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="fd00c-109">type</span><span class="sxs-lookup"><span data-stu-id="fd00c-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd00c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fd00c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fd00c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fd00c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd00c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="fd00c-112">Attributes</span></span>  
  
|<span data-ttu-id="fd00c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="fd00c-113">Attribute</span></span>|<span data-ttu-id="fd00c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="fd00c-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="fd00c-115"><xref:System.TimeSpan> Hodnota, která určuje časový interval, ve kterém musí být transakce dokončeny nebo automaticky ukončeny.</span><span class="sxs-lookup"><span data-stu-id="fd00c-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="fd00c-116">Výchozí hodnota je "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="fd00c-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd00c-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fd00c-117">Child Elements</span></span>  
 <span data-ttu-id="fd00c-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="fd00c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd00c-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fd00c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fd00c-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="fd00c-120">Element</span></span>|<span data-ttu-id="fd00c-121">Popis</span><span class="sxs-lookup"><span data-stu-id="fd00c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd00c-122">\<> chování</span><span class="sxs-lookup"><span data-stu-id="fd00c-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="fd00c-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="fd00c-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd00c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd00c-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
