---
title: '&lt;callbackTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 85e7b1f0d009e27cbacd9f69b381e4f05984bf56
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149108"
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="1bc65-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="1bc65-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="1bc65-103">Určuje maximální dobu proudění transakcí ze serveru do zpětně volaném scénáři kontraktu duplexního zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="1bc65-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="1bc65-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1bc65-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1bc65-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1bc65-105">\<behaviors></span></span>  
<span data-ttu-id="1bc65-106">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1bc65-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="1bc65-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1bc65-107">\<behavior></span></span>  
<span data-ttu-id="1bc65-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="1bc65-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bc65-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bc65-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="1bc65-110">Typ</span><span class="sxs-lookup"><span data-stu-id="1bc65-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bc65-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1bc65-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1bc65-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1bc65-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bc65-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1bc65-113">Attributes</span></span>  
  
|<span data-ttu-id="1bc65-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="1bc65-114">Attribute</span></span>|<span data-ttu-id="1bc65-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1bc65-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="1bc65-116">A <xref:System.TimeSpan> hodnota, která určuje dobu v rámci transakce, které musíte dokončit nebo bude automaticky ukončena.</span><span class="sxs-lookup"><span data-stu-id="1bc65-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="1bc65-117">Výchozí hodnota je "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="1bc65-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1bc65-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1bc65-118">Child Elements</span></span>  
 <span data-ttu-id="1bc65-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="1bc65-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1bc65-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1bc65-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1bc65-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="1bc65-121">Element</span></span>|<span data-ttu-id="1bc65-122">Popis</span><span class="sxs-lookup"><span data-stu-id="1bc65-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1bc65-123">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1bc65-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1bc65-124">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1bc65-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1bc65-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bc65-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
