---
title: 'Postupy: Připojení delegáta pomocí reflexe'
description: Podívejte se, jak připojit delegáta pomocí reflexe v rozhraní .NET. Připojení existující metody k události získáním potřebných typů prostřednictvím reflexe.
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
ms.openlocfilehash: b5d93efd278a53a4e6382f2321918e58ead55899
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865083"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="356bb-104">Postupy: Připojení delegáta pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="356bb-104">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="356bb-105">Použijete-li reflexi pro načtení a spuštění sestavení, nemůžete použít funkce jazyka, jako je operátor jazyka C# `+=` nebo [příkaz Visual Basic AddHandler](../../visual-basic/language-reference/statements/addhandler-statement.md) k zapojení událostí.</span><span class="sxs-lookup"><span data-stu-id="356bb-105">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="356bb-106">Následující postupy ukazují, jak připojit existující metodu k události tím, že získá všechny nezbytné typy prostřednictvím reflexe a jak vytvořit dynamickou metodu pomocí generování reflexe a připojit ji k události.</span><span class="sxs-lookup"><span data-stu-id="356bb-106">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="356bb-107">Další způsob, jak připojit delegáta zpracování událostí, naleznete v příkladu kódu pro <xref:System.Reflection.EventInfo.AddEventHandler%2A> metodu <xref:System.Reflection.EventInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="356bb-107">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="356bb-108">Připojení delegáta pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="356bb-108">To hook up a delegate using reflection</span></span>  
  
1. <span data-ttu-id="356bb-109">Načte sestavení, které obsahuje typ, který vyvolává události.</span><span class="sxs-lookup"><span data-stu-id="356bb-109">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="356bb-110">Sestavení jsou obvykle načtena pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="356bb-110">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="356bb-111">Chcete-li tento příklad jednoduché, je použit odvozený formulář v aktuálním sestavení, takže <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> Metoda slouží k načtení aktuálního sestavení.</span><span class="sxs-lookup"><span data-stu-id="356bb-111">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <span data-ttu-id="356bb-112">Získání <xref:System.Type> objektu představujícího typ a vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="356bb-112">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="356bb-113"><xref:System.Activator.CreateInstance%28System.Type%29>Metoda je použita v následujícím kódu, protože formulář obsahuje konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="356bb-113">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a parameterless constructor.</span></span> <span data-ttu-id="356bb-114">Existuje několik dalších přetížení <xref:System.Activator.CreateInstance%2A> metody, kterou můžete použít, pokud typ, který vytváříte, nemá konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="356bb-114">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a parameterless constructor.</span></span> <span data-ttu-id="356bb-115">Nová instance je uložena jako typ <xref:System.Object> pro zachování fiktivního, že pro sestavení není nic známé.</span><span class="sxs-lookup"><span data-stu-id="356bb-115">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="356bb-116">(Reflexe umožňuje získat typy v sestavení, aniž byste museli znát jejich názvy předem.)</span><span class="sxs-lookup"><span data-stu-id="356bb-116">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <span data-ttu-id="356bb-117">Získat <xref:System.Reflection.EventInfo> objekt reprezentující událost a použít <xref:System.Reflection.EventInfo.EventHandlerType%2A> vlastnost k získání typu delegáta použitého ke zpracování události.</span><span class="sxs-lookup"><span data-stu-id="356bb-117">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="356bb-118">V následujícím kódu <xref:System.Reflection.EventInfo> <xref:System.Windows.Forms.Control.Click> je získána pro událost.</span><span class="sxs-lookup"><span data-stu-id="356bb-118">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <span data-ttu-id="356bb-119">Získat <xref:System.Reflection.MethodInfo> objekt reprezentující metodu, která zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="356bb-119">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="356bb-120">Úplný kód programu v příkladu níže v tomto tématu obsahuje metodu, která odpovídá signatuře <xref:System.EventHandler> delegáta, který zpracovává <xref:System.Windows.Forms.Control.Click> událost, ale můžete také generovat dynamické metody za běhu.</span><span class="sxs-lookup"><span data-stu-id="356bb-120">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="356bb-121">Podrobnosti naleznete v doprovodné proceduře pro generování obslužné rutiny události v době běhu pomocí dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="356bb-121">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <span data-ttu-id="356bb-122">Vytvořte instanci delegáta pomocí <xref:System.Delegate.CreateDelegate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="356bb-122">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="356bb-123">Tato metoda je statická ( `Shared` v Visual Basic), proto je nutné zadat typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="356bb-123">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="356bb-124">Použití přetížení <xref:System.Delegate.CreateDelegate%2A> , které přijímá, <xref:System.Reflection.MethodInfo> je doporučeno.</span><span class="sxs-lookup"><span data-stu-id="356bb-124">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. <span data-ttu-id="356bb-125">Získat `add` přístupovou metodu a vyvolat ji pro zapojení události.</span><span class="sxs-lookup"><span data-stu-id="356bb-125">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="356bb-126">Všechny události mají `add` přistupující objekt a `remove` přistupující objekt, který je skryt syntaxí jazyků vysoké úrovně.</span><span class="sxs-lookup"><span data-stu-id="356bb-126">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="356bb-127">Například jazyk C# používá `+=` operátor k zavěšení událostí a Visual Basic používá [příkaz AddHandler](../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="356bb-127">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="356bb-128">Následující kód získá `add` přistupující objekt <xref:System.Windows.Forms.Control.Click> události a vyvolá pozdní vazbu s předáním do instance delegáta.</span><span class="sxs-lookup"><span data-stu-id="356bb-128">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="356bb-129">Argumenty musí být předány jako pole.</span><span class="sxs-lookup"><span data-stu-id="356bb-129">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. <span data-ttu-id="356bb-130">Otestujte událost.</span><span class="sxs-lookup"><span data-stu-id="356bb-130">Test the event.</span></span> <span data-ttu-id="356bb-131">Následující kód ukazuje formulář definovaný v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="356bb-131">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="356bb-132">Kliknutím na formulář se vyvolá obslužná rutina události.</span><span class="sxs-lookup"><span data-stu-id="356bb-132">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="356bb-133">Generování obslužné rutiny události v době běhu pomocí dynamické metody</span><span class="sxs-lookup"><span data-stu-id="356bb-133">To generate an event handler at run time by using a dynamic method</span></span>  
  
1. <span data-ttu-id="356bb-134">Metody obslužné rutiny události mohou být generovány v době běhu pomocí zjednodušených dynamických metod a generování reflexe.</span><span class="sxs-lookup"><span data-stu-id="356bb-134">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="356bb-135">Chcete-li vytvořit obslužnou rutinu události, budete potřebovat návratový typ a typy parametrů delegáta.</span><span class="sxs-lookup"><span data-stu-id="356bb-135">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="356bb-136">Ty lze získat prozkoumáním metody delegáta `Invoke` .</span><span class="sxs-lookup"><span data-stu-id="356bb-136">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="356bb-137">Následující kód používá `GetDelegateReturnType` `GetDelegateParameterTypes` metody a k získání těchto informací.</span><span class="sxs-lookup"><span data-stu-id="356bb-137">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="356bb-138">Kód pro tyto metody lze nalézt v části příklad dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="356bb-138">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="356bb-139">Není nutné pojmenovat <xref:System.Reflection.Emit.DynamicMethod> , aby bylo možné použít prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="356bb-139">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="356bb-140">V následujícím kódu poslední argument přidružuje dynamickou metodu k aktuálnímu typu, což dává delegátovi přístup ke všem veřejným a soukromým členům `Example` třídy.</span><span class="sxs-lookup"><span data-stu-id="356bb-140">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. <span data-ttu-id="356bb-141">Vygeneruje tělo metody.</span><span class="sxs-lookup"><span data-stu-id="356bb-141">Generate a method body.</span></span> <span data-ttu-id="356bb-142">Tato metoda načte řetězec, zavolá přetížení <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metody, která přijímá řetězec, vyvolá vrácenou hodnotu mimo zásobník (protože obslužná rutina nemá žádný návratový typ) a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="356bb-142">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="356bb-143">Další informace o generování dynamických metod naleznete v tématu [How to: Define and Execute Dynamic](how-to-define-and-execute-dynamic-methods.md)Methods.</span><span class="sxs-lookup"><span data-stu-id="356bb-143">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <span data-ttu-id="356bb-144">Dokončete dynamickou metodu voláním její <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="356bb-144">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="356bb-145">Pomocí `add` přístupového objektu přidejte delegáta do seznamu vyvolání pro událost.</span><span class="sxs-lookup"><span data-stu-id="356bb-145">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. <span data-ttu-id="356bb-146">Otestujte událost.</span><span class="sxs-lookup"><span data-stu-id="356bb-146">Test the event.</span></span> <span data-ttu-id="356bb-147">Následující kód načte formulář definovaný v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="356bb-147">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="356bb-148">Kliknutím na formulář se vyvolá předdefinovaná obslužná rutina události a obslužná rutina emitované události.</span><span class="sxs-lookup"><span data-stu-id="356bb-148">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="356bb-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="356bb-149">Example</span></span>  
 <span data-ttu-id="356bb-150">Následující příklad kódu ukazuje, jak připojit existující metodu k události pomocí reflexe a také jak použít <xref:System.Reflection.Emit.DynamicMethod> třídu k vygenerování metody v době běhu a jejímu zapojení do události.</span><span class="sxs-lookup"><span data-stu-id="356bb-150">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="356bb-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="356bb-151">See also</span></span>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="356bb-152">Postupy: Definování a provádění dynamických metod</span><span class="sxs-lookup"><span data-stu-id="356bb-152">How to: Define and Execute Dynamic Methods</span></span>](how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="356bb-153">Reflexe</span><span class="sxs-lookup"><span data-stu-id="356bb-153">Reflection</span></span>](reflection.md)
