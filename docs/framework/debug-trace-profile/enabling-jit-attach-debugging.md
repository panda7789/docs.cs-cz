---
title: 'Povolení JIT – ladění Attach '
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b92592500f0babf29891710cedf1228b0ddcb0e4
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45587490"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="20b4d-102">Povolení JIT – ladění Attach </span><span class="sxs-lookup"><span data-stu-id="20b4d-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="20b4d-103">JIT – ladění attach je frázi používají k popisu připojení ladicího programu k procesu, pokud narazíte na chyby, nebo se dá spouštět podle konkrétní metody nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="20b4d-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="20b4d-104">JIT – ladění attach slouží za následujících podmínek selhání:</span><span class="sxs-lookup"><span data-stu-id="20b4d-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
-   <span data-ttu-id="20b4d-105">Neošetřené výjimky (v nativní a spravovaný kód).</span><span class="sxs-lookup"><span data-stu-id="20b4d-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
-   <span data-ttu-id="20b4d-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> Metoda nebo [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) – funkce (řady Windows 7).</span><span class="sxs-lookup"><span data-stu-id="20b4d-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) function (Windows 7 family).</span></span>  
  
-   <span data-ttu-id="20b4d-107">Závažné chyby za běhu.</span><span class="sxs-lookup"><span data-stu-id="20b4d-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="20b4d-108">JIT – ladění attach také aktivuje volání těchto metod a funkce:</span><span class="sxs-lookup"><span data-stu-id="20b4d-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
-   <span data-ttu-id="20b4d-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="20b4d-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="20b4d-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="20b4d-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="20b4d-111">[DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) – funkce (Win32).</span><span class="sxs-lookup"><span data-stu-id="20b4d-111">[DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) function (Win32).</span></span>  
  
 <span data-ttu-id="20b4d-112">Před [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], rozhraní .NET Framework poskytuje klíče samostatné registru, které řídí chování ladicí programy pro nativní a spravované.</span><span class="sxs-lookup"><span data-stu-id="20b4d-112">Before the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="20b4d-113">Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], ovládací prvek je konsolidovány do jednoho registru: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="20b4d-113">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="20b4d-114">Hodnoty, které můžete nastavit pro daný klíč určit, zda ladicí program je vyvolán, a pokud ano, zda je vyvolána s dialogové okno, které vyžaduje zásah uživatele.</span><span class="sxs-lookup"><span data-stu-id="20b4d-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="20b4d-115">Informace o nastavení tohoto klíče registru najdete v tématu [konfiguraci automatického ladění](https://go.microsoft.com/fwlink/?LinkId=181767).</span><span class="sxs-lookup"><span data-stu-id="20b4d-115">For information about setting this registry key, see [Configuring Automatic Debugging](https://go.microsoft.com/fwlink/?LinkId=181767).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20b4d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="20b4d-116">See Also</span></span>  
 [<span data-ttu-id="20b4d-117">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="20b4d-117">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)  
 [<span data-ttu-id="20b4d-118">Usnadnění ladění obrázku</span><span class="sxs-lookup"><span data-stu-id="20b4d-118">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 [<span data-ttu-id="20b4d-119">Povolení profilace</span><span class="sxs-lookup"><span data-stu-id="20b4d-119">Enabling Profiling</span></span>](https://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
