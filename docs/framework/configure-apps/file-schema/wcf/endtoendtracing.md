---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1a274f15800c6a132994a2437943c83982de9de0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855293"
---
# <a name="endtoendtracing"></a><span data-ttu-id="d71c8-101">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="d71c8-101">\<endToEndTracing></span></span>
<span data-ttu-id="d71c8-102">Prvek konfigurace, který umožňuje povolit nebo zakázat různé aspekty komplexního trasování během běžící aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="d71c8-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
<span data-ttu-id="d71c8-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d71c8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d71c8-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d71c8-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d71c8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> diagnostiky**](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="d71c8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="d71c8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<endToEndTracing >**</span><span class="sxs-lookup"><span data-stu-id="d71c8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d71c8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d71c8-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d71c8-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d71c8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d71c8-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d71c8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d71c8-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d71c8-110">Attributes</span></span>  
  
|<span data-ttu-id="d71c8-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="d71c8-111">Attribute</span></span>|<span data-ttu-id="d71c8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d71c8-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="d71c8-113">Logická hodnota, která určuje, zda je povoleno trasování aktivit.</span><span class="sxs-lookup"><span data-stu-id="d71c8-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="d71c8-114">Logická hodnota, která určuje, zda je povoleno sledování toku zprávy.</span><span class="sxs-lookup"><span data-stu-id="d71c8-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="d71c8-115">Logická hodnota určující, zda je atribut rozšíření nastaven na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="d71c8-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d71c8-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d71c8-116">Child Elements</span></span>  
 <span data-ttu-id="d71c8-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="d71c8-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d71c8-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d71c8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d71c8-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="d71c8-119">Element</span></span>|<span data-ttu-id="d71c8-120">Popis</span><span class="sxs-lookup"><span data-stu-id="d71c8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d71c8-121">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="d71c8-121">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="d71c8-122">Definuje nastavení WCF pro kontrolu a kontrolu za běhu pro správce.</span><span class="sxs-lookup"><span data-stu-id="d71c8-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d71c8-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d71c8-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="d71c8-124">Komplexní trasování</span><span class="sxs-lookup"><span data-stu-id="d71c8-124">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
