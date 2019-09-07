---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: a1c2ee68fb039e24e1462148cb52daf1bb57f8ed
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398114"
---
# <a name="clientvia"></a><span data-ttu-id="c59c0-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="c59c0-101">\<clientVia></span></span>
<span data-ttu-id="c59c0-102">Určuje identifikátor URI, pro který má být vytvořen přenosový kanál.</span><span class="sxs-lookup"><span data-stu-id="c59c0-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="c59c0-103">Další informace naleznete v tématu <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="c59c0-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
<span data-ttu-id="c59c0-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c59c0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c59c0-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c59c0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c59c0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c59c0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c59c0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c59c0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="c59c0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c59c0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="c59c0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clientVia >**</span><span class="sxs-lookup"><span data-stu-id="c59c0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c59c0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c59c0-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c59c0-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c59c0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c59c0-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c59c0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c59c0-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="c59c0-113">Attributes</span></span>  
  
|<span data-ttu-id="c59c0-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="c59c0-114">Attribute</span></span>|<span data-ttu-id="c59c0-115">Popis</span><span class="sxs-lookup"><span data-stu-id="c59c0-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="c59c0-116">Řetězec určující identifikátor URI, který označuje cestu, kterou by měla zpráva trvat.</span><span class="sxs-lookup"><span data-stu-id="c59c0-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c59c0-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c59c0-117">Child Elements</span></span>  
 <span data-ttu-id="c59c0-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="c59c0-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c59c0-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c59c0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c59c0-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="c59c0-120">Element</span></span>|<span data-ttu-id="c59c0-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c59c0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c59c0-122">\<> chování</span><span class="sxs-lookup"><span data-stu-id="c59c0-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c59c0-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c59c0-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c59c0-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c59c0-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
