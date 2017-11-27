---
title: "Trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e0a291e3ca277bc58f69b8016c523b383b3cece8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="tracing"></a><span data-ttu-id="02dbc-102">Trasování</span><span class="sxs-lookup"><span data-stu-id="02dbc-102">Tracing</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="02dbc-103">poskytuje instrumentace aplikací a diagnostických dat pro monitorování selhání a analýzy.</span><span class="sxs-lookup"><span data-stu-id="02dbc-103"> provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="02dbc-104">Trasování místo ladicí program vám pomůže pochopit, jak se chovají aplikace nebo proč chyb.</span><span class="sxs-lookup"><span data-stu-id="02dbc-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="02dbc-105">Zpracování chyb a také mohou korelovat mezi komponentami a poskytuje prostředí začátku do konce.</span><span class="sxs-lookup"><span data-stu-id="02dbc-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="02dbc-106">výstupy následující data pro diagnostické trasování:</span><span class="sxs-lookup"><span data-stu-id="02dbc-106"> outputs the following data for diagnostic tracing:</span></span>  
  
-   <span data-ttu-id="02dbc-107">Trasování pro milníky procesu pro všechny součásti aplikací, jako je například volání operací kód výjimky, upozornění a další důležité zpracování událostí."</span><span class="sxs-lookup"><span data-stu-id="02dbc-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
-   <span data-ttu-id="02dbc-108">Události systému Windows chybu při trasování funkce nefunguje správně.</span><span class="sxs-lookup"><span data-stu-id="02dbc-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="02dbc-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="02dbc-109">In This Section</span></span>  
 [<span data-ttu-id="02dbc-110">Konfigurace trasování</span><span class="sxs-lookup"><span data-stu-id="02dbc-110">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
 <span data-ttu-id="02dbc-111">Toto téma popisuje, jak konfigurovat trasování na různých úrovních, aby vyhovovala vašim konkrétním potřebám.</span><span class="sxs-lookup"><span data-stu-id="02dbc-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="02dbc-112">Konec Konec trasování</span><span class="sxs-lookup"><span data-stu-id="02dbc-112">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)  
  
 <span data-ttu-id="02dbc-113">Tato část popisuje, jak můžete použít aktivitu trasování a šíření pro korelaci začátku do konce pomůže ladění.</span><span class="sxs-lookup"><span data-stu-id="02dbc-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="02dbc-114">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="02dbc-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="02dbc-115">Tato část popisuje, jak můžete trasování ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="02dbc-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="02dbc-116">Otázky zabezpečení a užitečné tipy pro trasování</span><span class="sxs-lookup"><span data-stu-id="02dbc-116">Security Concerns and Useful Tips for Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="02dbc-117">Toto téma popisuje, jak můžete chránit citlivé informace před vystavením i užitečné tipy, při použití webového hostitele.</span><span class="sxs-lookup"><span data-stu-id="02dbc-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="02dbc-118">Trasování – přehled</span><span class="sxs-lookup"><span data-stu-id="02dbc-118">Traces Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/traces-reference.md)  
  
 <span data-ttu-id="02dbc-119">Toto téma obsahuje seznam všech trasování generované [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02dbc-119">This topic lists all the traces generated by [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02dbc-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="02dbc-120">See Also</span></span>  
 [<span data-ttu-id="02dbc-121">Nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="02dbc-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
