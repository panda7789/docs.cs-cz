---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: b12a882d942555a24c145b243d2cea764ba106b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919507"
---
# <a name="clientvia"></a><span data-ttu-id="52151-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="52151-101">\<clientVia></span></span>
<span data-ttu-id="52151-102">Určuje identifikátor URI, pro který má být vytvořen přenosový kanál.</span><span class="sxs-lookup"><span data-stu-id="52151-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="52151-103">Další informace naleznete v tématu <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="52151-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="52151-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="52151-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="52151-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="52151-105">\<behaviors></span></span>  
<span data-ttu-id="52151-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="52151-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="52151-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="52151-107">\<behavior></span></span>  
<span data-ttu-id="52151-108">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="52151-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52151-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52151-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52151-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="52151-110">Attributes and Elements</span></span>  
 <span data-ttu-id="52151-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="52151-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52151-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="52151-112">Attributes</span></span>  
  
|<span data-ttu-id="52151-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="52151-113">Attribute</span></span>|<span data-ttu-id="52151-114">Popis</span><span class="sxs-lookup"><span data-stu-id="52151-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="52151-115">Řetězec určující identifikátor URI, který označuje cestu, kterou by měla zpráva trvat.</span><span class="sxs-lookup"><span data-stu-id="52151-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52151-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="52151-116">Child Elements</span></span>  
 <span data-ttu-id="52151-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="52151-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52151-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="52151-118">Parent Elements</span></span>  
  
|<span data-ttu-id="52151-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="52151-119">Element</span></span>|<span data-ttu-id="52151-120">Popis</span><span class="sxs-lookup"><span data-stu-id="52151-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52151-121">\<> chování</span><span class="sxs-lookup"><span data-stu-id="52151-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="52151-122">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="52151-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52151-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52151-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
