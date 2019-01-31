---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 063dbee71a91e098e26026ea78c74642115c7955
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266660"
---
# <a name="clientvia"></a><span data-ttu-id="a16e1-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="a16e1-101">\<clientVia></span></span>
<span data-ttu-id="a16e1-102">Určuje identifikátor URI, pro který by měl být vytvořen přenosový kanál.</span><span class="sxs-lookup"><span data-stu-id="a16e1-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="a16e1-103">Další informace naleznete v tématu <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="a16e1-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="a16e1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a16e1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a16e1-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a16e1-105">\<behaviors></span></span>  
<span data-ttu-id="a16e1-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="a16e1-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="a16e1-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a16e1-107">\<behavior></span></span>  
<span data-ttu-id="a16e1-108">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="a16e1-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a16e1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a16e1-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a16e1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a16e1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a16e1-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a16e1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a16e1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a16e1-112">Attributes</span></span>  
  
|<span data-ttu-id="a16e1-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="a16e1-113">Attribute</span></span>|<span data-ttu-id="a16e1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a16e1-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="a16e1-115">Řetězec určující identifikátor URI, který označuje cestu zpráva měla použít.</span><span class="sxs-lookup"><span data-stu-id="a16e1-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a16e1-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a16e1-116">Child Elements</span></span>  
 <span data-ttu-id="a16e1-117">Žádná</span><span class="sxs-lookup"><span data-stu-id="a16e1-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a16e1-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a16e1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a16e1-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="a16e1-119">Element</span></span>|<span data-ttu-id="a16e1-120">Popis</span><span class="sxs-lookup"><span data-stu-id="a16e1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a16e1-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a16e1-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a16e1-122">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a16e1-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a16e1-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a16e1-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
