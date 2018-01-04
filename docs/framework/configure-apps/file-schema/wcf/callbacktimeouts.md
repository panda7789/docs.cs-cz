---
title: '&lt;callbackTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71fc89a4b9735c13429b31d8cd7c5995f641afa8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="fec29-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="fec29-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="fec29-103">Určuje hodnotu časového limitu při toku transakcí ze serveru pro položku scénáři zpětného volání duplexní kontrakt.</span><span class="sxs-lookup"><span data-stu-id="fec29-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="fec29-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fec29-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fec29-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="fec29-105">\<behaviors></span></span>  
<span data-ttu-id="fec29-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fec29-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="fec29-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="fec29-107">\<behavior></span></span>  
<span data-ttu-id="fec29-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="fec29-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fec29-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fec29-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="fec29-110">Typ</span><span class="sxs-lookup"><span data-stu-id="fec29-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fec29-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fec29-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fec29-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fec29-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fec29-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="fec29-113">Attributes</span></span>  
  
|<span data-ttu-id="fec29-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="fec29-114">Attribute</span></span>|<span data-ttu-id="fec29-115">Popis</span><span class="sxs-lookup"><span data-stu-id="fec29-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="fec29-116">A <xref:System.TimeSpan> hodnotu, která udává interval času v rámci transakce, které musíte dokončit nebo automaticky ukončena.</span><span class="sxs-lookup"><span data-stu-id="fec29-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="fec29-117">Výchozí hodnota je "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="fec29-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fec29-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fec29-118">Child Elements</span></span>  
 <span data-ttu-id="fec29-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="fec29-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fec29-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fec29-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fec29-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="fec29-121">Element</span></span>|<span data-ttu-id="fec29-122">Popis</span><span class="sxs-lookup"><span data-stu-id="fec29-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fec29-123">\<chování ></span><span class="sxs-lookup"><span data-stu-id="fec29-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="fec29-124">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="fec29-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fec29-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="fec29-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
