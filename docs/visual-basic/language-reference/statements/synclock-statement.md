---
title: "SyncLock – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c363b41bb7a409c490a6e07d4a1a4f1bb44c1438
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="synclock-statement"></a><span data-ttu-id="cb326-102">SyncLock – příkaz</span><span class="sxs-lookup"><span data-stu-id="cb326-102">SyncLock Statement</span></span>
<span data-ttu-id="cb326-103">Získá výhradní zámek pro příkaz blok před provedením bloku.</span><span class="sxs-lookup"><span data-stu-id="cb326-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb326-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb326-104">Syntax</span></span>  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="cb326-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="cb326-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="cb326-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="cb326-106">Required.</span></span> <span data-ttu-id="cb326-107">Výraz, který se vyhodnotí jako odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="cb326-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="cb326-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="cb326-108">Optional.</span></span> <span data-ttu-id="cb326-109">Blok příkazů, které se mají spustit, když je získat zámek.</span><span class="sxs-lookup"><span data-stu-id="cb326-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="cb326-110">Ukončí `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="cb326-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb326-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb326-111">Remarks</span></span>  
 <span data-ttu-id="cb326-112">`SyncLock` Příkaz zajistí, že více vláken nespouštějte příkaz bloku ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="cb326-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="cb326-113">`SyncLock`každé vlákno zabrání zadávání bloku, dokud ho spustíte žádné jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="cb326-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="cb326-114">Nejběžnější použití `SyncLock` je ochrana dat před více než jedním vláknem aktualizované současně.</span><span class="sxs-lookup"><span data-stu-id="cb326-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="cb326-115">Pokud příkazů, které manipulovat s daty, třeba přejít k dokončení bez přerušení, umístí je uvnitř `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="cb326-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="cb326-116">Blok příkazu chráněn výhradní zámek se někdy nazývá *kritická sekce*.</span><span class="sxs-lookup"><span data-stu-id="cb326-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="cb326-117">Pravidla</span><span class="sxs-lookup"><span data-stu-id="cb326-117">Rules</span></span>  
  
-   <span data-ttu-id="cb326-118">Vytvoření větve.</span><span class="sxs-lookup"><span data-stu-id="cb326-118">Branching.</span></span> <span data-ttu-id="cb326-119">Můžete nemůže provést větvení do `SyncLock` blokovat z mimo blok.</span><span class="sxs-lookup"><span data-stu-id="cb326-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
-   <span data-ttu-id="cb326-120">Hodnota zámek objektu.</span><span class="sxs-lookup"><span data-stu-id="cb326-120">Lock Object Value.</span></span> <span data-ttu-id="cb326-121">Hodnota `lockobject` nemůže být `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="cb326-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="cb326-122">Než ho použijete, musíte vytvořit zámek objektu `SyncLock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="cb326-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="cb326-123">Nelze změnit hodnotu `lockobject` při provádění `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="cb326-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="cb326-124">Tento mechanismus vyžaduje, že zůstanou nezměněny zámek objektu.</span><span class="sxs-lookup"><span data-stu-id="cb326-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
-   <span data-ttu-id="cb326-125">Nelze použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="cb326-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="cb326-126">Chování</span><span class="sxs-lookup"><span data-stu-id="cb326-126">Behavior</span></span>  
  
-   <span data-ttu-id="cb326-127">Mechanismus.</span><span class="sxs-lookup"><span data-stu-id="cb326-127">Mechanism.</span></span> <span data-ttu-id="cb326-128">Když se dosáhne vlákna `SyncLock` příkaz, vyhodnocuje `lockobject` výraz a pozastaví spuštění, dokud ho získá výhradní zámek na objekt vrácený výrazem.</span><span class="sxs-lookup"><span data-stu-id="cb326-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="cb326-129">Když se dosáhne jiné vlákno `SyncLock` příkaz ji není získat zámek dokud provede první vlákno `End SyncLock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="cb326-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
-   <span data-ttu-id="cb326-130">Chráněná Data.</span><span class="sxs-lookup"><span data-stu-id="cb326-130">Protected Data.</span></span> <span data-ttu-id="cb326-131">Pokud `lockobject` je `Shared` proměnné, vlákno v žádné instanci třídy výhradní zámek brání v provádění `SyncLock` blokovat, když se spouští jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="cb326-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="cb326-132">To chrání data, která je sdílena mezi všemi instancemi.</span><span class="sxs-lookup"><span data-stu-id="cb326-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="cb326-133">Pokud `lockobject` je proměnná instance (není `Shared`), zámek brání spuštěné v aktuální instanci ze provádění vlákna `SyncLock` bloku ve stejnou dobu jako jiné vlákno ve stejné instanci.</span><span class="sxs-lookup"><span data-stu-id="cb326-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="cb326-134">To chrání data zachována jednotlivých instancí.</span><span class="sxs-lookup"><span data-stu-id="cb326-134">This protects data maintained by the individual instance.</span></span>  
  
-   <span data-ttu-id="cb326-135">Získání a verzi.</span><span class="sxs-lookup"><span data-stu-id="cb326-135">Acquisition and Release.</span></span> <span data-ttu-id="cb326-136">A `SyncLock` bloku se chová stejně jako `Try...Finally` konstrukce, ve kterém `Try` bloku získá výhradní zámek na `lockobject` a `Finally` uvolněním bloku.</span><span class="sxs-lookup"><span data-stu-id="cb326-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="cb326-137">Z toho důvodu `SyncLock` bloku zaručuje verze zámku, bez ohledu na to, jak byl ukončen blok.</span><span class="sxs-lookup"><span data-stu-id="cb326-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="cb326-138">To platí i v případě neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="cb326-138">This is true even in the case of an unhandled exception.</span></span>  
  
-   <span data-ttu-id="cb326-139">Volá Framework.</span><span class="sxs-lookup"><span data-stu-id="cb326-139">Framework Calls.</span></span> <span data-ttu-id="cb326-140">`SyncLock` Bloku operace čtení a uvolní výhradní zámek voláním `Enter` a `Exit` metody `Monitor` třídy v <xref:System.Threading> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cb326-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="cb326-141">Postupy programování</span><span class="sxs-lookup"><span data-stu-id="cb326-141">Programming Practices</span></span>  
 <span data-ttu-id="cb326-142">`lockobject` Výraz by měl být vždy vyhodnocen objekt, který patří výhradně na třídu.</span><span class="sxs-lookup"><span data-stu-id="cb326-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="cb326-143">By měly deklarovat `Private` objektová proměnná k ochraně dat, které patří do aktuální instance nebo `Private Shared` objektová proměnná k ochraně dat, které jsou společné pro všechny instance.</span><span class="sxs-lookup"><span data-stu-id="cb326-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="cb326-144">Neměli byste používat `Me` data pro instanci objektu – klíčové slovo zajistit zámek.</span><span class="sxs-lookup"><span data-stu-id="cb326-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="cb326-145">Pokud kód externí ke třídě obsahuje odkaz na instanci třídě, by mohl použít tento odkaz jako objekt zámku pro `SyncLock` bloku zcela liší od váš, ochrana dat na jiný.</span><span class="sxs-lookup"><span data-stu-id="cb326-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="cb326-146">Tímto způsobem třídě a jiná třída může blokovat navzájem z provedením jejich nesouvisejícími `SyncLock` bloky.</span><span class="sxs-lookup"><span data-stu-id="cb326-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="cb326-147">Vzhledem k tomu, že jakýkoli jiný kód v procesu pomocí stejné řetězce budou sdílet stejnou zámek může být problematické podobně uzamčení na řetězec.</span><span class="sxs-lookup"><span data-stu-id="cb326-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="cb326-148">Byste neměli používat `Me.GetType` metody můžete zajistit objekt zámku pro sdílená data.</span><span class="sxs-lookup"><span data-stu-id="cb326-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="cb326-149">Důvodem je, že `GetType` vždy vrátí stejné `Type` objekt pro název dané třídy.</span><span class="sxs-lookup"><span data-stu-id="cb326-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="cb326-150">Externí kód může volat `GetType` na vaší třídě a získat používáte stejný objekt zámku.</span><span class="sxs-lookup"><span data-stu-id="cb326-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="cb326-151">To by způsobilo dvě třídy blokování jiných z jejich `SyncLock` bloky.</span><span class="sxs-lookup"><span data-stu-id="cb326-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cb326-152">Příklady</span><span class="sxs-lookup"><span data-stu-id="cb326-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="cb326-153">Popis</span><span class="sxs-lookup"><span data-stu-id="cb326-153">Description</span></span>  
 <span data-ttu-id="cb326-154">Následující příklad ukazuje třídu, která udržuje jednoduchý seznam zpráv.</span><span class="sxs-lookup"><span data-stu-id="cb326-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="cb326-155">Drží zprávy v matici a posledních použít element tohoto pole v proměnné.</span><span class="sxs-lookup"><span data-stu-id="cb326-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="cb326-156">`addAnotherMessage` Postup zvýší posledním elementem a uloží novou zprávu.</span><span class="sxs-lookup"><span data-stu-id="cb326-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="cb326-157">Tyto dvě operace jsou chráněny `SyncLock` a `End SyncLock` příkazy, protože po posledním elementem se zvýší, nové zprávy musí být uložen před posledním elementem můžete zvýšit znovu jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="cb326-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="cb326-158">Pokud `simpleMessageList` třída sdílet jeden seznam zpráv mezi všechny jeho instance, proměnné `messagesList` a `messagesLast` by být deklarována jako `Shared`.</span><span class="sxs-lookup"><span data-stu-id="cb326-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="cb326-159">V tomto případě proměnnou `messagesLock` navíc by měl mít `Shared`, takže by jeden zámek objekt použitý objektem všechny instance.</span><span class="sxs-lookup"><span data-stu-id="cb326-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cb326-160">Kód</span><span class="sxs-lookup"><span data-stu-id="cb326-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a><span data-ttu-id="cb326-161">Popis</span><span class="sxs-lookup"><span data-stu-id="cb326-161">Description</span></span>  
 <span data-ttu-id="cb326-162">Následující příklad používá vláken a `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="cb326-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="cb326-163">Tak dlouho, dokud `SyncLock` příkaz, příkaz blok je důležitý oddíl a `balance` nikdy se změní na záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="cb326-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="cb326-164">Můžete Zakomentovat `SyncLock` a `End SyncLock` příkazy zobrazíte účinek vynechala `SyncLock` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="cb326-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cb326-165">Kód</span><span class="sxs-lookup"><span data-stu-id="cb326-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="cb326-166">Komentáře</span><span class="sxs-lookup"><span data-stu-id="cb326-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb326-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb326-167">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="cb326-168">Synchronizace vláken</span><span class="sxs-lookup"><span data-stu-id="cb326-168">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="cb326-169">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="cb326-169">Threading</span></span>](../../programming-guide/concepts/threading/index.md)
