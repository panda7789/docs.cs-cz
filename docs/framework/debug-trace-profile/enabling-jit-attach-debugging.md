---
title: Povolení JIT – ladění Attach
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4d4e2b3806d2c4d84b59e1cd44eb03ab7b278c9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052827"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="ef5af-102">Povolení JIT – ladění Attach</span><span class="sxs-lookup"><span data-stu-id="ef5af-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="ef5af-103">Ladění JIT za běhu je fráze sloužící k popisu připojení ladicího programu k procesu, když dojde k chybám, nebo může být aktivována konkrétními metodami nebo funkcemi.</span><span class="sxs-lookup"><span data-stu-id="ef5af-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="ef5af-104">Ladění JIT JIT se používá v následujících podmínkách selhání:</span><span class="sxs-lookup"><span data-stu-id="ef5af-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="ef5af-105">Neošetřené výjimky (v nativním i spravovaném kódu).</span><span class="sxs-lookup"><span data-stu-id="ef5af-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="ef5af-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType>Metoda nebo funkce [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) (řada Windows 7).</span><span class="sxs-lookup"><span data-stu-id="ef5af-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="ef5af-107">Kritické chyby modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ef5af-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="ef5af-108">Ladění JIT JIT se spouští také voláními následujících metod a funkcí:</span><span class="sxs-lookup"><span data-stu-id="ef5af-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="ef5af-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="ef5af-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="ef5af-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="ef5af-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="ef5af-111">Funkce [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) (Win32).</span><span class="sxs-lookup"><span data-stu-id="ef5af-111">[DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) function (Win32).</span></span>  
  
 <span data-ttu-id="ef5af-112">Před .NET Framework 4 poskytovala .NET Framework samostatné klíče registru pro řízení chování nativních a spravovaných ladicích programů.</span><span class="sxs-lookup"><span data-stu-id="ef5af-112">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="ef5af-113">Počínaje .NET Framework 4 je ovládací prvek konsolidován v rámci jednoho klíče registru: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="ef5af-113">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="ef5af-114">Hodnoty, které lze nastavit pro tento klíč, určují, zda je vyvolán ladicí program, a pokud ano, zda je vyvolána s dialogovým oknem, které vyžaduje zásah uživatele.</span><span class="sxs-lookup"><span data-stu-id="ef5af-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="ef5af-115">Informace o nastavení tohoto klíče registru najdete v tématu [Konfigurace automatického ladění](https://go.microsoft.com/fwlink/?LinkId=181767).</span><span class="sxs-lookup"><span data-stu-id="ef5af-115">For information about setting this registry key, see [Configuring Automatic Debugging](https://go.microsoft.com/fwlink/?LinkId=181767).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef5af-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef5af-116">See also</span></span>

- [<span data-ttu-id="ef5af-117">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="ef5af-117">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="ef5af-118">Usnadnění ladění obrázku</span><span class="sxs-lookup"><span data-stu-id="ef5af-118">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
