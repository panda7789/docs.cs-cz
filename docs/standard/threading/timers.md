---
title: "Časovače"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 80b4cee03e934d3aec98ca323aac43f934c56455
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="timers"></a><span data-ttu-id="86c66-102">Časovače</span><span class="sxs-lookup"><span data-stu-id="86c66-102">Timers</span></span>
<span data-ttu-id="86c66-103">Časovače jsou zjednodušené objekty, které umožňují delegátu, aby byl zavolán v určený čas.</span><span class="sxs-lookup"><span data-stu-id="86c66-103">Timers are lightweight objects that enable you to specify a delegate to be called at a specified time.</span></span> <span data-ttu-id="86c66-104">Vlákno ve fondu vláken provádí operaci čekání.</span><span class="sxs-lookup"><span data-stu-id="86c66-104">A thread in the thread pool performs the wait operation.</span></span>  
  
 <span data-ttu-id="86c66-105">Používání třídy <xref:System.Threading.Timer?displayProperty=nameWithType> je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="86c66-105">Using the <xref:System.Threading.Timer?displayProperty=nameWithType> class is straightforward.</span></span> <span data-ttu-id="86c66-106">Vytváření **časovače**, předejte <xref:System.Threading.TimerCallback> delegátovi, aby se metoda zpětného volání, objekt reprezentující stav, který se předá zpětné volání, vyvolat počáteční čas a čas představující dobu mezi volání zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="86c66-106">You create a **Timer**, passing a <xref:System.Threading.TimerCallback> delegate to the callback method, an object representing state that will be passed to the callback, an initial raise time, and a time representing the period between callback invocations.</span></span> <span data-ttu-id="86c66-107">Chcete-li zrušit čekající časovač, zavolejte **Timer.Dispose** funkce.</span><span class="sxs-lookup"><span data-stu-id="86c66-107">To cancel a pending timer, call the **Timer.Dispose** function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86c66-108">Existují dvě další třídy časovače.</span><span class="sxs-lookup"><span data-stu-id="86c66-108">There are two other timer classes.</span></span> <span data-ttu-id="86c66-109">Třída <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> je ovládací prvek, který pracuje s vizuálními návrháři, a používá se v kontextu uživatelského rozhraní. Vyvolává události na vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="86c66-109">The <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> class is a control that works with visual designers and is meant to be used in user interface contexts; it raises events on the user interface thread.</span></span> <span data-ttu-id="86c66-110">Třída <xref:System.Timers.Timer?displayProperty=nameWithType> je odvozena z třídy <xref:System.ComponentModel.Component>, takže ji lze použít s vizuálními návrháři, a také vyvolává události, avšak na vlákně <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="86c66-110">The <xref:System.Timers.Timer?displayProperty=nameWithType> class derives from <xref:System.ComponentModel.Component>, so it can be used with visual designers; it also raises events, but it raises them on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="86c66-111">Třída <xref:System.Threading.Timer?displayProperty=nameWithType> vytváří zpětná volání na vlákno <xref:System.Threading.ThreadPool> a nepoužívá model událostí.</span><span class="sxs-lookup"><span data-stu-id="86c66-111">The <xref:System.Threading.Timer?displayProperty=nameWithType> class makes callbacks on a <xref:System.Threading.ThreadPool> thread and does not use the event model at all.</span></span> <span data-ttu-id="86c66-112">Poskytuje také stav objektu metodě zpětného volání, což jiné časovače neumožňují.</span><span class="sxs-lookup"><span data-stu-id="86c66-112">It also provides a state object to the callback method, which the other timers do not.</span></span> <span data-ttu-id="86c66-113">Je to velmi jednoduché.</span><span class="sxs-lookup"><span data-stu-id="86c66-113">It is extremely lightweight.</span></span>  
  
 <span data-ttu-id="86c66-114">Následující příklad kódu spustí časovač, která se spouští za sekundu (1000 milisekund) a rysky každou sekundu se stisknutím **Enter** klíč.</span><span class="sxs-lookup"><span data-stu-id="86c66-114">The following code example starts a timer that starts after one second (1000 milliseconds) and ticks every second until you press the **Enter** key.</span></span> <span data-ttu-id="86c66-115">Proměnná obsahující odkaz na časovač je pole na úrovni třídy. Díky tomu nebude časovač uvolněn z paměti, pokud je stále spuštěn.</span><span class="sxs-lookup"><span data-stu-id="86c66-115">The variable containing the reference to the timer is a class-level field, to ensure that the timer is not subject to garbage collection while it is still running.</span></span> <span data-ttu-id="86c66-116">Další informace o agresivním uvolňování paměti naleznete v tématu <xref:System.GC.KeepAlive%2A>.</span><span class="sxs-lookup"><span data-stu-id="86c66-116">For more information on aggressive garbage collection, see <xref:System.GC.KeepAlive%2A>.</span></span>  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="86c66-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="86c66-117">See Also</span></span>  
 <xref:System.Threading.Timer>  
 [<span data-ttu-id="86c66-118">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="86c66-118">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
