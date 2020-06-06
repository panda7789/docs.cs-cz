---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: a1c2ee68fb039e24e1462148cb52daf1bb57f8ed
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398114"
---
# \<clientVia>
<span data-ttu-id="ffc7e-101">Určuje identifikátor URI, pro který má být vytvořen přenosový kanál.</span><span class="sxs-lookup"><span data-stu-id="ffc7e-101">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="ffc7e-102">Další informace naleznete v tématu <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="ffc7e-102">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**  
  
## <a name="syntax"></a><span data-ttu-id="ffc7e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffc7e-103">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffc7e-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ffc7e-104">Attributes and Elements</span></span>  
 <span data-ttu-id="ffc7e-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ffc7e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffc7e-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="ffc7e-106">Attributes</span></span>  
  
|<span data-ttu-id="ffc7e-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="ffc7e-107">Attribute</span></span>|<span data-ttu-id="ffc7e-108">Popis</span><span class="sxs-lookup"><span data-stu-id="ffc7e-108">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="ffc7e-109">Řetězec určující identifikátor URI, který označuje cestu, kterou by měla zpráva trvat.</span><span class="sxs-lookup"><span data-stu-id="ffc7e-109">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ffc7e-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ffc7e-110">Child Elements</span></span>  
 <span data-ttu-id="ffc7e-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="ffc7e-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ffc7e-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ffc7e-112">Parent Elements</span></span>  
  
|<span data-ttu-id="ffc7e-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="ffc7e-113">Element</span></span>|<span data-ttu-id="ffc7e-114">Description</span><span class="sxs-lookup"><span data-stu-id="ffc7e-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ffc7e-115">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ffc7e-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ffc7e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffc7e-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
