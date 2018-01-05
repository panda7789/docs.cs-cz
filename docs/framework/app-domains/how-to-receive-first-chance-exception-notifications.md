---
title: "Postupy: Přijímání oznámení o první odpovídající výjimce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- first-chance exception notifications
- exceptions, first chance notifications
ms.assetid: 66f002b8-a97d-4a6e-a503-2cec01689113
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8c98f8a1f09488bb2d93c4fda531f695354059a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-receive-first-chance-exception-notifications"></a><span data-ttu-id="58a05-102">Postupy: Přijímání oznámení o první odpovídající výjimce</span><span class="sxs-lookup"><span data-stu-id="58a05-102">How to: Receive First-Chance Exception Notifications</span></span>
<span data-ttu-id="58a05-103"><xref:System.AppDomain.FirstChanceException> Události <xref:System.AppDomain> třída umožňuje přijímat oznámení, že byla vyvolána výjimka, před common language runtime začne hledat obslužné rutiny výjimek.</span><span class="sxs-lookup"><span data-stu-id="58a05-103">The <xref:System.AppDomain.FirstChanceException> event of the <xref:System.AppDomain> class lets you receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
 <span data-ttu-id="58a05-104">Událost se vyvolá na úrovni domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="58a05-104">The event is raised at the application domain level.</span></span> <span data-ttu-id="58a05-105">Podproces provádění mohou procházet několik domén aplikace, tak v jiné doméně aplikace může zpracovávat výjimka, která je neošetřená v jedné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="58a05-105">A thread of execution can pass through multiple application domains, so an exception that is unhandled in one application domain could be handled in another application domain.</span></span> <span data-ttu-id="58a05-106">Oznámení dochází v každé doméně aplikace, který byl přidán obslužnou rutinu události, dokud doménu aplikace ošetří výjimku.</span><span class="sxs-lookup"><span data-stu-id="58a05-106">The notification occurs in each application domain that has added a handler for the event, until an application domain handles the exception.</span></span>  
  
 <span data-ttu-id="58a05-107">Postupy a příklady v tomto článku ukazují, jak dostávat oznámení o první odpovídající výjimce v jednoduchý program, který má jednu doménu aplikace a v doméně aplikace, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="58a05-107">The procedures and examples in this article show how to receive first-chance exception notifications in a simple program that has one application domain, and in an application domain that you create.</span></span>  
  
 <span data-ttu-id="58a05-108">Složitější příklad, který obsahuje několik domén aplikace, podívejte se příklad <xref:System.AppDomain.FirstChanceException> událostí.</span><span class="sxs-lookup"><span data-stu-id="58a05-108">For a more complex example that spans several application domains, see the example for the <xref:System.AppDomain.FirstChanceException> event.</span></span>  
  
## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a><span data-ttu-id="58a05-109">Příjem oznámení první odpovídající výjimce ve výchozí doméně aplikace</span><span class="sxs-lookup"><span data-stu-id="58a05-109">Receiving First-Chance Exception Notifications in the Default Application Domain</span></span>  
 <span data-ttu-id="58a05-110">V následujícím postupu, vstupní bod pro aplikaci `Main()` metoda, běží ve výchozí doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="58a05-110">In the following procedure, the entry point for the application, the `Main()` method, runs in the default application domain.</span></span>  
  
#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a><span data-ttu-id="58a05-111">K předvedení první odpovídající výjimce oznámení ve výchozí doméně aplikace</span><span class="sxs-lookup"><span data-stu-id="58a05-111">To demonstrate first-chance exception notifications in the default application domain</span></span>  
  
1.  <span data-ttu-id="58a05-112">Definování obslužné rutiny události pro <xref:System.AppDomain.FirstChanceException> událost, pomocí lambda funkce a připojte ji k události.</span><span class="sxs-lookup"><span data-stu-id="58a05-112">Define an event handler for the <xref:System.AppDomain.FirstChanceException> event, using a lambda function, and attach it to the event.</span></span> <span data-ttu-id="58a05-113">V tomto příkladu obslužné rutiny události vytiskne název domény aplikace, kde byla zpracována událost a v výjimky <xref:System.Exception.Message%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="58a05-113">In this example, the event handler prints the name of the application domain where the event was handled and the exception's <xref:System.Exception.Message%2A> property.</span></span>  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]  
  
2.  <span data-ttu-id="58a05-114">Způsobí výjimku a zachyťte ji.</span><span class="sxs-lookup"><span data-stu-id="58a05-114">Throw an exception and catch it.</span></span> <span data-ttu-id="58a05-115">Před běhové prostředí vyhledává obslužná rutina výjimky <xref:System.AppDomain.FirstChanceException> zobrazí zprávu a je vyvolána událost.</span><span class="sxs-lookup"><span data-stu-id="58a05-115">Before the runtime locates the exception handler, the <xref:System.AppDomain.FirstChanceException> event is raised and displays a message.</span></span> <span data-ttu-id="58a05-116">Tato zpráva je následován zprávu, která se zobrazí při obslužná rutina výjimky.</span><span class="sxs-lookup"><span data-stu-id="58a05-116">This message is followed by the message that is displayed by the exception handler.</span></span>  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]  
  
3.  <span data-ttu-id="58a05-117">Způsobí výjimku, ale není catch.</span><span class="sxs-lookup"><span data-stu-id="58a05-117">Throw an exception, but do not catch it.</span></span> <span data-ttu-id="58a05-118">Před běhové prostředí vyhledává obslužné rutiny výjimky <xref:System.AppDomain.FirstChanceException> událost se vyvolá a zobrazí zprávu.</span><span class="sxs-lookup"><span data-stu-id="58a05-118">Before the runtime looks for an exception handler, the <xref:System.AppDomain.FirstChanceException> event is raised and displays a message.</span></span> <span data-ttu-id="58a05-119">Neexistuje žádná obslužná rutina výjimky, takže aplikace se ukončí.</span><span class="sxs-lookup"><span data-stu-id="58a05-119">There is no exception handler, so the application terminates.</span></span>  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]  
  
     <span data-ttu-id="58a05-120">Kód, který se zobrazí v první tři kroky tohoto postupu, tvoří úplnou konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="58a05-120">The code that is shown in the first three steps of this procedure forms a complete console application.</span></span> <span data-ttu-id="58a05-121">Výstup z aplikace se liší v závislosti na název souboru .exe, protože název výchozí doméně aplikace se skládá z název a příponu souboru .exe.</span><span class="sxs-lookup"><span data-stu-id="58a05-121">The output from the application varies, depending on the name of the .exe file, because the name of the default application domain consists of the name and extension of the .exe file.</span></span> <span data-ttu-id="58a05-122">Viz následující ukázka výstupu.</span><span class="sxs-lookup"><span data-stu-id="58a05-122">See the following for sample output.</span></span>  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]  
  
## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a><span data-ttu-id="58a05-123">Příjem oznámení první odpovídající výjimce v jiné doméně aplikace</span><span class="sxs-lookup"><span data-stu-id="58a05-123">Receiving First-Chance Exception Notifications in Another Application Domain</span></span>  
 <span data-ttu-id="58a05-124">Pokud váš program obsahuje více než jednu doménu aplikace, můžete vybrat, které aplikační domény přijímat oznámení.</span><span class="sxs-lookup"><span data-stu-id="58a05-124">If your program contains more than one application domain, you can choose which application domains receive notifications.</span></span>  
  
#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a><span data-ttu-id="58a05-125">Pro příjem oznámení první odpovídající výjimce v doméně aplikace, kterou vytvoříte</span><span class="sxs-lookup"><span data-stu-id="58a05-125">To receive first-chance exception notifications in an application domain that you create</span></span>  
  
1.  <span data-ttu-id="58a05-126">Definování obslužné rutiny události pro <xref:System.AppDomain.FirstChanceException> událostí.</span><span class="sxs-lookup"><span data-stu-id="58a05-126">Define an event handler for the <xref:System.AppDomain.FirstChanceException> event.</span></span> <span data-ttu-id="58a05-127">Tento příklad používá `static` – metoda (`Shared` metody v jazyce Visual Basic), vytiskne název domény aplikace, kde byla zpracována událost a v výjimky <xref:System.Exception.Message%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="58a05-127">This example uses a `static` method (`Shared` method in Visual Basic) that prints the name of the application domain where the event was handled and the exception's <xref:System.Exception.Message%2A> property.</span></span>  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]  
  
2.  <span data-ttu-id="58a05-128">Vytvoření domény aplikace a přidejte obslužné rutiny události pro <xref:System.AppDomain.FirstChanceException> události pro tuto doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="58a05-128">Create an application domain and add the event handler to the <xref:System.AppDomain.FirstChanceException> event for that application domain.</span></span> <span data-ttu-id="58a05-129">V tomto příkladu je název domény aplikace `AD1`.</span><span class="sxs-lookup"><span data-stu-id="58a05-129">In this example, the application domain is named `AD1`.</span></span>  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]  
  
     <span data-ttu-id="58a05-130">Tato událost ve výchozí doméně aplikace můžete zpracovat stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="58a05-130">You can handle this event in the default application domain in the same way.</span></span> <span data-ttu-id="58a05-131">Použití `static` (`Shared` v jazyce Visual Basic) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> vlastnost `Main()` získat odkaz na výchozí doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="58a05-131">Use the `static` (`Shared` in Visual Basic) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property in `Main()` to get a reference to the default application domain.</span></span>  
  
#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a><span data-ttu-id="58a05-132">K předvedení první odpovídající výjimce oznámení v doméně aplikace</span><span class="sxs-lookup"><span data-stu-id="58a05-132">To demonstrate first-chance exception notifications in the application domain</span></span>  
  
1.  <span data-ttu-id="58a05-133">Vytvoření `Worker` objekt v doméně aplikace, kterou jste vytvořili v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="58a05-133">Create a `Worker` object in the application domain that you created in the previous procedure.</span></span> <span data-ttu-id="58a05-134">`Worker` Třídy musí být veřejná a musí být odvozeny od <xref:System.MarshalByRefObject>, jak je znázorněno v příkladu na konci tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="58a05-134">The `Worker` class must be public, and must derive from <xref:System.MarshalByRefObject>, as shown in the complete example at the end of this article.</span></span>  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]  
  
2.  <span data-ttu-id="58a05-135">Volání metody `Worker` objekt, který vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="58a05-135">Call a method of the `Worker` object that throws an exception.</span></span> <span data-ttu-id="58a05-136">V tomto příkladu `Thrower` metoda je volána dvakrát.</span><span class="sxs-lookup"><span data-stu-id="58a05-136">In this example, the `Thrower` method is called twice.</span></span> <span data-ttu-id="58a05-137">První argument metoda je `true`, což způsobí, že metoda zachytí svou vlastní výjimku.</span><span class="sxs-lookup"><span data-stu-id="58a05-137">The first time, the method argument is `true`, which causes the method to catch its own exception.</span></span> <span data-ttu-id="58a05-138">Při druhém argument je `false`a `Main()` metoda zachytí výjimky ve výchozí doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="58a05-138">The second time, the argument is `false`, and the `Main()` method catches the exception in the default application domain.</span></span>  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]  
  
3.  <span data-ttu-id="58a05-139">Umístěte kód `Thrower` metoda řídit, jestli tato metoda obsluhuje svou vlastní výjimku.</span><span class="sxs-lookup"><span data-stu-id="58a05-139">Place code in the `Thrower` method to control whether the method handles its own exception.</span></span>  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="58a05-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="58a05-140">Example</span></span>  
 <span data-ttu-id="58a05-141">Následující příklad vytvoří doménu aplikace s názvem `AD1` a přidá obslužné rutiny události do domény aplikace <xref:System.AppDomain.FirstChanceException> událostí.</span><span class="sxs-lookup"><span data-stu-id="58a05-141">The following example creates an application domain named `AD1` and adds an event handler to the application domain's <xref:System.AppDomain.FirstChanceException> event.</span></span> <span data-ttu-id="58a05-142">V příkladu se vytváří instance `Worker` třídy v doméně aplikace a volá metodu pojmenovanou `Thrower` , vyvolá <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="58a05-142">The example creates an instance of the `Worker` class in the application domain, and calls a method named `Thrower` that throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="58a05-143">V závislosti na hodnotě argumentu metoda buď zachytí výjimky, nebo selže se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="58a05-143">Depending on the value of its argument, the method either catches the exception or fails to handle it.</span></span>  
  
 <span data-ttu-id="58a05-144">Pokaždé, když `Thrower` metoda vyvolá výjimku `AD1`, <xref:System.AppDomain.FirstChanceException> událost se vyvolá v `AD1`, a zobrazí zprávu, obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="58a05-144">Each time the `Thrower` method throws an exception in `AD1`, the <xref:System.AppDomain.FirstChanceException> event is raised in `AD1`, and the event handler displays a message.</span></span> <span data-ttu-id="58a05-145">Modul runtime pak hledá obslužnou rutinu výjimky.</span><span class="sxs-lookup"><span data-stu-id="58a05-145">The runtime then looks for an exception handler.</span></span> <span data-ttu-id="58a05-146">V prvním případě je obslužná rutina výjimky nalezena v `AD1`.</span><span class="sxs-lookup"><span data-stu-id="58a05-146">In the first case, the exception handler is found in `AD1`.</span></span> <span data-ttu-id="58a05-147">V druhém případě je výjimka ošetřena v `AD1`a místo toho je zachycena ve výchozí doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="58a05-147">In the second case, the exception is unhandled in `AD1`, and instead is caught in the default application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58a05-148">Název výchozí doméně aplikace je stejný jako název spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="58a05-148">The name of the default application domain is the same as the name of the executable.</span></span>  
  
 <span data-ttu-id="58a05-149">Pokud přidáte obslužnou rutinu pro <xref:System.AppDomain.FirstChanceException> je událost, která má výchozí doménu aplikace, událost vyvolána a zpracovává než výchozí doméně aplikace ošetří výjimku.</span><span class="sxs-lookup"><span data-stu-id="58a05-149">If you add a handler for the <xref:System.AppDomain.FirstChanceException> event to the default application domain, the event is raised and handled before the default application domain handles the exception.</span></span> <span data-ttu-id="58a05-150">Chcete-li najdete v článku, přidejte kód C# `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (v jazyce Visual Basic `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`) na začátku `Main()`.</span><span class="sxs-lookup"><span data-stu-id="58a05-150">To see this, add the C# code `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (in Visual Basic, `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`) at the beginning of `Main()`.</span></span>  
  
 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="58a05-151">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="58a05-151">Compiling the Code</span></span>  
  
-   <span data-ttu-id="58a05-152">V tomto příkladu je aplikace příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="58a05-152">This example is a command-line application.</span></span> <span data-ttu-id="58a05-153">Pro zkompilování a spuštění tohoto kódu [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], přidejte kód C# `Console.ReadLine();` (v jazyce Visual Basic `Console.ReadLine()`) na konci `Main()`, aby se zabránilo příkazové okno Ukončit předtím, než si můžete přečíst výstup.</span><span class="sxs-lookup"><span data-stu-id="58a05-153">To compile and run this code in [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], add the C# code `Console.ReadLine();` (in Visual Basic, `Console.ReadLine()`) at the end of `Main()`, to prevent the command window from closing before you can read the output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58a05-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="58a05-154">See Also</span></span>  
 <xref:System.AppDomain.FirstChanceException>
