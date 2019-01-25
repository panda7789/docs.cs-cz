---
title: Analytické trasování s ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: 4651c515a938ed8f8736597808156080cfb0bbed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609080"
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="6161a-102">Analytické trasování s ETW</span><span class="sxs-lookup"><span data-stu-id="6161a-102">Analytic Tracing with ETW</span></span>
<span data-ttu-id="6161a-103">Analytické trasování Windows Communication Foundation (WCF) nabízí způsob, jak zachytit diagnostické informace během provádění ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="6161a-103">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="6161a-104">Události analytického trasování WCF jsou emitovány klíčových bodů v zásobníku WCF povolit Poradce při potížích pro služby WCF v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="6161a-104">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="6161a-105">Analytické trasování pro služby WCF má minimální dopad na výkon server produktu, který je hostitelem [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] služby WCF, protože tyto události jsou velmi efektivně vygenerován pro relaci Event Tracing for Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="6161a-105">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6161a-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6161a-106">In This Section</span></span>  
 [<span data-ttu-id="6161a-107">Přehled analytického trasování</span><span class="sxs-lookup"><span data-stu-id="6161a-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="6161a-108">Tento článek popisuje princip analytické trasování WCF v [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6161a-108">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="6161a-109">Dynamické povolování analytického sledování</span><span class="sxs-lookup"><span data-stu-id="6161a-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="6161a-110">Popisuje, jak povolit nebo zakázat trasování dynamicky pomocí trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="6161a-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="6161a-111">Konfigurace trasování toku zpráv</span><span class="sxs-lookup"><span data-stu-id="6161a-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="6161a-112">Popisuje postup konfigurace trasování toku zpráv.</span><span class="sxs-lookup"><span data-stu-id="6161a-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="6161a-113">Události analytického trasování – přehled</span><span class="sxs-lookup"><span data-stu-id="6161a-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="6161a-114">Zobrazuje tabulku ID událostí s jejich úrovně události, zprávy o událostech a klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="6161a-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6161a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6161a-115">See also</span></span>
- [<span data-ttu-id="6161a-116">Služby WCF a Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="6161a-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
- [<span data-ttu-id="6161a-117">Sledování událostí v Trasování událostí ve Windows</span><span class="sxs-lookup"><span data-stu-id="6161a-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
