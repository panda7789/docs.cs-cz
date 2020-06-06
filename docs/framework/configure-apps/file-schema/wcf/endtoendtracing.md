---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1a274f15800c6a132994a2437943c83982de9de0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855293"
---
# \<endToEndTracing>
<span data-ttu-id="59f60-101">Prvek konfigurace, který umožňuje povolit nebo zakázat různé aspekty komplexního trasování během běžící aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="59f60-101">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**  
  
## <a name="syntax"></a><span data-ttu-id="59f60-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59f60-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59f60-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59f60-103">Attributes and Elements</span></span>  
 <span data-ttu-id="59f60-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="59f60-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59f60-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="59f60-105">Attributes</span></span>  
  
|<span data-ttu-id="59f60-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="59f60-106">Attribute</span></span>|<span data-ttu-id="59f60-107">Popis</span><span class="sxs-lookup"><span data-stu-id="59f60-107">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="59f60-108">Logická hodnota, která určuje, zda je povoleno trasování aktivit.</span><span class="sxs-lookup"><span data-stu-id="59f60-108">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="59f60-109">Logická hodnota, která určuje, zda je povoleno sledování toku zprávy.</span><span class="sxs-lookup"><span data-stu-id="59f60-109">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="59f60-110">Logická hodnota určující, zda je atribut rozšíření nastaven na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="59f60-110">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59f60-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59f60-111">Child Elements</span></span>  
 <span data-ttu-id="59f60-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="59f60-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59f60-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="59f60-113">Parent Elements</span></span>  
  
|<span data-ttu-id="59f60-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="59f60-114">Element</span></span>|<span data-ttu-id="59f60-115">Description</span><span class="sxs-lookup"><span data-stu-id="59f60-115">Description</span></span>|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="59f60-116">Definuje nastavení WCF pro kontrolu a kontrolu za běhu pro správce.</span><span class="sxs-lookup"><span data-stu-id="59f60-116">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59f60-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="59f60-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="59f60-118">Komplexní trasování</span><span class="sxs-lookup"><span data-stu-id="59f60-118">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
