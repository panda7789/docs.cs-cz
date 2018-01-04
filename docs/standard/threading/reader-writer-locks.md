---
title: "Zámky modulů pro čtení a zápis"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d005442ee74b46a0ecb1eaafe214e7190330cfe7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="reader-writer-locks"></a><span data-ttu-id="9e0ba-102">Zámky modulů pro čtení a zápis</span><span class="sxs-lookup"><span data-stu-id="9e0ba-102">Reader-Writer Locks</span></span>
<span data-ttu-id="9e0ba-103"><xref:System.Threading.ReaderWriterLockSlim> Třída umožňuje více vláken současně číst prostředek, ale vyžaduje vlákna počkat, aby bylo možné zapsat do prostředku výhradní zámek.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-103">The <xref:System.Threading.ReaderWriterLockSlim> class enables multiple threads to read a resource concurrently, but requires a thread to wait for an exclusive lock in order to write to the resource.</span></span>  
  
 <span data-ttu-id="9e0ba-104">Můžete použít <xref:System.Threading.ReaderWriterLockSlim> ve vaší aplikaci zajistit spolupráci synchronizace mezi vláken, která přístup ke sdíleným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-104">You might use a <xref:System.Threading.ReaderWriterLockSlim> in your application to provide cooperative synchronization among threads that access a shared resource.</span></span> <span data-ttu-id="9e0ba-105">Zámky jsou přesměrováni <xref:System.Threading.ReaderWriterLockSlim> sám sebe.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-105">Locks are taken on the <xref:System.Threading.ReaderWriterLockSlim> itself.</span></span>  
  
 <span data-ttu-id="9e0ba-106">Jako s mechanismus synchronizace přístup z více vláken, je nutné zajistit, že nejsou žádná vlákna nepoužívat zamykání, které poskytuje <xref:System.Threading.ReaderWriterLockSlim>.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-106">As with any thread synchronization mechanism, you must ensure that no threads bypass the locking that is provided by <xref:System.Threading.ReaderWriterLockSlim>.</span></span> <span data-ttu-id="9e0ba-107">Jeden způsob, jak zajistit toto je návrh třídy, který zapouzdřuje sdílený prostředek.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-107">One way to ensure this is to design a class that encapsulates the shared resource.</span></span> <span data-ttu-id="9e0ba-108">Tato třída by poskytují členy, přístup k privátním sdílený prostředek a které používají soukromé <xref:System.Threading.ReaderWriterLockSlim> pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-108">This class would provide members that access the private shared resource and that use a private <xref:System.Threading.ReaderWriterLockSlim> for synchronization.</span></span> <span data-ttu-id="9e0ba-109">Příklad, podívejte se na příklad kódu pro <xref:System.Threading.ReaderWriterLockSlim> třídy.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-109">For an example, see the code example for the <xref:System.Threading.ReaderWriterLockSlim> class.</span></span> <span data-ttu-id="9e0ba-110"><xref:System.Threading.ReaderWriterLockSlim>je dostatečně efektivní, který se má použít k synchronizaci jednotlivých objektů.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-110"><xref:System.Threading.ReaderWriterLockSlim> is efficient enough to be used to synchronize individual objects.</span></span>  
  
 <span data-ttu-id="9e0ba-111">Struktury aplikace minimalizovat dobu trvání pro čtení a zápisu operace.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-111">Structure your application to minimize the duration of read and write operations.</span></span> <span data-ttu-id="9e0ba-112">Operace zápisu dlouho ovlivnit propustnost přímo, protože je určena výhradně uzamčení pro zápis.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-112">Long write operations affect throughput directly because the write lock is exclusive.</span></span> <span data-ttu-id="9e0ba-113">Dlouho čtení operations bloku čekání zapisovače a pokud alespoň jedno vlákno čeká přístup pro zápis, vláken, které požadují přístup pro čtení se zablokuje také.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-113">Long read operations block waiting writers, and if at least one thread is waiting for write access, threads that request read access will be blocked as well.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e0ba-114">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Má dva zámků čtení a zápis, <xref:System.Threading.ReaderWriterLockSlim> a <xref:System.Threading.ReaderWriterLock>.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-114">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] has two reader-writer locks, <xref:System.Threading.ReaderWriterLockSlim> and <xref:System.Threading.ReaderWriterLock>.</span></span> <span data-ttu-id="9e0ba-115"><xref:System.Threading.ReaderWriterLockSlim>doporučuje se pro všechny nové vývoj.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-115"><xref:System.Threading.ReaderWriterLockSlim> is recommended for all new development.</span></span> <span data-ttu-id="9e0ba-116"><xref:System.Threading.ReaderWriterLockSlim>je podobná <xref:System.Threading.ReaderWriterLock>, ale zjednodušila pravidla pro rekurze a pro upgrade a přechod na starší verzi Stav zámku.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-116"><xref:System.Threading.ReaderWriterLockSlim> is similar to <xref:System.Threading.ReaderWriterLock>, but it has simplified rules for recursion and for upgrading and downgrading lock state.</span></span> <span data-ttu-id="9e0ba-117"><xref:System.Threading.ReaderWriterLockSlim>zabraňuje mnoha případech potenciální zablokování.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-117"><xref:System.Threading.ReaderWriterLockSlim> avoids many cases of potential deadlock.</span></span> <span data-ttu-id="9e0ba-118">Kromě toho výkon <xref:System.Threading.ReaderWriterLockSlim> je výrazně lepší, než <xref:System.Threading.ReaderWriterLock>.</span><span class="sxs-lookup"><span data-stu-id="9e0ba-118">In addition, the performance of <xref:System.Threading.ReaderWriterLockSlim> is significantly better than <xref:System.Threading.ReaderWriterLock>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0ba-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e0ba-119">See Also</span></span>  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [<span data-ttu-id="9e0ba-120">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="9e0ba-120">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="9e0ba-121">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="9e0ba-121">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
