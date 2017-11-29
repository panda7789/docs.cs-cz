---
title: "Povolení JIT – ladění Attach "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 107b47ba8abcbd1084bed6e043f5a648aa91cc91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="2a725-102">Povolení JIT – ladění Attach </span><span class="sxs-lookup"><span data-stu-id="2a725-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="2a725-103">JIT – připojené ladění je fráze používají k popisu připojení ladicího programu procesu, když dojde k chybám, nebo ji můžete aktivovat konkrétní metody nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="2a725-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="2a725-104">JIT – připojené ladění se používá za následujících podmínek chyby:</span><span class="sxs-lookup"><span data-stu-id="2a725-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
-   <span data-ttu-id="2a725-105">Nezpracované výjimky (v nativního a spravovaného kódu).</span><span class="sxs-lookup"><span data-stu-id="2a725-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
-   <span data-ttu-id="2a725-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType>Metoda nebo [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) – funkce (rodiny Windows 7).</span><span class="sxs-lookup"><span data-stu-id="2a725-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) function (Windows 7 family).</span></span>  
  
-   <span data-ttu-id="2a725-107">Závažné chyby za běhu.</span><span class="sxs-lookup"><span data-stu-id="2a725-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="2a725-108">JIT – připojené ladění se aktivuje také při volání těchto metod a funkce:</span><span class="sxs-lookup"><span data-stu-id="2a725-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
-   <span data-ttu-id="2a725-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="2a725-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="2a725-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="2a725-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="2a725-111">[Debugbreak –](http://go.microsoft.com/fwlink/?LinkId=182106) – funkce (Win32).</span><span class="sxs-lookup"><span data-stu-id="2a725-111">[DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) function (Win32).</span></span>  
  
 <span data-ttu-id="2a725-112">Před [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], rozhraní .NET Framework poskytuje klíče registru samostatné pro řízení chování nativní a spravovaná ladicí programy.</span><span class="sxs-lookup"><span data-stu-id="2a725-112">Before the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="2a725-113">Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], je ovládací prvek konsolidovány do klíče registru jednu: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="2a725-113">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="2a725-114">Hodnoty, které můžete nastavit pro tento klíč určit, zda je volána ladicí program a pokud ano, zda je volána, dialogové okno, které vyžaduje interakci uživatele.</span><span class="sxs-lookup"><span data-stu-id="2a725-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="2a725-115">Informace o nastavení tohoto klíče registru najdete v tématu [konfigurace automatické ladění](http://go.microsoft.com/fwlink/?LinkId=181767).</span><span class="sxs-lookup"><span data-stu-id="2a725-115">For information about setting this registry key, see [Configuring Automatic Debugging](http://go.microsoft.com/fwlink/?LinkId=181767).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a725-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a725-116">See Also</span></span>  
 [<span data-ttu-id="2a725-117">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="2a725-117">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)  
 [<span data-ttu-id="2a725-118">Usnadnění ladění obrázku</span><span class="sxs-lookup"><span data-stu-id="2a725-118">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 [<span data-ttu-id="2a725-119">Povolení profilace</span><span class="sxs-lookup"><span data-stu-id="2a725-119">Enabling Profiling</span></span>](http://msdn.microsoft.com/en-us/3b669676-f0e0-4ebf-8674-68986dd2020d)
