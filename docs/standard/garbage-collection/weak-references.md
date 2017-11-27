---
title: "Slabé odkazy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 906c23caa7065486bb094ad2475ed9e7e24b3d9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="weak-references"></a><span data-ttu-id="33cc5-102">Slabé odkazy</span><span class="sxs-lookup"><span data-stu-id="33cc5-102">Weak References</span></span>
<span data-ttu-id="33cc5-103">Uvolňování paměti nelze shromažďovat objekt používá jiná aplikace při kódu aplikace dosáhnout tento objekt.</span><span class="sxs-lookup"><span data-stu-id="33cc5-103">The garbage collector cannot collect an object in use by an application while the application's code can reach that object.</span></span> <span data-ttu-id="33cc5-104">Aplikace se říká obsahují silné odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="33cc5-104">The application is said to have a strong reference to the object.</span></span>  
  
 <span data-ttu-id="33cc5-105">Slabé odkazy umožňuje uvolňování ke shromažďování objekt zároveň umožňuje aplikaci získat přístup k objektu.</span><span class="sxs-lookup"><span data-stu-id="33cc5-105">A weak reference permits the garbage collector to collect the object while still allowing the application to access the object.</span></span> <span data-ttu-id="33cc5-106">Slabé odkazy je platný pouze během neurčitém množství času, dokud nebude objekt shromažďuje, když neexistuje žádné silné odkazy.</span><span class="sxs-lookup"><span data-stu-id="33cc5-106">A weak reference is valid only during the indeterminate amount of time until the object is collected when no strong references exist.</span></span> <span data-ttu-id="33cc5-107">Pokud použijete slabé odkaz, aplikace můžete získat stále silné odkaz na objekt, který zabraňuje v jeho nejsou shromažďována.</span><span class="sxs-lookup"><span data-stu-id="33cc5-107">When you use a weak reference, the application can still obtain a strong reference to the object, which prevents it from being collected.</span></span> <span data-ttu-id="33cc5-108">Však není vždy riziko, že uvolňování paměti získá k objektu nejprve předtím, než se obnovila silné odkaz.</span><span class="sxs-lookup"><span data-stu-id="33cc5-108">However, there is always the risk that the garbage collector will get to the object first before a strong reference is reestablished.</span></span>  
  
 <span data-ttu-id="33cc5-109">Slabé odkazy jsou užitečné pro objekty, které používají velké množství paměti, ale můžete je znovu vytvořit snadno Pokud jsou převzaty systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="33cc5-109">Weak references are useful for objects that use a lot of memory, but can be recreated easily if they are reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="33cc5-110">Předpokládejme, že je stromové zobrazení v aplikaci Windows Forms zobrazí komplexní hierarchické výběr možností pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="33cc5-110">Suppose a tree view in a Windows Forms application displays a complex hierarchical choice of options to the user.</span></span> <span data-ttu-id="33cc5-111">Základní dat je velká, udržování stromu v paměti je v případě, když uživatel se zabývá něco jiného v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="33cc5-111">If the underlying data is large, keeping the tree in memory is inefficient when the user is involved with something else in the application.</span></span>  
  
 <span data-ttu-id="33cc5-112">Když uživatel přepíná rychle do jiné části aplikace, můžete použít <xref:System.WeakReference> třída vytvořit slabé odkaz na stromu a zrušení silné všechny odkazy.</span><span class="sxs-lookup"><span data-stu-id="33cc5-112">When the user switches away to another part of the application, you can use the <xref:System.WeakReference> class to create a weak reference to the tree and destroy all strong references.</span></span> <span data-ttu-id="33cc5-113">Když uživatel přejde zpět do stromu, aplikace se pokusí získat silné odkaz na stromu a v případě úspěšného zabraňuje rekonstrukce stromu.</span><span class="sxs-lookup"><span data-stu-id="33cc5-113">When the user switches back to the tree, the application attempts to obtain a strong reference to the tree and, if successful, avoids reconstructing the tree.</span></span>  
  
 <span data-ttu-id="33cc5-114">Když Pokud chcete stanovit slabé odkaz s objektem, vytvoříte <xref:System.WeakReference> pomocí instance objektu sledovat.</span><span class="sxs-lookup"><span data-stu-id="33cc5-114">To establish a weak reference with an object, you create a <xref:System.WeakReference> using the instance of the object to be tracked.</span></span> <span data-ttu-id="33cc5-115">Pak můžete nastavit <xref:System.WeakReference.Target%2A> vlastnost, která má tento objekt a sadu původní odkaz na objekt, který má `null`.</span><span class="sxs-lookup"><span data-stu-id="33cc5-115">You then set the <xref:System.WeakReference.Target%2A> property to that object and set the original reference to the object to `null`.</span></span> <span data-ttu-id="33cc5-116">Příklad kódu, najdete v článku <xref:System.WeakReference> v knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="33cc5-116">For a code example, see <xref:System.WeakReference> in the class library.</span></span>  
  
## <a name="short-and-long-weak-references"></a><span data-ttu-id="33cc5-117">Krátký a dlouhý slabé odkazy</span><span class="sxs-lookup"><span data-stu-id="33cc5-117">Short and Long Weak References</span></span>  
 <span data-ttu-id="33cc5-118">Můžete vytvořit odkaz na krátké slabé nebo dlouho slabé odkazy:</span><span class="sxs-lookup"><span data-stu-id="33cc5-118">You can create a short weak reference or a long weak reference:</span></span>  
  
-   <span data-ttu-id="33cc5-119">krátký</span><span class="sxs-lookup"><span data-stu-id="33cc5-119">Short</span></span>  
  
     <span data-ttu-id="33cc5-120">Cíl krátký slabé odkaz se změní na `null` když je objekt uvolněn systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="33cc5-120">The target of a short weak reference becomes `null` when the object is reclaimed by garbage collection.</span></span> <span data-ttu-id="33cc5-121">Odkaz na slabé je sám spravovaného objektu a mohou podléhat uvolňování paměti stejně jako ostatní spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="33cc5-121">The weak reference is itself a managed object, and is subject to garbage collection just like any other managed object.</span></span>  <span data-ttu-id="33cc5-122">Odkaz na krátké slabé je pro výchozí konstruktor <xref:System.WeakReference>.</span><span class="sxs-lookup"><span data-stu-id="33cc5-122">A short weak reference is the default constructor for <xref:System.WeakReference>.</span></span>  
  
-   <span data-ttu-id="33cc5-123">dlouhá</span><span class="sxs-lookup"><span data-stu-id="33cc5-123">Long</span></span>  
  
     <span data-ttu-id="33cc5-124">Dlouho slabé odkaz se uchovávají objektu <xref:System.Object.Finalize%2A> byla volána metoda.</span><span class="sxs-lookup"><span data-stu-id="33cc5-124">A long weak reference is retained after the object's <xref:System.Object.Finalize%2A> method has been called.</span></span> <span data-ttu-id="33cc5-125">To umožňuje objekt, který má být znovu vytvořen, ale pořád nepředvídatelným stav objektu.</span><span class="sxs-lookup"><span data-stu-id="33cc5-125">This allows the object to be recreated, but the state of the object remains unpredictable.</span></span> <span data-ttu-id="33cc5-126">Chcete-li použít dlouho odkaz, zadejte `true` v <xref:System.WeakReference> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="33cc5-126">To use a long reference, specify `true` in the <xref:System.WeakReference> constructor.</span></span>  
  
     <span data-ttu-id="33cc5-127">Pokud nemá typ objektu <xref:System.Object.Finalize%2A> používá funkci krátké Slabý odkaz metoda, a je slabé odkaz platný pouze dokud cíle jsou shromažďovány, kterému může dojít, kdykoli později finalizační metodu je spustit.</span><span class="sxs-lookup"><span data-stu-id="33cc5-127">If the object's type does not have a <xref:System.Object.Finalize%2A> method, the short weak reference functionality applies and the weak reference is valid only until the target is collected, which can occur anytime after the finalizer is run.</span></span>  
  
 <span data-ttu-id="33cc5-128">Vytvořit odkaz na silné a znovu použít objekt přetypovat <xref:System.WeakReference.Target%2A> vlastnost <xref:System.WeakReference> na typ objektu.</span><span class="sxs-lookup"><span data-stu-id="33cc5-128">To establish a strong reference and use the object again, cast the <xref:System.WeakReference.Target%2A> property of a <xref:System.WeakReference> to the type of the object.</span></span> <span data-ttu-id="33cc5-129">Pokud <xref:System.WeakReference.Target%2A> vlastnost vrátí `null`objektu byla shromážděných jinak, můžete nadále používat objekt, protože aplikace je znovu získali silné odkaz na jeho.</span><span class="sxs-lookup"><span data-stu-id="33cc5-129">If the <xref:System.WeakReference.Target%2A> property returns `null`, the object was collected; otherwise, you can continue to use the object because the application has regained a strong reference to it.</span></span>  
  
## <a name="guidelines-for-using-weak-references"></a><span data-ttu-id="33cc5-130">Pokyny k používání slabé odkazy</span><span class="sxs-lookup"><span data-stu-id="33cc5-130">Guidelines for Using Weak References</span></span>  
 <span data-ttu-id="33cc5-131">Použijte dlouho slabé odkazy pouze v případě potřeby, protože stav objektu nepředvídatelným po dokončení.</span><span class="sxs-lookup"><span data-stu-id="33cc5-131">Use long weak references only when necessary as the state of the object is unpredictable after finalization.</span></span>  
  
 <span data-ttu-id="33cc5-132">Nepoužívejte slabé odkazy na objekty malé, protože ukazatel samotné může být jako velké nebo větší.</span><span class="sxs-lookup"><span data-stu-id="33cc5-132">Avoid using weak references to small objects because the pointer itself may be as large or larger.</span></span>  
  
 <span data-ttu-id="33cc5-133">Nepoužívejte slabé odkazy jako automatické řešení problémů správu paměti.</span><span class="sxs-lookup"><span data-stu-id="33cc5-133">Avoid using weak references as an automatic solution to memory management problems.</span></span> <span data-ttu-id="33cc5-134">Místo toho vytvořte efektivní zásady ukládání do mezipaměti pro zpracování objektů vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="33cc5-134">Instead, develop an effective caching policy for handling your application's objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33cc5-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="33cc5-135">See Also</span></span>  
 [<span data-ttu-id="33cc5-136">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="33cc5-136">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
