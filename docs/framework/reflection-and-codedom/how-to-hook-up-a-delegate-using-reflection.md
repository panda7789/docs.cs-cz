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
ms.openlocfilehash: d748d9f8bdd0b4d831880548d4aceb1c77a0b0c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180508"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="58aed-102">Postupy: Připojení delegáta pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="58aed-102">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="58aed-103">Při použití reflexe načíst a spustit sestavení, nelze použít `+=` funkce jazyka, jako je operátor C# nebo Visual Basic [AddHandler prohlášení](../../visual-basic/language-reference/statements/addhandler-statement.md) připojit události.</span><span class="sxs-lookup"><span data-stu-id="58aed-103">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="58aed-104">Následující postupy ukazují, jak připojit existující metodu k události získáním všech potřebných typů prostřednictvím reflexe a jak vytvořit dynamickou metodu pomocí odrazu vyzařovat a připojit k události.</span><span class="sxs-lookup"><span data-stu-id="58aed-104">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58aed-105">Pro jiný způsob, jak připojit delegáta zpracování událostí, <xref:System.Reflection.EventInfo.AddEventHandler%2A> naleznete <xref:System.Reflection.EventInfo> v příkladu kódu pro metodu třídy.</span><span class="sxs-lookup"><span data-stu-id="58aed-105">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="58aed-106">Připojení delegáta pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="58aed-106">To hook up a delegate using reflection</span></span>  
  
1. <span data-ttu-id="58aed-107">Načtěte sestavení, které obsahuje typ, který vyvolává události.</span><span class="sxs-lookup"><span data-stu-id="58aed-107">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="58aed-108">Sestavení jsou obvykle načteny <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodou.</span><span class="sxs-lookup"><span data-stu-id="58aed-108">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="58aed-109">Chcete-li zachovat tento příklad jednoduché, odvozený formulář v <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> aktuální sestavě se používá, takže metoda se používá k načtení aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="58aed-109">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <span data-ttu-id="58aed-110">Získejte <xref:System.Type> objekt představující typ a vytvořte instanci typu.</span><span class="sxs-lookup"><span data-stu-id="58aed-110">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="58aed-111">Metoda <xref:System.Activator.CreateInstance%28System.Type%29> se používá v následujícím kódu, protože formulář má konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="58aed-111">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a parameterless constructor.</span></span> <span data-ttu-id="58aed-112">Existuje několik dalších přetížení <xref:System.Activator.CreateInstance%2A> metody, které můžete použít, pokud typ, který vytváříte nemá konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="58aed-112">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a parameterless constructor.</span></span> <span data-ttu-id="58aed-113">Nová instance je uložena jako typ <xref:System.Object> zachovat fikci, že nic není známo o sestavení.</span><span class="sxs-lookup"><span data-stu-id="58aed-113">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="58aed-114">(Reflexe umožňuje získat typy v sestavení bez znalosti jejich názvy předem.)</span><span class="sxs-lookup"><span data-stu-id="58aed-114">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <span data-ttu-id="58aed-115">Získejte <xref:System.Reflection.EventInfo> objekt představující událost a <xref:System.Reflection.EventInfo.EventHandlerType%2A> pomocí vlastnosti získat typ delegáta slouží ke zpracování události.</span><span class="sxs-lookup"><span data-stu-id="58aed-115">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="58aed-116">V následujícím kódu <xref:System.Reflection.EventInfo> je <xref:System.Windows.Forms.Control.Click> získán a for the event.</span><span class="sxs-lookup"><span data-stu-id="58aed-116">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <span data-ttu-id="58aed-117">Získejte <xref:System.Reflection.MethodInfo> objekt představující metodu, která zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="58aed-117">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="58aed-118">Úplný kód programu v části Příklad dále v tomto tématu <xref:System.EventHandler> obsahuje metodu, <xref:System.Windows.Forms.Control.Click> která odpovídá podpisu delegáta, který zpracovává událost, ale můžete také generovat dynamické metody za běhu.</span><span class="sxs-lookup"><span data-stu-id="58aed-118">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="58aed-119">Podrobnosti naleznete v doprovodném postupu, pro generování obslužné rutiny události za běhu pomocí dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="58aed-119">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <span data-ttu-id="58aed-120">Vytvořte instanci delegáta <xref:System.Delegate.CreateDelegate%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="58aed-120">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="58aed-121">Tato metoda je`Shared` statická ( v jazyce Visual Basic), takže musí být zadán typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="58aed-121">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="58aed-122">Použití <xref:System.Delegate.CreateDelegate%2A> přetížení, které se <xref:System.Reflection.MethodInfo> doporučuje.</span><span class="sxs-lookup"><span data-stu-id="58aed-122">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. <span data-ttu-id="58aed-123">Získejte `add` přistupující metodu a vyvolat ji připojit událost.</span><span class="sxs-lookup"><span data-stu-id="58aed-123">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="58aed-124">Všechny události `add` mají přistupující objekt a přistupující `remove` objekt, které jsou skryty syntaxí jazyků vysoké úrovně.</span><span class="sxs-lookup"><span data-stu-id="58aed-124">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="58aed-125">Například C# používá `+=` operátor k připojení událostí a Visual Basic používá [AddHandler prohlášení](../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="58aed-125">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="58aed-126">Následující kód získá `add` přistupující ho <xref:System.Windows.Forms.Control.Click> události a vyvolá ji pozdní vazbu, předávání v instanci delegáta.</span><span class="sxs-lookup"><span data-stu-id="58aed-126">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="58aed-127">Argumenty musí být předány jako pole.</span><span class="sxs-lookup"><span data-stu-id="58aed-127">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. <span data-ttu-id="58aed-128">Otestujte událost.</span><span class="sxs-lookup"><span data-stu-id="58aed-128">Test the event.</span></span> <span data-ttu-id="58aed-129">Následující kód zobrazuje formulář definovaný v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="58aed-129">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="58aed-130">Klepnutím na formulář vyvoláte obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="58aed-130">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="58aed-131">Generování obslužné rutiny události za běhu pomocí dynamické metody</span><span class="sxs-lookup"><span data-stu-id="58aed-131">To generate an event handler at run time by using a dynamic method</span></span>  
  
1. <span data-ttu-id="58aed-132">Metody obslužné rutiny událostí lze generovat za běhu pomocí zjednodušené dynamické metody a odraz emit.</span><span class="sxs-lookup"><span data-stu-id="58aed-132">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="58aed-133">Chcete-li vytvořit obslužnou rutinu události, potřebujete návratový typ a typy parametrů delegáta.</span><span class="sxs-lookup"><span data-stu-id="58aed-133">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="58aed-134">Ty lze získat kontrolou metody delegáta. `Invoke`</span><span class="sxs-lookup"><span data-stu-id="58aed-134">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="58aed-135">Následující kód používá `GetDelegateReturnType` `GetDelegateParameterTypes` metody a k získání těchto informací.</span><span class="sxs-lookup"><span data-stu-id="58aed-135">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="58aed-136">Kód pro tyto metody naleznete v části Příklad dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="58aed-136">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="58aed-137">Není nutné pojmenovat <xref:System.Reflection.Emit.DynamicMethod>, takže lze použít prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="58aed-137">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="58aed-138">V následujícím kódu poslední argument přidruží dynamickou metodu k aktuálnímu typu a poskytuje `Example` delegátovi přístup všem veřejným a soukromým členům třídy.</span><span class="sxs-lookup"><span data-stu-id="58aed-138">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. <span data-ttu-id="58aed-139">Generovat tělo metody.</span><span class="sxs-lookup"><span data-stu-id="58aed-139">Generate a method body.</span></span> <span data-ttu-id="58aed-140">Tato metoda načte řetězec, volá <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> přetížení metody, která přebírá řetězec, vyskočí vrácená hodnota ze zásobníku (protože obslužná rutina nemá žádný návratový typ) a vrátí.</span><span class="sxs-lookup"><span data-stu-id="58aed-140">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="58aed-141">Další informace o vyzařování dynamických metod naleznete v [tématu How to: Define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="58aed-141">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <span data-ttu-id="58aed-142">Dokončete dynamickou metodu voláním její <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="58aed-142">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="58aed-143">Pomocí `add` přistupujícího seznamu přidejte delegáta do seznamu vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="58aed-143">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. <span data-ttu-id="58aed-144">Otestujte událost.</span><span class="sxs-lookup"><span data-stu-id="58aed-144">Test the event.</span></span> <span data-ttu-id="58aed-145">Následující kód načte formulář definovaný v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="58aed-145">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="58aed-146">Kliknutím na formulář vyvoláte předdefinovanou obslužnou rutinu události i eemitovní obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="58aed-146">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="58aed-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="58aed-147">Example</span></span>  
 <span data-ttu-id="58aed-148">Následující příklad kódu ukazuje, jak připojit existující metodu k události pomocí <xref:System.Reflection.Emit.DynamicMethod> reflexe a také jak použít třídu k vyzařování metody za běhu a připojit ji k události.</span><span class="sxs-lookup"><span data-stu-id="58aed-148">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="58aed-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="58aed-149">See also</span></span>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="58aed-150">Postupy: Definování a provádění dynamických metod</span><span class="sxs-lookup"><span data-stu-id="58aed-150">How to: Define and Execute Dynamic Methods</span></span>](how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="58aed-151">Reflexe</span><span class="sxs-lookup"><span data-stu-id="58aed-151">Reflection</span></span>](reflection.md)
