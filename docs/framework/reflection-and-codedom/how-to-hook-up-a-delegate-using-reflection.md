---
title: "Postupy: Připojení delegáta pomocí reflexe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ff800eb78b07fc79193c2aa8cb71a461be2fc1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="d04ad-102">Postupy: Připojení delegáta pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="d04ad-102">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="d04ad-103">Pokud používáte reflexe načíst a spuštění sestavení, nelze použít jazykové funkce jako jazyka C# `+=` operátor nebo Visual Basic [AddHandler – příkaz](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) spojit události.</span><span class="sxs-lookup"><span data-stu-id="d04ad-103">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="d04ad-104">Následující postupy ukazují, jak spojit stávající metodu pro událost získáním všechny potřebné typy prostřednictvím reflexe a postup vytvoření dynamické metody pomocí reflexe emitování a propojte ho až událost.</span><span class="sxs-lookup"><span data-stu-id="d04ad-104">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d04ad-105">Pro další způsob spojit delegáta zpracování událostí, podívejte se na příklad kódu pro <xref:System.Reflection.EventInfo.AddEventHandler%2A> metodu <xref:System.Reflection.EventInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="d04ad-105">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="d04ad-106">Chcete-li připojení delegáta pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="d04ad-106">To hook up a delegate using reflection</span></span>  
  
1.  <span data-ttu-id="d04ad-107">Načtení sestavení, které obsahuje typ, který vyvolává události.</span><span class="sxs-lookup"><span data-stu-id="d04ad-107">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="d04ad-108">Sestavení jsou obvykle načíst pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="d04ad-108">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d04ad-109">Pro zjednodušení tento příklad používá odvozené formuláře v aktuální sestavení, proto <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metoda se používá k načtení aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="d04ad-109">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2.  <span data-ttu-id="d04ad-110">Získání <xref:System.Type> objekt představující typ a vytvořit instanci typu.</span><span class="sxs-lookup"><span data-stu-id="d04ad-110">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="d04ad-111"><xref:System.Activator.CreateInstance%28System.Type%29> Metoda se používá v následujícím kódu, protože formulář má výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d04ad-111">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a default constructor.</span></span> <span data-ttu-id="d04ad-112">Existuje několik dalších přetížení <xref:System.Activator.CreateInstance%2A> metoda, kterou můžete použít, pokud typ vytváříte nemá výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d04ad-112">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a default constructor.</span></span> <span data-ttu-id="d04ad-113">Nová instance je uložený jako typ <xref:System.Object> udržovat fiction se označuje tento není nic o sestavení.</span><span class="sxs-lookup"><span data-stu-id="d04ad-113">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="d04ad-114">(Reflexe umožňuje získat typy v sestavení bez znalosti jejich názvy předem.)</span><span class="sxs-lookup"><span data-stu-id="d04ad-114">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3.  <span data-ttu-id="d04ad-115">Získat <xref:System.Reflection.EventInfo> objekt reprezentující události a použít <xref:System.Reflection.EventInfo.EventHandlerType%2A> vlastnost k získání typu delegát používá ke zpracování události.</span><span class="sxs-lookup"><span data-stu-id="d04ad-115">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="d04ad-116">Následující kód <xref:System.Reflection.EventInfo> pro <xref:System.Windows.Forms.Control.Click> se získávají událostí.</span><span class="sxs-lookup"><span data-stu-id="d04ad-116">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4.  <span data-ttu-id="d04ad-117">Získání <xref:System.Reflection.MethodInfo> objektu, který představuje metodu, která zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="d04ad-117">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="d04ad-118">Kód dokončení programu v části Příklad později v tomto tématu obsahuje metodu, která odpovídá podpis <xref:System.EventHandler> delegovat, která zpracovává <xref:System.Windows.Forms.Control.Click> událostí, ale můžete také vygenerovat dynamických metod v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d04ad-118">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="d04ad-119">Podrobnosti najdete v tématu doprovodné postupu pro vytvoření obslužné rutiny události v době běhu pomocí dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="d04ad-119">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5.  <span data-ttu-id="d04ad-120">Vytvořte instanci delegáta pomocí <xref:System.Delegate.CreateDelegate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="d04ad-120">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="d04ad-121">Tato metoda je statická (`Shared` v jazyce Visual Basic), takže je nutné zadat typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="d04ad-121">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="d04ad-122">Pomocí přetížení <xref:System.Delegate.CreateDelegate%2A> trvají <xref:System.Reflection.MethodInfo> se doporučuje.</span><span class="sxs-lookup"><span data-stu-id="d04ad-122">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6.  <span data-ttu-id="d04ad-123">Získat `add` metoda přistupujícího objektu a vyvolání ho spojit události.</span><span class="sxs-lookup"><span data-stu-id="d04ad-123">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="d04ad-124">Mají všechny události `add` přistupujícího objektu a `remove` přistupujícího objektu, který skryty pomocí syntaxe vysoké úrovně jazyky.</span><span class="sxs-lookup"><span data-stu-id="d04ad-124">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="d04ad-125">Například C# používá `+=` operátor spojit události a používá jazyka Visual Basic [AddHandler – příkaz](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d04ad-125">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="d04ad-126">Následující kód získá `add` přistupujícího <xref:System.Windows.Forms.Control.Click> událostí a vyvolá ho pozdní vazbu předávání v instanci delegáta.</span><span class="sxs-lookup"><span data-stu-id="d04ad-126">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="d04ad-127">Argumenty, které musí být předán jako pole.</span><span class="sxs-lookup"><span data-stu-id="d04ad-127">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7.  <span data-ttu-id="d04ad-128">Otestujte události.</span><span class="sxs-lookup"><span data-stu-id="d04ad-128">Test the event.</span></span> <span data-ttu-id="d04ad-129">Následující kód ukazuje formuláře definované v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="d04ad-129">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="d04ad-130">Obslužné rutiny události kliknutí na formuláři vyvolá.</span><span class="sxs-lookup"><span data-stu-id="d04ad-130">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="d04ad-131">Generovat obslužné rutiny události v době běhu pomocí dynamické metody</span><span class="sxs-lookup"><span data-stu-id="d04ad-131">To generate an event handler at run time by using a dynamic method</span></span>  
  
1.  <span data-ttu-id="d04ad-132">Metody obslužné rutiny události může být generována v době běhu pomocí lightweight dynamických metod a emitování reflexe.</span><span class="sxs-lookup"><span data-stu-id="d04ad-132">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="d04ad-133">K vytvoření obslužné rutiny události, musíte návratový typ a typy parametrů delegáta.</span><span class="sxs-lookup"><span data-stu-id="d04ad-133">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="d04ad-134">To můžete získat tak, že prověří delegáta `Invoke` metoda.</span><span class="sxs-lookup"><span data-stu-id="d04ad-134">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="d04ad-135">Následující kód používá `GetDelegateReturnType` a `GetDelegateParameterTypes` metody pro získání těchto informací.</span><span class="sxs-lookup"><span data-stu-id="d04ad-135">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="d04ad-136">Kód pro tyto metody naleznete v části Příklad později v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="d04ad-136">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="d04ad-137">Není nutné pojmenovat <xref:System.Reflection.Emit.DynamicMethod>, takže lze prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="d04ad-137">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="d04ad-138">V následujícím kódu, poslední argument přidruží dynamické metoda má aktuální typ udělení delegát přístup k všechny veřejné a soukromé členy `Example` třídy.</span><span class="sxs-lookup"><span data-stu-id="d04ad-138">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2.  <span data-ttu-id="d04ad-139">Generovat těla metody.</span><span class="sxs-lookup"><span data-stu-id="d04ad-139">Generate a method body.</span></span> <span data-ttu-id="d04ad-140">Tato metoda načte řetězec, volá přetížení <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metoda, která přebírá řetězec, POP návratovou hodnotu ze zásobníku (protože obslužná rutina nemá žádný návratový typ) a vrátí.</span><span class="sxs-lookup"><span data-stu-id="d04ad-140">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="d04ad-141">Další informace o Emitování dynamických metod najdete v tématu [postupy: definování a spouštět dynamické metody](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d04ad-141">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3.  <span data-ttu-id="d04ad-142">Dokončení dynamické metoda voláním jeho <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="d04ad-142">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="d04ad-143">Použití `add` přistupujícího objektu delegát přidat do seznamu vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="d04ad-143">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4.  <span data-ttu-id="d04ad-144">Otestujte události.</span><span class="sxs-lookup"><span data-stu-id="d04ad-144">Test the event.</span></span> <span data-ttu-id="d04ad-145">Následující kód načte formuláře definované v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="d04ad-145">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="d04ad-146">Klepnutím na formulář vyvolá obslužnou rutinu události předdefinované a obslužné rutiny emitovaného události.</span><span class="sxs-lookup"><span data-stu-id="d04ad-146">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="d04ad-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="d04ad-147">Example</span></span>  
 <span data-ttu-id="d04ad-148">Následující příklad kódu ukazuje, jak spojit stávající metodu pro událost pomocí reflexe a také způsob použití <xref:System.Reflection.Emit.DynamicMethod> třídy emitování metodu v době běhu a propojte ho až událost.</span><span class="sxs-lookup"><span data-stu-id="d04ad-148">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d04ad-149">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d04ad-149">Compiling the Code</span></span>  
  
-   <span data-ttu-id="d04ad-150">Obsahuje kód jazyka C# `using` příkazy (`Imports` v jazyce Visual Basic) potřebné pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="d04ad-150">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="d04ad-151">Žádné odkazy na další sestavení jsou požadovány pro kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d04ad-151">No additional assembly references are required for compiling from the command line.</span></span> <span data-ttu-id="d04ad-152">V sadě Visual Studio musíte přidat odkaz na System.Windows.Forms.dll, protože v tomto příkladu je konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="d04ad-152">In Visual Studio you must add a reference to System.Windows.Forms.dll because this example is a console application.</span></span>  
  
-   <span data-ttu-id="d04ad-153">Kompilace kódu na příkazovém řádku pomocí csc.exe, vbc.exe nebo cl.exe.</span><span class="sxs-lookup"><span data-stu-id="d04ad-153">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="d04ad-154">Kompilace kódu v sadě Visual Studio, umístěte ho do šablony projektu konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="d04ad-154">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d04ad-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="d04ad-155">See Also</span></span>  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Emit.DynamicMethod>  
 <xref:System.Activator.CreateInstance%2A>  
 <xref:System.Delegate.CreateDelegate%2A>  
 [<span data-ttu-id="d04ad-156">Postupy: Definování a provádění dynamických metod</span><span class="sxs-lookup"><span data-stu-id="d04ad-156">How to: Define and Execute Dynamic Methods</span></span>](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)  
 [<span data-ttu-id="d04ad-157">Reflexe</span><span class="sxs-lookup"><span data-stu-id="d04ad-157">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)
