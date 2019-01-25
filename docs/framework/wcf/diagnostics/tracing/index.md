---
title: Trasování
ms.date: 03/30/2017
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
ms.openlocfilehash: 4165dbb68ac962737c9dcc99e984248c668bb1b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506794"
---
# <a name="tracing"></a><span data-ttu-id="0196f-102">Trasování</span><span class="sxs-lookup"><span data-stu-id="0196f-102">Tracing</span></span>
<span data-ttu-id="0196f-103">Windows Communication Foundation (WCF) poskytuje instrumentace aplikací a diagnostických dat pro sledování chyb a analýzu.</span><span class="sxs-lookup"><span data-stu-id="0196f-103">Windows Communication Foundation (WCF) provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="0196f-104">Trasování můžete použít namísto ladicí program pochopit, jak se aplikace chová nebo proč chyb.</span><span class="sxs-lookup"><span data-stu-id="0196f-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="0196f-105">Můžete také porovnat chyb a zpracování mezi komponentami a poskytovalo vám začátku do konce.</span><span class="sxs-lookup"><span data-stu-id="0196f-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 <span data-ttu-id="0196f-106">WCF následující výstupní data odesílá do pro diagnostické trasování:</span><span class="sxs-lookup"><span data-stu-id="0196f-106">WCF outputs the following data for diagnostic tracing:</span></span>  
  
-   <span data-ttu-id="0196f-107">Trasování pro proces milníky pro všechny součásti aplikace, jako je volání operace kód výjimky, upozornění a dalších operací zpracování událostí."</span><span class="sxs-lookup"><span data-stu-id="0196f-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
-   <span data-ttu-id="0196f-108">Události chyb Windows při trasování funkce nepracuje správně.</span><span class="sxs-lookup"><span data-stu-id="0196f-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0196f-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0196f-109">In This Section</span></span>  
 [<span data-ttu-id="0196f-110">Konfigurace trasování</span><span class="sxs-lookup"><span data-stu-id="0196f-110">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
 <span data-ttu-id="0196f-111">Toto téma popisuje, jak nakonfigurovat trasování na různých úrovních tak, aby odpovídala vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="0196f-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="0196f-112">Komplexní trasování</span><span class="sxs-lookup"><span data-stu-id="0196f-112">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)  
  
 <span data-ttu-id="0196f-113">Tato část popisuje, jak můžete pomocí aktivity trasování a šíření pro korelaci začátku do konce pomáhat ladění.</span><span class="sxs-lookup"><span data-stu-id="0196f-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="0196f-114">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="0196f-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="0196f-115">Tato část popisuje, jak můžete pomocí trasování pro ladění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="0196f-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="0196f-116">Otázky zabezpečení a užitečné tipy pro trasování</span><span class="sxs-lookup"><span data-stu-id="0196f-116">Security Concerns and Useful Tips for Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="0196f-117">Toto téma popisuje, jak můžete chránit citlivé informace z vystaven i užitečné tipy při použití webového hostitele.</span><span class="sxs-lookup"><span data-stu-id="0196f-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="0196f-118">Trasování – přehled</span><span class="sxs-lookup"><span data-stu-id="0196f-118">Traces Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/traces-reference.md)  
  
 <span data-ttu-id="0196f-119">Toto téma obsahuje seznam všech trasování vygenerovaná WCF.</span><span class="sxs-lookup"><span data-stu-id="0196f-119">This topic lists all the traces generated by WCF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0196f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0196f-120">See also</span></span>
- [<span data-ttu-id="0196f-121">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="0196f-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
