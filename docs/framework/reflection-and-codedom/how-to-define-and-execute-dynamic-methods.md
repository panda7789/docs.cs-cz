---
title: 'Postupy: Definování a provádění dynamických metod'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17bc7c417980c0850788f082ebb6e810fd0c53d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333298"
---
# <a name="how-to-define-and-execute-dynamic-methods"></a><span data-ttu-id="48c55-102">Postupy: Definování a provádění dynamických metod</span><span class="sxs-lookup"><span data-stu-id="48c55-102">How to: Define and Execute Dynamic Methods</span></span>
<span data-ttu-id="48c55-103">Následující postupy ukazují, jak definovat a spustí jednoduchou dynamickou metodu a dynamická metoda svázána s instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="48c55-103">The following procedures show how to define and execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span> <span data-ttu-id="48c55-104">Další informace o dynamické metody, naleznete v tématu <xref:System.Reflection.Emit.DynamicMethod> třídy a [emitování dynamické metody scénáře reflexe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="48c55-104">For more information on dynamic methods, see the <xref:System.Reflection.Emit.DynamicMethod> class and [Reflection Emit Dynamic Method Scenarios](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100)).</span></span>  
  
### <a name="to-define-and-execute-a-dynamic-method"></a><span data-ttu-id="48c55-105">Definování a spouštění dynamické – metoda</span><span class="sxs-lookup"><span data-stu-id="48c55-105">To define and execute a dynamic method</span></span>  
  
1. <span data-ttu-id="48c55-106">Deklarujte typ delegáta se vykonat metodu.</span><span class="sxs-lookup"><span data-stu-id="48c55-106">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="48c55-107">Zvažte, chcete-li minimalizovat počet typy delegátů, které je potřeba deklarovat pomocí obecného delegáta.</span><span class="sxs-lookup"><span data-stu-id="48c55-107">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="48c55-108">Následující kód deklaruje delegáta dva typy, které by mohly být použity `SquareIt` metoda a jeden z nich je obecný.</span><span class="sxs-lookup"><span data-stu-id="48c55-108">The following code declares two delegate types that could be used for the `SquareIt` method, and one of them is generic.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2. <span data-ttu-id="48c55-109">Vytvořte pole, která určuje typy parametrů pro dynamickou metodu.</span><span class="sxs-lookup"><span data-stu-id="48c55-109">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="48c55-110">V tomto příkladu je jediným parametrem `int` (`Integer` v jazyce Visual Basic), takže pole obsahuje pouze jeden element.</span><span class="sxs-lookup"><span data-stu-id="48c55-110">In this example, the only parameter is an `int` (`Integer` in Visual Basic), so the array has only one element.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3. <span data-ttu-id="48c55-111">Vytvoření <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="48c55-111">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="48c55-112">V tomto příkladu je pojmenována metodu `SquareIt`.</span><span class="sxs-lookup"><span data-stu-id="48c55-112">In this example the method is named `SquareIt`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="48c55-113">Není nutné pojmenovat dynamických metod a není možné vyvolat podle názvu.</span><span class="sxs-lookup"><span data-stu-id="48c55-113">It is not necessary to give dynamic methods names, and they cannot be invoked by name.</span></span> <span data-ttu-id="48c55-114">Více dynamické metody mohou mít stejný název.</span><span class="sxs-lookup"><span data-stu-id="48c55-114">Multiple dynamic methods can have the same name.</span></span> <span data-ttu-id="48c55-115">Ale název se zobrazí v zásobnících volání a může být užitečné pro ladění.</span><span class="sxs-lookup"><span data-stu-id="48c55-115">However, the name appears in call stacks and can be useful for debugging.</span></span>  
  
     <span data-ttu-id="48c55-116">Typ vrácené hodnoty je určen jako `long`.</span><span class="sxs-lookup"><span data-stu-id="48c55-116">The type of the return value is specified as `long`.</span></span> <span data-ttu-id="48c55-117">Metoda je spojen s modulem, který obsahuje `Example` třídu, která obsahuje příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="48c55-117">The method is associated with the module that contains the `Example` class, which contains the example code.</span></span> <span data-ttu-id="48c55-118">Jakýkoli načíst modul by mohl být specifikován.</span><span class="sxs-lookup"><span data-stu-id="48c55-118">Any loaded module could be specified.</span></span> <span data-ttu-id="48c55-119">Dynamická metoda funguje jako úroveň modulu `static` – metoda (`Shared` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="48c55-119">The dynamic method acts like a module-level `static` method (`Shared` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4. <span data-ttu-id="48c55-120">Vygenerování těla metody.</span><span class="sxs-lookup"><span data-stu-id="48c55-120">Emit the method body.</span></span> <span data-ttu-id="48c55-121">V tomto příkladu <xref:System.Reflection.Emit.ILGenerator> objekt se používá ke generování Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="48c55-121">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="48c55-122">Můžete také <xref:System.Reflection.Emit.DynamicILInfo> objektu můžete použít ve spojení s nespravovaným kódem generátorů ke generování tělo metody <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="48c55-122">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="48c55-123">Jazyk MSIL v tomto příkladě načte argument, který je `int`, do zásobníku, převede jej na `long`, duplicitní položky `long`a součin dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="48c55-123">The MSIL in this example loads the argument, which is an `int`, onto the stack, converts it to a `long`, duplicates the `long`, and multiplies the two numbers.</span></span> <span data-ttu-id="48c55-124">Tak zůstanou ve čtverci výsledek v zásobníku a vše, co tato metoda má udělat je vrácená.</span><span class="sxs-lookup"><span data-stu-id="48c55-124">This leaves the squared result on the stack, and all the method has to do is return.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5. <span data-ttu-id="48c55-125">Vytvoření instance delegáta (deklaruje se v kroku 1), který představuje dynamickou metodu. voláním <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="48c55-125">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="48c55-126">Vytvoření delegáta je metoda dokončena a žádné další pokusy o změnit metodu – například přidat další jazyk MSIL, jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="48c55-126">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span> <span data-ttu-id="48c55-127">Následující kód vytvoří delegát a vyvolá, pomocí obecného delegáta.</span><span class="sxs-lookup"><span data-stu-id="48c55-127">The following code creates the delegate and invokes it, using a generic delegate.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a><span data-ttu-id="48c55-128">Definování a spouštění dynamickou metodu, která je vázána na objekt</span><span class="sxs-lookup"><span data-stu-id="48c55-128">To define and execute a dynamic method that is bound to an object</span></span>  
  
1. <span data-ttu-id="48c55-129">Deklarujte typ delegáta se vykonat metodu.</span><span class="sxs-lookup"><span data-stu-id="48c55-129">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="48c55-130">Zvažte, chcete-li minimalizovat počet typy delegátů, které je potřeba deklarovat pomocí obecného delegáta.</span><span class="sxs-lookup"><span data-stu-id="48c55-130">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="48c55-131">Následující kód deklaruje typ obecného delegátu, který je možné spustit libovolnou metodu s jedním parametrem a návratovou hodnotu, nebo metodu se dvěma parametry a návratové hodnoty, když je delegát je vázán na objekt.</span><span class="sxs-lookup"><span data-stu-id="48c55-131">The following code declares a generic delegate type that can be used to execute any method with one parameter and a return value, or a method with two parameters and a return value if the delegate is bound to an object.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2. <span data-ttu-id="48c55-132">Vytvořte pole, která určuje typy parametrů pro dynamickou metodu.</span><span class="sxs-lookup"><span data-stu-id="48c55-132">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="48c55-133">Pokud delegát představující metodu je vázán na objekt, první parametr musí odpovídat typu, který je vázán na delegáta.</span><span class="sxs-lookup"><span data-stu-id="48c55-133">If the delegate representing the method is to be bound to an object, the first parameter must match the type the delegate is bound to.</span></span> <span data-ttu-id="48c55-134">V tomto příkladu jsou dva parametry typu `Example` a typ `int` (`Integer` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="48c55-134">In this example, there are two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3. <span data-ttu-id="48c55-135">Vytvoření <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="48c55-135">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="48c55-136">V tomto příkladu metoda nemá žádný název.</span><span class="sxs-lookup"><span data-stu-id="48c55-136">In this example the method has no name.</span></span> <span data-ttu-id="48c55-137">Typ vrácené hodnoty je určen jako `int` (`Integer` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="48c55-137">The type of the return value is specified as `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="48c55-138">Tato metoda má přístup k soukromým a chráněným členům `Example` třídy.</span><span class="sxs-lookup"><span data-stu-id="48c55-138">The method has access to the private and protected members of the `Example` class.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4. <span data-ttu-id="48c55-139">Vygenerování těla metody.</span><span class="sxs-lookup"><span data-stu-id="48c55-139">Emit the method body.</span></span> <span data-ttu-id="48c55-140">V tomto příkladu <xref:System.Reflection.Emit.ILGenerator> objekt se používá ke generování Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="48c55-140">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="48c55-141">Můžete také <xref:System.Reflection.Emit.DynamicILInfo> objektu můžete použít ve spojení s nespravovaným kódem generátorů ke generování tělo metody <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="48c55-141">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="48c55-142">Jazyk MSIL v tomto příkladě načte první argument, který je instancí nástroje `Example` třídy a použije ho k načtení hodnoty pole soukromé instanci typu `int`.</span><span class="sxs-lookup"><span data-stu-id="48c55-142">The MSIL in this example loads the first argument, which is an instance of the `Example` class, and uses it to load the value of a private instance field of type `int`.</span></span> <span data-ttu-id="48c55-143">Druhý argument je načten a jsou vynásobí dvě čísla.</span><span class="sxs-lookup"><span data-stu-id="48c55-143">The second argument is loaded, and the two numbers are multiplied.</span></span> <span data-ttu-id="48c55-144">Pokud je větší než výsledek `int`, je oříznutá hodnota a nejvýznamnější bity se zahodí.</span><span class="sxs-lookup"><span data-stu-id="48c55-144">If the result is larger than `int`, the value is truncated and the most significant bits are discarded.</span></span> <span data-ttu-id="48c55-145">Metoda vrátí s návratovou hodnotou v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="48c55-145">The method returns, with the return value on the stack.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5. <span data-ttu-id="48c55-146">Vytvoření instance delegáta (deklaruje se v kroku 1), který představuje dynamickou metodu. voláním <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="48c55-146">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> method overload.</span></span> <span data-ttu-id="48c55-147">Vytvoření delegáta je metoda dokončena a žádné další pokusy o změnit metodu – například přidat další jazyk MSIL, jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="48c55-147">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="48c55-148">Můžete volat <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metoda víc než jednou k vytváření delegátů vázán na ostatní instance cílového typu.</span><span class="sxs-lookup"><span data-stu-id="48c55-148">You can call the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method multiple times to create delegates bound to other instances of the target type.</span></span>  
  
     <span data-ttu-id="48c55-149">Následující kód vytvoří vazbu metodu na novou instanci třídy `Example` třídy, jehož privátní testovací je nastaveno na 42.</span><span class="sxs-lookup"><span data-stu-id="48c55-149">The following code binds the method to a new instance of the `Example` class whose private test field is set to 42.</span></span> <span data-ttu-id="48c55-150">To znamená, že pokaždé, když je delegát vyvolán instanci `Example` je předán pro první parametr metody.</span><span class="sxs-lookup"><span data-stu-id="48c55-150">That is, each time the delegate is invoked the instance of `Example` is passed to the first parameter of the method.</span></span>  
  
     <span data-ttu-id="48c55-151">Delegát `OneParameter` se používá, protože první parametr metody vždy přijímá instanci `Example`.</span><span class="sxs-lookup"><span data-stu-id="48c55-151">The delegate `OneParameter` is used because the first parameter of the method always receives the instance of `Example`.</span></span> <span data-ttu-id="48c55-152">Když je vyvolán delegát, pouze druhý parametr je povinný.</span><span class="sxs-lookup"><span data-stu-id="48c55-152">When the delegate is invoked, only the second parameter is required.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="48c55-153">Příklad</span><span class="sxs-lookup"><span data-stu-id="48c55-153">Example</span></span>  
 <span data-ttu-id="48c55-154">Následující příklad kódu ukazuje jednoduchou dynamickou metodu a dynamická metoda svázána s instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="48c55-154">The following code example demonstrates a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>  
  
 <span data-ttu-id="48c55-155">Jednoduchou dynamickou metodu přijímá jeden argument, 32bitové celé číslo a vrátí hodnotu 64-bit druhou mocninu tohoto čísla.</span><span class="sxs-lookup"><span data-stu-id="48c55-155">The simple dynamic method takes one argument, a 32-bit integer, and returns the 64-bit square of that integer.</span></span> <span data-ttu-id="48c55-156">Obecný delegát se používá k volání metody.</span><span class="sxs-lookup"><span data-stu-id="48c55-156">A generic delegate is used to invoke the method.</span></span>  
  
 <span data-ttu-id="48c55-157">Druhý dynamická metoda má dva parametry typu `Example` a typ `int` (`Integer` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="48c55-157">The second dynamic method has two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="48c55-158">Po vytvoření dynamické metody je vázán k instanci `Example`, pomocí obecného delegáta, který má jeden argument typu `int`.</span><span class="sxs-lookup"><span data-stu-id="48c55-158">When the dynamic method has been created, it is bound to an instance of `Example`, using a generic delegate that has one argument of type `int`.</span></span> <span data-ttu-id="48c55-159">Delegát nemá argument typu `Example` vzhledem k tomu, že první parametr metody vždy obdrží vázané instanci `Example`.</span><span class="sxs-lookup"><span data-stu-id="48c55-159">The delegate does not have an argument of type `Example` because the first parameter of the method always receives the bound instance of `Example`.</span></span> <span data-ttu-id="48c55-160">Když je vyvolán delegát, pouze `int` není zadaný argument.</span><span class="sxs-lookup"><span data-stu-id="48c55-160">When the delegate is invoked, only the `int` argument is supplied.</span></span> <span data-ttu-id="48c55-161">Tato dynamická metoda přistupuje k soukromé pole `Example` třídy a vrátí součin soukromé pole a `int` argument.</span><span class="sxs-lookup"><span data-stu-id="48c55-161">This dynamic method accesses a private field of the `Example` class and returns the product of the private field and the `int` argument.</span></span>  
  
 <span data-ttu-id="48c55-162">Příklad kódu definuje delegáty, které lze použít k provedení metody.</span><span class="sxs-lookup"><span data-stu-id="48c55-162">The code example defines delegates that can be used to execute the methods.</span></span>  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="48c55-163">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="48c55-163">Compiling the Code</span></span>  
  
-   <span data-ttu-id="48c55-164">Obsahuje kód jazyka C# `using` příkazy (`Imports` v jazyce Visual Basic) nezbytné pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="48c55-164">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="48c55-165">Nejsou vyžadovány žádné odkazy na další sestavení.</span><span class="sxs-lookup"><span data-stu-id="48c55-165">No additional assembly references are required.</span></span>  
  
-   <span data-ttu-id="48c55-166">Kompilace kódu do příkazového řádku pomocí csc.exe a vbc.exe, cl.exe.</span><span class="sxs-lookup"><span data-stu-id="48c55-166">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="48c55-167">Ke kompilaci kódu v sadě Visual Studio, umístěte ho do šablony projektu konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="48c55-167">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48c55-168">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48c55-168">See also</span></span>

- <xref:System.Reflection.Emit.DynamicMethod>
- <span data-ttu-id="48c55-169">[Použití generování reflexe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="48c55-169">[Using Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))</span></span>
- <span data-ttu-id="48c55-170">[Scénáře dynamických metod generování reflexe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="48c55-170">[Reflection Emit Dynamic Method Scenarios](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100))</span></span>
