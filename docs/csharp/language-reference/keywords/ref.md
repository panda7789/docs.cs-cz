---
title: REF – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 03/06/2018
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: e0b82de125246e95d8dce2a7afc20119a8a1fe4f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "47027801"
---
# <a name="ref-c-reference"></a><span data-ttu-id="0644f-102">ref (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0644f-102">ref (C# Reference)</span></span>

<span data-ttu-id="0644f-103">`ref` – Klíčové slovo určuje hodnotu, která je předána odkazem.</span><span class="sxs-lookup"><span data-stu-id="0644f-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="0644f-104">Používá se ve čtyřech různých kontextech:</span><span class="sxs-lookup"><span data-stu-id="0644f-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="0644f-105">V podpisu metody a volání metody, pro předání argumentu podle odkazu na metodu.</span><span class="sxs-lookup"><span data-stu-id="0644f-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="0644f-106">Zobrazit [předání argumentu podle odkazu](#passing-an-argument-by-reference) Další informace.</span><span class="sxs-lookup"><span data-stu-id="0644f-106">See [Passing an argument by reference](#passing-an-argument-by-reference) for more information.</span></span>
- <span data-ttu-id="0644f-107">V podpisu metody, vracet hodnotu odkazem volajícímu.</span><span class="sxs-lookup"><span data-stu-id="0644f-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="0644f-108">Zobrazit [referenční návratové hodnoty](#reference-return-values) Další informace.</span><span class="sxs-lookup"><span data-stu-id="0644f-108">See [Reference return values](#reference-return-values) for more information.</span></span>
- <span data-ttu-id="0644f-109">V těle členské k označení, že návratová hodnota odkazu uložená místně jako odkaz, který si klade za cíl volajícího k úpravě nebo obecně platí, místní proměnná přistupuje ke jiná hodnota podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="0644f-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="0644f-110">Zobrazit [místních](#ref-locals) Další informace.</span><span class="sxs-lookup"><span data-stu-id="0644f-110">See [Ref locals](#ref-locals) for more information.</span></span>
- <span data-ttu-id="0644f-111">V `struct` deklarace deklarovat `ref struct` nebo `ref readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="0644f-111">In a `struct` declaration to declare a `ref struct` or a `ref readonly struct`.</span></span> <span data-ttu-id="0644f-112">Další informace najdete v tématu [referenční sémantika s typy hodnot](../../reference-semantics-with-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="0644f-112">For more information, see [Reference semantics with value types](../../reference-semantics-with-value-types.md).</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="0644f-113">Předání argumentu podle odkazu</span><span class="sxs-lookup"><span data-stu-id="0644f-113">Passing an argument by reference</span></span>

<span data-ttu-id="0644f-114">Při použití v seznamu parametrů metod, `ref` – klíčové slovo určuje, že argument se předá odkazem, ne podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0644f-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="0644f-115">Předávání odkazem efekt je, že všechny změny argumentů volané metody se projeví ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="0644f-115">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="0644f-116">Například pokud volající předává místní proměnnou výraz nebo výraz přístupu k elementu pole a volané metody nahradí objekt, na které odkazuje parametr ref a pak volajícího uživatele místní proměnné nebo element pole nyní odkazuje na nový objekt při Metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="0644f-116">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="0644f-117">Nezaměňujte koncept předávání odkazem s konceptem odkazových typů.</span><span class="sxs-lookup"><span data-stu-id="0644f-117">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="0644f-118">Dvě koncepce nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="0644f-118">The two concepts are not the same.</span></span> <span data-ttu-id="0644f-119">Parametr metody. je možné upravovat prostřednictvím `ref` bez ohledu na to, zda je typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="0644f-119">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="0644f-120">Pokud je předána odkazem. neexistuje žádná zabalení typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0644f-120">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="0644f-121">Použití `ref` parametr definici metody a volající metody musíte explicitně použít `ref` – klíčové slovo, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0644f-121">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="0644f-122">Argument, který je předán `ref` nebo `in` parametr musí být inicializován před jeho předáním.</span><span class="sxs-lookup"><span data-stu-id="0644f-122">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="0644f-123">Tím se liší od [si](out-parameter-modifier.md) parametry, jejichž argumenty není nutné explicitně inicializovat předtím, než jsou předány.</span><span class="sxs-lookup"><span data-stu-id="0644f-123">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="0644f-124">Členy třídy nemůže mít podpisy, které se liší pouze `ref`, `in`, nebo `out`.</span><span class="sxs-lookup"><span data-stu-id="0644f-124">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="0644f-125">Chyba kompilátoru nastane, pokud jediným rozdílem mezi dva členy typu je, že jedna z nich má `ref` má parametr a druhý `out`, nebo `in` parametru.</span><span class="sxs-lookup"><span data-stu-id="0644f-125">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="0644f-126">Například následující kód, nebude kompilovat.</span><span class="sxs-lookup"><span data-stu-id="0644f-126">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="0644f-127">Však metody mohou být přetíženy, když má jednu metodu `ref`, `in`, nebo `out` parametr a druhý je hodnota parametru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0644f-127">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="0644f-128">V jiných situacích, které vyžadují párování podpis, například přepsání, zobrazení nebo skrytí `in`, `ref`, a `out` jsou součást podpisu a navzájem neodpovídají.</span><span class="sxs-lookup"><span data-stu-id="0644f-128">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="0644f-129">Vlastnosti nejsou proměnné.</span><span class="sxs-lookup"><span data-stu-id="0644f-129">Properties are not variables.</span></span> <span data-ttu-id="0644f-130">Jsou metody a nelze předat `ref` parametry.</span><span class="sxs-lookup"><span data-stu-id="0644f-130">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="0644f-131">Nelze použít `ref`, `in`, a `out` klíčová slova pro následující druhy metod:</span><span class="sxs-lookup"><span data-stu-id="0644f-131">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="0644f-132">Asynchronní metody, které definujete pomocí [asynchronní](async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="0644f-132">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="0644f-133">Metody iterátorů, mezi které patří [yield return](yield.md) nebo `yield break` příkazu.</span><span class="sxs-lookup"><span data-stu-id="0644f-133">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="0644f-134">Předání argumentu podle odkazu: příklad</span><span class="sxs-lookup"><span data-stu-id="0644f-134">Passing an argument by reference: An example</span></span>

<span data-ttu-id="0644f-135">V předchozích příkladech předávání typů hodnot pomocí odkazu.</span><span class="sxs-lookup"><span data-stu-id="0644f-135">The previous examples pass value types by reference.</span></span> <span data-ttu-id="0644f-136">Můžete také použít `ref` – klíčové slovo k předání referenční typy podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="0644f-136">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="0644f-137">Typ odkazu předávání odkazem umožňuje volané metody k nahrazení objektu, na které odkazuje parametr odkazu volajícího.</span><span class="sxs-lookup"><span data-stu-id="0644f-137">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="0644f-138">Umístění úložiště objekt je předán metodě jako hodnota parametru odkazu.</span><span class="sxs-lookup"><span data-stu-id="0644f-138">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="0644f-139">Pokud změníte hodnotu v umístění úložiště parametru (tak, aby odkazoval na nový objekt), také změnit umístění úložiště, na který odkazuje volající.</span><span class="sxs-lookup"><span data-stu-id="0644f-139">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="0644f-140">Následující příklad předá instance typu odkaz jako `ref` parametru.</span><span class="sxs-lookup"><span data-stu-id="0644f-140">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="0644f-141">Další informace o tom, jak předat typy odkazů podle hodnoty a podle reference najdete v tématu [předávání parametrů typu odkazu](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="0644f-141">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="0644f-142">Referenční návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="0644f-142">Reference return values</span></span>

<span data-ttu-id="0644f-143">Referenční návratové hodnoty (nebo návratové) jsou hodnoty, které metoda vrací odkazem na volajícího.</span><span class="sxs-lookup"><span data-stu-id="0644f-143">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="0644f-144">To znamená že volající může změnit hodnotu, vrací metoda, a tato změna se projeví ve stavu objektu, který obsahuje metodu.</span><span class="sxs-lookup"><span data-stu-id="0644f-144">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="0644f-145">Vrátí odkaz hodnota je definována pomocí `ref` – klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="0644f-145">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="0644f-146">V podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="0644f-146">In the method signature.</span></span> <span data-ttu-id="0644f-147">Například následující podpis metody Určuje, že `GetCurrentPrice` metoda vrátí hodnotu <xref:System.Decimal> hodnota podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="0644f-147">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="0644f-148">Mezi `return` token a vrácené v proměnné `return` příkaz v metodě.</span><span class="sxs-lookup"><span data-stu-id="0644f-148">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="0644f-149">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0644f-149">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="0644f-150">Aby volající změnit stav objektu, vrátit hodnota musí být uložen do proměnné, která není výslovně uveden jako odkaz [lokální proměnná podle odkazu](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="0644f-150">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="0644f-151">Příklad najdete v tématu [A návratové a příklad místní hodnoty ref](#a-ref-returns-and-ref-locals-example)</span><span class="sxs-lookup"><span data-stu-id="0644f-151">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="0644f-152">Místní referenční hodnoty</span><span class="sxs-lookup"><span data-stu-id="0644f-152">Ref locals</span></span>

<span data-ttu-id="0644f-153">Lokální proměnná ref se používá k odkazování na hodnoty, které jsou vráceny za použití `return ref`.</span><span class="sxs-lookup"><span data-stu-id="0644f-153">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="0644f-154">Lokální proměnná ref nejde inicializovat na návratovou hodnotu bez ref.</span><span class="sxs-lookup"><span data-stu-id="0644f-154">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="0644f-155">Jinými slovy pravou stranu inicializace musí být odkaz.</span><span class="sxs-lookup"><span data-stu-id="0644f-155">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="0644f-156">Všechny změny na hodnotu lokální proměnnou se projeví ve stavu objektu, jehož metoda vrátila hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="0644f-156">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="0644f-157">Definice lokální proměnnou s použitím `ref` – klíčové slovo před deklaraci proměnné, stejně jako bezprostředně před volání metody, která vrátí hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="0644f-157">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="0644f-158">Například následující příkaz definuje ref místní hodnotu, která je vrácena metodou s názvem `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="0644f-158">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="0644f-159">Stejným způsobem můžete přistupovat hodnota podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="0644f-159">You can access a value by reference in the same way.</span></span> <span data-ttu-id="0644f-160">V některých případech se přístup k hodnota podle odkazu zvyšuje výkon se vyhnout operaci kopírování potenciálně nákladné.</span><span class="sxs-lookup"><span data-stu-id="0644f-160">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="0644f-161">Následující příkaz například ukazuje, jak jeden můžete definovat, který se používá k odkazování hodnotu lokální hodnota ref.</span><span class="sxs-lookup"><span data-stu-id="0644f-161">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="0644f-162">Všimněte si, že v obou příkladech `ref` – klíčové slovo musí být použit v obou místech, nebo kompilátor vygeneruje chybu CS8172 "Nelze inicializovat proměnnou podle odkazu s hodnotou".</span><span class="sxs-lookup"><span data-stu-id="0644f-162">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="0644f-163">A návratové a příklad místní hodnoty ref</span><span class="sxs-lookup"><span data-stu-id="0644f-163">A ref returns and ref locals example</span></span>

<span data-ttu-id="0644f-164">Následující příklad definuje `Book` třídu, která má dvě <xref:System.String> pole, `Title` a `Author`.</span><span class="sxs-lookup"><span data-stu-id="0644f-164">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="0644f-165">Definuje také `BookCollection` třídu, která obsahuje privátní pole `Book` objekty.</span><span class="sxs-lookup"><span data-stu-id="0644f-165">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="0644f-166">Jednotlivé knihy objekty jsou vráceny ve vztahu voláním jeho `GetBookByTitle` metoda.</span><span class="sxs-lookup"><span data-stu-id="0644f-166">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="0644f-167">Pokud volající uloží hodnoty vrácené `GetBookByTitle` změny, které umožňuje volajícímu návratovou hodnotu metody jako lokální proměnná podle odkazu, se projeví v `BookCollection` objektu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="0644f-167">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="0644f-168">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0644f-168">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0644f-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0644f-169">See also</span></span>

- [<span data-ttu-id="0644f-170">Referenční sémantika s typy hodnot</span><span class="sxs-lookup"><span data-stu-id="0644f-170">Reference semantics with value types</span></span>](../../reference-semantics-with-value-types.md)  
- [<span data-ttu-id="0644f-171">Předávání parametrů</span><span class="sxs-lookup"><span data-stu-id="0644f-171">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)  
- [<span data-ttu-id="0644f-172">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="0644f-172">Method Parameters</span></span>](method-parameters.md)  
- [<span data-ttu-id="0644f-173">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0644f-173">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="0644f-174">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0644f-174">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="0644f-175">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0644f-175">C# Keywords</span></span>](index.md)