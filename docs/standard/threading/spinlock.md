---
title: SpinLock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: efe9b3126b3c952ab156f9ca40752ad8d3fddcd1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="spinlock"></a><span data-ttu-id="27117-102">SpinLock</span><span class="sxs-lookup"><span data-stu-id="27117-102">SpinLock</span></span>
<span data-ttu-id="27117-103"><xref:System.Threading.SpinLock> Struktura je nízké úrovně, vzájemné vyloučení synchronizaci primitivní, otáčí během čekání na získání zámku.</span><span class="sxs-lookup"><span data-stu-id="27117-103">The <xref:System.Threading.SpinLock> structure is a low-level, mutual-exclusion synchronization primitive that spins while it waits to acquire a lock.</span></span> <span data-ttu-id="27117-104">Na počítači, vícejádrovými, když se očekává, dobu čekání být krátké a pokud je minimální, kolizí <xref:System.Threading.SpinLock> můžete provádět lépe než jiné druhy zámky.</span><span class="sxs-lookup"><span data-stu-id="27117-104">On multicore computers, when wait times are expected to be short and when contention is minimal, <xref:System.Threading.SpinLock> can perform better than other kinds of locks.</span></span> <span data-ttu-id="27117-105">Doporučujeme však používat <xref:System.Threading.SpinLock> pouze, když určíte profilace, který <xref:System.Threading.Monitor?displayProperty=nameWithType> metoda nebo <xref:System.Threading.Interlocked> metody jsou výrazně zpomalení výkonu vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="27117-105">However, we recommend that you use <xref:System.Threading.SpinLock> only when you determine by profiling that the <xref:System.Threading.Monitor?displayProperty=nameWithType> method or the <xref:System.Threading.Interlocked> methods are significantly slowing the performance of your program.</span></span>  
  
 <span data-ttu-id="27117-106"><xref:System.Threading.SpinLock>může yield časového intervalu vlákna, i když ho ještě nebyla získat zámek.</span><span class="sxs-lookup"><span data-stu-id="27117-106"><xref:System.Threading.SpinLock> may yield the time slice of the thread even if it has not yet acquired the lock.</span></span> <span data-ttu-id="27117-107">Dělá to předejdete prioritu podprocesu inverzi a umožňuje uvolňování pokračovat.</span><span class="sxs-lookup"><span data-stu-id="27117-107">It does this to avoid thread-priority inversion, and to enable the garbage collector to make progress.</span></span> <span data-ttu-id="27117-108">Při použití <xref:System.Threading.SpinLock>, ujistěte se, že žádný přístup z více vláken může obsahovat zámek pro více než velmi krátké časové období a že žádný přístup z více vláken můžete blokovat, když drží zámek.</span><span class="sxs-lookup"><span data-stu-id="27117-108">When you use a <xref:System.Threading.SpinLock>, ensure that no thread can hold the lock for more than a very brief time span, and that no thread can block while it holds the lock.</span></span>  
  
 <span data-ttu-id="27117-109">Protože SpinLock je typ hodnoty, je nutné explicitně předat ji odkazem Pokud máte v úmyslu dvě kopie odkazovat na stejné zámek.</span><span class="sxs-lookup"><span data-stu-id="27117-109">Because SpinLock is a value type, you must explicitly pass it by reference if you intend the two copies to refer to the same lock.</span></span>  
  
 <span data-ttu-id="27117-110">Další informace o tom, jak pomocí tohoto typu najdete v tématu <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="27117-110">For more information about how to use this type, see <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span></span> <span data-ttu-id="27117-111">Příklad, naleznete v části [postupy: použití SpinLock pro synchronizaci nižší úrovně](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="27117-111">For an example, see [How to: Use SpinLock for Low-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).</span></span>  
  
 <span data-ttu-id="27117-112"><xref:System.Threading.SpinLock>podporuje *vlákno*-*sledování* režim, který můžete použít během fáze vývoje k usnadnění sledování vláken, která nastavila zámek v určitém čase.</span><span class="sxs-lookup"><span data-stu-id="27117-112"><xref:System.Threading.SpinLock> supports a *thread*-*tracking* mode that you can use during the development phase to help track the thread that is holding the lock at a specific time.</span></span> <span data-ttu-id="27117-113">Režimu sledování vláken je velmi užitečná pro ladění, ale doporučujeme vypnout ho ve verzi vašeho programu vzhledem k tomu může zpomalit výkon.</span><span class="sxs-lookup"><span data-stu-id="27117-113">Thread-tracking mode is very useful for debugging, but we recommend that you turn it off in the release version of your program because it may slow performance.</span></span> <span data-ttu-id="27117-114">Další informace najdete v tématu [postupy: povolení vlákna sledování režimu ve struktuře SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).</span><span class="sxs-lookup"><span data-stu-id="27117-114">For more information, see [How to: Enable Thread-Tracking Mode in SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27117-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="27117-115">See Also</span></span>  
 [<span data-ttu-id="27117-116">Dělení na vlákna objektů a funkcí</span><span class="sxs-lookup"><span data-stu-id="27117-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
