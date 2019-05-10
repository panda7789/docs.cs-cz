---
title: SyncLock – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: a2bd6ca11072113d8acff78032c19d48c30933c3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615130"
---
# <a name="synclock-statement"></a><span data-ttu-id="3dbb0-102">SyncLock – příkaz</span><span class="sxs-lookup"><span data-stu-id="3dbb0-102">SyncLock Statement</span></span>
<span data-ttu-id="3dbb0-103">Získá výhradní zámek pro blok příkazů, který před spuštěním bloku.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dbb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dbb0-104">Syntax</span></span>  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="3dbb0-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="3dbb0-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="3dbb0-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-106">Required.</span></span> <span data-ttu-id="3dbb0-107">Výraz, který se vyhodnotí jako odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="3dbb0-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-108">Optional.</span></span> <span data-ttu-id="3dbb0-109">Blok příkazů, které se má provést, když je požadován zámek.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="3dbb0-110">Ukončí `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dbb0-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3dbb0-111">Remarks</span></span>  
 <span data-ttu-id="3dbb0-112">`SyncLock` Prohlášení zajišťuje, že více vláken neprovádět tohoto bloku příkazů ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="3dbb0-113">`SyncLock` každé vlákno zabrání v zadání bloku, dokud žádné vlákno provádí.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="3dbb0-114">Nejběžnější použití nástroje `SyncLock` je k ochraně dat aktualizovány podle více než jedno vlákno současně.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="3dbb0-115">Pokud příkazy, které pracuje s daty musí přejít do dokončení bez přerušení, vytvořte z nich uvnitř `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="3dbb0-116">Někdy se označuje jako blok příkazů, který je chráněn výhradní zámek *kritický oddíl*.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3dbb0-117">pravidla</span><span class="sxs-lookup"><span data-stu-id="3dbb0-117">Rules</span></span>  
  
- <span data-ttu-id="3dbb0-118">Větvení.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-118">Branching.</span></span> <span data-ttu-id="3dbb0-119">Nelze větvit do `SyncLock` znemožní mimo blok.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="3dbb0-120">Hodnota objektu zámku.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-120">Lock Object Value.</span></span> <span data-ttu-id="3dbb0-121">Hodnota `lockobject` nemůže být `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="3dbb0-122">Zamknout objekt musíte vytvořit předtím, než ho použijete `SyncLock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="3dbb0-123">Nelze změnit hodnotu `lockobject` při provádění `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="3dbb0-124">Mechanismus vyžaduje, že zámek objektu zůstanou beze změny.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="3dbb0-125">Nelze použít [Await](../../../visual-basic/language-reference/operators/await-operator.md) operátor `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="3dbb0-126">Chování</span><span class="sxs-lookup"><span data-stu-id="3dbb0-126">Behavior</span></span>  
  
- <span data-ttu-id="3dbb0-127">Mechanismus.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-127">Mechanism.</span></span> <span data-ttu-id="3dbb0-128">Když vlákno dosáhne `SyncLock` prohlášení, vyhodnotí `lockobject` výraz a pozastaví spuštění, dokud získá výhradní zámek na objekt vrácený výrazem.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="3dbb0-129">Když jiné vlákno dosáhne `SyncLock` příkazu, to není získat zámek až do první vlákno spustí `End SyncLock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="3dbb0-130">Chráněná Data.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-130">Protected Data.</span></span> <span data-ttu-id="3dbb0-131">Pokud `lockobject` je `Shared` proměnné, vlákno v jakékoli instance třídy výhradní zámek brání v provádění `SyncLock` zablokuje při provádění jakékoli jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="3dbb0-132">To chrání data, jež jsou sdílena mezi všemi instancemi.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="3dbb0-133">Pokud `lockobject` je proměnná instance (ne `Shared`), zámek je chrání vlákna běžícího v aktuální instanci spuštění `SyncLock` bloku ve stejnou dobu jako jiné vlákno ve stejné instanci.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="3dbb0-134">To chrání data udržovaná jednotlivých instancí.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-134">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="3dbb0-135">Získání a uvolnění.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-135">Acquisition and Release.</span></span> <span data-ttu-id="3dbb0-136">A `SyncLock` bloku se chová stejně jako `Try...Finally` konstrukce, ve kterém `Try` bloku získá výhradní zámek na `lockobject` a `Finally` ho uvolní blok.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="3dbb0-137">Z toho důvodu `SyncLock` bloku zaručuje uvolnění zámku, bez ohledu na to, jak ukončení bloku.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="3dbb0-138">To platí i v případě neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-138">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="3dbb0-139">Rámec volá.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-139">Framework Calls.</span></span> <span data-ttu-id="3dbb0-140">`SyncLock` Blokovat operace čtení a uvolní zámek voláním `Enter` a `Exit` metody `Monitor` třídy v <xref:System.Threading> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="3dbb0-141">Postupy pro programování</span><span class="sxs-lookup"><span data-stu-id="3dbb0-141">Programming Practices</span></span>  
 <span data-ttu-id="3dbb0-142">`lockobject` Objekt, který patří do vaší třídy výhradně vždy by se měl vyhodnotit výraz.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="3dbb0-143">By měla deklarovat `Private` proměnné objektu k ochraně dat, které patří k aktuální instanci nebo `Private Shared` proměnné objektu k ochraně dat, které jsou společné pro všechny instance.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="3dbb0-144">Neměli byste používat `Me` data pro instanci objektu – klíčové slovo kvůli zámku.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="3dbb0-145">Pokud má kód do vaší třídy externí odkaz na instanci třídy, pomocí tohoto odkazu jako objekt zámek pro `SyncLock` bloku zcela liší od patří vám, chrání různé datové.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="3dbb0-146">Tímto způsobem vaší třídy a jiná třída může blokovat mezi sebou z provádění jejich nesouvisejících `SyncLock` bloky.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="3dbb0-147">Podobně uzamčení na řetězec může být problematické, protože jakýkoli jiný kód v procesu pomocí stejný řetězec budou sdílet stejnou zámku.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="3dbb0-148">Také byste neměli používat `Me.GetType` metodu k dispozici zámek objektu, pro sdílená data.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="3dbb0-149">Důvodem je, že `GetType` vždy vrátí stejné `Type` objekt pro název dané třídy.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="3dbb0-150">Externí kód lze zavolat `GetType` na třídě a získat stejné zamknout objekt, který používáte.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="3dbb0-151">To způsobí dvě třídy blokování druhý z jejich `SyncLock` bloky.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3dbb0-152">Příklady</span><span class="sxs-lookup"><span data-stu-id="3dbb0-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="3dbb0-153">Popis</span><span class="sxs-lookup"><span data-stu-id="3dbb0-153">Description</span></span>  
 <span data-ttu-id="3dbb0-154">Následující příklad ukazuje třídu, která udržuje jednoduchý seznam zpráv.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="3dbb0-155">V poli obsahuje zprávy a poslední prvek pole použitá v proměnné.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="3dbb0-156">`addAnotherMessage` Postup zvýší poslední prvek a uloží novou zprávu.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="3dbb0-157">Tyto dvě operace jsou chráněny `SyncLock` a `End SyncLock` příkazy, protože po posledním prvku byl navýšen, nová zpráva musí být uložen před jakékoli vlákno může zvýšit poslední prvek znovu.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="3dbb0-158">Pokud `simpleMessageList` třídy sdílí jeden seznam zpráv mezi všechny její instance, proměnné `messagesList` a `messagesLast` by být deklarovaný jako `Shared`.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="3dbb0-159">V tomto případě, proměnná `messagesLock` by mělo být také `Shared`, takže by existovat jeden zámek objekt použitý objektem každou instanci.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3dbb0-160">Kód</span><span class="sxs-lookup"><span data-stu-id="3dbb0-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="3dbb0-161">Popis</span><span class="sxs-lookup"><span data-stu-id="3dbb0-161">Description</span></span>  
 <span data-ttu-id="3dbb0-162">Následující příklad používá vlákna a `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="3dbb0-163">Za předpokladu, `SyncLock` příkaz je k dispozici, je důležité části tohoto bloku příkazů a `balance` nikdy nebude záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="3dbb0-164">Můžete Zakomentovat `SyncLock` a `End SyncLock` příkazy a vidět její účinek ponechání navýšení kapacity `SyncLock` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="3dbb0-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3dbb0-165">Kód</span><span class="sxs-lookup"><span data-stu-id="3dbb0-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="3dbb0-166">Komentáře</span><span class="sxs-lookup"><span data-stu-id="3dbb0-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dbb0-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3dbb0-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="3dbb0-168">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="3dbb0-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
