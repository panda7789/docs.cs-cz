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
ms.workload: dotnet
ms.openlocfilehash: a43801f4c45d7ac518c3b24cadc58ffbec40adb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="ebf69-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="ebf69-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="ebf69-103">Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování během spuštění aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="ebf69-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="ebf69-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ebf69-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ebf69-105">\<diagnostické ></span><span class="sxs-lookup"><span data-stu-id="ebf69-105">\<diagnostic></span></span>  
<span data-ttu-id="ebf69-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="ebf69-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf69-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebf69-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebf69-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ebf69-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ebf69-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ebf69-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebf69-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ebf69-110">Attributes</span></span>  
  
|<span data-ttu-id="ebf69-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="ebf69-111">Attribute</span></span>|<span data-ttu-id="ebf69-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ebf69-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="ebf69-113">Logická hodnota, která určuje, jestli je povolené trasování aktivity.</span><span class="sxs-lookup"><span data-stu-id="ebf69-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="ebf69-114">Logická hodnota, která určuje, jestli je povolené trasování v tok zpráv.</span><span class="sxs-lookup"><span data-stu-id="ebf69-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="ebf69-115">Logická hodnota, která určuje, zda je atribut propagate nastavena na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="ebf69-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebf69-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ebf69-116">Child Elements</span></span>  
 <span data-ttu-id="ebf69-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="ebf69-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ebf69-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ebf69-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ebf69-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="ebf69-119">Element</span></span>|<span data-ttu-id="ebf69-120">Popis</span><span class="sxs-lookup"><span data-stu-id="ebf69-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ebf69-121">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="ebf69-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="ebf69-122">Definuje nastavení WCF pro modul runtime kontroly a řízení pro správce.</span><span class="sxs-lookup"><span data-stu-id="ebf69-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ebf69-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebf69-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="ebf69-124">Komplexní trasování</span><span class="sxs-lookup"><span data-stu-id="ebf69-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
