---
title: Implementace asynchronního vzoru založeného na událostech
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
ms.openlocfilehash: 3cb38cd9d7b27ab28b602e4e4c813d58d904abd3
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584244"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="0bd04-102">Implementace asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="0bd04-102">Implementing the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="0bd04-103">Pokud píšete třída s atributem některé operace, které případně utrpíte významnému zpoždění, zvažte jeho asynchronní funkce implementací [založený na událostech přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0bd04-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="0bd04-104">Asynchronní vzor založený na událostech poskytuje standardizované způsob, jak zabalit třídu, která obsahuje asynchronní funkce.</span><span class="sxs-lookup"><span data-stu-id="0bd04-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="0bd04-105">Pokud se implementuje pomocí tříd pomocných rutin, jako jsou <xref:System.ComponentModel.AsyncOperationManager>, vaše třída bude správně fungovat v jakékoli aplikační model, včetně [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], konzolových aplikací a aplikací Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0bd04-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Console applications, and Windows Forms applications.</span></span>  
  
 <span data-ttu-id="0bd04-106">Příklad, který implementuje asynchronního vzoru založeného na událostech, naleznete v tématu [postupy: implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="0bd04-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="0bd04-107">Pro jednoduché asynchronní operace, můžete zjistit <xref:System.ComponentModel.BackgroundWorker> komponenty vhodná.</span><span class="sxs-lookup"><span data-stu-id="0bd04-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="0bd04-108">Další informace o <xref:System.ComponentModel.BackgroundWorker>, naleznete v tématu [postupy: spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="0bd04-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
 <span data-ttu-id="0bd04-109">Následující seznam popisuje funkce asynchronního vzoru založeného na událostech popsané v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="0bd04-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>  
  
-   <span data-ttu-id="0bd04-110">Příležitosti pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="0bd04-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
  
-   <span data-ttu-id="0bd04-111">Názvy asynchronních metod</span><span class="sxs-lookup"><span data-stu-id="0bd04-111">Naming Asynchronous Methods</span></span>  
  
-   <span data-ttu-id="0bd04-112">Volitelně podporují zrušení</span><span class="sxs-lookup"><span data-stu-id="0bd04-112">Optionally Support Cancellation</span></span>  
  
-   <span data-ttu-id="0bd04-113">Volitelně podporovat vlastnost IsBusy</span><span class="sxs-lookup"><span data-stu-id="0bd04-113">Optionally Support the IsBusy Property</span></span>  
  
-   <span data-ttu-id="0bd04-114">Volitelně můžete poskytovat podporu pro vykazování průběhu</span><span class="sxs-lookup"><span data-stu-id="0bd04-114">Optionally Provide Support for Progress Reporting</span></span>  
  
-   <span data-ttu-id="0bd04-115">Volitelně můžete poskytovat podporu pro vrácení přírůstkové výsledků</span><span class="sxs-lookup"><span data-stu-id="0bd04-115">Optionally Provide Support for Returning Incremental Results</span></span>  
  
-   <span data-ttu-id="0bd04-116">Zpracování Out a Ref parametrů metody</span><span class="sxs-lookup"><span data-stu-id="0bd04-116">Handling Out and Ref Parameters in Methods</span></span>  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="0bd04-117">Příležitosti pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="0bd04-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
 <span data-ttu-id="0bd04-118">Zvažte implementaci asynchronního vzoru založeného na událostech při:</span><span class="sxs-lookup"><span data-stu-id="0bd04-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>  
  
-   <span data-ttu-id="0bd04-119">Není nutné klientům vaší třídy <xref:System.Threading.WaitHandle> a <xref:System.IAsyncResult> objekty, které jsou k dispozici pro asynchronní operace, což znamená, že dotazování a <xref:System.Threading.WaitHandle.WaitAll%2A> nebo <xref:System.Threading.WaitHandle.WaitAny%2A> muset být vytvářeny klientem.</span><span class="sxs-lookup"><span data-stu-id="0bd04-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>  
  
-   <span data-ttu-id="0bd04-120">Chcete, aby asynchronní operace lze spravovat pomocí klienta s modelem známé události nebo delegáta.</span><span class="sxs-lookup"><span data-stu-id="0bd04-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>  
  
 <span data-ttu-id="0bd04-121">Všechny operace je kandidátem pro implementaci asynchronních, ale ty očekáváte, že budou účtovat dlouhé latenci by měl být.</span><span class="sxs-lookup"><span data-stu-id="0bd04-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="0bd04-122">Operace ve kterých klientech volání metody a upozorněni na dokončení bez dalšího zásahu vyžaduje jsou zvlášť vhodná.</span><span class="sxs-lookup"><span data-stu-id="0bd04-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="0bd04-123">Vhodné jsou také operace, které běží nepřetržitě, pravidelně upozornění klientů průběh, přírůstkové výsledky nebo změny stavu.</span><span class="sxs-lookup"><span data-stu-id="0bd04-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>  
  
 <span data-ttu-id="0bd04-124">Další informace o rozhodování, kdy podporují asynchronní vzor založený na událostech najdete v tématu [rozhodování o tom, když k implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="0bd04-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="naming-asynchronous-methods"></a><span data-ttu-id="0bd04-125">Názvy asynchronních metod</span><span class="sxs-lookup"><span data-stu-id="0bd04-125">Naming Asynchronous Methods</span></span>  
 <span data-ttu-id="0bd04-126">Pro každou metodu synchronní *MethodName* pro které chcete poskytnout asynchronní protějšek:</span><span class="sxs-lookup"><span data-stu-id="0bd04-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>  
  
 <span data-ttu-id="0bd04-127">Definování _MethodName_**asynchronní** metoda, která:</span><span class="sxs-lookup"><span data-stu-id="0bd04-127">Define a _MethodName_**Async** method that:</span></span>  
  
-   <span data-ttu-id="0bd04-128">Vrátí `void`.</span><span class="sxs-lookup"><span data-stu-id="0bd04-128">Returns `void`.</span></span>  
  
-   <span data-ttu-id="0bd04-129">Má stejné parametry jako *MethodName* metody.</span><span class="sxs-lookup"><span data-stu-id="0bd04-129">Takes the same parameters as the *MethodName* method.</span></span>  
  
-   <span data-ttu-id="0bd04-130">Přijímá více volání.</span><span class="sxs-lookup"><span data-stu-id="0bd04-130">Accepts multiple invocations.</span></span>  
  
 <span data-ttu-id="0bd04-131">Volitelně můžete definovat _MethodName_**asynchronní** přetížení, stejný jako _MethodName_**asynchronní**, ale ještě objekt s hodnotou Parametr s názvem `userState`.</span><span class="sxs-lookup"><span data-stu-id="0bd04-131">Optionally define a _MethodName_**Async** overload, identical to _MethodName_**Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="0bd04-132">To provést, pokud jste připraveni spravovat více souběžných volání metody, v takovém případě `userState` doručí hodnotu zpět na všechny obslužné rutiny události k rozlišení volání metody.</span><span class="sxs-lookup"><span data-stu-id="0bd04-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="0bd04-133">Můžete to udělat jednoduše jako místo k uložení stavu uživatele pro pozdější načtení.</span><span class="sxs-lookup"><span data-stu-id="0bd04-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>  
  
 <span data-ttu-id="0bd04-134">Pro každou zvláštní _MethodName_**asynchronní** podpis metody:</span><span class="sxs-lookup"><span data-stu-id="0bd04-134">For each separate _MethodName_**Async** method signature:</span></span>  
  
1.  <span data-ttu-id="0bd04-135">Definujte následující událost ve stejné třídě, jako metodu:</span><span class="sxs-lookup"><span data-stu-id="0bd04-135">Define the following event in the same class as the method:</span></span>  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  <span data-ttu-id="0bd04-136">Definovat následující delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="0bd04-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="0bd04-137">Tyto bude mít definici pravděpodobně mimo vlastní třídy, ale stejný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="0bd04-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>  
  
    ```vb  
    Public Delegate Sub MethodNameCompletedEventHandler( _  
        ByVal sender As Object, _  
        ByVal e As MethodNameCompletedEventArgs)  
  
    Public Class MethodNameCompletedEventArgs  
        Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As MyReturnType  
    End Property  
    ```  
  
    ```csharp  
    public delegate void MethodNameCompletedEventHandler(object sender,   
        MethodNameCompletedEventArgs e);  
  
    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
    {  
        public MyReturnType Result { get; }  
    }  
    ```  
  
    -   <span data-ttu-id="0bd04-138">Ujistěte se, _MethodName_**CompletedEventArgs** třída zveřejňuje její členy jako vlastnosti jen pro čtení a nikoli pole jako pole datové vazby.</span><span class="sxs-lookup"><span data-stu-id="0bd04-138">Ensure that the _MethodName_**CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>  
  
    -   <span data-ttu-id="0bd04-139">Není definován žádný <xref:System.ComponentModel.AsyncCompletedEventArgs>-odvozené třídy pro metody, které neposkytují výsledky.</span><span class="sxs-lookup"><span data-stu-id="0bd04-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="0bd04-140">Stačí použít instanci <xref:System.ComponentModel.AsyncCompletedEventArgs> samotný.</span><span class="sxs-lookup"><span data-stu-id="0bd04-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="0bd04-141">Je zcela přijatelné, když a proveditelné, opakovaně používat delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs> typy.</span><span class="sxs-lookup"><span data-stu-id="0bd04-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="0bd04-142">V tomto případě pojmenování nebude odpovídat jako název metody, od daného delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs> nesmí být vázán na jedinou metodu.</span><span class="sxs-lookup"><span data-stu-id="0bd04-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>  
  
## <a name="optionally-support-cancellation"></a><span data-ttu-id="0bd04-143">Volitelně podporují zrušení</span><span class="sxs-lookup"><span data-stu-id="0bd04-143">Optionally Support Cancellation</span></span>  
 <span data-ttu-id="0bd04-144">Pokud vaše třída bude podporovat zrušení asynchronní operace, by měly být vystaveny zrušení klientovi, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="0bd04-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="0bd04-145">Všimněte si, že existují dvě rozhodovací body, které je potřeba dosáhnout před definováním podpoře zrušení:</span><span class="sxs-lookup"><span data-stu-id="0bd04-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>  
  
-   <span data-ttu-id="0bd04-146">Má vaše třída, včetně budoucí očekávané dodatky, pouze jedna asynchronní operace, která podporuje zrušení?</span><span class="sxs-lookup"><span data-stu-id="0bd04-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>  
  
-   <span data-ttu-id="0bd04-147">Je asynchronní operace, které podporují více čekající operace podporu zrušení?</span><span class="sxs-lookup"><span data-stu-id="0bd04-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="0bd04-148">To znamená, nemá _MethodName_**asynchronní** take – metoda `userState` parametr, a to neumožňuje několika vyvoláními čeká na dokončení některého?</span><span class="sxs-lookup"><span data-stu-id="0bd04-148">That is, does the _MethodName_**Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>  
  
 <span data-ttu-id="0bd04-149">Chcete-li zjistit, co by měl být podpis pro metodu zrušení pomocí odpovědi na tyto dvě otázky v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="0bd04-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>  
  
### <a name="visual-basic"></a><span data-ttu-id="0bd04-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0bd04-150">Visual Basic</span></span>  
  
||<span data-ttu-id="0bd04-151">Nepodporuje více souběžných operací.</span><span class="sxs-lookup"><span data-stu-id="0bd04-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="0bd04-152">Pouze jedna operace v čase</span><span class="sxs-lookup"><span data-stu-id="0bd04-152">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="0bd04-153">Jedna asynchronní operace v celé třídy</span><span class="sxs-lookup"><span data-stu-id="0bd04-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|<span data-ttu-id="0bd04-154">Více asynchronních operací v třídě</span><span class="sxs-lookup"><span data-stu-id="0bd04-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a><span data-ttu-id="0bd04-155">C#</span><span class="sxs-lookup"><span data-stu-id="0bd04-155">C#</span></span>  
  
||<span data-ttu-id="0bd04-156">Nepodporuje více souběžných operací.</span><span class="sxs-lookup"><span data-stu-id="0bd04-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="0bd04-157">Pouze jedna operace v čase</span><span class="sxs-lookup"><span data-stu-id="0bd04-157">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="0bd04-158">Jedna asynchronní operace v celé třídy</span><span class="sxs-lookup"><span data-stu-id="0bd04-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|<span data-ttu-id="0bd04-159">Více asynchronních operací v třídě</span><span class="sxs-lookup"><span data-stu-id="0bd04-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 <span data-ttu-id="0bd04-160">Pokud definujete `CancelAsync(object userState)` metody, klienti musí být opatrní při volbě jejich stavu hodnoty tak, aby je schopna rozlišovat mezi všechny asynchronní metody vyvolané na objekt a ne jenom mezi všechny volání jedné asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="0bd04-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>  
  
 <span data-ttu-id="0bd04-161">Rozhodnutí o název verze jedním. asynchronní operace _MethodName_**AsyncCancel** vychází nebudou moct snadněji zjistit metodu v návrhovém prostředí, jako je IntelliSense ve Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0bd04-161">The decision to name the single-async-operation version _MethodName_**AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="0bd04-162">Tím se skupiny souvisejících členů a odlišuje od ostatních členů, které nesouvisí s asynchronní funkcí.</span><span class="sxs-lookup"><span data-stu-id="0bd04-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="0bd04-163">Pokud očekáváte, že můžou existovat další asynchronních operací přibylo v dalších verzích, je lepší definovat `CancelAsync`.</span><span class="sxs-lookup"><span data-stu-id="0bd04-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>  
  
 <span data-ttu-id="0bd04-164">Ve stejné třídě nedefinují více metod z výše uvedené tabulce.</span><span class="sxs-lookup"><span data-stu-id="0bd04-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="0bd04-165">Který nebude dávat smysl, nebo ji bude dál sbližuje tyto rozhraní třídy s růst počtu metody.</span><span class="sxs-lookup"><span data-stu-id="0bd04-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>  
  
 <span data-ttu-id="0bd04-166">Tyto metody obvykle vrátí okamžitě, a tato operace může nebo nemusí skutečně zrušit.</span><span class="sxs-lookup"><span data-stu-id="0bd04-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="0bd04-167">V obslužné rutině události pro _MethodName_**dokončeno** událostí, _MethodName_**CompletedEventArgs** objekt obsahuje `Cancelled` pole, které můžou klienti použít k určení, zda došlo k zrušení.</span><span class="sxs-lookup"><span data-stu-id="0bd04-167">In the event handler for the _MethodName_**Completed** event, the _MethodName_**CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>  
  
 <span data-ttu-id="0bd04-168">Dodržováním podle sémantiky zrušení [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="0bd04-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="0bd04-169">Volitelně podporovat vlastnost IsBusy</span><span class="sxs-lookup"><span data-stu-id="0bd04-169">Optionally Support the IsBusy Property</span></span>  
 <span data-ttu-id="0bd04-170">Pokud vaše třída nepodporuje více souběžných volání, vezměte v úvahu vystavení `IsBusy` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0bd04-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="0bd04-171">To umožňuje vývojářům určit, jestli _MethodName_**asynchronní** metodu je spuštěna bez zachycování výjimky z _MethodName_**asynchronní**  metody.</span><span class="sxs-lookup"><span data-stu-id="0bd04-171">This allows developers to determine whether a _MethodName_**Async** method is running without catching an exception from the _MethodName_**Async** method.</span></span>  
  
 <span data-ttu-id="0bd04-172">Dodržováním `IsBusy` podle sémantiky [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="0bd04-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="0bd04-173">Volitelně můžete poskytovat podporu pro vykazování průběhu</span><span class="sxs-lookup"><span data-stu-id="0bd04-173">Optionally Provide Support for Progress Reporting</span></span>  
 <span data-ttu-id="0bd04-174">Je často žádoucí, aby asynchronní operaci na informace o průběhu během jeho operace.</span><span class="sxs-lookup"><span data-stu-id="0bd04-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="0bd04-175">Asynchronní vzor založený na událostech poskytuje vodítko to udělat.</span><span class="sxs-lookup"><span data-stu-id="0bd04-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>  
  
-   <span data-ttu-id="0bd04-176">Volitelně definuje události vyvolané službou asynchronní operace a vyvolána na odpovídající vlákno.</span><span class="sxs-lookup"><span data-stu-id="0bd04-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="0bd04-177"><xref:System.ComponentModel.ProgressChangedEventArgs> Objekt představuje indikátor průběhu vracející celé číslo, který má být v rozmezí od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="0bd04-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>  
  
-   <span data-ttu-id="0bd04-178">Pojmenujte tuto událost následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0bd04-178">Name this event as follows:</span></span>  
  
    -   <span data-ttu-id="0bd04-179">`ProgressChanged` Pokud třída má více asynchronních operací (nebo se očekává růst zahrnout více asynchronních operací v budoucích verzích);</span><span class="sxs-lookup"><span data-stu-id="0bd04-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>  
  
    -   <span data-ttu-id="0bd04-180">_MethodName_**ProgressChanged** Pokud má třída jedné asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="0bd04-180">_MethodName_**ProgressChanged** if the class has a single asynchronous operation.</span></span>  
  
     <span data-ttu-id="0bd04-181">Tato volba názvů, který vytvořil pro metodu zrušení parallels, jak je popsáno v části volitelně podporu zrušení.</span><span class="sxs-lookup"><span data-stu-id="0bd04-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>  
  
 <span data-ttu-id="0bd04-182">Tato událost používejte <xref:System.ComponentModel.ProgressChangedEventHandler> delegáta a <xref:System.ComponentModel.ProgressChangedEventArgs> třídy.</span><span class="sxs-lookup"><span data-stu-id="0bd04-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="0bd04-183">Případně, pokud indikátor průběhu více specifického pro doménu může být poskytnuta (pro instanci, přečtených bajtů a celkový počet bajtů pro operace nástroje download), pak byste měli definovat odvozenou třídu <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="0bd04-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>  
  
 <span data-ttu-id="0bd04-184">Všimněte si, že existuje pouze jeden `ProgressChanged` nebo _MethodName_**ProgressChanged** události pro třídu, bez ohledu na počet asynchronních metod, které podporuje.</span><span class="sxs-lookup"><span data-stu-id="0bd04-184">Note that there is only one `ProgressChanged` or _MethodName_**ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="0bd04-185">Se očekává, že klienti používat `userState` objekt, který je předán _MethodName_**asynchronní** metody k rozlišení mezi průběh aktualizací na více souběžných operací.</span><span class="sxs-lookup"><span data-stu-id="0bd04-185">Clients are expected to use the `userState` object that is passed to the _MethodName_**Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>  
  
 <span data-ttu-id="0bd04-186">Může nastat situace, ve kterých více operací podporují průběh a každá vrátí jiný indikátor průběhu.</span><span class="sxs-lookup"><span data-stu-id="0bd04-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="0bd04-187">V tomto případě jediný `ProgressChanged` událostí není vhodná, a může být vhodné, podpora více `ProgressChanged` události.</span><span class="sxs-lookup"><span data-stu-id="0bd04-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="0bd04-188">V tomto případě použijte vzor pojmenování spočívající v _MethodName_**ProgressChanged** pro každou _MethodName_**asynchronní** metody.</span><span class="sxs-lookup"><span data-stu-id="0bd04-188">In this case use a naming pattern of _MethodName_**ProgressChanged** for each _MethodName_**Async** method.</span></span>  
  
 <span data-ttu-id="0bd04-189">Dodržováním vykazování průběhu sémantiku popsané [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="0bd04-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="0bd04-190">Volitelně můžete poskytovat podporu pro vrácení přírůstkové výsledků</span><span class="sxs-lookup"><span data-stu-id="0bd04-190">Optionally Provide Support for Returning Incremental Results</span></span>  
 <span data-ttu-id="0bd04-191">Asynchronní operace v některých případech může vrátit přírůstkové výsledky před dokončením.</span><span class="sxs-lookup"><span data-stu-id="0bd04-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="0bd04-192">Existuje mnoho možností, které lze použít pro podporu tohoto scénáře.</span><span class="sxs-lookup"><span data-stu-id="0bd04-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="0bd04-193">Některé příklady.</span><span class="sxs-lookup"><span data-stu-id="0bd04-193">Some examples follow.</span></span>  
  
### <a name="single-operation-class"></a><span data-ttu-id="0bd04-194">Jedním operation – třída</span><span class="sxs-lookup"><span data-stu-id="0bd04-194">Single-operation Class</span></span>  
 <span data-ttu-id="0bd04-195">Pokud vaše třída podporuje pouze jeden asynchronní operace a tato operace se bude moct vrátit přírůstkové výsledky, pak:</span><span class="sxs-lookup"><span data-stu-id="0bd04-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>  
  
-   <span data-ttu-id="0bd04-196">Rozšíření <xref:System.ComponentModel.ProgressChangedEventArgs> typu provádět přírůstkové Výsledná data a definujte _MethodName_**ProgressChanged** událostí s tímto Rozšířená data.</span><span class="sxs-lookup"><span data-stu-id="0bd04-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a _MethodName_**ProgressChanged** event with this extended data.</span></span>  
  
-   <span data-ttu-id="0bd04-197">Vyvolat to _MethodName_**ProgressChanged** událost v případě, že je výsledek přírůstkové do sestavy.</span><span class="sxs-lookup"><span data-stu-id="0bd04-197">Raise this _MethodName_**ProgressChanged** event when there is an incremental result to report.</span></span>  
  
 <span data-ttu-id="0bd04-198">Toto řešení platí konkrétně pro třídu jedním. asynchronní operace, protože neexistuje žádný problém s stejné události, ke kterým dochází pro vracení výsledků přírůstkové "všechny operace", jako _MethodName_**ProgressChanged**  nepodporuje události.</span><span class="sxs-lookup"><span data-stu-id="0bd04-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the _MethodName_**ProgressChanged** event does.</span></span>  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="0bd04-199">Třída více operace s homogenní přírůstkové výsledky</span><span class="sxs-lookup"><span data-stu-id="0bd04-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>  
 <span data-ttu-id="0bd04-200">V tomto případě vaše třída podporuje několik asynchronních metod každý může vracet přírůstkové výsledků, a tyto přírůstkové výsledky všechny mají stejný typ dat.</span><span class="sxs-lookup"><span data-stu-id="0bd04-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>  
  
 <span data-ttu-id="0bd04-201">Postupujte podle výše uvedeného třídy jedné operace, jako stejný model <xref:System.EventArgs> struktura bude fungovat pro všechny přírůstkové výsledky.</span><span class="sxs-lookup"><span data-stu-id="0bd04-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="0bd04-202">Definování `ProgressChanged` události místo _MethodName_**ProgressChanged** událost, protože se vztahuje na několik asynchronních metod.</span><span class="sxs-lookup"><span data-stu-id="0bd04-202">Define a `ProgressChanged` event instead of a _MethodName_**ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="0bd04-203">Třída více operace s heterogenní přírůstkové výsledky</span><span class="sxs-lookup"><span data-stu-id="0bd04-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>  
 <span data-ttu-id="0bd04-204">Pokud vaše třída podporuje několik asynchronních metod, každé vrácení jiný typ dat, měli byste:</span><span class="sxs-lookup"><span data-stu-id="0bd04-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>  
  
-   <span data-ttu-id="0bd04-205">Oddělení přírůstkových výsledků generování sestav z vykazování průběhu.</span><span class="sxs-lookup"><span data-stu-id="0bd04-205">Separate your incremental result reporting from your progress reporting.</span></span>  
  
-   <span data-ttu-id="0bd04-206">Definujte samostatný _MethodName_**ProgressChanged** událost s odpovídající <xref:System.EventArgs> pro každou asynchronní metodu ke zpracování dat přírůstkové výsledek této metody.</span><span class="sxs-lookup"><span data-stu-id="0bd04-206">Define a separate _MethodName_**ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>  
  
 <span data-ttu-id="0bd04-207">Vyvolání této obslužné rutiny události v příslušné vláknu, jak je popsáno v [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="0bd04-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="0bd04-208">Zpracování Out a Ref parametrů metody</span><span class="sxs-lookup"><span data-stu-id="0bd04-208">Handling Out and Ref Parameters in Methods</span></span>  
 <span data-ttu-id="0bd04-209">I když využívání `out` a `ref` se obecně nedoporučuje v rozhraní .NET Framework, jsou zde pravidla při jsou k dispozici:</span><span class="sxs-lookup"><span data-stu-id="0bd04-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>  
  
 <span data-ttu-id="0bd04-210">Zadaný synchronní metoda *MethodName*:</span><span class="sxs-lookup"><span data-stu-id="0bd04-210">Given a synchronous method *MethodName*:</span></span>  
  
-   <span data-ttu-id="0bd04-211">`out` Parametry se mají *MethodName* by neměly být součástí _MethodName_**asynchronní**.</span><span class="sxs-lookup"><span data-stu-id="0bd04-211">`out` parameters to *MethodName* should not be part of _MethodName_**Async**.</span></span> <span data-ttu-id="0bd04-212">Místo toho by měla být součástí _MethodName_**CompletedEventArgs** se stejným názvem jako svůj parametr ekvivalentní v *MethodName* (Pokud není vhodnější Název).</span><span class="sxs-lookup"><span data-stu-id="0bd04-212">Instead, they should be part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
-   <span data-ttu-id="0bd04-213">`ref` Parametry se mají *MethodName* by se měla zobrazit jako součást _MethodName_**asynchronní**a jako součást _MethodName_  **CompletedEventArgs** se stejným názvem jako svůj parametr ekvivalentní v *MethodName* (Pokud není vhodnější název).</span><span class="sxs-lookup"><span data-stu-id="0bd04-213">`ref` parameters to *MethodName* should appear as part of _MethodName_**Async**, and as part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
 <span data-ttu-id="0bd04-214">Mějme například:</span><span class="sxs-lookup"><span data-stu-id="0bd04-214">For example, given:</span></span>  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 <span data-ttu-id="0bd04-215">Asynchronní metody a jeho <xref:System.ComponentModel.AsyncCompletedEventArgs> třídy bude vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="0bd04-215">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>  
  
```vb  
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)  
  
Public Class MethodNameCompletedEventArgs  
    Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As Integer   
    End Property  
    Public ReadOnly Property Arg2() As String   
    End Property  
    Public ReadOnly Property Arg3() As String   
    End Property  
End Class  
```  
  
```csharp  
public void MethodNameAsync(string arg1, string arg2);  
  
public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
{  
    public int Result { get; };  
    public string Arg2 { get; };  
    public string Arg3 { get; };  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0bd04-216">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bd04-216">See also</span></span>

- <xref:System.ComponentModel.ProgressChangedEventArgs>  
- <xref:System.ComponentModel.AsyncCompletedEventArgs>  
- [<span data-ttu-id="0bd04-217">Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="0bd04-217">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
- [<span data-ttu-id="0bd04-218">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="0bd04-218">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
- [<span data-ttu-id="0bd04-219">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="0bd04-219">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
- [<span data-ttu-id="0bd04-220">Rozhodování, kdy implementovat asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="0bd04-220">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
- [<span data-ttu-id="0bd04-221">Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="0bd04-221">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
- [<span data-ttu-id="0bd04-222">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="0bd04-222">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
