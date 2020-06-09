---
title: Trasování
ms.date: 03/30/2017
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
ms.openlocfilehash: 569a97dc21a434cd711ad4c735f828df588f3af7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578978"
---
# <a name="tracing"></a><span data-ttu-id="1f581-102">Trasování</span><span class="sxs-lookup"><span data-stu-id="1f581-102">Tracing</span></span>
<span data-ttu-id="1f581-103">Windows Communication Foundation (WCF) poskytuje instrumentaci aplikace a diagnostická data pro monitorování a analýzu chyb.</span><span class="sxs-lookup"><span data-stu-id="1f581-103">Windows Communication Foundation (WCF) provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="1f581-104">K pochopení, jak se aplikace chová, nebo proč chyby, můžete použít trasování namísto ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="1f581-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="1f581-105">K zajištění komplexního prostředí můžete také korelovat chyby a zpracování napříč komponentami.</span><span class="sxs-lookup"><span data-stu-id="1f581-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 <span data-ttu-id="1f581-106">WCF vyprodukuje následující data pro diagnostické trasování:</span><span class="sxs-lookup"><span data-stu-id="1f581-106">WCF outputs the following data for diagnostic tracing:</span></span>  
  
- <span data-ttu-id="1f581-107">Trasování pro milníky procesů napříč všemi komponentami aplikací, například volání operací, výjimky kódu, upozornění a další významné události zpracování. "</span><span class="sxs-lookup"><span data-stu-id="1f581-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
- <span data-ttu-id="1f581-108">Chybové události systému Windows, pokud funkce trasování nepracuje správně.</span><span class="sxs-lookup"><span data-stu-id="1f581-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f581-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1f581-109">In This Section</span></span>  
 [<span data-ttu-id="1f581-110">Konfigurace trasování</span><span class="sxs-lookup"><span data-stu-id="1f581-110">Configuring Tracing</span></span>](configuring-tracing.md)  
  
 <span data-ttu-id="1f581-111">Toto téma popisuje, jak můžete nakonfigurovat trasování na různých úrovních, aby vyhovovalo vašim konkrétním potřebám.</span><span class="sxs-lookup"><span data-stu-id="1f581-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="1f581-112">Komplexní trasování</span><span class="sxs-lookup"><span data-stu-id="1f581-112">End-to-End Tracing</span></span>](end-to-end-tracing.md)  
  
 <span data-ttu-id="1f581-113">V této části se dozvíte, jak můžete využít trasování aktivit a šíření pro ucelenou korelaci pro usnadnění ladění.</span><span class="sxs-lookup"><span data-stu-id="1f581-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="1f581-114">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="1f581-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="1f581-115">Tato část popisuje, jak lze pomocí trasování ladit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1f581-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="1f581-116">Otázky zabezpečení a užitečné tipy pro trasování</span><span class="sxs-lookup"><span data-stu-id="1f581-116">Security Concerns and Useful Tips for Tracing</span></span>](security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="1f581-117">V tomto tématu se dozvíte, jak můžete při použití webhosta chránit citlivé informace, které se zveřejňují, a užitečné tipy.</span><span class="sxs-lookup"><span data-stu-id="1f581-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="1f581-118">Trasování – přehled</span><span class="sxs-lookup"><span data-stu-id="1f581-118">Traces Reference</span></span>](traces-reference.md)  
  
 <span data-ttu-id="1f581-119">Toto téma obsahuje seznam všech trasování generovaných službou WCF.</span><span class="sxs-lookup"><span data-stu-id="1f581-119">This topic lists all the traces generated by WCF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f581-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f581-120">See also</span></span>

- [<span data-ttu-id="1f581-121">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="1f581-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
