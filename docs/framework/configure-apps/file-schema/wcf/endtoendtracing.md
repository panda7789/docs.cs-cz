---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 6b23728451a051f21ad3863b9a29e6290c3c837a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919001"
---
# <a name="endtoendtracing"></a><span data-ttu-id="2312f-101">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="2312f-101">\<endToEndTracing></span></span>
<span data-ttu-id="2312f-102">Prvek konfigurace, který umožňuje povolit nebo zakázat různé aspekty komplexního trasování během běžící aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="2312f-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="2312f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2312f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2312f-104">\<> diagnostiky</span><span class="sxs-lookup"><span data-stu-id="2312f-104">\<diagnostic></span></span>  
<span data-ttu-id="2312f-105">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="2312f-105">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2312f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2312f-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2312f-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2312f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2312f-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2312f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2312f-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="2312f-109">Attributes</span></span>  
  
|<span data-ttu-id="2312f-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="2312f-110">Attribute</span></span>|<span data-ttu-id="2312f-111">Popis</span><span class="sxs-lookup"><span data-stu-id="2312f-111">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="2312f-112">Logická hodnota, která určuje, zda je povoleno trasování aktivit.</span><span class="sxs-lookup"><span data-stu-id="2312f-112">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="2312f-113">Logická hodnota, která určuje, zda je povoleno sledování toku zprávy.</span><span class="sxs-lookup"><span data-stu-id="2312f-113">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="2312f-114">Logická hodnota určující, zda je atribut rozšíření nastaven na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="2312f-114">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2312f-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2312f-115">Child Elements</span></span>  
 <span data-ttu-id="2312f-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="2312f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2312f-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2312f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2312f-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="2312f-118">Element</span></span>|<span data-ttu-id="2312f-119">Popis</span><span class="sxs-lookup"><span data-stu-id="2312f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2312f-120">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="2312f-120">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="2312f-121">Definuje nastavení WCF pro kontrolu a kontrolu za běhu pro správce.</span><span class="sxs-lookup"><span data-stu-id="2312f-121">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2312f-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2312f-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="2312f-123">Komplexní trasování</span><span class="sxs-lookup"><span data-stu-id="2312f-123">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
