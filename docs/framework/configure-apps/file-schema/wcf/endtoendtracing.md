---
title: '&lt;endToEndTracing&gt;'
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 78a69256a391e97ff1962eea923f09115c4ebadd
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150107"
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="a6101-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="a6101-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="a6101-103">Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování za běhu aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="a6101-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="a6101-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a6101-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a6101-105">\<diagnostiky ></span><span class="sxs-lookup"><span data-stu-id="a6101-105">\<diagnostic></span></span>  
<span data-ttu-id="a6101-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="a6101-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6101-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6101-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6101-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a6101-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a6101-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a6101-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6101-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a6101-110">Attributes</span></span>  
  
|<span data-ttu-id="a6101-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a6101-111">Attribute</span></span>|<span data-ttu-id="a6101-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a6101-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="a6101-113">Logická hodnota určující, zda je povoleno trasování činnosti.</span><span class="sxs-lookup"><span data-stu-id="a6101-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="a6101-114">Logická hodnota určující, zda je povoleno sledování toku zprávy.</span><span class="sxs-lookup"><span data-stu-id="a6101-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="a6101-115">Logická hodnota, která určuje, zda je atribut propagate nastaven na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="a6101-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6101-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a6101-116">Child Elements</span></span>  
 <span data-ttu-id="a6101-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="a6101-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6101-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a6101-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a6101-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="a6101-119">Element</span></span>|<span data-ttu-id="a6101-120">Popis</span><span class="sxs-lookup"><span data-stu-id="a6101-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6101-121">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="a6101-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="a6101-122">Definuje nastavení kontroly runtime WCF a ovládací prvek pro správce.</span><span class="sxs-lookup"><span data-stu-id="a6101-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6101-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6101-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="a6101-124">Komplexní trasování</span><span class="sxs-lookup"><span data-stu-id="a6101-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
