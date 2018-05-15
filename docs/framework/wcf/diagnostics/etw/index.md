---
title: Analytické trasování s ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: 210418b8a8765a1fc59658e9df57c92ce087c95f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="fd871-102">Analytické trasování s ETW</span><span class="sxs-lookup"><span data-stu-id="fd871-102">Analytic Tracing with ETW</span></span>
<span data-ttu-id="fd871-103">Analytické trasování Windows Communication Foundation (WCF) nabízí způsob, jak zachytit diagnostické informace během provádění služby WCF.</span><span class="sxs-lookup"><span data-stu-id="fd871-103">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="fd871-104">Události analytické trasování WCF jsou vydávány v klíčové body v zásobníku WCF umožňuje řešení potíží s služby WCF v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="fd871-104">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="fd871-105">Analytické trasování pro služby WCF má minimální dopad na výkon produktu serveru, který je hostitelem [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] služeb WCF, jak tyto události jsou velmi efektivně vygenerované relaci události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="fd871-105">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd871-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fd871-106">In This Section</span></span>  
 [<span data-ttu-id="fd871-107">Přehled analytického trasování</span><span class="sxs-lookup"><span data-stu-id="fd871-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="fd871-108">Popisuje, jak funguje analytické trasování WCF [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd871-108">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="fd871-109">Dynamické povolování analytického sledování</span><span class="sxs-lookup"><span data-stu-id="fd871-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="fd871-110">Popisuje, jak povolit nebo zakázat trasování dynamicky pomocí trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="fd871-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="fd871-111">Konfigurace trasování toku zpráv</span><span class="sxs-lookup"><span data-stu-id="fd871-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="fd871-112">Popisuje postup konfigurace trasování toku zpráv.</span><span class="sxs-lookup"><span data-stu-id="fd871-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="fd871-113">Události analytického trasování – přehled</span><span class="sxs-lookup"><span data-stu-id="fd871-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="fd871-114">Příklad ID událostí s úrovní událostí, zprávy o událostech a klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="fd871-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd871-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd871-115">See Also</span></span>  
 [<span data-ttu-id="fd871-116">Služby WCF a Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="fd871-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [<span data-ttu-id="fd871-117">Sledování událostí v Trasování událostí ve Windows</span><span class="sxs-lookup"><span data-stu-id="fd871-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
