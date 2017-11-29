---
title: "Postupy: Definování a provádění dynamických metod"
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
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 52f6b425ae4df138a843c6a790f10f78dc5a2b40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-and-execute-dynamic-methods"></a><span data-ttu-id="58d32-102">Postupy: Definování a provádění dynamických metod</span><span class="sxs-lookup"><span data-stu-id="58d32-102">How to: Define and Execute Dynamic Methods</span></span>
<span data-ttu-id="58d32-103">Následující postupy ukazují, jak definovat a provést jednoduchý dynamické metody a dynamické metoda vázaný na instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="58d32-103">The following procedures show how to define and execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span> <span data-ttu-id="58d32-104">Další informace o dynamických metod najdete v tématu <xref:System.Reflection.Emit.DynamicMethod> třídy a [reflexe Emitování dynamických metoda scénáře](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).</span><span class="sxs-lookup"><span data-stu-id="58d32-104">For more information on dynamic methods, see the <xref:System.Reflection.Emit.DynamicMethod> class and [Reflection Emit Dynamic Method Scenarios](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).</span></span>  
  
### <a name="to-define-and-execute-a-dynamic-method"></a><span data-ttu-id="58d32-105">K definování a provedení dynamické metody</span><span class="sxs-lookup"><span data-stu-id="58d32-105">To define and execute a dynamic method</span></span>  
  
1.  <span data-ttu-id="58d32-106">Deklarace typu delegáta spuštění metody.</span><span class="sxs-lookup"><span data-stu-id="58d32-106">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="58d32-107">Zvažte použití obecný delegát minimalizovat počet typů delegáta, které je třeba deklarovat.</span><span class="sxs-lookup"><span data-stu-id="58d32-107">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="58d32-108">Následující kód deklaruje dva typy, které by mohly být použity delegovat `SquareIt` metoda a jeden z nich je obecná.</span><span class="sxs-lookup"><span data-stu-id="58d32-108">The following code declares two delegate types that could be used for the `SquareIt` method, and one of them is generic.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  <span data-ttu-id="58d32-109">Vytvořte pole, které určuje typy parametrů pro metodu dynamické.</span><span class="sxs-lookup"><span data-stu-id="58d32-109">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="58d32-110">V tomto příkladu je parametr pouze `int` (`Integer` v jazyce Visual Basic), takže pole má pouze jeden element.</span><span class="sxs-lookup"><span data-stu-id="58d32-110">In this example, the only parameter is an `int` (`Integer` in Visual Basic), so the array has only one element.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  <span data-ttu-id="58d32-111">Vytvoření <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="58d32-111">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="58d32-112">V tomto příkladu je název metody `SquareIt`.</span><span class="sxs-lookup"><span data-stu-id="58d32-112">In this example the method is named `SquareIt`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="58d32-113">Není nutné poskytnout názvy dynamických metod a nemůže být volána podle názvu.</span><span class="sxs-lookup"><span data-stu-id="58d32-113">It is not necessary to give dynamic methods names, and they cannot be invoked by name.</span></span> <span data-ttu-id="58d32-114">Více dynamických metod může mít stejný název.</span><span class="sxs-lookup"><span data-stu-id="58d32-114">Multiple dynamic methods can have the same name.</span></span> <span data-ttu-id="58d32-115">Ale název se zobrazí v zásobníky volání a může být užitečná pro ladění.</span><span class="sxs-lookup"><span data-stu-id="58d32-115">However, the name appears in call stacks and can be useful for debugging.</span></span>  
  
     <span data-ttu-id="58d32-116">Typ vrácené hodnoty je zadán jako `long`.</span><span class="sxs-lookup"><span data-stu-id="58d32-116">The type of the return value is specified as `long`.</span></span> <span data-ttu-id="58d32-117">Metoda souvisí s modul, který obsahuje `Example` třídy, která obsahuje ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="58d32-117">The method is associated with the module that contains the `Example` class, which contains the example code.</span></span> <span data-ttu-id="58d32-118">Libovolný načíst modul může být určen.</span><span class="sxs-lookup"><span data-stu-id="58d32-118">Any loaded module could be specified.</span></span> <span data-ttu-id="58d32-119">Dynamické metoda funguje jako úroveň modulu `static` – metoda (`Shared` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="58d32-119">The dynamic method acts like a module-level `static` method (`Shared` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  <span data-ttu-id="58d32-120">Emitování metoda textu.</span><span class="sxs-lookup"><span data-stu-id="58d32-120">Emit the method body.</span></span> <span data-ttu-id="58d32-121">V tomto příkladu <xref:System.Reflection.Emit.ILGenerator> objekt se používá k vydávání Microsoft (MSIL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="58d32-121">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="58d32-122">Alternativně <xref:System.Reflection.Emit.DynamicILInfo> objekt můžete použít ve spojení s nespravovaným kódem generátory pro vydávání metoda obsah <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="58d32-122">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="58d32-123">MSIL v tomto příkladu načte argument, který je `int`, do zásobníku, převede ji na `long`, duplicitní položky `long`a vynásobí dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="58d32-123">The MSIL in this example loads the argument, which is an `int`, onto the stack, converts it to a `long`, duplicates the `long`, and multiplies the two numbers.</span></span> <span data-ttu-id="58d32-124">Kvadratických výsledek tak zůstane v zásobníku a všechny metody musí provést je návratový.</span><span class="sxs-lookup"><span data-stu-id="58d32-124">This leaves the squared result on the stack, and all the method has to do is return.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  <span data-ttu-id="58d32-125">Vytvořte instanci delegáta (deklarované v kroku 1), která představuje dynamické metodu voláním <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="58d32-125">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="58d32-126">Vytváření delegáta je metoda dokončena a všechny další pokusí změnit metodu – například přidání další MSIL – jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="58d32-126">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span> <span data-ttu-id="58d32-127">Následující kód vytvoří delegáta a vyvolá, pomocí obecný delegát.</span><span class="sxs-lookup"><span data-stu-id="58d32-127">The following code creates the delegate and invokes it, using a generic delegate.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a><span data-ttu-id="58d32-128">K definování a provádění dynamických metodu, která je vázána na objekt</span><span class="sxs-lookup"><span data-stu-id="58d32-128">To define and execute a dynamic method that is bound to an object</span></span>  
  
1.  <span data-ttu-id="58d32-129">Deklarace typu delegáta spuštění metody.</span><span class="sxs-lookup"><span data-stu-id="58d32-129">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="58d32-130">Zvažte použití obecný delegát minimalizovat počet typů delegáta, které je třeba deklarovat.</span><span class="sxs-lookup"><span data-stu-id="58d32-130">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="58d32-131">Následující kód deklaruje typ obecný delegát, který můžete použít ke spuštění libovolné metody s jeden parametr a návratovou hodnotu, nebo metodu s dva parametry a návratové hodnoty, pokud delegát je vázána na objekt.</span><span class="sxs-lookup"><span data-stu-id="58d32-131">The following code declares a generic delegate type that can be used to execute any method with one parameter and a return value, or a method with two parameters and a return value if the delegate is bound to an object.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  <span data-ttu-id="58d32-132">Vytvořte pole, které určuje typy parametrů pro metodu dynamické.</span><span class="sxs-lookup"><span data-stu-id="58d32-132">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="58d32-133">Pokud delegát představující metoda má být vázána na objekt, první parametr musí odpovídat typu, který je vázána delegát.</span><span class="sxs-lookup"><span data-stu-id="58d32-133">If the delegate representing the method is to be bound to an object, the first parameter must match the type the delegate is bound to.</span></span> <span data-ttu-id="58d32-134">V tomto příkladu jsou dva parametry typu `Example` a typ `int` (`Integer` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="58d32-134">In this example, there are two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  <span data-ttu-id="58d32-135">Vytvoření <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="58d32-135">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="58d32-136">V tomto příkladu metoda nemá žádný název.</span><span class="sxs-lookup"><span data-stu-id="58d32-136">In this example the method has no name.</span></span> <span data-ttu-id="58d32-137">Typ vrácené hodnoty je zadán jako `int` (`Integer` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="58d32-137">The type of the return value is specified as `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="58d32-138">Metoda má přístup k privátním a chráněné členy `Example` třídy.</span><span class="sxs-lookup"><span data-stu-id="58d32-138">The method has access to the private and protected members of the `Example` class.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  <span data-ttu-id="58d32-139">Emitování metoda textu.</span><span class="sxs-lookup"><span data-stu-id="58d32-139">Emit the method body.</span></span> <span data-ttu-id="58d32-140">V tomto příkladu <xref:System.Reflection.Emit.ILGenerator> objekt se používá k vydávání Microsoft (MSIL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="58d32-140">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="58d32-141">Alternativně <xref:System.Reflection.Emit.DynamicILInfo> objekt můžete použít ve spojení s nespravovaným kódem generátory pro vydávání metoda obsah <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="58d32-141">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="58d32-142">MSIL v tomto příkladu načte první argument, což je instance služby `Example` třídy a používá ji načíst hodnotu pole privátní instance typu `int`.</span><span class="sxs-lookup"><span data-stu-id="58d32-142">The MSIL in this example loads the first argument, which is an instance of the `Example` class, and uses it to load the value of a private instance field of type `int`.</span></span> <span data-ttu-id="58d32-143">Druhý argument je načten a se násobí dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="58d32-143">The second argument is loaded, and the two numbers are multiplied.</span></span> <span data-ttu-id="58d32-144">Pokud je výsledkem je větší než `int`, se zkrátí hodnota a nejdůležitější bits se zahodí.</span><span class="sxs-lookup"><span data-stu-id="58d32-144">If the result is larger than `int`, the value is truncated and the most significant bits are discarded.</span></span> <span data-ttu-id="58d32-145">Metoda vrátí s hodnotou vrácenou v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="58d32-145">The method returns, with the return value on the stack.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  <span data-ttu-id="58d32-146">Vytvořte instanci delegáta (deklarované v kroku 1), která představuje dynamické metodu voláním <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="58d32-146">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> method overload.</span></span> <span data-ttu-id="58d32-147">Vytváření delegáta je metoda dokončena a všechny další pokusí změnit metodu – například přidání další MSIL – jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="58d32-147">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="58d32-148">Můžete volat <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metoda několikrát k vytvoření delegáti vázána na ostatní instance typu cíle.</span><span class="sxs-lookup"><span data-stu-id="58d32-148">You can call the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method multiple times to create delegates bound to other instances of the target type.</span></span>  
  
     <span data-ttu-id="58d32-149">Následující kód vytvoří novou instanci třídy vazbu metodu `Example` třídu, jejíž privátní testovací je nastaveno na 42.</span><span class="sxs-lookup"><span data-stu-id="58d32-149">The following code binds the method to a new instance of the `Example` class whose private test field is set to 42.</span></span> <span data-ttu-id="58d32-150">To znamená, pokaždé, když je delegát vyvolat instanci `Example` předaný první parametr metody.</span><span class="sxs-lookup"><span data-stu-id="58d32-150">That is, each time the delegate is invoked the instance of `Example` is passed to the first parameter of the method.</span></span>  
  
     <span data-ttu-id="58d32-151">Delegát `OneParameter` je použít, protože první parametr metody vždy obdrží instanci `Example`.</span><span class="sxs-lookup"><span data-stu-id="58d32-151">The delegate `OneParameter` is used because the first parameter of the method always receives the instance of `Example`.</span></span> <span data-ttu-id="58d32-152">Po vyvolání delegáta je jenom druhý parametr je povinný.</span><span class="sxs-lookup"><span data-stu-id="58d32-152">When the delegate is invoked, only the second parameter is required.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="58d32-153">Příklad</span><span class="sxs-lookup"><span data-stu-id="58d32-153">Example</span></span>  
 <span data-ttu-id="58d32-154">Následující příklad kódu ukazuje jednoduchý dynamické metody a dynamické metoda vázaný na instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="58d32-154">The following code example demonstrates a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>  
  
 <span data-ttu-id="58d32-155">Jednoduché dynamické metoda přijímá jeden argument, 32bitové celé číslo a vrátí druhou 64-bit této celé číslo.</span><span class="sxs-lookup"><span data-stu-id="58d32-155">The simple dynamic method takes one argument, a 32-bit integer, and returns the 64-bit square of that integer.</span></span> <span data-ttu-id="58d32-156">– Obecný delegát se používá k vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="58d32-156">A generic delegate is used to invoke the method.</span></span>  
  
 <span data-ttu-id="58d32-157">Druhý dynamické metoda má dva parametry typu `Example` a typ `int` (`Integer` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="58d32-157">The second dynamic method has two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="58d32-158">Po vytvoření dynamické metody, je vázána na instanci `Example`, pomocí obecný delegát, který má jeden argument typu `int`.</span><span class="sxs-lookup"><span data-stu-id="58d32-158">When the dynamic method has been created, it is bound to an instance of `Example`, using a generic delegate that has one argument of type `int`.</span></span> <span data-ttu-id="58d32-159">Delegát nemá argument typu `Example` protože první parametr metody vždy obdrží vázané instanci `Example`.</span><span class="sxs-lookup"><span data-stu-id="58d32-159">The delegate does not have an argument of type `Example` because the first parameter of the method always receives the bound instance of `Example`.</span></span> <span data-ttu-id="58d32-160">Pokud delegát je vyvolána, pouze `int` zadán argument.</span><span class="sxs-lookup"><span data-stu-id="58d32-160">When the delegate is invoked, only the `int` argument is supplied.</span></span> <span data-ttu-id="58d32-161">Tato metoda dynamické přistupuje k privátní pole `Example` třídy a vrátí součin soukromé pole a `int` argument.</span><span class="sxs-lookup"><span data-stu-id="58d32-161">This dynamic method accesses a private field of the `Example` class and returns the product of the private field and the `int` argument.</span></span>  
  
 <span data-ttu-id="58d32-162">Příklad kódu definuje delegáti, které můžete použít ke spuštění metody.</span><span class="sxs-lookup"><span data-stu-id="58d32-162">The code example defines delegates that can be used to execute the methods.</span></span>  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="58d32-163">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="58d32-163">Compiling the Code</span></span>  
  
-   <span data-ttu-id="58d32-164">Obsahuje kód jazyka C# `using` příkazy (`Imports` v jazyce Visual Basic) potřebné pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="58d32-164">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="58d32-165">Nejsou vyžadovány žádné odkazy na další sestavení.</span><span class="sxs-lookup"><span data-stu-id="58d32-165">No additional assembly references are required.</span></span>  
  
-   <span data-ttu-id="58d32-166">Kompilace kódu na příkazovém řádku pomocí csc.exe, vbc.exe nebo cl.exe.</span><span class="sxs-lookup"><span data-stu-id="58d32-166">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="58d32-167">Kompilace kódu v sadě Visual Studio, umístěte ho do šablony projektu konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="58d32-167">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d32-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="58d32-168">See Also</span></span>  
 <xref:System.Reflection.Emit.DynamicMethod>  
 [<span data-ttu-id="58d32-169">Emitování pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="58d32-169">Using Reflection Emit</span></span>](http://msdn.microsoft.com/en-us/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [<span data-ttu-id="58d32-170">Emitování reflexe scénáře dynamické – metoda</span><span class="sxs-lookup"><span data-stu-id="58d32-170">Reflection Emit Dynamic Method Scenarios</span></span>](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)
