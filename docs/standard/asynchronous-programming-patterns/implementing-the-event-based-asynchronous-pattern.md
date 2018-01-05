---
title: "Implementace asynchronního vzoru založeného na událostech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 77156eb1ceeb549ce5fe09532e05096376b4569b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="733bb-102">Implementace asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="733bb-102">Implementing the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="733bb-103">Pokud píšete třídu s některé operace, které může vést k významnému zpoždění, zvažte, udělíte tím, že implementujete asynchronní funkce [na základě událostí přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="733bb-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="733bb-104">Asynchronní vzor založený na událostech poskytuje standardizovaného způsobu balíček třídy, která má asynchronní funkce.</span><span class="sxs-lookup"><span data-stu-id="733bb-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="733bb-105">Pokud se implementuje pomocí pomocné třídy jako <xref:System.ComponentModel.AsyncOperationManager>, třídě nebude pracovat správně v rámci modelu všechny aplikace, včetně [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], konzolové aplikace a aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="733bb-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Console applications, and Windows Forms applications.</span></span>  
  
 <span data-ttu-id="733bb-106">Příklad, který implementuje asynchronní vzor na základě událostí, naleznete v části [postupy: implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="733bb-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="733bb-107">Pro jednoduché asynchronní operace, můžete zjistit <xref:System.ComponentModel.BackgroundWorker> součást vhodný.</span><span class="sxs-lookup"><span data-stu-id="733bb-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="733bb-108">Další informace o <xref:System.ComponentModel.BackgroundWorker>, najdete v části [postupy: spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="733bb-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
 <span data-ttu-id="733bb-109">Následující seznam popisuje funkce asynchronního vzoru založeného na událostech popsané v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="733bb-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>  
  
-   <span data-ttu-id="733bb-110">Možnosti pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="733bb-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
  
-   <span data-ttu-id="733bb-111">Pojmenování asynchronních metod</span><span class="sxs-lookup"><span data-stu-id="733bb-111">Naming Asynchronous Methods</span></span>  
  
-   <span data-ttu-id="733bb-112">Volitelně podporovat zrušení</span><span class="sxs-lookup"><span data-stu-id="733bb-112">Optionally Support Cancellation</span></span>  
  
-   <span data-ttu-id="733bb-113">Volitelně podporovat vlastnost IsBusy</span><span class="sxs-lookup"><span data-stu-id="733bb-113">Optionally Support the IsBusy Property</span></span>  
  
-   <span data-ttu-id="733bb-114">Volitelně můžete poskytovat podporu pro vytváření sestav průběh</span><span class="sxs-lookup"><span data-stu-id="733bb-114">Optionally Provide Support for Progress Reporting</span></span>  
  
-   <span data-ttu-id="733bb-115">Volitelně můžete poskytovat podporu pro vrácení přírůstkové výsledky</span><span class="sxs-lookup"><span data-stu-id="733bb-115">Optionally Provide Support for Returning Incremental Results</span></span>  
  
-   <span data-ttu-id="733bb-116">Zpracování Out a parametry Ref v metody</span><span class="sxs-lookup"><span data-stu-id="733bb-116">Handling Out and Ref Parameters in Methods</span></span>  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="733bb-117">Možnosti pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="733bb-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
 <span data-ttu-id="733bb-118">Zvažte implementaci asynchronního vzoru založeného na událostech při:</span><span class="sxs-lookup"><span data-stu-id="733bb-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>  
  
-   <span data-ttu-id="733bb-119">Není třeba klienty vaší třídy <xref:System.Threading.WaitHandle> a <xref:System.IAsyncResult> objekty, které jsou k dispozici pro asynchronní operace, což znamená, že dotazování a <xref:System.Threading.WaitHandle.WaitAll%2A> nebo <xref:System.Threading.WaitHandle.WaitAny%2A> muset sestavena klienta.</span><span class="sxs-lookup"><span data-stu-id="733bb-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>  
  
-   <span data-ttu-id="733bb-120">Chcete asynchronní operace lze spravovat pomocí klienta s modelem známé událostí/delegování.</span><span class="sxs-lookup"><span data-stu-id="733bb-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>  
  
 <span data-ttu-id="733bb-121">Všechny operace je kandidátem pro implementaci asynchronního, ale ty očekáváte zabývat dlouho latence potřeba vzít v úvahu.</span><span class="sxs-lookup"><span data-stu-id="733bb-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="733bb-122">Zejména příslušné jsou operace, ve kterých klientech volání metody, které jsou při dokončení, bez nutnosti zásahu Další.</span><span class="sxs-lookup"><span data-stu-id="733bb-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="733bb-123">Odpovídající jsou také operací, které spouštět nepřetržitě, pravidelně upozornění klientů průběh, přírůstkové výsledků nebo změny stavu.</span><span class="sxs-lookup"><span data-stu-id="733bb-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>  
  
 <span data-ttu-id="733bb-124">Další informace o rozhodování, kdy podporují asynchronní vzor založený na událostech najdete v tématu [rozhodování při implementovat asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="733bb-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="naming-asynchronous-methods"></a><span data-ttu-id="733bb-125">Pojmenování asynchronních metod</span><span class="sxs-lookup"><span data-stu-id="733bb-125">Naming Asynchronous Methods</span></span>  
 <span data-ttu-id="733bb-126">Pro každou metodu synchronní *MethodName* pro které byste chtěli poskytnout asynchronní protějšku:</span><span class="sxs-lookup"><span data-stu-id="733bb-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>  
  
 <span data-ttu-id="733bb-127">Definování *MethodName* `Async` metoda který:</span><span class="sxs-lookup"><span data-stu-id="733bb-127">Define a *MethodName*`Async` method that:</span></span>  
  
-   <span data-ttu-id="733bb-128">Vrátí `void`.</span><span class="sxs-lookup"><span data-stu-id="733bb-128">Returns `void`.</span></span>  
  
-   <span data-ttu-id="733bb-129">Používá stejný parametry, jako *MethodName* metoda.</span><span class="sxs-lookup"><span data-stu-id="733bb-129">Takes the same parameters as the *MethodName* method.</span></span>  
  
-   <span data-ttu-id="733bb-130">Přijme více volání.</span><span class="sxs-lookup"><span data-stu-id="733bb-130">Accepts multiple invocations.</span></span>  
  
 <span data-ttu-id="733bb-131">Volitelně můžete definovat *MethodName* `Async` přetížení, identické *MethodName*`Async`, ale s další parametr s hodnotou objekt názvem `userState`.</span><span class="sxs-lookup"><span data-stu-id="733bb-131">Optionally define a *MethodName*`Async` overload, identical to *MethodName*`Async`, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="733bb-132">To udělat, pokud jste se připravili na správu více souběžných volání metody, v takovém případě `userState` hodnota bude doručen zpět do všech obslužné rutiny událostí k rozlišení volání metody.</span><span class="sxs-lookup"><span data-stu-id="733bb-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="733bb-133">Také můžete k tomu jednoduše jako místo pro uložení stavu uživatele pro pozdější načtení.</span><span class="sxs-lookup"><span data-stu-id="733bb-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>  
  
 <span data-ttu-id="733bb-134">Pro každou zvláštní *MethodName* `Async` podpis metody:</span><span class="sxs-lookup"><span data-stu-id="733bb-134">For each separate *MethodName*`Async` method signature:</span></span>  
  
1.  <span data-ttu-id="733bb-135">Ve stejné třídě jako metodu definujte následující událost:</span><span class="sxs-lookup"><span data-stu-id="733bb-135">Define the following event in the same class as the method:</span></span>  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  <span data-ttu-id="733bb-136">Definovat následující delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="733bb-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="733bb-137">Ty se být definovány pravděpodobně mimo vlastní třídy, ale o stejný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="733bb-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>  
  
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
  
    -   <span data-ttu-id="733bb-138">Ujistěte se, že *MethodName* `CompletedEventArgs` – třída zveřejňuje jeho členy jako vlastnosti jen pro čtení a nikoli pole jako pole datová vazba.</span><span class="sxs-lookup"><span data-stu-id="733bb-138">Ensure that the *MethodName*`CompletedEventArgs` class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>  
  
    -   <span data-ttu-id="733bb-139">Nejsou definovány žádné <xref:System.ComponentModel.AsyncCompletedEventArgs>-odvozených tříd pro metody, které neposkytují výsledky.</span><span class="sxs-lookup"><span data-stu-id="733bb-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="733bb-140">Jednoduše použijte instanci <xref:System.ComponentModel.AsyncCompletedEventArgs> sám sebe.</span><span class="sxs-lookup"><span data-stu-id="733bb-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="733bb-141">Je zcela přijatelné, pokud a proveditelné, znovu použít delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs> typy.</span><span class="sxs-lookup"><span data-stu-id="733bb-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="733bb-142">V takovém případě pojmenování nebude jako konzistentní s názvem metody od daného delegáta a <xref:System.ComponentModel.AsyncCompletedEventArgs> nebude vázaný na jedné metody.</span><span class="sxs-lookup"><span data-stu-id="733bb-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>  
  
## <a name="optionally-support-cancellation"></a><span data-ttu-id="733bb-143">Volitelně podporovat zrušení</span><span class="sxs-lookup"><span data-stu-id="733bb-143">Optionally Support Cancellation</span></span>  
 <span data-ttu-id="733bb-144">Pokud vaše třída bude podporovat zrušení asynchronních operací, by měly být vystaveny zrušení klientovi, jak je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="733bb-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="733bb-145">Všimněte si, že existují dvě rozhodovací body, které je třeba dostupný před definováním zrušení podporu:</span><span class="sxs-lookup"><span data-stu-id="733bb-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>  
  
-   <span data-ttu-id="733bb-146">Má vaše třídy, včetně budoucí předpokládaného dodatky, jenom jeden asynchronní operaci, která podporuje zrušení?</span><span class="sxs-lookup"><span data-stu-id="733bb-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>  
  
-   <span data-ttu-id="733bb-147">Můžete asynchronní operace, které podporují více čekající operace zrušení podporu?</span><span class="sxs-lookup"><span data-stu-id="733bb-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="733bb-148">To znamená, nemá *MethodName* `Async` metoda proveďte `userState` parametr, a tomu více volání před čekání na všechny ukončíte?</span><span class="sxs-lookup"><span data-stu-id="733bb-148">That is, does the *MethodName*`Async` method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>  
  
 <span data-ttu-id="733bb-149">Chcete-li zjistit, co by měl být podpis pro metodu zrušení pomocí odpovědi na tyto otázky dvě v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="733bb-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>  
  
### <a name="visual-basic"></a><span data-ttu-id="733bb-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="733bb-150">Visual Basic</span></span>  
  
||<span data-ttu-id="733bb-151">Podporováno více souběžných operací.</span><span class="sxs-lookup"><span data-stu-id="733bb-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="733bb-152">Vždy pouze jednu operaci</span><span class="sxs-lookup"><span data-stu-id="733bb-152">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="733bb-153">Jeden asynchronní operace v celé – třída</span><span class="sxs-lookup"><span data-stu-id="733bb-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|<span data-ttu-id="733bb-154">Více asynchronních operací v – třída</span><span class="sxs-lookup"><span data-stu-id="733bb-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a><span data-ttu-id="733bb-155">C#</span><span class="sxs-lookup"><span data-stu-id="733bb-155">C#</span></span>  
  
||<span data-ttu-id="733bb-156">Podporováno více souběžných operací.</span><span class="sxs-lookup"><span data-stu-id="733bb-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="733bb-157">Vždy pouze jednu operaci</span><span class="sxs-lookup"><span data-stu-id="733bb-157">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="733bb-158">Jeden asynchronní operace v celé – třída</span><span class="sxs-lookup"><span data-stu-id="733bb-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|<span data-ttu-id="733bb-159">Více asynchronních operací v – třída</span><span class="sxs-lookup"><span data-stu-id="733bb-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 <span data-ttu-id="733bb-160">Pokud definujete `CancelAsync(object userState)` metody, klienti musí být opatrní při volbě jejich stavu hodnoty tak, aby byly schopna rozlišovat mezi všechny asynchronní metody volá v objektu, ne jenom mezi všechny volání jedné asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="733bb-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>  
  
 <span data-ttu-id="733bb-161">Rozhodnutí ohledně název verze jedním. asynchronní operace *MethodName* `AsyncCancel` je založena na schopnost snadněji zjistit metodu v prostředí návrhu jako Visual Studio IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="733bb-161">The decision to name the single-async-operation version *MethodName*`AsyncCancel` is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="733bb-162">To související členy skupiny a je odlišuje od ostatních členů, které nemají co dělat s asynchronní funkce.</span><span class="sxs-lookup"><span data-stu-id="733bb-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="733bb-163">Pokud očekáváte, že mohou být další asynchronních operací přibylo v dalších verzích, je lepší definovat `CancelAsync`.</span><span class="sxs-lookup"><span data-stu-id="733bb-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>  
  
 <span data-ttu-id="733bb-164">Ve stejné třídě nedefinují několik metod z výše uvedené tabulce.</span><span class="sxs-lookup"><span data-stu-id="733bb-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="733bb-165">Která nebude mít smysl, nebo ho bude zbytečných souborů třídy rozhraní s jak narůstá počet metody.</span><span class="sxs-lookup"><span data-stu-id="733bb-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>  
  
 <span data-ttu-id="733bb-166">Tyto metody se obvykle vrátí okamžitě a tato operace může nebo nemusí ve skutečnosti zrušit.</span><span class="sxs-lookup"><span data-stu-id="733bb-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="733bb-167">V obslužné rutiny události pro *MethodName* `Completed` událostí, *MethodName* `CompletedEventArgs` objekt obsahuje `Cancelled` pole, které můžou klienti použít k určení zda zrušení došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="733bb-167">In the event handler for the *MethodName*`Completed` event, the *MethodName*`CompletedEventArgs` object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>  
  
 <span data-ttu-id="733bb-168">Dodržováním sémantiku zrušení popsané v [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="733bb-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="733bb-169">Volitelně podporovat vlastnost IsBusy</span><span class="sxs-lookup"><span data-stu-id="733bb-169">Optionally Support the IsBusy Property</span></span>  
 <span data-ttu-id="733bb-170">Pokud vaše třída nepodporuje více souběžných volání, vezměte v úvahu vystavení `IsBusy` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="733bb-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="733bb-171">To umožňuje vývojářům určit, zda *MethodName* `Async` metoda běží bez zachytávání výjimku z *MethodName* `Async` metoda.</span><span class="sxs-lookup"><span data-stu-id="733bb-171">This allows developers to determine whether a *MethodName*`Async` method is running without catching an exception from the *MethodName*`Async` method.</span></span>  
  
 <span data-ttu-id="733bb-172">Dodržováním `IsBusy` sémantiku popsané v [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="733bb-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="733bb-173">Volitelně můžete poskytovat podporu pro vytváření sestav průběh</span><span class="sxs-lookup"><span data-stu-id="733bb-173">Optionally Provide Support for Progress Reporting</span></span>  
 <span data-ttu-id="733bb-174">Je často žádoucí, aby asynchronní operaci sestava pokroku při své činnosti.</span><span class="sxs-lookup"><span data-stu-id="733bb-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="733bb-175">Asynchronní vzor založený na událostech uvádí postup, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="733bb-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>  
  
-   <span data-ttu-id="733bb-176">Volitelně můžete definujte události vyvolané asynchronní operaci a vyvolána na příslušné vlákno.</span><span class="sxs-lookup"><span data-stu-id="733bb-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="733bb-177"><xref:System.ComponentModel.ProgressChangedEventArgs> Objekt představuje indikátor průběhu celočíselný, který musí být mezi 0 a 100.</span><span class="sxs-lookup"><span data-stu-id="733bb-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>  
  
-   <span data-ttu-id="733bb-178">Tato událost název následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="733bb-178">Name this event as follows:</span></span>  
  
    -   <span data-ttu-id="733bb-179">`ProgressChanged`Pokud třída má více asynchronních operací (nebo se očekává dosáhnout zahrnují více asynchronních operací v budoucích verzích);</span><span class="sxs-lookup"><span data-stu-id="733bb-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>  
  
    -   <span data-ttu-id="733bb-180">*MethodName* `ProgressChanged` Pokud třída má jeden asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="733bb-180">*MethodName* `ProgressChanged` if the class has a single asynchronous operation.</span></span>  
  
     <span data-ttu-id="733bb-181">Tato volba pojmenování paralelní s výrobce pro metodu zrušení, jak je popsáno v části volitelně podporu zrušení.</span><span class="sxs-lookup"><span data-stu-id="733bb-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>  
  
 <span data-ttu-id="733bb-182">Tato událost se má použít <xref:System.ComponentModel.ProgressChangedEventHandler> podpisu delegáta a <xref:System.ComponentModel.ProgressChangedEventArgs> třídy.</span><span class="sxs-lookup"><span data-stu-id="733bb-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="733bb-183">Případně, pokud indikátor průběhu více specifické pro doménu lze zadat (pro instance, čtení bajtů a celkový počet bajtů pro operace nástroje download), pak byste měli definovat třídu odvozenou z <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="733bb-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>  
  
 <span data-ttu-id="733bb-184">Všimněte si, že pouze jeden `ProgressChanged` nebo *MethodName* `ProgressChanged` události pro třídu, bez ohledu na počet asynchronních metod podporuje.</span><span class="sxs-lookup"><span data-stu-id="733bb-184">Note that there is only one `ProgressChanged` or *MethodName*`ProgressChanged` event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="733bb-185">Klienti budou používat `userState` objekt, který je předán *MethodName* `Async` metody k rozlišení mezi průběh aktualizací na více souběžných operací.</span><span class="sxs-lookup"><span data-stu-id="733bb-185">Clients are expected to use the `userState` object that is passed to the *MethodName*`Async` methods to distinguish among progress updates on multiple concurrent operations.</span></span>  
  
 <span data-ttu-id="733bb-186">Mohou nastat situace, ve kterých průběh podporovat více operací a každé vrátí na jiný ukazatel průběh.</span><span class="sxs-lookup"><span data-stu-id="733bb-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="733bb-187">V tomto případě jedné `ProgressChanged` událostí není vhodná, a můžete zvážit podpora více `ProgressChanged` události.</span><span class="sxs-lookup"><span data-stu-id="733bb-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="733bb-188">V takovém případě pomocí vzoru pro pojmenovávání z *MethodName* `ProgressChanged` pro každou *MethodName* `Async` metoda.</span><span class="sxs-lookup"><span data-stu-id="733bb-188">In this case use a naming pattern of *MethodName*`ProgressChanged` for each *MethodName*`Async` method.</span></span>  
  
 <span data-ttu-id="733bb-189">Dodržováním reporting průběh sémantiky popsané [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="733bb-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="733bb-190">Volitelně můžete poskytovat podporu pro vrácení přírůstkové výsledky</span><span class="sxs-lookup"><span data-stu-id="733bb-190">Optionally Provide Support for Returning Incremental Results</span></span>  
 <span data-ttu-id="733bb-191">Asynchronní operace někdy může vrátit přírůstkové výsledky před dokončením.</span><span class="sxs-lookup"><span data-stu-id="733bb-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="733bb-192">Existuje několik možností, které lze použít pro podporu tohoto scénáře.</span><span class="sxs-lookup"><span data-stu-id="733bb-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="733bb-193">Níže jsou uvedeny příklady.</span><span class="sxs-lookup"><span data-stu-id="733bb-193">Some examples follow.</span></span>  
  
### <a name="single-operation-class"></a><span data-ttu-id="733bb-194">Operace jedním – třída</span><span class="sxs-lookup"><span data-stu-id="733bb-194">Single-operation Class</span></span>  
 <span data-ttu-id="733bb-195">Pokud třídě podporuje pouze jeden asynchronní operaci, a že operace se bude moct vrátit přírůstkové výsledky, pak:</span><span class="sxs-lookup"><span data-stu-id="733bb-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>  
  
-   <span data-ttu-id="733bb-196">Rozšíření <xref:System.ComponentModel.ProgressChangedEventArgs> typu k provedení přírůstkových výsledných dat a definujte *MethodName* `ProgressChanged` událost s tuto rozšířenou data.</span><span class="sxs-lookup"><span data-stu-id="733bb-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a *MethodName*`ProgressChanged` event with this extended data.</span></span>  
  
-   <span data-ttu-id="733bb-197">Vyvolat to *MethodName* `ProgressChanged` událost, pokud je výsledek přírůstkové do sestavy.</span><span class="sxs-lookup"><span data-stu-id="733bb-197">Raise this *MethodName*`ProgressChanged` event when there is an incremental result to report.</span></span>  
  
 <span data-ttu-id="733bb-198">Toto řešení platí konkrétně pro třídu jedním. asynchronní operace, protože žádný problém s stejné událostí, ke kterým dochází k vrácení přírůstkové výsledky v "všechny operace", jako *MethodName* `ProgressChanged` událostí nemá.</span><span class="sxs-lookup"><span data-stu-id="733bb-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the *MethodName*`ProgressChanged` event does.</span></span>  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="733bb-199">Třída více operaci s homogenní přírůstkové výsledky</span><span class="sxs-lookup"><span data-stu-id="733bb-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>  
 <span data-ttu-id="733bb-200">V takovém případě třídě podporuje více asynchronní metody každý může vrácení přírůstkové výsledky, a tyto přírůstkové výsledky všechny mít stejný typ data.</span><span class="sxs-lookup"><span data-stu-id="733bb-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>  
  
 <span data-ttu-id="733bb-201">Postupujte podle modelu popsané výše pro třídy jedné operace, jako stejné <xref:System.EventArgs> struktura bude fungovat pro všechny přírůstkové výsledky.</span><span class="sxs-lookup"><span data-stu-id="733bb-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="733bb-202">Definování `ProgressChanged` událostí místo *MethodName* `ProgressChanged` událost, protože se vztahuje na více asynchronních metod.</span><span class="sxs-lookup"><span data-stu-id="733bb-202">Define a `ProgressChanged` event instead of a *MethodName*`ProgressChanged` event, since it applies to multiple asynchronous methods.</span></span>  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="733bb-203">Třída více operaci s heterogenní přírůstkové výsledky</span><span class="sxs-lookup"><span data-stu-id="733bb-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>  
 <span data-ttu-id="733bb-204">Pokud vaše třída podporuje více asynchronních metod, každý vrácení jiný typ dat, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="733bb-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>  
  
-   <span data-ttu-id="733bb-205">Samostatné sady přírůstkové výsledků sestavy průběhu sestav.</span><span class="sxs-lookup"><span data-stu-id="733bb-205">Separate your incremental result reporting from your progress reporting.</span></span>  
  
-   <span data-ttu-id="733bb-206">Definování samostatné *MethodName* `ProgressChanged` událost s příslušnou <xref:System.EventArgs> pro každou asynchronní metodu pro zpracování dat přírůstkové výsledek této metody.</span><span class="sxs-lookup"><span data-stu-id="733bb-206">Define a separate *MethodName*`ProgressChanged` event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>  
  
 <span data-ttu-id="733bb-207">Vyvolání této obslužné rutiny události ve vlákně, v příslušné, jak je popsáno v [osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="733bb-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="733bb-208">Zpracování Out a parametry Ref v metody</span><span class="sxs-lookup"><span data-stu-id="733bb-208">Handling Out and Ref Parameters in Methods</span></span>  
 <span data-ttu-id="733bb-209">I když použití `out` a `ref` se nedoporučuje v rozhraní .NET Framework, tady jsou obecně pravidel tak, aby použijte, pokud jsou přítomna:</span><span class="sxs-lookup"><span data-stu-id="733bb-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>  
  
 <span data-ttu-id="733bb-210">Synchronní metoda zadané *MethodName*:</span><span class="sxs-lookup"><span data-stu-id="733bb-210">Given a synchronous method *MethodName*:</span></span>  
  
-   <span data-ttu-id="733bb-211">`out`parametry, které *MethodName* by neměl být součástí *MethodName*`Async`.</span><span class="sxs-lookup"><span data-stu-id="733bb-211">`out` parameters to *MethodName* should not be part of *MethodName*`Async`.</span></span> <span data-ttu-id="733bb-212">Místo toho by měla být součástí *MethodName* `CompletedEventArgs` se stejným názvem jako jeho parametr ekvivalentní v *MethodName* (Pokud je vhodnější název).</span><span class="sxs-lookup"><span data-stu-id="733bb-212">Instead, they should be part of *MethodName*`CompletedEventArgs` with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
-   <span data-ttu-id="733bb-213">`ref`parametry, které *MethodName* mají zobrazit jako součást *MethodName*`Async`a jako součást *MethodName* `CompletedEventArgs` se stejným názvem jako jeho Parametr ekvivalentní v *MethodName* (Pokud je vhodnější název).</span><span class="sxs-lookup"><span data-stu-id="733bb-213">`ref` parameters to *MethodName* should appear as part of *MethodName*`Async`, and as part of *MethodName*`CompletedEventArgs` with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
 <span data-ttu-id="733bb-214">Například uděleno:</span><span class="sxs-lookup"><span data-stu-id="733bb-214">For example, given:</span></span>  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 <span data-ttu-id="733bb-215">Asynchronní metoda a jeho <xref:System.ComponentModel.AsyncCompletedEventArgs> třída bude vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="733bb-215">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="733bb-216">Viz také</span><span class="sxs-lookup"><span data-stu-id="733bb-216">See Also</span></span>  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [<span data-ttu-id="733bb-217">Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="733bb-217">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="733bb-218">Postupy: Spuštění operace na pozadí</span><span class="sxs-lookup"><span data-stu-id="733bb-218">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="733bb-219">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="733bb-219">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="733bb-220">Rozhodování, kdy implementovat asynchronní vzor založený na událostech</span><span class="sxs-lookup"><span data-stu-id="733bb-220">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="733bb-221">Vícevláknové programování s asynchronním vzorem založeným na událostech</span><span class="sxs-lookup"><span data-stu-id="733bb-221">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="733bb-222">Osvědčené postupy pro implementaci asynchronního vzoru založeného na událostech</span><span class="sxs-lookup"><span data-stu-id="733bb-222">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
