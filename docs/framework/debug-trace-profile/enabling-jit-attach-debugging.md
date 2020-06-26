---
title: 'Povolení JIT – ladění Attach '
description: Povolit JIT (just-in time) připojit ladění pro připojení ladicího programu k procesu, když dojde k chybám Může se aktivovat určitými metodami nebo funkcemi.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: d1190c51a9cc6b5322ec832e0d35bc01dc855b12
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416041"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="f3e93-104">Povolení JIT – ladění Attach </span><span class="sxs-lookup"><span data-stu-id="f3e93-104">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="f3e93-105">Ladění JIT za běhu je fráze sloužící k popisu připojení ladicího programu k procesu, když dojde k chybám, nebo může být aktivována konkrétními metodami nebo funkcemi.</span><span class="sxs-lookup"><span data-stu-id="f3e93-105">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="f3e93-106">Ladění JIT JIT se používá v následujících podmínkách selhání:</span><span class="sxs-lookup"><span data-stu-id="f3e93-106">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="f3e93-107">Neošetřené výjimky (v nativním i spravovaném kódu).</span><span class="sxs-lookup"><span data-stu-id="f3e93-107">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="f3e93-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType>Metoda nebo funkce [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) (řada Windows 7).</span><span class="sxs-lookup"><span data-stu-id="f3e93-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="f3e93-109">Kritické chyby modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f3e93-109">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="f3e93-110">Ladění JIT JIT se spouští také voláními následujících metod a funkcí:</span><span class="sxs-lookup"><span data-stu-id="f3e93-110">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="f3e93-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="f3e93-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="f3e93-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>Metoda.</span><span class="sxs-lookup"><span data-stu-id="f3e93-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="f3e93-113">Funkce [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) (Win32).</span><span class="sxs-lookup"><span data-stu-id="f3e93-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) function (Win32).</span></span>  
  
 <span data-ttu-id="f3e93-114">Před .NET Framework 4 poskytovala .NET Framework samostatné klíče registru pro řízení chování nativních a spravovaných ladicích programů.</span><span class="sxs-lookup"><span data-stu-id="f3e93-114">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="f3e93-115">Počínaje .NET Framework 4 je ovládací prvek konsolidován v jednom klíči registru: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="f3e93-115">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="f3e93-116">Hodnoty, které lze nastavit pro tento klíč, určují, zda je vyvolán ladicí program, a pokud ano, zda je vyvolána s dialogovým oknem, které vyžaduje zásah uživatele.</span><span class="sxs-lookup"><span data-stu-id="f3e93-116">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="f3e93-117">Informace o nastavení tohoto klíče registru najdete v tématu [Konfigurace automatického ladění](/windows/win32/debug/configuring-automatic-debugging).</span><span class="sxs-lookup"><span data-stu-id="f3e93-117">For information about setting this registry key, see [Configuring Automatic Debugging](/windows/win32/debug/configuring-automatic-debugging).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e93-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3e93-118">See also</span></span>

- [<span data-ttu-id="f3e93-119">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="f3e93-119">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="f3e93-120">Usnadnění ladění image</span><span class="sxs-lookup"><span data-stu-id="f3e93-120">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
