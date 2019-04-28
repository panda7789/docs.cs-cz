---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 266b33e9b0386d0346a86ba8bd82cc65def4f0c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673053"
---
# <a name="endtoendtracing"></a><span data-ttu-id="885c0-101">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="885c0-101">\<endToEndTracing></span></span>
<span data-ttu-id="885c0-102">Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování za běhu aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="885c0-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="885c0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="885c0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="885c0-104">\<diagnostic></span><span class="sxs-lookup"><span data-stu-id="885c0-104">\<diagnostic></span></span>  
<span data-ttu-id="885c0-105">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="885c0-105">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="885c0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="885c0-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="885c0-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="885c0-107">Attributes and Elements</span></span>  
 <span data-ttu-id="885c0-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="885c0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="885c0-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="885c0-109">Attributes</span></span>  
  
|<span data-ttu-id="885c0-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="885c0-110">Attribute</span></span>|<span data-ttu-id="885c0-111">Popis</span><span class="sxs-lookup"><span data-stu-id="885c0-111">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="885c0-112">Logická hodnota určující, zda je povoleno trasování činnosti.</span><span class="sxs-lookup"><span data-stu-id="885c0-112">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="885c0-113">Logická hodnota určující, zda je povoleno sledování toku zprávy.</span><span class="sxs-lookup"><span data-stu-id="885c0-113">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="885c0-114">Logická hodnota, která určuje, zda je atribut propagate nastaven na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="885c0-114">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="885c0-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="885c0-115">Child Elements</span></span>  
 <span data-ttu-id="885c0-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="885c0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="885c0-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="885c0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="885c0-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="885c0-118">Element</span></span>|<span data-ttu-id="885c0-119">Popis</span><span class="sxs-lookup"><span data-stu-id="885c0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="885c0-120">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="885c0-120">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="885c0-121">Definuje nastavení kontroly runtime WCF a ovládací prvek pro správce.</span><span class="sxs-lookup"><span data-stu-id="885c0-121">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="885c0-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="885c0-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="885c0-123">Komplexní trasování</span><span class="sxs-lookup"><span data-stu-id="885c0-123">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
