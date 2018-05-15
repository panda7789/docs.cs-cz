---
title: '&lt;endToEndTracing&gt;'
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 855f579241dfd495e7f8603ce3bd57aa2556ca2d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="d1eb0-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="d1eb0-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="d1eb0-103">Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování během spuštění aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="d1eb0-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="d1eb0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d1eb0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d1eb0-105">\<diagnostické ></span><span class="sxs-lookup"><span data-stu-id="d1eb0-105">\<diagnostic></span></span>  
<span data-ttu-id="d1eb0-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="d1eb0-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1eb0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1eb0-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1eb0-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d1eb0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d1eb0-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d1eb0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1eb0-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d1eb0-110">Attributes</span></span>  
  
|<span data-ttu-id="d1eb0-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="d1eb0-111">Attribute</span></span>|<span data-ttu-id="d1eb0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d1eb0-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="d1eb0-113">Logická hodnota, která určuje, jestli je povolené trasování aktivity.</span><span class="sxs-lookup"><span data-stu-id="d1eb0-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="d1eb0-114">Logická hodnota, která určuje, jestli je povolené trasování v tok zpráv.</span><span class="sxs-lookup"><span data-stu-id="d1eb0-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="d1eb0-115">Logická hodnota, která určuje, zda je atribut propagate nastavena na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="d1eb0-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1eb0-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d1eb0-116">Child Elements</span></span>  
 <span data-ttu-id="d1eb0-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="d1eb0-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1eb0-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d1eb0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d1eb0-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="d1eb0-119">Element</span></span>|<span data-ttu-id="d1eb0-120">Popis</span><span class="sxs-lookup"><span data-stu-id="d1eb0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1eb0-121">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="d1eb0-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="d1eb0-122">Definuje nastavení WCF pro modul runtime kontroly a řízení pro správce.</span><span class="sxs-lookup"><span data-stu-id="d1eb0-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1eb0-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1eb0-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="d1eb0-124">Komplexní trasování</span><span class="sxs-lookup"><span data-stu-id="d1eb0-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
