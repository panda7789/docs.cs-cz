---
title: 'Postupy: Povolení režimu sledování vláken ve struktuře SpinLock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
ms.openlocfilehash: f52a844284cf46bcace3f54f8b320d336050a64e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138037"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="c8ee5-102">Postupy: Povolení režimu sledování vláken ve struktuře SpinLock</span><span class="sxs-lookup"><span data-stu-id="c8ee5-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="c8ee5-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> je vzájemný zámek pro vzájemné vyloučení, který můžete použít pro scénáře s velmi krátkými čekacími časy.</span><span class="sxs-lookup"><span data-stu-id="c8ee5-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="c8ee5-104"><xref:System.Threading.SpinLock> není znovu vstupující.</span><span class="sxs-lookup"><span data-stu-id="c8ee5-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="c8ee5-105">Po vložení vlákna do zámku musí být zámek správně ukončen, než bude možné ho znovu zadat.</span><span class="sxs-lookup"><span data-stu-id="c8ee5-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="c8ee5-106">Každý pokus o opětovné zadání zámku by obvykle způsobil zablokování a zablokování může být pro ladění velmi obtížné.</span><span class="sxs-lookup"><span data-stu-id="c8ee5-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="c8ee5-107">Jako pomůcka pro vývoj <xref:System.Threading.SpinLock?displayProperty=nameWithType> podporuje režim sledování vláken, který způsobí vyvolání výjimky, když se vlákno pokusí znovu zadat zámek, který už je uložený.</span><span class="sxs-lookup"><span data-stu-id="c8ee5-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="c8ee5-108">To vám umožní snadněji najít bod, ve kterém se zámek neukončil správně.</span><span class="sxs-lookup"><span data-stu-id="c8ee5-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="c8ee5-109">Režim sledování vláken lze zapnout pomocí <xref:System.Threading.SpinLock> konstruktoru, který přebírá logický vstupní parametr a je v argumentu `true`.</span><span class="sxs-lookup"><span data-stu-id="c8ee5-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="c8ee5-110">Po dokončení fází vývoje a testování vypněte režim sledování vláken pro lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="c8ee5-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8ee5-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="c8ee5-111">Example</span></span>  
 <span data-ttu-id="c8ee5-112">Následující příklad znázorňuje režim sledování vláken.</span><span class="sxs-lookup"><span data-stu-id="c8ee5-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="c8ee5-113">Řádky, které správně ukončí zámek, jsou zakomentovány, aby se simulovala Chyba kódování, která způsobuje jednu z následujících výsledků:</span><span class="sxs-lookup"><span data-stu-id="c8ee5-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
- <span data-ttu-id="c8ee5-114">Pokud byl <xref:System.Threading.SpinLock> vytvořen pomocí argumentu `true` (`True` v Visual Basic), je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c8ee5-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
- <span data-ttu-id="c8ee5-115">Zablokování, pokud byl <xref:System.Threading.SpinLock> vytvořen pomocí argumentu `false` (`False` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c8ee5-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="c8ee5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8ee5-116">See also</span></span>

- [<span data-ttu-id="c8ee5-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="c8ee5-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
