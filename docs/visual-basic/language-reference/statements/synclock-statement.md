---
title: SyncLock – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: fd932a20af274faf2b56136a94675b28399989b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404158"
---
# <a name="synclock-statement"></a><span data-ttu-id="5ae75-102">SyncLock – příkaz</span><span class="sxs-lookup"><span data-stu-id="5ae75-102">SyncLock Statement</span></span>
<span data-ttu-id="5ae75-103">Získá výhradní zámek pro blok příkazu před spuštěním bloku.</span><span class="sxs-lookup"><span data-stu-id="5ae75-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ae75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ae75-104">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="5ae75-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="5ae75-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="5ae75-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="5ae75-106">Required.</span></span> <span data-ttu-id="5ae75-107">Výraz, který se vyhodnocuje jako odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="5ae75-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="5ae75-108">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5ae75-108">Optional.</span></span> <span data-ttu-id="5ae75-109">Blok příkazů, které mají být provedeny při získání zámku.</span><span class="sxs-lookup"><span data-stu-id="5ae75-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="5ae75-110">Ukončí `SyncLock` blok.</span><span class="sxs-lookup"><span data-stu-id="5ae75-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ae75-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ae75-111">Remarks</span></span>  
 <span data-ttu-id="5ae75-112">`SyncLock`Příkaz zajistí, že více vláken nespustí blok příkazu současně.</span><span class="sxs-lookup"><span data-stu-id="5ae75-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="5ae75-113">`SyncLock`zabrání každému vláknu v vstupu do bloku, dokud žádné jiné vlákno neprovádí.</span><span class="sxs-lookup"><span data-stu-id="5ae75-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="5ae75-114">Nejběžnějším použitím nástroje `SyncLock` je chránit data před aktualizací více než jedním vláknem současně.</span><span class="sxs-lookup"><span data-stu-id="5ae75-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="5ae75-115">Pokud příkazy, které pracují s daty, musí přejít k dokončení bez přerušení, umístit je dovnitř `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="5ae75-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="5ae75-116">Blok příkazu chráněný výhradním zámkem se někdy nazývá *kritická sekce*.</span><span class="sxs-lookup"><span data-stu-id="5ae75-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5ae75-117">Pravidla</span><span class="sxs-lookup"><span data-stu-id="5ae75-117">Rules</span></span>  
  
- <span data-ttu-id="5ae75-118">Větvení.</span><span class="sxs-lookup"><span data-stu-id="5ae75-118">Branching.</span></span> <span data-ttu-id="5ae75-119">Nemůžete vytvořit větev do `SyncLock` bloku z vnějšího bloku.</span><span class="sxs-lookup"><span data-stu-id="5ae75-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="5ae75-120">Zamkne hodnotu objektu.</span><span class="sxs-lookup"><span data-stu-id="5ae75-120">Lock Object Value.</span></span> <span data-ttu-id="5ae75-121">Hodnota `lockobject` nemůže být `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="5ae75-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="5ae75-122">Objekt zámku je nutné vytvořit před jeho použitím v `SyncLock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="5ae75-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="5ae75-123">Při provádění bloku nelze změnit hodnotu `lockobject` `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="5ae75-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="5ae75-124">Mechanismus vyžaduje, aby objekt zámku zůstal beze změny.</span><span class="sxs-lookup"><span data-stu-id="5ae75-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="5ae75-125">V bloku nelze použít operátor [await](../operators/await-operator.md) `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="5ae75-125">You can't use the [Await](../operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="5ae75-126">Chování</span><span class="sxs-lookup"><span data-stu-id="5ae75-126">Behavior</span></span>  
  
- <span data-ttu-id="5ae75-127">Mechanismy.</span><span class="sxs-lookup"><span data-stu-id="5ae75-127">Mechanism.</span></span> <span data-ttu-id="5ae75-128">Když vlákno dosáhne `SyncLock` příkazu, vyhodnotí `lockobject` výraz a pozastaví provádění, dokud nezíská výhradní zámek objektu vráceného výrazem.</span><span class="sxs-lookup"><span data-stu-id="5ae75-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="5ae75-129">Když jiný podproces dosáhne `SyncLock` příkazu, nezíská zámek, dokud první vlákno neprovede `End SyncLock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="5ae75-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="5ae75-130">Chráněná data.</span><span class="sxs-lookup"><span data-stu-id="5ae75-130">Protected Data.</span></span> <span data-ttu-id="5ae75-131">Pokud `lockobject` je `Shared` Proměnná, exkluzivní zámek zabraňuje vláknu v jakékoli instanci třídy, aby vyspustila blok, `SyncLock` zatímco jakékoli jiné vlákno ji provádí.</span><span class="sxs-lookup"><span data-stu-id="5ae75-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="5ae75-132">Tato ochrana chrání data, která jsou sdílena mezi všemi instancemi.</span><span class="sxs-lookup"><span data-stu-id="5ae75-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="5ae75-133">Pokud `lockobject` je proměnná instance (ne `Shared` ), zámek zabraňuje vláknu běžícímu v aktuální instanci spouštět `SyncLock` blok ve stejnou dobu jako jiné vlákno ve stejné instanci.</span><span class="sxs-lookup"><span data-stu-id="5ae75-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="5ae75-134">Tato ochrana chrání data udržovaná individuální instancí.</span><span class="sxs-lookup"><span data-stu-id="5ae75-134">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="5ae75-135">Získání a vydání.</span><span class="sxs-lookup"><span data-stu-id="5ae75-135">Acquisition and Release.</span></span> <span data-ttu-id="5ae75-136">`SyncLock`Blok se chová jako `Try...Finally` konstrukce, ve které `Try` blok získá výhradní zámek `lockobject` , a `Finally` blok ho uvolní.</span><span class="sxs-lookup"><span data-stu-id="5ae75-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="5ae75-137">Z tohoto důvodu `SyncLock` blok garantuje vydání zámku bez ohledu na to, jak tento blok ukončujete.</span><span class="sxs-lookup"><span data-stu-id="5ae75-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="5ae75-138">To platí i v případě neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="5ae75-138">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="5ae75-139">Volání rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5ae75-139">Framework Calls.</span></span> <span data-ttu-id="5ae75-140">`SyncLock`Blok získá a uvolní výhradní zámek voláním `Enter` `Exit` metod a `Monitor` třídy v <xref:System.Threading> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5ae75-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="5ae75-141">Postupy programování</span><span class="sxs-lookup"><span data-stu-id="5ae75-141">Programming Practices</span></span>  
 <span data-ttu-id="5ae75-142">`lockobject`Výraz by měl vždy vyhodnocovat objekt, který patří exkluzivně do vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="5ae75-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="5ae75-143">Měli byste deklarovat `Private` objektovou proměnnou pro ochranu dat patřících k aktuální instanci nebo `Private Shared` proměnné objektu pro ochranu dat společných pro všechny instance.</span><span class="sxs-lookup"><span data-stu-id="5ae75-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="5ae75-144">Klíčové slovo byste neměli používat `Me` k poskytnutí objektu zámku pro data instance.</span><span class="sxs-lookup"><span data-stu-id="5ae75-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="5ae75-145">Pokud má externí kód pro vaši třídu odkaz na instanci vaší třídy, může použít tento odkaz jako objekt zámku pro `SyncLock` blok zcela odlišný od vašeho ze své ochrany a chránit tak jiná data.</span><span class="sxs-lookup"><span data-stu-id="5ae75-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="5ae75-146">Tímto způsobem může vaše třída a druhá třída vzájemně blokovat spouštění jejich nesouvisejících `SyncLock` bloků.</span><span class="sxs-lookup"><span data-stu-id="5ae75-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="5ae75-147">Podobně zamykání na řetězci může být problematické, protože jakýkoliv jiný kód v procesu používající stejný řetězec bude sdílet stejný zámek.</span><span class="sxs-lookup"><span data-stu-id="5ae75-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="5ae75-148">Tuto metodu byste neměli používat ani `Me.GetType` k poskytnutí objektu zámku pro sdílená data.</span><span class="sxs-lookup"><span data-stu-id="5ae75-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="5ae75-149">Je to proto `GetType` , že vždy vrátí stejný `Type` objekt pro daný název třídy.</span><span class="sxs-lookup"><span data-stu-id="5ae75-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="5ae75-150">Externí kód by mohl zavolat `GetType` na vaši třídu a získat stejný objekt zámku, který používáte.</span><span class="sxs-lookup"><span data-stu-id="5ae75-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="5ae75-151">To by vedlo ke vzájemnému blokování obou tříd z jejich `SyncLock` bloků.</span><span class="sxs-lookup"><span data-stu-id="5ae75-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5ae75-152">Příklady</span><span class="sxs-lookup"><span data-stu-id="5ae75-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="5ae75-153">Popis</span><span class="sxs-lookup"><span data-stu-id="5ae75-153">Description</span></span>  
 <span data-ttu-id="5ae75-154">Následující příklad ukazuje třídu, která udržuje jednoduchý seznam zpráv.</span><span class="sxs-lookup"><span data-stu-id="5ae75-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="5ae75-155">Obsahuje zprávy v poli a posledním použitém elementu tohoto pole v proměnné.</span><span class="sxs-lookup"><span data-stu-id="5ae75-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="5ae75-156">`addAnotherMessage`Procedura zvýší poslední prvek a uloží novou zprávu.</span><span class="sxs-lookup"><span data-stu-id="5ae75-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="5ae75-157">Tyto dvě operace jsou chráněny pomocí `SyncLock` `End SyncLock` příkazů a, protože po zvýšení posledního prvku se musí nová zpráva uložit předtím, než jakékoli jiné vlákno bude moci znovu zvýšit poslední prvek.</span><span class="sxs-lookup"><span data-stu-id="5ae75-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="5ae75-158">Pokud `simpleMessageList` Třída sdílela jeden seznam zpráv mezi všemi jeho instancemi, proměnné `messagesList` a by měly `messagesLast` být deklarovány jako `Shared` .</span><span class="sxs-lookup"><span data-stu-id="5ae75-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="5ae75-159">V takovém případě `messagesLock` by měla být proměnná také `Shared` , takže by existoval jediný objekt zámku, který používá každá instance.</span><span class="sxs-lookup"><span data-stu-id="5ae75-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5ae75-160">Kód</span><span class="sxs-lookup"><span data-stu-id="5ae75-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="5ae75-161">Description</span><span class="sxs-lookup"><span data-stu-id="5ae75-161">Description</span></span>  
 <span data-ttu-id="5ae75-162">Následující příklad používá vlákna a `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="5ae75-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="5ae75-163">Pokud `SyncLock` je k dispozici příkaz, blok příkazu je nepostradatelným oddílem a `balance` nikdy se nestane záporným číslem.</span><span class="sxs-lookup"><span data-stu-id="5ae75-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="5ae75-164">Můžete komentovat `SyncLock` příkazy a a podívat se, `End SyncLock` Jak `SyncLock` klíčové slovo opustí.</span><span class="sxs-lookup"><span data-stu-id="5ae75-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5ae75-165">Kód</span><span class="sxs-lookup"><span data-stu-id="5ae75-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="5ae75-166">Komentáře</span><span class="sxs-lookup"><span data-stu-id="5ae75-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ae75-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ae75-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="5ae75-168">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="5ae75-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
