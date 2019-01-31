---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 269500324ad1beaa0b519fa17d251ee942276faa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269065"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="dc7a8-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="dc7a8-101">\<callbackTimeouts></span></span>
<span data-ttu-id="dc7a8-102">Určuje maximální dobu proudění transakcí ze serveru do zpětně volaném scénáři kontraktu duplexního zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="dc7a8-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="dc7a8-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dc7a8-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="dc7a8-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="dc7a8-104">\<behaviors></span></span>  
<span data-ttu-id="dc7a8-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="dc7a8-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="dc7a8-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="dc7a8-106">\<behavior></span></span>  
<span data-ttu-id="dc7a8-107">\<callbackTimeOuts></span><span class="sxs-lookup"><span data-stu-id="dc7a8-107">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc7a8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc7a8-108">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="dc7a8-109">Typ</span><span class="sxs-lookup"><span data-stu-id="dc7a8-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc7a8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dc7a8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dc7a8-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dc7a8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc7a8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="dc7a8-112">Attributes</span></span>  
  
|<span data-ttu-id="dc7a8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="dc7a8-113">Attribute</span></span>|<span data-ttu-id="dc7a8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="dc7a8-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="dc7a8-115">A <xref:System.TimeSpan> hodnota, která určuje dobu v rámci transakce, které musíte dokončit nebo bude automaticky ukončena.</span><span class="sxs-lookup"><span data-stu-id="dc7a8-115">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="dc7a8-116">Výchozí hodnota je "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="dc7a8-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc7a8-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dc7a8-117">Child Elements</span></span>  
 <span data-ttu-id="dc7a8-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="dc7a8-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc7a8-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dc7a8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dc7a8-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="dc7a8-120">Element</span></span>|<span data-ttu-id="dc7a8-121">Popis</span><span class="sxs-lookup"><span data-stu-id="dc7a8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc7a8-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="dc7a8-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="dc7a8-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="dc7a8-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc7a8-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc7a8-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
