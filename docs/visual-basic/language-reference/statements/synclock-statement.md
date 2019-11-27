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
ms.openlocfilehash: 0f430edce99513b0de9ef437d70648a128b336b8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352809"
---
# <a name="synclock-statement"></a><span data-ttu-id="31fbe-102">SyncLock – příkaz</span><span class="sxs-lookup"><span data-stu-id="31fbe-102">SyncLock Statement</span></span>
<span data-ttu-id="31fbe-103">Získá výhradní zámek pro blok příkazu před spuštěním bloku.</span><span class="sxs-lookup"><span data-stu-id="31fbe-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31fbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31fbe-104">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="31fbe-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="31fbe-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="31fbe-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="31fbe-106">Required.</span></span> <span data-ttu-id="31fbe-107">Výraz, který se vyhodnocuje jako odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="31fbe-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="31fbe-108">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="31fbe-108">Optional.</span></span> <span data-ttu-id="31fbe-109">Blok příkazů, které mají být provedeny při získání zámku.</span><span class="sxs-lookup"><span data-stu-id="31fbe-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="31fbe-110">Ukončí blok `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="31fbe-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31fbe-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31fbe-111">Remarks</span></span>  
 <span data-ttu-id="31fbe-112">Příkaz `SyncLock` zajišťuje, že více vláken nespustí blok příkazu současně.</span><span class="sxs-lookup"><span data-stu-id="31fbe-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="31fbe-113">`SyncLock` zabrání každému vláknu v vstupu do bloku, dokud žádné jiné vlákno neprovádí.</span><span class="sxs-lookup"><span data-stu-id="31fbe-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="31fbe-114">Nejběžnějším použitím `SyncLock` je chránit data před jejich aktualizací více než jedním vláknem současně.</span><span class="sxs-lookup"><span data-stu-id="31fbe-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="31fbe-115">Pokud příkazy, které pracují s daty, musí přejít k dokončení bez přerušení, umístit je do bloku `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="31fbe-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="31fbe-116">Blok příkazu chráněný výhradním zámkem se někdy nazývá *kritická sekce*.</span><span class="sxs-lookup"><span data-stu-id="31fbe-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="31fbe-117">Pravidla</span><span class="sxs-lookup"><span data-stu-id="31fbe-117">Rules</span></span>  
  
- <span data-ttu-id="31fbe-118">Větvení.</span><span class="sxs-lookup"><span data-stu-id="31fbe-118">Branching.</span></span> <span data-ttu-id="31fbe-119">Nemůžete vytvořit větev `SyncLock` bloku z vnějšího bloku.</span><span class="sxs-lookup"><span data-stu-id="31fbe-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="31fbe-120">Zamkne hodnotu objektu.</span><span class="sxs-lookup"><span data-stu-id="31fbe-120">Lock Object Value.</span></span> <span data-ttu-id="31fbe-121">Hodnotu `lockobject` nelze `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="31fbe-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="31fbe-122">Objekt zámku je nutné vytvořit před jeho použitím v příkazu `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="31fbe-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="31fbe-123">Při provádění bloku `SyncLock` nemůžete změnit hodnotu `lockobject`.</span><span class="sxs-lookup"><span data-stu-id="31fbe-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="31fbe-124">Mechanismus vyžaduje, aby objekt zámku zůstal beze změny.</span><span class="sxs-lookup"><span data-stu-id="31fbe-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="31fbe-125">V bloku `SyncLock` nemůžete použít operátor [await](../../../visual-basic/language-reference/operators/await-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="31fbe-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="31fbe-126">Chování</span><span class="sxs-lookup"><span data-stu-id="31fbe-126">Behavior</span></span>  
  
- <span data-ttu-id="31fbe-127">Mechanismy.</span><span class="sxs-lookup"><span data-stu-id="31fbe-127">Mechanism.</span></span> <span data-ttu-id="31fbe-128">Když vlákno dosáhne příkazu `SyncLock`, vyhodnotí výraz `lockobject` a pozastaví provádění, dokud nezíská výhradní zámek objektu vráceného výrazem.</span><span class="sxs-lookup"><span data-stu-id="31fbe-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="31fbe-129">Když další vlákno dosáhne příkazu `SyncLock`, nezíská zámek, dokud první vlákno nespustí příkaz `End SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="31fbe-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="31fbe-130">Chráněná data.</span><span class="sxs-lookup"><span data-stu-id="31fbe-130">Protected Data.</span></span> <span data-ttu-id="31fbe-131">Pokud je `lockobject` `Shared` proměnné, exkluzivní zámek zabraňuje vláknu v jakékoli instanci třídy ve spuštění bloku `SyncLock`, zatímco jakékoli jiné vlákno provádí jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="31fbe-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="31fbe-132">Tato ochrana chrání data, která jsou sdílena mezi všemi instancemi.</span><span class="sxs-lookup"><span data-stu-id="31fbe-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="31fbe-133">Pokud `lockobject` je proměnná instance (není `Shared`), zámek brání vláknu běžícímu v aktuální instanci ve stejném okamžiku, kdy je spuštěn blok `SyncLock` ve stejnou dobu jako jiné vlákno ve stejné instanci.</span><span class="sxs-lookup"><span data-stu-id="31fbe-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="31fbe-134">Tato ochrana chrání data udržovaná individuální instancí.</span><span class="sxs-lookup"><span data-stu-id="31fbe-134">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="31fbe-135">Získání a vydání.</span><span class="sxs-lookup"><span data-stu-id="31fbe-135">Acquisition and Release.</span></span> <span data-ttu-id="31fbe-136">`SyncLock` blok se chová jako `Try...Finally` konstrukce, ve které blok `Try` získá výhradní zámek na `lockobject` a `Finally` blok ho uvolní.</span><span class="sxs-lookup"><span data-stu-id="31fbe-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="31fbe-137">Z tohoto důvodu blok `SyncLock` garantuje vydání zámku bez ohledu na to, jak tento blok ukončujete.</span><span class="sxs-lookup"><span data-stu-id="31fbe-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="31fbe-138">To platí i v případě neošetřené výjimky.</span><span class="sxs-lookup"><span data-stu-id="31fbe-138">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="31fbe-139">Volání rozhraní.</span><span class="sxs-lookup"><span data-stu-id="31fbe-139">Framework Calls.</span></span> <span data-ttu-id="31fbe-140">Blok `SyncLock` získá a uvolní výhradní zámek voláním metod `Enter` a `Exit` třídy `Monitor` v oboru názvů <xref:System.Threading>.</span><span class="sxs-lookup"><span data-stu-id="31fbe-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="31fbe-141">Postupy programování</span><span class="sxs-lookup"><span data-stu-id="31fbe-141">Programming Practices</span></span>  
 <span data-ttu-id="31fbe-142">Výraz `lockobject` by měl vždy vyhodnocovat objekt, který patří výhradně do vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="31fbe-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="31fbe-143">Měli byste deklarovat `Private` proměnnou objektu, chcete-li chránit data, která patří do aktuální instance, nebo proměnnou objektu `Private Shared` a chránit tak data společná pro všechny instance.</span><span class="sxs-lookup"><span data-stu-id="31fbe-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="31fbe-144">Klíčové slovo `Me` byste neměli používat k poskytnutí objektu zámku pro data instance.</span><span class="sxs-lookup"><span data-stu-id="31fbe-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="31fbe-145">Pokud má externí kód pro vaši třídu odkaz na instanci vaší třídy, může použít tento odkaz jako objekt zámku pro `SyncLock` blok, který zcela odlišná od vaší ze svých vlastních dat.</span><span class="sxs-lookup"><span data-stu-id="31fbe-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="31fbe-146">Tímto způsobem může vaše třída a druhá třída vzájemně blokovat provádění jejich nesouvisejících `SyncLock`ch bloků.</span><span class="sxs-lookup"><span data-stu-id="31fbe-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="31fbe-147">Podobně zamykání na řetězci může být problematické, protože jakýkoliv jiný kód v procesu používající stejný řetězec bude sdílet stejný zámek.</span><span class="sxs-lookup"><span data-stu-id="31fbe-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="31fbe-148">Kromě toho byste neměli používat metodu `Me.GetType` k poskytnutí objektu zámku pro sdílená data.</span><span class="sxs-lookup"><span data-stu-id="31fbe-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="31fbe-149">Důvodem je, že `GetType` vždy vrací stejný objekt `Type` pro daný název třídy.</span><span class="sxs-lookup"><span data-stu-id="31fbe-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="31fbe-150">Externí kód může volat `GetType` ve vaší třídě a získat stejný objekt zámku, který používáte.</span><span class="sxs-lookup"><span data-stu-id="31fbe-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="31fbe-151">To by vedlo k tomu, že obě třídy jsou vzájemně blokující od jejich `SyncLock`ch bloků.</span><span class="sxs-lookup"><span data-stu-id="31fbe-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="31fbe-152">Příklady</span><span class="sxs-lookup"><span data-stu-id="31fbe-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="31fbe-153">Popis</span><span class="sxs-lookup"><span data-stu-id="31fbe-153">Description</span></span>  
 <span data-ttu-id="31fbe-154">Následující příklad ukazuje třídu, která udržuje jednoduchý seznam zpráv.</span><span class="sxs-lookup"><span data-stu-id="31fbe-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="31fbe-155">Obsahuje zprávy v poli a posledním použitém elementu tohoto pole v proměnné.</span><span class="sxs-lookup"><span data-stu-id="31fbe-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="31fbe-156">`addAnotherMessage` procedura zvýší poslední prvek a uloží novou zprávu.</span><span class="sxs-lookup"><span data-stu-id="31fbe-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="31fbe-157">Tyto dvě operace jsou chráněny pomocí příkazů `SyncLock` a `End SyncLock`, protože po zvýšení posledního prvku musí být nová zpráva uložena předtím, než jakékoli jiné vlákno bude moci znovu zvýšit poslední prvek.</span><span class="sxs-lookup"><span data-stu-id="31fbe-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="31fbe-158">Pokud `simpleMessageList` třída sdílela jeden seznam zpráv mezi všemi jeho instancemi, proměnné `messagesList` a `messagesLast` budou deklarovány jako `Shared`.</span><span class="sxs-lookup"><span data-stu-id="31fbe-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="31fbe-159">V takovém případě by měla být proměnná `messagesLock` také `Shared`, takže by existoval jeden objekt zámku používaný každou instancí.</span><span class="sxs-lookup"><span data-stu-id="31fbe-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="31fbe-160">Kód</span><span class="sxs-lookup"><span data-stu-id="31fbe-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="31fbe-161">Popis</span><span class="sxs-lookup"><span data-stu-id="31fbe-161">Description</span></span>  
 <span data-ttu-id="31fbe-162">Následující příklad používá vlákna a `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="31fbe-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="31fbe-163">Pokud je přítomen příkaz `SyncLock`, je blok příkazu kritickým oddílem a `balance` nikdy se nestane záporným číslem.</span><span class="sxs-lookup"><span data-stu-id="31fbe-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="31fbe-164">Můžete přidat komentář k příkazům `SyncLock` a `End SyncLock` a zobrazit efekt vynechání klíčového slova `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="31fbe-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="31fbe-165">Kód</span><span class="sxs-lookup"><span data-stu-id="31fbe-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="31fbe-166">Komentáře</span><span class="sxs-lookup"><span data-stu-id="31fbe-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31fbe-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31fbe-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="31fbe-168">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="31fbe-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
