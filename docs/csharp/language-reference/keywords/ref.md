---
title: "ref (Referenční dokumentace jazyka C#)"
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 427045317e9d7d0fe3435a486b9f761908ab5e78
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="ref-c-reference"></a><span data-ttu-id="5da9b-102">ref (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5da9b-102">ref (C# Reference)</span></span>

<span data-ttu-id="5da9b-103">`ref` – Klíčové slovo označuje hodnotu, která je předána odkazem.</span><span class="sxs-lookup"><span data-stu-id="5da9b-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="5da9b-104">Používá se ve třech různých kontextů:</span><span class="sxs-lookup"><span data-stu-id="5da9b-104">It is used in three different contexts:</span></span> 

- <span data-ttu-id="5da9b-105">V podpis metody a volání metody, mají být předány argument metodu odkazem.</span><span class="sxs-lookup"><span data-stu-id="5da9b-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="5da9b-106">V tématu [předáním argumentu podle reference](#passing-an-argument-by-reference) Další informace.</span><span class="sxs-lookup"><span data-stu-id="5da9b-106">See [Passing an argument by reference](#passing-an-argument-by-reference) for more information.</span></span>

- <span data-ttu-id="5da9b-107">V podpis metody, bude vrácena hodnota volajícímu odkazem.</span><span class="sxs-lookup"><span data-stu-id="5da9b-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="5da9b-108">V tématu [návratové hodnoty odkaz](#reference-return-values) Další informace.</span><span class="sxs-lookup"><span data-stu-id="5da9b-108">See [Reference return values](#reference-return-values) for more information.</span></span>

- <span data-ttu-id="5da9b-109">V člen textu, k označení, že návratovou hodnotu odkazu ukládají se místně jako odkaz, který má volající v úmyslu upravit.</span><span class="sxs-lookup"><span data-stu-id="5da9b-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify.</span></span> <span data-ttu-id="5da9b-110">V tématu [místní hodnoty Ref](#ref-locals) Další informace.</span><span class="sxs-lookup"><span data-stu-id="5da9b-110">See [Ref locals](#ref-locals) for more information.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="5da9b-111">Předáním argumentu podle reference</span><span class="sxs-lookup"><span data-stu-id="5da9b-111">Passing an argument by reference</span></span>

<span data-ttu-id="5da9b-112">Při použití v seznamu parametrů metody, `ref` – klíčové slovo znamená, že je argumentem úspěšně odkazem, ne podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5da9b-112">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="5da9b-113">Účinek předání odkazem je tato všechny změny argument volané metody se odrazí v volání metody.</span><span class="sxs-lookup"><span data-stu-id="5da9b-113">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="5da9b-114">Například pokud volající předá místní proměnné výraz nebo výraz přístup k elementu pole a nahradí názvem metoda objektu, na kterou odkazuje parametr ref pak volající je místní proměnné nebo element pole nyní odkazuje na nový objekt při Metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="5da9b-114">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
>  <span data-ttu-id="5da9b-115">Nezaměňujte koncept předání odkazem pojmu odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="5da9b-115">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="5da9b-116">Dvěma konceptů nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="5da9b-116">The two concepts are not the same.</span></span> <span data-ttu-id="5da9b-117">Parametr metody mohou být upravena `ref` bez ohledu na to, zda je hodnota typu nebo typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="5da9b-117">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="5da9b-118">Když je předána odkazem neexistuje žádné zabalení typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5da9b-118">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="5da9b-119">Použít `ref` nutné explicitně zadat parametr definici metody a volání metody `ref` – klíčové slovo, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5da9b-119">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="5da9b-120">Argument, který je předán `ref` nebo `in` parametr se musí inicializovat před předáním.</span><span class="sxs-lookup"><span data-stu-id="5da9b-120">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="5da9b-121">Tím se liší od [out](out-parameter-modifier.md) parametry, jejichž argumenty nemusíte před jsou předávány explicitně inicializovat.</span><span class="sxs-lookup"><span data-stu-id="5da9b-121">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="5da9b-122">Členy třídy, nemůže mít podpisy, které se liší pouze `ref`, `in`, nebo `out`.</span><span class="sxs-lookup"><span data-stu-id="5da9b-122">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="5da9b-123">Chyba kompilátoru dojde, pokud mezi dva členy typu jediným rozdílem je, že jedna z nich má `ref` má parametr a druhý `out`, nebo `in` parametr.</span><span class="sxs-lookup"><span data-stu-id="5da9b-123">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="5da9b-124">Například následující kód, není zkompilují.</span><span class="sxs-lookup"><span data-stu-id="5da9b-124">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
<span data-ttu-id="5da9b-125">Ale metody mohou být přetíženy, když má jednu metodu `ref`, `in`, nebo `out` parametr a dalších má parametr hodnotu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5da9b-125">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="5da9b-126">V jiných situacích, které vyžadují párování podpisu, jako je například přepsání, zobrazení nebo skrytí `in`, `ref`, a `out` jsou součástí podpisu a navzájem neodpovídají.</span><span class="sxs-lookup"><span data-stu-id="5da9b-126">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="5da9b-127">Vlastnosti nejsou proměnné.</span><span class="sxs-lookup"><span data-stu-id="5da9b-127">Properties are not variables.</span></span> <span data-ttu-id="5da9b-128">Jsou metody a nelze předat `ref` parametry.</span><span class="sxs-lookup"><span data-stu-id="5da9b-128">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="5da9b-129">Informace o tom, jak předat pole najdete v tématu [předávání polí pomocí parametrů ref a out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="5da9b-129">For information about how to pass arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="5da9b-130">Nelze použít `ref`, `in`, a `out` klíčová slova pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="5da9b-130">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="5da9b-131">Asynchronní metody, které definují pomocí [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="5da9b-131">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
- <span data-ttu-id="5da9b-132">Iterator metody, které zahrnují [yield vrátit](../../../csharp/language-reference/keywords/yield.md) nebo `yield break` příkaz.</span><span class="sxs-lookup"><span data-stu-id="5da9b-132">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="5da9b-133">Předáním argumentu podle reference: příklad</span><span class="sxs-lookup"><span data-stu-id="5da9b-133">Passing an argument by reference: An example</span></span>

<span data-ttu-id="5da9b-134">V předchozích příkladech předat hodnotu typy odkazem.</span><span class="sxs-lookup"><span data-stu-id="5da9b-134">The previous examples pass value types by reference.</span></span> <span data-ttu-id="5da9b-135">Můžete také `ref` – klíčové slovo předat referenční typy odkazem.</span><span class="sxs-lookup"><span data-stu-id="5da9b-135">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="5da9b-136">Předání typu odkazu odkazem umožňuje vyvolání metody lze nahradit objektu, na který odkazuje parametr odkazu v volající.</span><span class="sxs-lookup"><span data-stu-id="5da9b-136">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="5da9b-137">Umístění úložiště objektu je předaný metodě jako hodnota parametru odkazu.</span><span class="sxs-lookup"><span data-stu-id="5da9b-137">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="5da9b-138">Pokud změníte hodnotu v umístění úložiště parametru (tak, aby odkazoval na nový objekt), můžete také změnit umístění úložiště, na který odkazuje volající.</span><span class="sxs-lookup"><span data-stu-id="5da9b-138">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="5da9b-139">Následující příklad předá instance typu odkaz jako `ref` parametr.</span><span class="sxs-lookup"><span data-stu-id="5da9b-139">The following example passes an instance of a reference type as a `ref` parameter.</span></span>   
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="5da9b-140">Další informace o tom, jak předat odkazové typy podle hodnoty a podle reference najdete v tématu [předávání parametrů typu odkazu](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5da9b-140">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="5da9b-141">Referenční dokumentace návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="5da9b-141">Reference return values</span></span>

<span data-ttu-id="5da9b-142">Referenční dokumentace návratové hodnoty (nebo ref vrátí) jsou hodnoty, které metoda vrátí odkaz na volajícího.</span><span class="sxs-lookup"><span data-stu-id="5da9b-142">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="5da9b-143">To znamená volající můžete upravit hodnota vrácená metodou a tato změna se projeví ve stavu objektu, který obsahuje metodu.</span><span class="sxs-lookup"><span data-stu-id="5da9b-143">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span> 

<span data-ttu-id="5da9b-144">Odkaz vrátit hodnota je definována pomocí `ref` – klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="5da9b-144">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="5da9b-145">V podpis metody.</span><span class="sxs-lookup"><span data-stu-id="5da9b-145">In the method signature.</span></span> <span data-ttu-id="5da9b-146">Například následující indikuje metoda podpis, `GetCurrentPrice` metoda vrátí <xref:System.Decimal> hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="5da9b-146">For example, the following method signature inidicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- <span data-ttu-id="5da9b-147">Mezi `return` token a proměnná, vrátí se v `return` příkaz v metodě.</span><span class="sxs-lookup"><span data-stu-id="5da9b-147">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="5da9b-148">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5da9b-148">For example:</span></span>
 
   ```csharp
   return ref DecimalArray[0];
   ``` 

<span data-ttu-id="5da9b-149">V pořadí pro volající změnit stav objektu vrátit hodnota musí být uložen do proměnné, která je explicitně definován jako odkaz [ref místní](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="5da9b-149">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span> 

<span data-ttu-id="5da9b-150">Příklad, naleznete v části [A ref vrátí a ref místní hodnoty – příklad](#a-ref-returns-and-ref-locals-example)</span><span class="sxs-lookup"><span data-stu-id="5da9b-150">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="5da9b-151">Místní hodnoty REF</span><span class="sxs-lookup"><span data-stu-id="5da9b-151">Ref locals</span></span>

<span data-ttu-id="5da9b-152">Místní proměnné ref slouží k odkazování na hodnot vrácených pomocí `return ref`.</span><span class="sxs-lookup"><span data-stu-id="5da9b-152">A ref local variable is used to refer to values returned using `return ref`.</span></span>  <span data-ttu-id="5da9b-153">Místní proměnné ref musí být inicializován a přiřadit ref návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5da9b-153">A ref local variable must be initialized and assigned to a ref return value.</span></span> <span data-ttu-id="5da9b-154">Všechny změny na hodnotu místní ref se projeví ve stavu objektu, jehož metoda vrátila hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="5da9b-154">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="5da9b-155">Definovat místní ref pomocí `ref` – klíčové slovo před deklarace proměnné, a také bezprostředně před volání metody, která vrátí hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="5da9b-155">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span> 

<span data-ttu-id="5da9b-156">Například následující příkaz definuje ref místní hodnotu, která vrátí metodu s názvem `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="5da9b-156">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="5da9b-157">Všimněte si, že `ref` – klíčové slovo se musí použít v obou místech nebo kompilátor vygeneruje chyba CS8172, "Nelze inicializovat proměnnou podle odkazu s hodnotou".</span><span class="sxs-lookup"><span data-stu-id="5da9b-157">Note that the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="5da9b-158">A vrátí ref a ref místní hodnoty – příklad</span><span class="sxs-lookup"><span data-stu-id="5da9b-158">A ref returns and ref locals example</span></span>

<span data-ttu-id="5da9b-159">V následujícím příkladu definuje `Book` třídu, která má dva <xref:System.String> pole, `Title` a `Author`.</span><span class="sxs-lookup"><span data-stu-id="5da9b-159">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="5da9b-160">Také definuje `BookCollection` třídu, která zahrnuje privátní pole `Book` objekty.</span><span class="sxs-lookup"><span data-stu-id="5da9b-160">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="5da9b-161">Jednotlivé knihy objektů odkazem voláním jeho `GetBookByTitle` metoda.</span><span class="sxs-lookup"><span data-stu-id="5da9b-161">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="5da9b-162">Pokud má volající ukládá hodnoty vrácené `GetBookByTitle` metoda jako místní ref změn prováděných volající návratovou hodnotu se projeví v `BookCollection` objekt, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="5da9b-162">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="5da9b-163">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5da9b-163">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5da9b-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="5da9b-164">See Also</span></span>  
 [<span data-ttu-id="5da9b-165">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5da9b-165">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5da9b-166">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5da9b-166">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5da9b-167">Předávání parametrů</span><span class="sxs-lookup"><span data-stu-id="5da9b-167">Passing Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [<span data-ttu-id="5da9b-168">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="5da9b-168">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)  
 [<span data-ttu-id="5da9b-169">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5da9b-169">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
