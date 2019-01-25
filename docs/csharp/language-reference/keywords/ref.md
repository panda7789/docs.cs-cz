---
title: REF – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 10/24/2018
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: dc19638dc3753132be01235466a98f87bdce4569
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726647"
---
# <a name="ref-c-reference"></a><span data-ttu-id="1cae7-102">ref (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1cae7-102">ref (C# Reference)</span></span>

<span data-ttu-id="1cae7-103">`ref` – Klíčové slovo určuje hodnotu, která je předána odkazem.</span><span class="sxs-lookup"><span data-stu-id="1cae7-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="1cae7-104">Používá se ve čtyřech různých kontextech:</span><span class="sxs-lookup"><span data-stu-id="1cae7-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="1cae7-105">V podpisu metody a volání metody, pro předání argumentu podle odkazu na metodu.</span><span class="sxs-lookup"><span data-stu-id="1cae7-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="1cae7-106">Další informace najdete v tématu [předání argumentu podle odkazu](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="1cae7-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="1cae7-107">V podpisu metody, vracet hodnotu odkazem volajícímu.</span><span class="sxs-lookup"><span data-stu-id="1cae7-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="1cae7-108">Další informace najdete v tématu [referenční návratové hodnoty](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="1cae7-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="1cae7-109">V těle členské k označení, že návratová hodnota odkazu uložená místně jako odkaz, který si klade za cíl volajícího k úpravě nebo obecně platí, místní proměnná přistupuje ke jiná hodnota podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="1cae7-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="1cae7-110">Další informace najdete v tématu [místních](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="1cae7-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="1cae7-111">V `struct` deklarace deklarovat `ref struct` nebo `ref readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="1cae7-111">In a `struct` declaration to declare a `ref struct` or a `ref readonly struct`.</span></span> <span data-ttu-id="1cae7-112">Další informace najdete v tématu [typy struktury ref](#ref-struct-types).</span><span class="sxs-lookup"><span data-stu-id="1cae7-112">For more information, see [ref struct types](#ref-struct-types).</span></span>


## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="1cae7-113">Předání argumentu podle odkazu</span><span class="sxs-lookup"><span data-stu-id="1cae7-113">Passing an argument by reference</span></span>

<span data-ttu-id="1cae7-114">Při použití v seznamu parametrů metod, `ref` – klíčové slovo určuje, že argument se předá odkazem, ne podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1cae7-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="1cae7-115">Předávání odkazem efekt je, že všechny změny argumentů volané metody se projeví ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="1cae7-115">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="1cae7-116">Například pokud volající předává místní proměnnou výraz nebo výraz přístupu k elementu pole a volané metody nahradí objekt, na které odkazuje parametr ref a pak volajícího uživatele místní proměnné nebo element pole nyní odkazuje na nový objekt při Metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="1cae7-116">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="1cae7-117">Nezaměňujte koncept předávání odkazem s konceptem odkazových typů.</span><span class="sxs-lookup"><span data-stu-id="1cae7-117">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="1cae7-118">Dvě koncepce nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="1cae7-118">The two concepts are not the same.</span></span> <span data-ttu-id="1cae7-119">Parametr metody. je možné upravovat prostřednictvím `ref` bez ohledu na to, zda je typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="1cae7-119">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="1cae7-120">Pokud je předána odkazem. neexistuje žádná zabalení typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1cae7-120">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="1cae7-121">Použití `ref` parametr definici metody a volající metody musíte explicitně použít `ref` – klíčové slovo, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1cae7-121">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="1cae7-122">Argument, který je předán `ref` nebo `in` parametr musí být inicializován před jeho předáním.</span><span class="sxs-lookup"><span data-stu-id="1cae7-122">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="1cae7-123">Tím se liší od [si](out-parameter-modifier.md) parametry, jejichž argumenty není nutné explicitně inicializovat předtím, než jsou předány.</span><span class="sxs-lookup"><span data-stu-id="1cae7-123">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="1cae7-124">Členy třídy nemůže mít podpisy, které se liší pouze `ref`, `in`, nebo `out`.</span><span class="sxs-lookup"><span data-stu-id="1cae7-124">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="1cae7-125">Chyba kompilátoru nastane, pokud jediným rozdílem mezi dva členy typu je, že jedna z nich má `ref` má parametr a druhý `out`, nebo `in` parametru.</span><span class="sxs-lookup"><span data-stu-id="1cae7-125">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="1cae7-126">Například následující kód, nebude kompilovat.</span><span class="sxs-lookup"><span data-stu-id="1cae7-126">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="1cae7-127">Však metody mohou být přetíženy, když má jednu metodu `ref`, `in`, nebo `out` parametr a druhý je hodnota parametru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1cae7-127">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="1cae7-128">V jiných situacích, které vyžadují párování podpis, například přepsání, zobrazení nebo skrytí `in`, `ref`, a `out` jsou součást podpisu a navzájem neodpovídají.</span><span class="sxs-lookup"><span data-stu-id="1cae7-128">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="1cae7-129">Vlastnosti nejsou proměnné.</span><span class="sxs-lookup"><span data-stu-id="1cae7-129">Properties are not variables.</span></span> <span data-ttu-id="1cae7-130">Jsou metody a nelze předat `ref` parametry.</span><span class="sxs-lookup"><span data-stu-id="1cae7-130">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="1cae7-131">Nelze použít `ref`, `in`, a `out` klíčová slova pro následující druhy metod:</span><span class="sxs-lookup"><span data-stu-id="1cae7-131">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="1cae7-132">Asynchronní metody, které definujete pomocí [asynchronní](async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="1cae7-132">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="1cae7-133">Metody iterátorů, mezi které patří [yield return](yield.md) nebo `yield break` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1cae7-133">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="1cae7-134">Předání argumentu podle odkazu: Příklad</span><span class="sxs-lookup"><span data-stu-id="1cae7-134">Passing an argument by reference: An example</span></span>

<span data-ttu-id="1cae7-135">V předchozích příkladech předávání typů hodnot pomocí odkazu.</span><span class="sxs-lookup"><span data-stu-id="1cae7-135">The previous examples pass value types by reference.</span></span> <span data-ttu-id="1cae7-136">Můžete také použít `ref` – klíčové slovo k předání referenční typy podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="1cae7-136">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="1cae7-137">Typ odkazu předávání odkazem umožňuje volané metody k nahrazení objektu, na které odkazuje parametr odkazu volajícího.</span><span class="sxs-lookup"><span data-stu-id="1cae7-137">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="1cae7-138">Umístění úložiště objekt je předán metodě jako hodnota parametru odkazu.</span><span class="sxs-lookup"><span data-stu-id="1cae7-138">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="1cae7-139">Pokud změníte hodnotu v umístění úložiště parametru (tak, aby odkazoval na nový objekt), také změnit umístění úložiště, na který odkazuje volající.</span><span class="sxs-lookup"><span data-stu-id="1cae7-139">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="1cae7-140">Následující příklad předá instance typu odkaz jako `ref` parametru.</span><span class="sxs-lookup"><span data-stu-id="1cae7-140">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="1cae7-141">Další informace o tom, jak předat typy odkazů podle hodnoty a podle reference najdete v tématu [předávání parametrů typu odkazu](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="1cae7-141">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="1cae7-142">Referenční návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="1cae7-142">Reference return values</span></span>

<span data-ttu-id="1cae7-143">Referenční návratové hodnoty (nebo návratové) jsou hodnoty, které metoda vrací odkazem na volajícího.</span><span class="sxs-lookup"><span data-stu-id="1cae7-143">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="1cae7-144">To znamená že volající může změnit hodnotu, vrací metoda, a tato změna se projeví ve stavu objektu, který obsahuje metodu.</span><span class="sxs-lookup"><span data-stu-id="1cae7-144">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="1cae7-145">Vrátí odkaz hodnota je definována pomocí `ref` – klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="1cae7-145">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="1cae7-146">V podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="1cae7-146">In the method signature.</span></span> <span data-ttu-id="1cae7-147">Například následující podpis metody Určuje, že `GetCurrentPrice` metoda vrátí hodnotu <xref:System.Decimal> hodnota podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="1cae7-147">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="1cae7-148">Mezi `return` token a vrácené v proměnné `return` příkaz v metodě.</span><span class="sxs-lookup"><span data-stu-id="1cae7-148">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="1cae7-149">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1cae7-149">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="1cae7-150">Aby volající změnit stav objektu, vrátit hodnota musí být uložen do proměnné, která není výslovně uveden jako odkaz [lokální proměnná podle odkazu](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="1cae7-150">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="1cae7-151">Volané metody mohou také deklarovat jako návratová hodnota `ref readonly` vracet hodnotu odkazem a vynutit, aby volající kód nelze změnit vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1cae7-151">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="1cae7-152">Volání metody se můžete vyhnout kopírování vrácené oceňují uložení hodnoty v místním [jen pro čtení ref](#ref-readonly-locals) proměnné.</span><span class="sxs-lookup"><span data-stu-id="1cae7-152">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="1cae7-153">Příklad najdete v tématu [A návratové a příklad místní hodnoty ref](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="1cae7-153">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="1cae7-154">Místní referenční hodnoty</span><span class="sxs-lookup"><span data-stu-id="1cae7-154">Ref locals</span></span>

<span data-ttu-id="1cae7-155">Lokální proměnná ref se používá k odkazování na hodnoty, které jsou vráceny za použití `return ref`.</span><span class="sxs-lookup"><span data-stu-id="1cae7-155">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="1cae7-156">Lokální proměnná ref nejde inicializovat na návratovou hodnotu bez ref.</span><span class="sxs-lookup"><span data-stu-id="1cae7-156">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="1cae7-157">Jinými slovy pravou stranu inicializace musí být odkaz.</span><span class="sxs-lookup"><span data-stu-id="1cae7-157">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="1cae7-158">Všechny změny na hodnotu lokální proměnnou se projeví ve stavu objektu, jehož metoda vrátila hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="1cae7-158">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="1cae7-159">Definice lokální proměnnou s použitím `ref` – klíčové slovo před deklaraci proměnné, stejně jako bezprostředně před volání metody, která vrátí hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="1cae7-159">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="1cae7-160">Například následující příkaz definuje ref místní hodnotu, která je vrácena metodou s názvem `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="1cae7-160">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="1cae7-161">Stejným způsobem můžete přistupovat hodnota podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="1cae7-161">You can access a value by reference in the same way.</span></span> <span data-ttu-id="1cae7-162">V některých případech se přístup k hodnota podle odkazu zvyšuje výkon se vyhnout operaci kopírování potenciálně nákladné.</span><span class="sxs-lookup"><span data-stu-id="1cae7-162">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="1cae7-163">Následující příkaz například ukazuje, jak jeden můžete definovat, který se používá k odkazování hodnotu lokální hodnota ref.</span><span class="sxs-lookup"><span data-stu-id="1cae7-163">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="1cae7-164">Všimněte si, že v obou příkladech `ref` – klíčové slovo musí být použit v obou místech, nebo kompilátor vygeneruje chybu CS8172 "Nelze inicializovat proměnnou podle odkazu s hodnotou".</span><span class="sxs-lookup"><span data-stu-id="1cae7-164">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="1cae7-165">Počínaje C# 7.3, proměnné iterace `foreach` příkaz může být lokální proměnnou nebo místní proměnná jen pro čtení ref.</span><span class="sxs-lookup"><span data-stu-id="1cae7-165">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="1cae7-166">Další informace najdete v tématu [výraz foreach](foreach-in.md) článku.</span><span class="sxs-lookup"><span data-stu-id="1cae7-166">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="1cae7-167">místních jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1cae7-167">Ref readonly locals</span></span>

<span data-ttu-id="1cae7-168">Lokální proměnná podle odkazu jen pro čtení se používá k odkazování na hodnoty, vrátí metoda nebo vlastnost, která má `ref readonly` v jeho podpis a používá `return ref`.</span><span class="sxs-lookup"><span data-stu-id="1cae7-168">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="1cae7-169">A `ref readonly` proměnné kombinuje vlastnosti `ref` místní proměnná se `readonly` proměnná: je alias do úložiště je přiřazen, a nemůže být upraven.</span><span class="sxs-lookup"><span data-stu-id="1cae7-169">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span> 

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="1cae7-170">A návratové a příklad místní hodnoty ref</span><span class="sxs-lookup"><span data-stu-id="1cae7-170">A ref returns and ref locals example</span></span>

<span data-ttu-id="1cae7-171">Následující příklad definuje `Book` třídu, která má dvě <xref:System.String> pole, `Title` a `Author`.</span><span class="sxs-lookup"><span data-stu-id="1cae7-171">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="1cae7-172">Definuje také `BookCollection` třídu, která obsahuje privátní pole `Book` objekty.</span><span class="sxs-lookup"><span data-stu-id="1cae7-172">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="1cae7-173">Jednotlivé knihy objekty jsou vráceny ve vztahu voláním jeho `GetBookByTitle` metoda.</span><span class="sxs-lookup"><span data-stu-id="1cae7-173">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="1cae7-174">Pokud volající uloží hodnoty vrácené `GetBookByTitle` změny, které umožňuje volajícímu návratovou hodnotu metody jako lokální proměnná podle odkazu, se projeví v `BookCollection` objektu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="1cae7-174">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a><span data-ttu-id="1cae7-175">Typy struktury REF</span><span class="sxs-lookup"><span data-stu-id="1cae7-175">Ref struct types</span></span>

<span data-ttu-id="1cae7-176">Přidávání `ref` modifikátor `struct` prohlášení definuje, že instance tohoto typu musí být přiděleny.</span><span class="sxs-lookup"><span data-stu-id="1cae7-176">Adding the `ref` modifier to a `struct` declaration defines that instances of that type must be stack allocated.</span></span> <span data-ttu-id="1cae7-177">Jinými slovy instancí těchto typů může nikdy být vytvořen na haldě jako člena jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="1cae7-177">In other words, instances of these types can never be created on the heap as a member of another class.</span></span> <span data-ttu-id="1cae7-178">Byl primární motivace pro tuto funkci <xref:System.Span%601> a související struktury.</span><span class="sxs-lookup"><span data-stu-id="1cae7-178">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span>

<span data-ttu-id="1cae7-179">Cílem vedení `ref struct` zadejte jako proměnnou přidělený na zásobník zavádí několik pravidel, které kompilátor vynucuje pro všechny `ref struct` typy.</span><span class="sxs-lookup"><span data-stu-id="1cae7-179">The goal of keeping a `ref struct` type as a stack-allocated variable introduces several rules that the compiler enforces for all `ref struct` types.</span></span>

- <span data-ttu-id="1cae7-180">Nelze pole `ref struct`.</span><span class="sxs-lookup"><span data-stu-id="1cae7-180">You can't box a `ref struct`.</span></span> <span data-ttu-id="1cae7-181">Nelze přiřadit `ref struct` typ proměnné typu `object`, `dynamic`, nebo libovolný typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1cae7-181">You cannot assign a `ref struct` type to a variable of type `object`, `dynamic`, or any interface type.</span></span>
- <span data-ttu-id="1cae7-182">`ref struct` typy nemůžou implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1cae7-182">`ref struct` types cannot implement interfaces.</span></span>
- <span data-ttu-id="1cae7-183">Nelze deklarovat `ref struct` jako člen třídy nebo struktury normální.</span><span class="sxs-lookup"><span data-stu-id="1cae7-183">You can't declare a `ref struct` as a member of a class or a normal struct.</span></span>
- <span data-ttu-id="1cae7-184">Nelze deklarovat lokální proměnné, které jsou `ref struct` typy v asynchronních metodách.</span><span class="sxs-lookup"><span data-stu-id="1cae7-184">You cannot declare local variables that are `ref struct` types in async methods.</span></span> <span data-ttu-id="1cae7-185">Můžete je deklarovat v synchronní metody, které vracejí <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> nebo `Task`– typy, jako je.</span><span class="sxs-lookup"><span data-stu-id="1cae7-185">You can declare them in synchronous methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> or `Task`-like types.</span></span>
- <span data-ttu-id="1cae7-186">Nelze deklarovat `ref struct` lokální proměnné iterátory.</span><span class="sxs-lookup"><span data-stu-id="1cae7-186">You cannot declare `ref struct` local variables in iterators.</span></span>
- <span data-ttu-id="1cae7-187">Nelze zachytit `ref struct` proměnné ve výrazech lambda nebo místní funkce.</span><span class="sxs-lookup"><span data-stu-id="1cae7-187">You cannot capture `ref struct` variables in lambda expressions or local functions.</span></span>

<span data-ttu-id="1cae7-188">Tato omezení zajistit nepoužívejte omylem `ref struct` způsobem, který může převést na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="1cae7-188">These restrictions ensure you don't accidentally use a `ref struct` in a manner that could promote it to the managed heap.</span></span>

<span data-ttu-id="1cae7-189">Můžete kombinovat modifikátory pro deklaraci struktury jako `readonly ref`.</span><span class="sxs-lookup"><span data-stu-id="1cae7-189">You can combine modifiers to declare a struct as `readonly ref`.</span></span> <span data-ttu-id="1cae7-190">A `readonly ref struct` kombinuje výhody a omezení `ref struct` a `readonly struct` deklarace.</span><span class="sxs-lookup"><span data-stu-id="1cae7-190">A `readonly ref struct` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1cae7-191">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1cae7-191">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1cae7-192">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1cae7-192">See also</span></span>

- [<span data-ttu-id="1cae7-193">Psát bezpečný kód efektivní</span><span class="sxs-lookup"><span data-stu-id="1cae7-193">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="1cae7-194">Návratové a místní referenční hodnoty</span><span class="sxs-lookup"><span data-stu-id="1cae7-194">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="1cae7-195">Ref podmíněný výraz</span><span class="sxs-lookup"><span data-stu-id="1cae7-195">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="1cae7-196">operátoru přiřazení odkazu</span><span class="sxs-lookup"><span data-stu-id="1cae7-196">ref assignment operator</span></span>](../operators/assignment-operator.md#ref-assignment-operator)
- [<span data-ttu-id="1cae7-197">Předávání parametrů</span><span class="sxs-lookup"><span data-stu-id="1cae7-197">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="1cae7-198">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="1cae7-198">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="1cae7-199">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1cae7-199">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1cae7-200">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1cae7-200">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1cae7-201">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1cae7-201">C# Keywords</span></span>](index.md)
