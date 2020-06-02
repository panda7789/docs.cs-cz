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
ms.openlocfilehash: 484050b45b5da72386e9ac29805d7faf0ca9cbd6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289379"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="fe333-102">Implementace asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="fe333-102">Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="fe333-103">Pokud píšete třídu s některými operacemi, které mohou znamenat znatelné prodlevy, zvažte, že je možné poskytnout asynchronní funkce pomocí [přehledu asynchronního vzoru založeného na událostech](event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fe333-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md).</span></span>

<span data-ttu-id="fe333-104">Asynchronní vzor založený na událostech poskytuje standardizovaný způsob, jak zabalit třídu, která obsahuje asynchronní funkce.</span><span class="sxs-lookup"><span data-stu-id="fe333-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="fe333-105">Pokud je tato třída implementována s podpůrnými třídami jako <xref:System.ComponentModel.AsyncOperationManager> , bude správně fungovat v jakémkoli modelu aplikace, včetně ASP.NET, konzolových aplikací a aplikací model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fe333-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including ASP.NET, Console applications, and Windows Forms applications.</span></span>

<span data-ttu-id="fe333-106">Příklad, který implementuje asynchronní vzor založený na událostech, naleznete v tématu [How to: Implementing a Component, která podporuje asynchronní vzor založený na událostech](component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="fe333-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="fe333-107">U jednoduchých asynchronních operací můžete najít <xref:System.ComponentModel.BackgroundWorker> vhodnou komponentu.</span><span class="sxs-lookup"><span data-stu-id="fe333-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="fe333-108">Další informace o najdete v <xref:System.ComponentModel.BackgroundWorker> tématu [Postup: spuštění operace na pozadí](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="fe333-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>

<span data-ttu-id="fe333-109">Následující seznam popisuje funkce asynchronního vzoru založeného na událostech, které jsou popsány v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="fe333-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>

- <span data-ttu-id="fe333-110">Příležitosti pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="fe333-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

- <span data-ttu-id="fe333-111">Pojmenovávání asynchronních metod</span><span class="sxs-lookup"><span data-stu-id="fe333-111">Naming Asynchronous Methods</span></span>

- <span data-ttu-id="fe333-112">Volitelně podpora zrušení</span><span class="sxs-lookup"><span data-stu-id="fe333-112">Optionally Support Cancellation</span></span>

- <span data-ttu-id="fe333-113">Volitelně podporuje vlastnost Busy</span><span class="sxs-lookup"><span data-stu-id="fe333-113">Optionally Support the IsBusy Property</span></span>

- <span data-ttu-id="fe333-114">Volitelně poskytuje podporu pro vytváření sestav o průběhu.</span><span class="sxs-lookup"><span data-stu-id="fe333-114">Optionally Provide Support for Progress Reporting</span></span>

- <span data-ttu-id="fe333-115">Volitelně poskytuje podporu pro vracení přírůstkových výsledků.</span><span class="sxs-lookup"><span data-stu-id="fe333-115">Optionally Provide Support for Returning Incremental Results</span></span>

- <span data-ttu-id="fe333-116">Zpracování parametrů a odkazů v metodách</span><span class="sxs-lookup"><span data-stu-id="fe333-116">Handling Out and Ref Parameters in Methods</span></span>

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="fe333-117">Příležitosti pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="fe333-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="fe333-118">Zvažte implementaci asynchronního vzoru založeného na událostech v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="fe333-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>

- <span data-ttu-id="fe333-119">Klienti vaší třídy nepotřebují <xref:System.Threading.WaitHandle> a <xref:System.IAsyncResult> k dispozici jsou objekty pro asynchronní operace, což znamená, že klient musí vytvořit cyklické dotazování a <xref:System.Threading.WaitHandle.WaitAll%2A> nebo <xref:System.Threading.WaitHandle.WaitAny%2A> bude muset být sestaven.</span><span class="sxs-lookup"><span data-stu-id="fe333-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>

- <span data-ttu-id="fe333-120">Chcete, aby byly asynchronní operace spravovány klientem se známým modelem události nebo delegáta.</span><span class="sxs-lookup"><span data-stu-id="fe333-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>

<span data-ttu-id="fe333-121">Každá operace je kandidátem na asynchronní implementaci, ale je třeba vzít v úvahu, že byste měli zvážit dlouhou latenci.</span><span class="sxs-lookup"><span data-stu-id="fe333-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="fe333-122">Zvlášť vhodné jsou operace, ve kterých klienti volají metodu a jsou informováni o dokončení, a to bez nutnosti dalšího zásahu.</span><span class="sxs-lookup"><span data-stu-id="fe333-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="fe333-123">Také vhodné jsou operace, které pracují průběžně a pravidelně upozorňují na jejich průběh, přírůstkové výsledky nebo změny stavu.</span><span class="sxs-lookup"><span data-stu-id="fe333-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>

<span data-ttu-id="fe333-124">Další informace o rozhodování o podpoře asynchronního vzoru založeného na událostech naleznete v tématu [rozhodování, kdy implementovat asynchronní vzor založený na událostech](deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="fe333-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="naming-asynchronous-methods"></a><span data-ttu-id="fe333-125">Pojmenovávání asynchronních metod</span><span class="sxs-lookup"><span data-stu-id="fe333-125">Naming Asynchronous Methods</span></span>

<span data-ttu-id="fe333-126">Pro každou synchronní metodu *methodName* , pro kterou chcete poskytnout asynchronní protějšek:</span><span class="sxs-lookup"><span data-stu-id="fe333-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>

<span data-ttu-id="fe333-127">Definujte**asynchronní** metodu _methodName_, která:</span><span class="sxs-lookup"><span data-stu-id="fe333-127">Define a _MethodName_**Async** method that:</span></span>

- <span data-ttu-id="fe333-128">Vrací objekt `void`.</span><span class="sxs-lookup"><span data-stu-id="fe333-128">Returns `void`.</span></span>

- <span data-ttu-id="fe333-129">Přebírá stejné parametry jako metoda *methodName* .</span><span class="sxs-lookup"><span data-stu-id="fe333-129">Takes the same parameters as the *MethodName* method.</span></span>

- <span data-ttu-id="fe333-130">Umožňuje přijmout vícenásobná volání.</span><span class="sxs-lookup"><span data-stu-id="fe333-130">Accepts multiple invocations.</span></span>

<span data-ttu-id="fe333-131">Volitelně definujte**asynchronní** přetížení _methodName_, které je identické s _methodName_**Async**, ale s dalším parametrem s hodnotou objektu s názvem `userState` .</span><span class="sxs-lookup"><span data-stu-id="fe333-131">Optionally define a _MethodName_**Async** overload, identical to _MethodName_**Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="fe333-132">Tuto akci proveďte, pokud jste připraveni ke správě více souběžných volání vaší metody. v takovém případě `userState` bude hodnota doručena zpět do všech obslužných rutin událostí pro odlišení vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="fe333-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="fe333-133">Můžete to také provést jednoduše jako místo pro uložení stavu uživatele pro pozdější načtení.</span><span class="sxs-lookup"><span data-stu-id="fe333-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>

<span data-ttu-id="fe333-134">Pro každou samostatnou signaturu**asynchronní** metody _methodName_:</span><span class="sxs-lookup"><span data-stu-id="fe333-134">For each separate _MethodName_**Async** method signature:</span></span>

1. <span data-ttu-id="fe333-135">Definujte následující událost ve stejné třídě jako metodu:</span><span class="sxs-lookup"><span data-stu-id="fe333-135">Define the following event in the same class as the method:</span></span>

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. <span data-ttu-id="fe333-136">Definujte následujícího delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="fe333-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="fe333-137">Tyto prvky budou pravděpodobně definovány mimo samotnou třídu, ale ve stejném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fe333-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>

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

    - <span data-ttu-id="fe333-138">Ujistěte se, že třída _methodName_**CompletedEventArgs** zpřístupňuje své členy jako vlastnosti jen pro čtení, nikoli pole, protože pole zabraňují vytváření datových vazeb.</span><span class="sxs-lookup"><span data-stu-id="fe333-138">Ensure that the _MethodName_**CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>

    - <span data-ttu-id="fe333-139">Nedefinujte žádné <xref:System.ComponentModel.AsyncCompletedEventArgs> odvozené třídy pro metody, které nevedou k výsledkům.</span><span class="sxs-lookup"><span data-stu-id="fe333-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="fe333-140">Jednoduše použijte instanci <xref:System.ComponentModel.AsyncCompletedEventArgs> sebe sama.</span><span class="sxs-lookup"><span data-stu-id="fe333-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>

      > [!NOTE]
      > <span data-ttu-id="fe333-141">Je dokonale přijatelné, pokud je to proveditelné a vhodné, k opakovanému použití delegátů a <xref:System.ComponentModel.AsyncCompletedEventArgs> typů.</span><span class="sxs-lookup"><span data-stu-id="fe333-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="fe333-142">V takovém případě nebude pojmenování konzistentní s názvem metody, protože daný delegát a <xref:System.ComponentModel.AsyncCompletedEventArgs> nebude svázán s jedinou metodou.</span><span class="sxs-lookup"><span data-stu-id="fe333-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>

## <a name="optionally-support-cancellation"></a><span data-ttu-id="fe333-143">Volitelně podpora zrušení</span><span class="sxs-lookup"><span data-stu-id="fe333-143">Optionally Support Cancellation</span></span>

<span data-ttu-id="fe333-144">Pokud vaše třída bude podporovat zrušení asynchronních operací, zrušení by mělo být zveřejněno klientovi, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="fe333-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="fe333-145">Všimněte si, že před definováním podpory zrušení se musí dosáhnout dva rozhodovací body:</span><span class="sxs-lookup"><span data-stu-id="fe333-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>

- <span data-ttu-id="fe333-146">Obsahuje vaše třída, včetně budoucích předpokládaných dodatků, jenom jednu asynchronní operaci, která podporuje zrušení?</span><span class="sxs-lookup"><span data-stu-id="fe333-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>

- <span data-ttu-id="fe333-147">Mohou asynchronní operace, které podporují zrušení, podporují více operací, které čekají na vyřízení?</span><span class="sxs-lookup"><span data-stu-id="fe333-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="fe333-148">To znamená, že**asynchronní** metoda _methodName_přijímá `userState` parametr a umožňuje vícenásobné vyvolání před čekáním na dokončení?</span><span class="sxs-lookup"><span data-stu-id="fe333-148">That is, does the _MethodName_**Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>

<span data-ttu-id="fe333-149">Pomocí odpovědí na tyto dvě otázky v následující tabulce zjistíte, jak by měl být signatura metody zrušení.</span><span class="sxs-lookup"><span data-stu-id="fe333-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="fe333-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe333-150">Visual Basic</span></span>

||<span data-ttu-id="fe333-151">Podporuje se víc souběžných operací.</span><span class="sxs-lookup"><span data-stu-id="fe333-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="fe333-152">Vždy jen jedna operace</span><span class="sxs-lookup"><span data-stu-id="fe333-152">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="fe333-153">Jedna asynchronní operace v celé třídě</span><span class="sxs-lookup"><span data-stu-id="fe333-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|<span data-ttu-id="fe333-154">Několik asynchronních operací ve třídě</span><span class="sxs-lookup"><span data-stu-id="fe333-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a><span data-ttu-id="fe333-155">C\#</span><span class="sxs-lookup"><span data-stu-id="fe333-155">C\#</span></span>

||<span data-ttu-id="fe333-156">Podporuje se víc souběžných operací.</span><span class="sxs-lookup"><span data-stu-id="fe333-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="fe333-157">Vždy jen jedna operace</span><span class="sxs-lookup"><span data-stu-id="fe333-157">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="fe333-158">Jedna asynchronní operace v celé třídě</span><span class="sxs-lookup"><span data-stu-id="fe333-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|<span data-ttu-id="fe333-159">Několik asynchronních operací ve třídě</span><span class="sxs-lookup"><span data-stu-id="fe333-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|

<span data-ttu-id="fe333-160">Pokud definujete `CancelAsync(object userState)` metodu, musí být klienti opatrní při volbě jejich hodnot stavu, aby je bylo možné rozlišovat mezi všemi asynchronními metodami, které jsou vyvolány u objektu, a nikoli pouze mezi všemi voláními jedné asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="fe333-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>

<span data-ttu-id="fe333-161">Rozhodnutí o pojmenování jedné asynchronní operace _methodName_**AsyncCancel** je založené na tom, že je možné snadněji zjistit metodu ve vývojovém prostředí, jako je například IntelliSense sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fe333-161">The decision to name the single-async-operation version _MethodName_**AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="fe333-162">Seskupení souvisejících členů a jejich rozlišení od jiných členů, kteří nemají nic dělat s asynchronními funkcemi.</span><span class="sxs-lookup"><span data-stu-id="fe333-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="fe333-163">Pokud očekáváte, že v následných verzích se přidaly další asynchronní operace, je lepší definovat `CancelAsync` .</span><span class="sxs-lookup"><span data-stu-id="fe333-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>

<span data-ttu-id="fe333-164">Nedefinujte více metod z tabulky výše ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="fe333-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="fe333-165">Který nebude dávat smysl, nebo by měl zazbytečně zaměnit rozhraní třídy s přemnožením metod.</span><span class="sxs-lookup"><span data-stu-id="fe333-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>

<span data-ttu-id="fe333-166">Tyto metody se obvykle vrátí okamžitě a operace může nebo nemusí ve skutečnosti zrušit.</span><span class="sxs-lookup"><span data-stu-id="fe333-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="fe333-167">V obslužné rutině události pro událost _methodName_**Completed** obsahuje objekt _methodName_**CompletedEventArgs** `Cancelled` pole, které klienti mohou použít k určení, zda došlo ke zrušení.</span><span class="sxs-lookup"><span data-stu-id="fe333-167">In the event handler for the _MethodName_**Completed** event, the _MethodName_**CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>

<span data-ttu-id="fe333-168">Řídí se sémantikou zrušení popsanou v tématu [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="fe333-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="fe333-169">Volitelně podporuje vlastnost Busy</span><span class="sxs-lookup"><span data-stu-id="fe333-169">Optionally Support the IsBusy Property</span></span>

<span data-ttu-id="fe333-170">Pokud vaše třída nepodporuje více souběžných volání, zvažte vystavení `IsBusy` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fe333-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="fe333-171">To umožňuje vývojářům určit, zda je _methodName_**asynchronní** metoda spuštěna bez zachycení výjimky z**asynchronní** metody _methodName_.</span><span class="sxs-lookup"><span data-stu-id="fe333-171">This allows developers to determine whether a _MethodName_**Async** method is running without catching an exception from the _MethodName_**Async** method.</span></span>

<span data-ttu-id="fe333-172">Dodržuje `IsBusy` sémantiku popsanou v tématu [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="fe333-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="fe333-173">Volitelně poskytuje podporu pro vytváření sestav o průběhu.</span><span class="sxs-lookup"><span data-stu-id="fe333-173">Optionally Provide Support for Progress Reporting</span></span>

<span data-ttu-id="fe333-174">Je často žádoucí, aby asynchronní operace nahlásila pokrok během jeho provozu.</span><span class="sxs-lookup"><span data-stu-id="fe333-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="fe333-175">Asynchronní vzor založený na událostech poskytuje pokyny pro to.</span><span class="sxs-lookup"><span data-stu-id="fe333-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>

- <span data-ttu-id="fe333-176">Volitelně můžete definovat událost, která má být vyvolána asynchronní operací a vyvolána v příslušném vlákně.</span><span class="sxs-lookup"><span data-stu-id="fe333-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="fe333-177"><xref:System.ComponentModel.ProgressChangedEventArgs>Objekt přenese ukazatel průběhu s celočíselnou hodnotou, který by měl být v rozmezí od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="fe333-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>

- <span data-ttu-id="fe333-178">Pojmenujte tuto událost následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="fe333-178">Name this event as follows:</span></span>

  - <span data-ttu-id="fe333-179">`ProgressChanged`Pokud má třída více asynchronních operací (nebo se očekává, že se má rozšířit, aby zahrnovalo více asynchronních operací v budoucích verzích);</span><span class="sxs-lookup"><span data-stu-id="fe333-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>

  - <span data-ttu-id="fe333-180">_MethodName_**ProgressChanged** , pokud má třída jedinou asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="fe333-180">_MethodName_**ProgressChanged** if the class has a single asynchronous operation.</span></span>

  <span data-ttu-id="fe333-181">Tato volba pojmenovává paralelně, kterou vytvořila metoda zrušení, jak je popsáno v části volitelná zrušení podpory.</span><span class="sxs-lookup"><span data-stu-id="fe333-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>

<span data-ttu-id="fe333-182">Tato událost by měla používat <xref:System.ComponentModel.ProgressChangedEventHandler> signaturu delegáta a <xref:System.ComponentModel.ProgressChangedEventArgs> třídu.</span><span class="sxs-lookup"><span data-stu-id="fe333-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="fe333-183">Případně, pokud je možné zadat více ukazatelů průběhu pro doménu (například přečtené bajty a celkový počet bajtů pro operaci stažení), je třeba definovat odvozenou třídu třídy <xref:System.ComponentModel.ProgressChangedEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="fe333-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>

<span data-ttu-id="fe333-184">Všimněte si, že existuje pouze jedna `ProgressChanged` nebo _methodName_**ProgressChanged** událost pro třídu, bez ohledu na počet asynchronních metod, které podporuje.</span><span class="sxs-lookup"><span data-stu-id="fe333-184">Note that there is only one `ProgressChanged` or _MethodName_**ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="fe333-185">U klientů se očekává použití `userState` objektu, který je předán**asynchronním** metodám _methodName_k rozlišení mezi aktualizacemi průběhu více souběžných operací.</span><span class="sxs-lookup"><span data-stu-id="fe333-185">Clients are expected to use the `userState` object that is passed to the _MethodName_**Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>

<span data-ttu-id="fe333-186">Mohou nastat situace, kdy více operací podporuje průběh a každý vrací jiný indikátor pro průběh.</span><span class="sxs-lookup"><span data-stu-id="fe333-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="fe333-187">V takovém případě jedna `ProgressChanged` událost není vhodná a může zvážit podporu více `ProgressChanged` událostí.</span><span class="sxs-lookup"><span data-stu-id="fe333-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="fe333-188">V tomto případě použijte pro každou _methodName_**asynchronní** metodu vzor pojmenování _methodName_**ProgressChanged** .</span><span class="sxs-lookup"><span data-stu-id="fe333-188">In this case use a naming pattern of _MethodName_**ProgressChanged** for each _MethodName_**Async** method.</span></span>

<span data-ttu-id="fe333-189">Dodržuje sémantické sémantiky vytváření sestav, které popisují [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="fe333-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="fe333-190">Volitelně poskytuje podporu pro vracení přírůstkových výsledků.</span><span class="sxs-lookup"><span data-stu-id="fe333-190">Optionally Provide Support for Returning Incremental Results</span></span>

<span data-ttu-id="fe333-191">V některých případech může asynchronní operace vracet přírůstkové výsledky před dokončením.</span><span class="sxs-lookup"><span data-stu-id="fe333-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="fe333-192">K dispozici je několik možností, které lze použít k podpoře tohoto scénáře.</span><span class="sxs-lookup"><span data-stu-id="fe333-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="fe333-193">Následuje několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="fe333-193">Some examples follow.</span></span>

### <a name="single-operation-class"></a><span data-ttu-id="fe333-194">Třída s jednou operací</span><span class="sxs-lookup"><span data-stu-id="fe333-194">Single-operation Class</span></span>

<span data-ttu-id="fe333-195">Pokud vaše třída podporuje jenom jednu asynchronní operaci a tato operace může vracet přírůstkové výsledky, pak:</span><span class="sxs-lookup"><span data-stu-id="fe333-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>

- <span data-ttu-id="fe333-196">Rozšiřte <xref:System.ComponentModel.ProgressChangedEventArgs> typ tak, aby převedl data přírůstkového výsledku, a definujte událost _methodName_**ProgressChanged** s rozšířenými daty.</span><span class="sxs-lookup"><span data-stu-id="fe333-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a _MethodName_**ProgressChanged** event with this extended data.</span></span>

- <span data-ttu-id="fe333-197">Vyvolá tuto událost _methodName_**ProgressChanged** , když se zobrazí přírůstkový výsledek pro sestavu.</span><span class="sxs-lookup"><span data-stu-id="fe333-197">Raise this _MethodName_**ProgressChanged** event when there is an incremental result to report.</span></span>

<span data-ttu-id="fe333-198">Toto řešení se vztahuje konkrétně na třídu s jednou asynchronní operací, protože neexistují žádné potíže se stejnou událostí, která by mohla vracet přírůstkové výsledky pro všechny operace, jako událost _methodName_**ProgressChanged** .</span><span class="sxs-lookup"><span data-stu-id="fe333-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the _MethodName_**ProgressChanged** event does.</span></span>

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="fe333-199">Třída s vícenásobnou operací s homogenními přírůstkovým výsledkem</span><span class="sxs-lookup"><span data-stu-id="fe333-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>

<span data-ttu-id="fe333-200">V takovém případě vaše třída podporuje několik asynchronních metod, z nichž každý dokáže vracet přírůstkové výsledky a tyto přírůstkové výsledky mají stejný typ dat.</span><span class="sxs-lookup"><span data-stu-id="fe333-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>

<span data-ttu-id="fe333-201">Použijte model popsaný výše pro třídy s jednou operací, protože stejná <xref:System.EventArgs> struktura bude fungovat pro všechny přírůstkové výsledky.</span><span class="sxs-lookup"><span data-stu-id="fe333-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="fe333-202">Definujte `ProgressChanged` událost namísto události _methodName_**ProgressChanged** , protože se vztahuje na více asynchronních metod.</span><span class="sxs-lookup"><span data-stu-id="fe333-202">Define a `ProgressChanged` event instead of a _MethodName_**ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="fe333-203">Třída vícenásobných operací s heterogenními přírůstkových výsledků</span><span class="sxs-lookup"><span data-stu-id="fe333-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>

<span data-ttu-id="fe333-204">Pokud vaše třída podporuje více asynchronních metod, každý z nich vrátí jiný typ dat, měli byste:</span><span class="sxs-lookup"><span data-stu-id="fe333-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>

- <span data-ttu-id="fe333-205">Oddělte sestavy přírůstkových výsledků od sestav průběhu.</span><span class="sxs-lookup"><span data-stu-id="fe333-205">Separate your incremental result reporting from your progress reporting.</span></span>

- <span data-ttu-id="fe333-206">Definujte samostatnou událost _methodName_**ProgressChanged** , <xref:System.EventArgs> která je vhodná pro každou asynchronní metodu pro zpracování dat přírůstkového výsledku této metody.</span><span class="sxs-lookup"><span data-stu-id="fe333-206">Define a separate _MethodName_**ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>

<span data-ttu-id="fe333-207">Vyvolejte tuto obslužnou rutinu události v příslušném vlákně, jak je popsáno v tématu [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="fe333-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="fe333-208">Zpracování parametrů a odkazů v metodách</span><span class="sxs-lookup"><span data-stu-id="fe333-208">Handling Out and Ref Parameters in Methods</span></span>

<span data-ttu-id="fe333-209">I když použití `out` a `ref` je obecně v .NET Framework nedoporučujeme, tady jsou pravidla, která se mají sledovat, když jsou k dispozici:</span><span class="sxs-lookup"><span data-stu-id="fe333-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>

<span data-ttu-id="fe333-210">Předané synchronní metodě *methodName*:</span><span class="sxs-lookup"><span data-stu-id="fe333-210">Given a synchronous method *MethodName*:</span></span>

- <span data-ttu-id="fe333-211">`out`parametry *methodName* by neměly být součástí**asynchronního** _methodName_.</span><span class="sxs-lookup"><span data-stu-id="fe333-211">`out` parameters to *MethodName* should not be part of _MethodName_**Async**.</span></span> <span data-ttu-id="fe333-212">Místo toho by měly být součástí _methodName_**CompletedEventArgs** se stejným názvem jako má ekvivalentní parametr v *methodName* (Pokud neexistuje vhodnější název).</span><span class="sxs-lookup"><span data-stu-id="fe333-212">Instead, they should be part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

- <span data-ttu-id="fe333-213">`ref`parametry *methodName* by se měly zobrazit jako součást _methodName_**Async**a jako součást _methodName_**CompletedEventArgs** se stejným názvem jako má ekvivalentní parametr v *methodName* (Pokud neexistuje vhodnější název).</span><span class="sxs-lookup"><span data-stu-id="fe333-213">`ref` parameters to *MethodName* should appear as part of _MethodName_**Async**, and as part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

<span data-ttu-id="fe333-214">Například předané:</span><span class="sxs-lookup"><span data-stu-id="fe333-214">For example, given:</span></span>

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

<span data-ttu-id="fe333-215">Asynchronní metoda a její <xref:System.ComponentModel.AsyncCompletedEventArgs> třída by vypadaly takto:</span><span class="sxs-lookup"><span data-stu-id="fe333-215">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fe333-216">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe333-216">See also</span></span>

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [<span data-ttu-id="fe333-217">Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="fe333-217">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="fe333-218">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="fe333-218">How to: Run an Operation in the Background</span></span>](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="fe333-219">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="fe333-219">How to: Implement a Form That Uses a Background Operation</span></span>](../../framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="fe333-220">Rozhodování, kdy implementovat asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="fe333-220">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="fe333-221">Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="fe333-221">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="fe333-222">Asynchronní vzor založený na událostech (EAP)</span><span class="sxs-lookup"><span data-stu-id="fe333-222">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
