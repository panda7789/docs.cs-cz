---
title: 'Postupy: Připojení delegáta pomocí reflexe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe90542d1ba106dd52e8995afab298b4b9f69899
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644388"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="ef9c9-102">Postupy: Připojení delegáta pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="ef9c9-102">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="ef9c9-103">Při použití reflexe načtení a spuštění sestavení nelze použít jazykové funkce, jako C# `+=` operátor nebo Visual Basic [AddHandler – příkaz](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) k připojení události.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-103">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="ef9c9-104">Následující postupy ukazují, jak připojit existující metodu na událost tím, že získáme všechny nezbytné typy prostřednictvím reflexe a vytvoření dynamickou metodu pomocí operace reflection emit a zapojit ji až událost.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-104">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef9c9-105">Dalším způsobem, jak připojit delegát zpracování událostí, naleznete v části příklad kódu pro <xref:System.Reflection.EventInfo.AddEventHandler%2A> metodu <xref:System.Reflection.EventInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-105">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="ef9c9-106">K připojení delegáta pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="ef9c9-106">To hook up a delegate using reflection</span></span>  
  
1.  <span data-ttu-id="ef9c9-107">Načtení sestavení obsahující typ, který vyvolává události.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-107">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="ef9c9-108">Sestavení jsou obvykle načtena s <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-108">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ef9c9-109">Pro zjednodušení tento příklad používá odvozený formulář v nástrojích pro aktuální sestavení, takže <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metoda se používá k načtení aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-109">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2.  <span data-ttu-id="ef9c9-110">Získání <xref:System.Type> objekt představující typ a vytvořte její instanci typu.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-110">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="ef9c9-111"><xref:System.Activator.CreateInstance%28System.Type%29> Metoda se používá v následujícím kódu, protože formulář nemá výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-111">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a default constructor.</span></span> <span data-ttu-id="ef9c9-112">Existuje několik dalších přetížení <xref:System.Activator.CreateInstance%2A> metodu, která můžete použít, pokud typ při vytváření nemá výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-112">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a default constructor.</span></span> <span data-ttu-id="ef9c9-113">Nová instance se ukládá jako typ <xref:System.Object> udržovat fiction této není nic vědět o sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-113">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="ef9c9-114">(Reflexe umožňuje získat typy v sestavení bez znalosti jejich názvy předem.)</span><span class="sxs-lookup"><span data-stu-id="ef9c9-114">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3.  <span data-ttu-id="ef9c9-115">Získat <xref:System.Reflection.EventInfo> objekt představující události a použít <xref:System.Reflection.EventInfo.EventHandlerType%2A> vlastnost k získání typu delegát, pomocí něhož chcete zpracovat událost.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-115">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="ef9c9-116">V následujícím kódu <xref:System.Reflection.EventInfo> pro <xref:System.Windows.Forms.Control.Click> získat události.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-116">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4.  <span data-ttu-id="ef9c9-117">Získání <xref:System.Reflection.MethodInfo> objekt reprezentující metodu, která zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-117">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="ef9c9-118">Kód dokončení programu v oddíle Příklad dále v tomto tématu obsahuje metodu, která se shoduje se signaturou <xref:System.EventHandler> delegovat, která zpracovává <xref:System.Windows.Forms.Control.Click> události, ale dají vygenerovat také dynamických metod v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-118">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="ef9c9-119">Podrobnosti najdete v tématu souvisejícím postupu pro vygenerování obslužné rutiny události v době běhu pomocí dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-119">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5.  <span data-ttu-id="ef9c9-120">Vytvoření instance delegáta pomocí <xref:System.Delegate.CreateDelegate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-120">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="ef9c9-121">Tato metoda je statická (`Shared` v jazyce Visual Basic), takže je nutné zadat typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-121">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="ef9c9-122">Pomocí přetížení <xref:System.Delegate.CreateDelegate%2A> trvají <xref:System.Reflection.MethodInfo> se doporučuje.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-122">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6.  <span data-ttu-id="ef9c9-123">Získejte `add` přístupové metody a použít ho k připojení události.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-123">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="ef9c9-124">Všechny události mají `add` přístupového objektu a `remove` přístupový objekt, který jsou skryty pomocí syntaxe vysoké úrovně jazyků.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-124">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="ef9c9-125">Například C# používá `+=` k připojení události a jazyk Visual Basic používá operátor [AddHandler – příkaz](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ef9c9-125">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="ef9c9-126">Následující kód získá `add` přistupující objekt <xref:System.Windows.Forms.Control.Click> událostí a spustí ho s pozdní vazbou, předejte instanci delegáta.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-126">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="ef9c9-127">Argumenty musí být předán jako pole.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-127">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7.  <span data-ttu-id="ef9c9-128">Testovací událost.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-128">Test the event.</span></span> <span data-ttu-id="ef9c9-129">Následující kód ukazuje formulář definovaný v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-129">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="ef9c9-130">Kliknutí na formuláři vyvolá obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-130">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="ef9c9-131">Ke generování obslužné rutiny události v době běhu pomocí dynamické metody</span><span class="sxs-lookup"><span data-stu-id="ef9c9-131">To generate an event handler at run time by using a dynamic method</span></span>  
  
1.  <span data-ttu-id="ef9c9-132">Metody obslužné rutiny události mohou být generovány v době běhu pomocí zjednodušené dynamických metod a emitování reflexe.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-132">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="ef9c9-133">K vytvoření obslužné rutiny události, budete potřebovat návratový typ a typy parametrů delegáta.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-133">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="ef9c9-134">Ty můžete získat prozkoumáním delegáta `Invoke` metody.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-134">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="ef9c9-135">Následující kód používá `GetDelegateReturnType` a `GetDelegateParameterTypes` metody pro získání těchto informací.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-135">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="ef9c9-136">Kód pro tyto metody lze nalézt v oddílu příklad dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-136">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="ef9c9-137">Není nutné pojmenovat <xref:System.Reflection.Emit.DynamicMethod>, takže se dají použít prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-137">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="ef9c9-138">V následujícím kódu, posledním argumentem přidruží dynamickou metodu s aktuálním typem delegáta poskytuje přístup k všechny veřejné a soukromé členy `Example` třídy.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-138">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2.  <span data-ttu-id="ef9c9-139">Vygenerování těla metody.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-139">Generate a method body.</span></span> <span data-ttu-id="ef9c9-140">Tato metoda načte řetězec, volá přetížení <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metodu, která přebírá řetězec, zobrazí návratová hodnota ze zásobníku (protože obslužná rutina nemá žádný návratový typ) a vrátí.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-140">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="ef9c9-141">Další informace o generování dynamických metod najdete v tématu [jak: Definování a provádění dynamických metod](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ef9c9-141">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3.  <span data-ttu-id="ef9c9-142">Dokončení dynamickou metodu. voláním jeho <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-142">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="ef9c9-143">Použití `add` přístupový objekt pro přidání do seznamu vyvolání události, delegát.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-143">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4.  <span data-ttu-id="ef9c9-144">Testovací událost.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-144">Test the event.</span></span> <span data-ttu-id="ef9c9-145">Následující kód načte formulář definovaný v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-145">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="ef9c9-146">Kliknutí na formuláři vyvolá obslužnou rutinu předdefinované události a obslužná rutina události emitovaný.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-146">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="ef9c9-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef9c9-147">Example</span></span>  
 <span data-ttu-id="ef9c9-148">Následující příklad kódu ukazuje, jak připojit existující metodu na událost pomocí reflexe a také způsob použití <xref:System.Reflection.Emit.DynamicMethod> třídu pro generování metodu v době běhu a zapojit ji do události.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-148">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ef9c9-149">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ef9c9-149">Compiling the Code</span></span>  
  
-   <span data-ttu-id="ef9c9-150">Obsahuje kód jazyka C# `using` příkazy (`Imports` v jazyce Visual Basic) nezbytné pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-150">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="ef9c9-151">Žádné odkazy na další sestavení jsou požadovány pro kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-151">No additional assembly references are required for compiling from the command line.</span></span> <span data-ttu-id="ef9c9-152">V sadě Visual Studio musíte přidat odkaz na System.Windows.Forms.dll, protože v tomto příkladu je konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-152">In Visual Studio you must add a reference to System.Windows.Forms.dll because this example is a console application.</span></span>  
  
-   <span data-ttu-id="ef9c9-153">Kompilace kódu do příkazového řádku pomocí csc.exe a vbc.exe, cl.exe.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-153">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="ef9c9-154">Ke kompilaci kódu v sadě Visual Studio, umístěte ho do šablony projektu konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="ef9c9-154">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef9c9-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef9c9-155">See also</span></span>
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="ef9c9-156">Postupy: Definování a provádění dynamických metod</span><span class="sxs-lookup"><span data-stu-id="ef9c9-156">How to: Define and Execute Dynamic Methods</span></span>](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="ef9c9-157">Reflexe</span><span class="sxs-lookup"><span data-stu-id="ef9c9-157">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)
