---
title: '&lt;endToEndTracing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb187302000291fd6b540b562ed7aebf1db7add2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="2ffe7-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="2ffe7-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="2ffe7-103">Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování během spuštění aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="2ffe7-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="2ffe7-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2ffe7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2ffe7-105">\<diagnostické ></span><span class="sxs-lookup"><span data-stu-id="2ffe7-105">\<diagnostic></span></span>  
<span data-ttu-id="2ffe7-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="2ffe7-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ffe7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ffe7-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ffe7-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2ffe7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2ffe7-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2ffe7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ffe7-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2ffe7-110">Attributes</span></span>  
  
|<span data-ttu-id="2ffe7-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2ffe7-111">Attribute</span></span>|<span data-ttu-id="2ffe7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2ffe7-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="2ffe7-113">Logická hodnota, která určuje, jestli je povolené trasování aktivity.</span><span class="sxs-lookup"><span data-stu-id="2ffe7-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="2ffe7-114">Logická hodnota, která určuje, jestli je povolené trasování v tok zpráv.</span><span class="sxs-lookup"><span data-stu-id="2ffe7-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="2ffe7-115">Logická hodnota, která určuje, zda je atribut propagate nastavena na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="2ffe7-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ffe7-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2ffe7-116">Child Elements</span></span>  
 <span data-ttu-id="2ffe7-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="2ffe7-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ffe7-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2ffe7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2ffe7-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="2ffe7-119">Element</span></span>|<span data-ttu-id="2ffe7-120">Popis</span><span class="sxs-lookup"><span data-stu-id="2ffe7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ffe7-121">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="2ffe7-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="2ffe7-122">Definuje nastavení WCF pro modul runtime kontroly a řízení pro správce.</span><span class="sxs-lookup"><span data-stu-id="2ffe7-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ffe7-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ffe7-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="2ffe7-124">Konec Konec trasování</span><span class="sxs-lookup"><span data-stu-id="2ffe7-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
