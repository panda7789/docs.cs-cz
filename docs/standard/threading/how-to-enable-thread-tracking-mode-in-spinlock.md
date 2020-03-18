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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138037"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="1d8b3-102">Postupy: Povolení režimu sledování vláken ve struktuře SpinLock</span><span class="sxs-lookup"><span data-stu-id="1d8b3-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="1d8b3-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType>je zámek vzájemného vyloučení nižší úrovně, který můžete použít pro scénáře, které mají velmi krátké čekací doby.</span><span class="sxs-lookup"><span data-stu-id="1d8b3-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="1d8b3-104"><xref:System.Threading.SpinLock>není znovu účastníkem.</span><span class="sxs-lookup"><span data-stu-id="1d8b3-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="1d8b3-105">Poté, co vlákno vstoupí do zámku, musí zámek před znovu zadat.</span><span class="sxs-lookup"><span data-stu-id="1d8b3-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="1d8b3-106">Obvykle jakýkoli pokus o opětovné zadání zámku by způsobit zablokování a zablokování může být velmi obtížné ladit.</span><span class="sxs-lookup"><span data-stu-id="1d8b3-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="1d8b3-107">Jako pomůcku pro vývoj podporuje režim sledování vláken, který způsobí, že výjimka má být vyvolána, když se vlákno pokusí znovu zadat zámek, <xref:System.Threading.SpinLock?displayProperty=nameWithType> který již obsahuje.</span><span class="sxs-lookup"><span data-stu-id="1d8b3-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="1d8b3-108">To umožňuje snadněji vyhledat bod, ve kterém zámek nebyl ukončen správně.</span><span class="sxs-lookup"><span data-stu-id="1d8b3-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="1d8b3-109">Můžete zapnout režim sledování vláken <xref:System.Threading.SpinLock> pomocí konstruktoru, který přebírá logický vstupní parametr `true`a předávání maješku argumentu .</span><span class="sxs-lookup"><span data-stu-id="1d8b3-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="1d8b3-110">Po dokončení fáze vývoje a testování vypněte režim sledování vláken pro lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="1d8b3-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d8b3-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d8b3-111">Example</span></span>  
 <span data-ttu-id="1d8b3-112">Následující příklad ukazuje režim sledování vláken.</span><span class="sxs-lookup"><span data-stu-id="1d8b3-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="1d8b3-113">Řádky, které správně ukončit zámek jsou zakomentovány, aby simulovaly chybu kódování, která způsobuje jeden z následujících výsledků:</span><span class="sxs-lookup"><span data-stu-id="1d8b3-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
- <span data-ttu-id="1d8b3-114">Výjimka je vyvolána, <xref:System.Threading.SpinLock> pokud byl vytvořen `true` `True` pomocí argumentu (v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="1d8b3-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
- <span data-ttu-id="1d8b3-115">Zablokování, pokud <xref:System.Threading.SpinLock> byl vytvořen pomocí `false` argumentu (`False` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="1d8b3-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="1d8b3-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d8b3-116">See also</span></span>

- [<span data-ttu-id="1d8b3-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="1d8b3-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
