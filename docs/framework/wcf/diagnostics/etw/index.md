---
title: Analytické trasování s ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: dd745730ca186b9489c547f790c546e95bf96372
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798087"
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="18e72-102">Analytické trasování s ETW</span><span class="sxs-lookup"><span data-stu-id="18e72-102">Analytic Tracing with ETW</span></span>
<span data-ttu-id="18e72-103">Analytické trasování Windows Communication Foundation (WCF) nabízí způsob, jak zachytit diagnostické informace během provádění služby WCF.</span><span class="sxs-lookup"><span data-stu-id="18e72-103">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="18e72-104">Události analytického trasování WCF se generují na klíčových místech v zásobníku WCF, aby bylo možné řešit potíže se službami WCF v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="18e72-104">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="18e72-105">Analytické trasování pro služby WCF má minimální dopad na výkon produktového serveru, který je hostitelem [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] služeb WCF, protože tyto události jsou velmi efektivně generovány do relace trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="18e72-105">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18e72-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="18e72-106">In This Section</span></span>  
 [<span data-ttu-id="18e72-107">Přehled analytického trasování</span><span class="sxs-lookup"><span data-stu-id="18e72-107">Analytic Tracing Overview</span></span>](analytic-tracing-overview.md)  
 <span data-ttu-id="18e72-108">Popisuje, jak funguje analytické trasování WCF [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]v.</span><span class="sxs-lookup"><span data-stu-id="18e72-108">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="18e72-109">Dynamické povolování analytického sledování</span><span class="sxs-lookup"><span data-stu-id="18e72-109">Dynamically Enabling Analytic Tracing</span></span>](dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="18e72-110">Popisuje, jak povolit nebo zakázat trasování dynamicky pomocí ETW.</span><span class="sxs-lookup"><span data-stu-id="18e72-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="18e72-111">Konfigurace trasování toku zpráv</span><span class="sxs-lookup"><span data-stu-id="18e72-111">Configuring Message Flow Tracing</span></span>](configuring-message-flow-tracing.md)  
 <span data-ttu-id="18e72-112">Popisuje postup konfigurace trasování toku zpráv.</span><span class="sxs-lookup"><span data-stu-id="18e72-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="18e72-113">Události analytického trasování – přehled</span><span class="sxs-lookup"><span data-stu-id="18e72-113">Analytic Trace Event Reference</span></span>](analytic-trace-event-reference.md)  
 <span data-ttu-id="18e72-114">Zobrazuje tabulku ID událostí s jejich úrovněmi události, zprávami o událostech a klíčovými slovy.</span><span class="sxs-lookup"><span data-stu-id="18e72-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e72-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18e72-115">See also</span></span>

- [<span data-ttu-id="18e72-116">Služby WCF a Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="18e72-116">WCF Services and Event Tracing for Windows</span></span>](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [<span data-ttu-id="18e72-117">Sledování událostí v Trasování událostí ve Windows</span><span class="sxs-lookup"><span data-stu-id="18e72-117">Tracking Events into Event Tracing in Windows</span></span>](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
