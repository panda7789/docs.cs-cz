---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e666bac0be772e417f140e1482649f82ea70e2f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173638"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="23d61-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="23d61-101">\<callbackTimeouts></span></span>
<span data-ttu-id="23d61-102">Určuje maximální dobu proudění transakcí ze serveru do zpětně volaném scénáři kontraktu duplexního zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="23d61-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="23d61-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="23d61-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="23d61-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="23d61-104">\<behaviors></span></span>  
<span data-ttu-id="23d61-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="23d61-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="23d61-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="23d61-106">\<behavior></span></span>  
<span data-ttu-id="23d61-107">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="23d61-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23d61-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23d61-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="23d61-109">Type</span><span class="sxs-lookup"><span data-stu-id="23d61-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23d61-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="23d61-110">Attributes and Elements</span></span>  
 <span data-ttu-id="23d61-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="23d61-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23d61-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="23d61-112">Attributes</span></span>  
  
|<span data-ttu-id="23d61-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="23d61-113">Attribute</span></span>|<span data-ttu-id="23d61-114">Popis</span><span class="sxs-lookup"><span data-stu-id="23d61-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="23d61-115">A <xref:System.TimeSpan> hodnota, která určuje dobu v rámci transakce, které musíte dokončit nebo bude automaticky ukončena.</span><span class="sxs-lookup"><span data-stu-id="23d61-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="23d61-116">Výchozí hodnota je "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="23d61-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23d61-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="23d61-117">Child Elements</span></span>  
 <span data-ttu-id="23d61-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="23d61-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23d61-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="23d61-119">Parent Elements</span></span>  
  
|<span data-ttu-id="23d61-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="23d61-120">Element</span></span>|<span data-ttu-id="23d61-121">Popis</span><span class="sxs-lookup"><span data-stu-id="23d61-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23d61-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="23d61-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="23d61-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="23d61-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23d61-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23d61-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
