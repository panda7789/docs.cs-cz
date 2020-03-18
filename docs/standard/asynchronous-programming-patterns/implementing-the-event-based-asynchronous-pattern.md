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
ms.openlocfilehash: 9865fa169e0776765f9a97ec0a7b4555bf253886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67663705"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="ad7c7-102">Implementace asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="ad7c7-102">Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="ad7c7-103">Pokud píšete třídu s některými operacemi, které mohou způsobit znatelné zpoždění, zvažte poskytnutí asynchronní funkce implementací [přehledu asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ad7c7-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>

<span data-ttu-id="ad7c7-104">Asynchronní vzor založený na událostech poskytuje standardizovaný způsob, jak zabalit třídu, která má asynchronní funkce.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="ad7c7-105">Pokud je implementována <xref:System.ComponentModel.AsyncOperationManager>s pomocné třídy, jako je , bude vaše třída pracovat správně v rámci libovolného modelu aplikace, včetně ASP.NET, konzolové aplikace a windows forms aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including ASP.NET, Console applications, and Windows Forms applications.</span></span>

<span data-ttu-id="ad7c7-106">Příklad, který implementuje asynchronní vzor založený na událostech, naleznete v tématu [How to: Implement a Component that Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="ad7c7-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="ad7c7-107">Pro jednoduché asynchronní operace můžete <xref:System.ComponentModel.BackgroundWorker> najít součást vhodné.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="ad7c7-108">Další informace <xref:System.ComponentModel.BackgroundWorker>o [aplikaci naleznete v tématu Postup: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="ad7c7-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>

<span data-ttu-id="ad7c7-109">Následující seznam popisuje funkce asynchronního vzoru založeného na událostech popsané v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>

- <span data-ttu-id="ad7c7-110">Příležitosti pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="ad7c7-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

- <span data-ttu-id="ad7c7-111">Pojmenování asynchronních metod</span><span class="sxs-lookup"><span data-stu-id="ad7c7-111">Naming Asynchronous Methods</span></span>

- <span data-ttu-id="ad7c7-112">Volitelně podpora zrušení</span><span class="sxs-lookup"><span data-stu-id="ad7c7-112">Optionally Support Cancellation</span></span>

- <span data-ttu-id="ad7c7-113">Volitelně podporovat vlastnost IsBusy</span><span class="sxs-lookup"><span data-stu-id="ad7c7-113">Optionally Support the IsBusy Property</span></span>

- <span data-ttu-id="ad7c7-114">Volitelně poskytovat podporu pro vykazování průběhu</span><span class="sxs-lookup"><span data-stu-id="ad7c7-114">Optionally Provide Support for Progress Reporting</span></span>

- <span data-ttu-id="ad7c7-115">Volitelně poskytují podporu pro vrácení přírůstkových výsledků</span><span class="sxs-lookup"><span data-stu-id="ad7c7-115">Optionally Provide Support for Returning Incremental Results</span></span>

- <span data-ttu-id="ad7c7-116">Zpracování a ref parametry v metodách</span><span class="sxs-lookup"><span data-stu-id="ad7c7-116">Handling Out and Ref Parameters in Methods</span></span>

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="ad7c7-117">Příležitosti pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="ad7c7-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="ad7c7-118">Zvažte implementaci asynchronního vzoru založeného na událostech, pokud:</span><span class="sxs-lookup"><span data-stu-id="ad7c7-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>

- <span data-ttu-id="ad7c7-119">Klienti vaší třídy <xref:System.Threading.WaitHandle> nepotřebují a <xref:System.IAsyncResult> objekty, které jsou k <xref:System.Threading.WaitHandle.WaitAll%2A> <xref:System.Threading.WaitHandle.WaitAny%2A> dispozici pro asynchronní operace, což znamená, že dotazování a nebo bude muset být vytvořen klientem.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>

- <span data-ttu-id="ad7c7-120">Chcete, aby asynchronní operace byly spravovány klientem se známým modelem události/delegáta.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>

<span data-ttu-id="ad7c7-121">Každá operace je kandidátem pro asynchronní implementaci, ale ty, které očekáváte, že vynaloží dlouhé latence by měly být považovány za.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="ad7c7-122">Zvláště vhodné jsou operace, při kterých klienti volají metodu a jsou upozorněni na dokončení, bez nutnosti dalšího zásahu.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="ad7c7-123">Vhodné jsou také operace, které běží nepřetržitě a pravidelně upozorňují klienty na průběh, přírůstkové výsledky nebo změny stavu.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>

<span data-ttu-id="ad7c7-124">Další informace o rozhodování o tom, kdy podporovat asynchronní vzor založený na událostech, naleznete [v tématu Rozhodování o tom, kdy implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="ad7c7-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="naming-asynchronous-methods"></a><span data-ttu-id="ad7c7-125">Pojmenování asynchronních metod</span><span class="sxs-lookup"><span data-stu-id="ad7c7-125">Naming Asynchronous Methods</span></span>

<span data-ttu-id="ad7c7-126">Pro každou synchronní metodu *MethodName,* pro kterou chcete poskytnout asynchronní protějšek:</span><span class="sxs-lookup"><span data-stu-id="ad7c7-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>

<span data-ttu-id="ad7c7-127">Definujte metodu _MethodName_**Async,** která:</span><span class="sxs-lookup"><span data-stu-id="ad7c7-127">Define a _MethodName_**Async** method that:</span></span>

- <span data-ttu-id="ad7c7-128">Vrací objekt `void`.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-128">Returns `void`.</span></span>

- <span data-ttu-id="ad7c7-129">Přebírá stejné parametry jako *MethodName Method.*</span><span class="sxs-lookup"><span data-stu-id="ad7c7-129">Takes the same parameters as the *MethodName* method.</span></span>

- <span data-ttu-id="ad7c7-130">Přijímá více vyvolání.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-130">Accepts multiple invocations.</span></span>

<span data-ttu-id="ad7c7-131">Volitelně definujte přetížení _MethodName_**Async,** identické s _MethodName_**Async**, `userState`ale s dalším nazývaným parametrem s hodnotou objektu .</span><span class="sxs-lookup"><span data-stu-id="ad7c7-131">Optionally define a _MethodName_**Async** overload, identical to _MethodName_**Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="ad7c7-132">Toto akci proveďte, pokud jste připraveni spravovat více souběžných `userState` vyvolání metody, v takovém případě bude hodnota doručena zpět všem obslužným rutinám událostí k rozlišení vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="ad7c7-133">Můžete také provést jednoduše jako místo pro uložení stavu uživatele pro pozdější načtení.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>

<span data-ttu-id="ad7c7-134">Pro každý samostatný podpis metody _MethodName_**Async:**</span><span class="sxs-lookup"><span data-stu-id="ad7c7-134">For each separate _MethodName_**Async** method signature:</span></span>

1. <span data-ttu-id="ad7c7-135">Definujte následující událost ve stejné třídě jako metoda:</span><span class="sxs-lookup"><span data-stu-id="ad7c7-135">Define the following event in the same class as the method:</span></span>

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. <span data-ttu-id="ad7c7-136">Definujte následující <xref:System.ComponentModel.AsyncCompletedEventArgs>hodelegáta a .</span><span class="sxs-lookup"><span data-stu-id="ad7c7-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="ad7c7-137">Ty budou pravděpodobně definovány mimo samotnou třídu, ale ve stejném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>

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

    - <span data-ttu-id="ad7c7-138">Ujistěte se, že třída _MethodName_**CompletedEventArgs** zveřejňuje své členy jako vlastnosti jen pro čtení a nikoli pole, protože pole zabraňují datové vazbě.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-138">Ensure that the _MethodName_**CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>

    - <span data-ttu-id="ad7c7-139">Nedefinujte <xref:System.ComponentModel.AsyncCompletedEventArgs>žádné odvozené třídy pro metody, které nevytvářejí výsledky.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="ad7c7-140">Jednoduše použijte instanci <xref:System.ComponentModel.AsyncCompletedEventArgs> sám o sobě.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>

      > [!NOTE]
      > <span data-ttu-id="ad7c7-141">Je naprosto přijatelné, pokud je to proveditelné a <xref:System.ComponentModel.AsyncCompletedEventArgs> vhodné, znovu použít delegáta a typy.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="ad7c7-142">V tomto případě nebude pojmenování tak konzistentní s názvem metody, <xref:System.ComponentModel.AsyncCompletedEventArgs> protože daný delegát a nebude vázán a jedinou metodou.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>

## <a name="optionally-support-cancellation"></a><span data-ttu-id="ad7c7-143">Volitelně podpora zrušení</span><span class="sxs-lookup"><span data-stu-id="ad7c7-143">Optionally Support Cancellation</span></span>

<span data-ttu-id="ad7c7-144">Pokud vaše třída bude podporovat zrušení asynchronní operace, zrušení by měla být vystavena klientovi, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="ad7c7-145">Všimněte si, že existují dva body rozhodnutí, které je třeba dosáhnout před definováním podpory zrušení:</span><span class="sxs-lookup"><span data-stu-id="ad7c7-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>

- <span data-ttu-id="ad7c7-146">Má vaše třída, včetně budoucích očekávaných dodatků k ní, pouze jednu asynchronní operaci, která podporuje zrušení?</span><span class="sxs-lookup"><span data-stu-id="ad7c7-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>

- <span data-ttu-id="ad7c7-147">Mohou asynchronní operace, které podporují zrušení, podporovat více čekajících operací?</span><span class="sxs-lookup"><span data-stu-id="ad7c7-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="ad7c7-148">To znamená, že metoda _MethodName_ `userState` **Async** trvá parametr a umožňuje více vyvolání před čekáním na dokončení jakékoli?</span><span class="sxs-lookup"><span data-stu-id="ad7c7-148">That is, does the _MethodName_**Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>

<span data-ttu-id="ad7c7-149">Pomocí odpovědí na tyto dvě otázky v následující tabulce určete, jaký by měl být podpis pro metodu zrušení.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="ad7c7-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad7c7-150">Visual Basic</span></span>

||<span data-ttu-id="ad7c7-151">Podporováno více souběžných operací</span><span class="sxs-lookup"><span data-stu-id="ad7c7-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="ad7c7-152">Pouze jedna operace najednou</span><span class="sxs-lookup"><span data-stu-id="ad7c7-152">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="ad7c7-153">Jedna asynchronní operace v celé třídě</span><span class="sxs-lookup"><span data-stu-id="ad7c7-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|<span data-ttu-id="ad7c7-154">Více asynchronních operací ve třídě</span><span class="sxs-lookup"><span data-stu-id="ad7c7-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a><span data-ttu-id="ad7c7-155">C\#</span><span class="sxs-lookup"><span data-stu-id="ad7c7-155">C\#</span></span>

||<span data-ttu-id="ad7c7-156">Podporováno více souběžných operací</span><span class="sxs-lookup"><span data-stu-id="ad7c7-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="ad7c7-157">Pouze jedna operace najednou</span><span class="sxs-lookup"><span data-stu-id="ad7c7-157">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="ad7c7-158">Jedna asynchronní operace v celé třídě</span><span class="sxs-lookup"><span data-stu-id="ad7c7-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|<span data-ttu-id="ad7c7-159">Více asynchronních operací ve třídě</span><span class="sxs-lookup"><span data-stu-id="ad7c7-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|

<span data-ttu-id="ad7c7-160">Pokud definujete `CancelAsync(object userState)` metodu, klienti musí být opatrní při výběru jejich hodnoty stavu, aby byly schopny rozlišit mezi všechny asynchronní metody vyvolané na objektu a nikoli pouze mezi všechny vyvolání jedné asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>

<span data-ttu-id="ad7c7-161">Rozhodnutí pojmenovat verzi methodname _MethodName_**AsyncCancel** s jednou asynchronní operací je založeno na možnosti snadněji zjistit metodu v návrhovém prostředí, jako je technologie IntelliSense sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-161">The decision to name the single-async-operation version _MethodName_**AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="ad7c7-162">To seskupuje související členy a odlišuje je od ostatních členů, kteří nemají nic společného s asynchronní funkce.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="ad7c7-163">Pokud očekáváte, že mohou být přidány další asynchronní operace v `CancelAsync`následujících verzích, je lepší definovat .</span><span class="sxs-lookup"><span data-stu-id="ad7c7-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>

<span data-ttu-id="ad7c7-164">Nedefinujte více metod z výše uvedené tabulky ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="ad7c7-165">To nebude dávat smysl, nebo to bude nepořádek třídy rozhraní s šíření metod.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>

<span data-ttu-id="ad7c7-166">Tyto metody se obvykle vrátí okamžitě a operace může nebo nemusí ve skutečnosti zrušit.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="ad7c7-167">V obslužné rutině události _MethodName_**Completed** objekt _MethodName_**Completed Obsahuje** `Cancelled` pole, které mohou klienti použít k určení, zda došlo ke zrušení.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-167">In the event handler for the _MethodName_**Completed** event, the _MethodName_**CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>

<span data-ttu-id="ad7c7-168">Řiďte se sémantikou zrušení popsanou v [doporučených postupech pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="ad7c7-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="ad7c7-169">Volitelně podporovat vlastnost IsBusy</span><span class="sxs-lookup"><span data-stu-id="ad7c7-169">Optionally Support the IsBusy Property</span></span>

<span data-ttu-id="ad7c7-170">Pokud vaše třída nepodporuje více souběžných vyvolání, `IsBusy` zvažte vystavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="ad7c7-171">To umožňuje vývojářům určit, zda method _MethodName_**Async** je spuštěna bez zachycení výjimky z _MethodName_**Async** metody.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-171">This allows developers to determine whether a _MethodName_**Async** method is running without catching an exception from the _MethodName_**Async** method.</span></span>

<span data-ttu-id="ad7c7-172">Řiďte `IsBusy` se sémantikou popsanou v [doporučených postupech pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="ad7c7-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="ad7c7-173">Volitelně poskytovat podporu pro vykazování průběhu</span><span class="sxs-lookup"><span data-stu-id="ad7c7-173">Optionally Provide Support for Progress Reporting</span></span>

<span data-ttu-id="ad7c7-174">Často je žádoucí, aby asynchronní operace hlásila průběh během operace.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="ad7c7-175">Asynchronní vzor založený na událostech poskytuje pokyny k tomu.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>

- <span data-ttu-id="ad7c7-176">Volitelně definujte událost, která má být vyvolána asynchronní operací a vyvolána v příslušném vlákně.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="ad7c7-177">Objekt <xref:System.ComponentModel.ProgressChangedEventArgs> nese indikátor průběhu s celočíselnou hodnotou, u kterého se očekává hodnota mezi 0 a 100.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>

- <span data-ttu-id="ad7c7-178">Pojmenujte tuto událost takto:</span><span class="sxs-lookup"><span data-stu-id="ad7c7-178">Name this event as follows:</span></span>

  - <span data-ttu-id="ad7c7-179">`ProgressChanged`pokud třída má více asynchronních operací (nebo se očekává, že růst zahrnout více asynchronních operací v budoucích verzích);</span><span class="sxs-lookup"><span data-stu-id="ad7c7-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>

  - <span data-ttu-id="ad7c7-180">_MethodName_**ProgressChanged** pokud má třída jednu asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-180">_MethodName_**ProgressChanged** if the class has a single asynchronous operation.</span></span>

  <span data-ttu-id="ad7c7-181">Tato volba pojmenování paralely, které byly provedeny pro metodu zrušení, jak je popsáno v volitelně podpora zrušení části.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>

<span data-ttu-id="ad7c7-182">Tato událost by <xref:System.ComponentModel.ProgressChangedEventHandler> měla používat <xref:System.ComponentModel.ProgressChangedEventArgs> podpis delegáta a třídu.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="ad7c7-183">Případně pokud lze poskytnout indikátor průběhu více specifický pro doménu (například bajty pro čtení a celkové bajty pro operaci <xref:System.ComponentModel.ProgressChangedEventArgs>stahování), měli byste definovat odvozenou třídu .</span><span class="sxs-lookup"><span data-stu-id="ad7c7-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>

<span data-ttu-id="ad7c7-184">Všimněte si, `ProgressChanged` že existuje pouze jeden nebo _MethodName_**ProgressChanged** událost pro třídu, bez ohledu na počet asynchronních metod, které podporuje.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-184">Note that there is only one `ProgressChanged` or _MethodName_**ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="ad7c7-185">Očekává se, že `userState` klienti budou používat objekt, který je předán metodám _MethodName_**Async,** k rozlišení mezi aktualizacemi průběhu více souběžných operací.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-185">Clients are expected to use the `userState` object that is passed to the _MethodName_**Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>

<span data-ttu-id="ad7c7-186">Mohou nastat situace, ve kterých více operací podporují průběh a každý vrátí jiný ukazatel pro průběh.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="ad7c7-187">V tomto případě `ProgressChanged` jedna událost není vhodné a můžete `ProgressChanged` zvážit podporu více událostí.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="ad7c7-188">V tomto případě použijte vzor pojmenování _MethodName_**ProgressChanged** pro každou _metodu MethodName_**Async.**</span><span class="sxs-lookup"><span data-stu-id="ad7c7-188">In this case use a naming pattern of _MethodName_**ProgressChanged** for each _MethodName_**Async** method.</span></span>

<span data-ttu-id="ad7c7-189">Dodržujte sémantiku hlášení průběhu popsanou [doporučené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="ad7c7-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="ad7c7-190">Volitelně poskytují podporu pro vrácení přírůstkových výsledků</span><span class="sxs-lookup"><span data-stu-id="ad7c7-190">Optionally Provide Support for Returning Incremental Results</span></span>

<span data-ttu-id="ad7c7-191">Někdy asynchronní operace může vrátit přírůstkové výsledky před dokončením.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="ad7c7-192">Existuje několik možností, které lze použít pro podporu tohoto scénáře.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="ad7c7-193">Některé příklady následují.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-193">Some examples follow.</span></span>

### <a name="single-operation-class"></a><span data-ttu-id="ad7c7-194">Třída s jednou operací</span><span class="sxs-lookup"><span data-stu-id="ad7c7-194">Single-operation Class</span></span>

<span data-ttu-id="ad7c7-195">Pokud vaše třída podporuje pouze jednu asynchronní operaci a tato operace je schopna vrátit přírůstkové výsledky, pak:</span><span class="sxs-lookup"><span data-stu-id="ad7c7-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>

- <span data-ttu-id="ad7c7-196">Rozšiřte <xref:System.ComponentModel.ProgressChangedEventArgs> typ tak, aby přenášel přírůstková data výsledků, a definujte událost _MethodName_**ProgressChanged** s těmito rozšířenými daty.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a _MethodName_**ProgressChanged** event with this extended data.</span></span>

- <span data-ttu-id="ad7c7-197">Raise this _MethodName_**ProgressChanged** událost když je přírůstkový výsledek sestavy.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-197">Raise this _MethodName_**ProgressChanged** event when there is an incremental result to report.</span></span>

<span data-ttu-id="ad7c7-198">Toto řešení platí konkrétně pro třídu single-async-operation, protože neexistuje žádný problém se stejnou událostí, ke které dochází, aby se vrátily přírůstkové výsledky na "všechny operace", jako to dělá událost _MethodName_**ProgressChanged.**</span><span class="sxs-lookup"><span data-stu-id="ad7c7-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the _MethodName_**ProgressChanged** event does.</span></span>

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="ad7c7-199">Třída s více operacemi s homogenními přírůstkovými výsledky</span><span class="sxs-lookup"><span data-stu-id="ad7c7-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>

<span data-ttu-id="ad7c7-200">V tomto případě vaše třída podporuje více asynchronních metod, z nichž každá je schopna vracet přírůstkové výsledky a tyto přírůstkové výsledky mají stejný typ dat.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>

<span data-ttu-id="ad7c7-201">Postupujte podle výše popsaného modelu pro třídy s jednou operací, protože stejná <xref:System.EventArgs> struktura bude fungovat pro všechny přírůstkové výsledky.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="ad7c7-202">Definujte `ProgressChanged` událost namísto události _MethodName_**ProgressChanged,** protože se vztahuje na více asynchronních metod.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-202">Define a `ProgressChanged` event instead of a _MethodName_**ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="ad7c7-203">Třída s více operacemi s heterogenními přírůstkovými výsledky</span><span class="sxs-lookup"><span data-stu-id="ad7c7-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>

<span data-ttu-id="ad7c7-204">Pokud vaše třída podporuje více asynchronních metod, každý vrací jiný typ dat, měli byste:</span><span class="sxs-lookup"><span data-stu-id="ad7c7-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>

- <span data-ttu-id="ad7c7-205">Oddělte přírůstkové vykazování výsledků od vykazování průběhu.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-205">Separate your incremental result reporting from your progress reporting.</span></span>

- <span data-ttu-id="ad7c7-206">Definujte samostatnou událost _MethodName_**ProgressChanged** s příslušnou <xref:System.EventArgs> pro každou asynchronní metodu pro zpracování přírůstkových dat výsledků této metody.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-206">Define a separate _MethodName_**ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>

<span data-ttu-id="ad7c7-207">Vyvolat tuto obslužnou rutinu události v příslušném vlákně, jak je popsáno v [doporučených postupech pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="ad7c7-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="ad7c7-208">Zpracování a ref parametry v metodách</span><span class="sxs-lookup"><span data-stu-id="ad7c7-208">Handling Out and Ref Parameters in Methods</span></span>

<span data-ttu-id="ad7c7-209">Přestože použití `out` `ref` a je obecně nedoporučuje v rozhraní .NET Framework, zde jsou pravidla dodržovat, když jsou k dispozici:</span><span class="sxs-lookup"><span data-stu-id="ad7c7-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>

<span data-ttu-id="ad7c7-210">Vzhledem k tomu, synchronní metoda *MethodName*:</span><span class="sxs-lookup"><span data-stu-id="ad7c7-210">Given a synchronous method *MethodName*:</span></span>

- <span data-ttu-id="ad7c7-211">`out`parametry *MethodName* by neměly být součástí _MethodName_**Async**.</span><span class="sxs-lookup"><span data-stu-id="ad7c7-211">`out` parameters to *MethodName* should not be part of _MethodName_**Async**.</span></span> <span data-ttu-id="ad7c7-212">Místo toho by měly být součástí _MethodName_**CompletedEventArgs** se stejným názvem jako jeho ekvivalent parametru v *MethodName* (pokud neexistuje vhodnější název).</span><span class="sxs-lookup"><span data-stu-id="ad7c7-212">Instead, they should be part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

- <span data-ttu-id="ad7c7-213">`ref`parametry *methodname* by se měly zobrazit jako součást _MethodName_**Async**a jako součást _MethodName_**CompletedEventArgs** se stejným názvem jako jeho ekvivalent parametru v *MethodName* (pokud není vhodnější název).</span><span class="sxs-lookup"><span data-stu-id="ad7c7-213">`ref` parameters to *MethodName* should appear as part of _MethodName_**Async**, and as part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

<span data-ttu-id="ad7c7-214">Například vzhledem k tomu, že:</span><span class="sxs-lookup"><span data-stu-id="ad7c7-214">For example, given:</span></span>

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

<span data-ttu-id="ad7c7-215">Vaše asynchronní metoda <xref:System.ComponentModel.AsyncCompletedEventArgs> a její třída bude vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="ad7c7-215">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ad7c7-216">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad7c7-216">See also</span></span>

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [<span data-ttu-id="ad7c7-217">Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="ad7c7-217">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="ad7c7-218">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="ad7c7-218">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="ad7c7-219">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="ad7c7-219">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="ad7c7-220">Rozhodování, kdy implementovat asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="ad7c7-220">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="ad7c7-221">Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="ad7c7-221">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="ad7c7-222">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="ad7c7-222">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
