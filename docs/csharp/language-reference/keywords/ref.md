---
title: ref – C# klíčové slovo Reference
ms.custom: seodec18
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: f11137b3c13bb9e8670c4df25fedf3251724a088
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566895"
---
# <a name="ref-c-reference"></a><span data-ttu-id="b7a54-102">ref (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b7a54-102">ref (C# Reference)</span></span>

<span data-ttu-id="b7a54-103">`ref` Klíčové slovo označuje hodnotu, která je předána odkazem.</span><span class="sxs-lookup"><span data-stu-id="b7a54-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="b7a54-104">Používá se ve čtyřech různých kontextech:</span><span class="sxs-lookup"><span data-stu-id="b7a54-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="b7a54-105">V signatuře metody a ve volání metody předejte argument metodě odkazem.</span><span class="sxs-lookup"><span data-stu-id="b7a54-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="b7a54-106">Další informace naleznete v tématu [předání argumentu odkazem](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="b7a54-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="b7a54-107">V signatuře metody pro vrácení hodnoty volajícímu odkazem.</span><span class="sxs-lookup"><span data-stu-id="b7a54-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="b7a54-108">Další informace najdete v tématu [referenční návratové hodnoty](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="b7a54-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="b7a54-109">V těle člena, aby označoval, že návratová hodnota odkazu je uložená místně jako odkaz, který volající chce změnit, nebo obecně místní proměnná přistupuje k jiné hodnotě odkazem.</span><span class="sxs-lookup"><span data-stu-id="b7a54-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="b7a54-110">Další informace naleznete v tématu [místní hodnoty REF](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="b7a54-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="b7a54-111">V deklaraci pro `ref struct` deklaraci nebo `readonly ref struct`. `struct`</span><span class="sxs-lookup"><span data-stu-id="b7a54-111">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="b7a54-112">Další informace naleznete v tématu [typy referenční struktury](#ref-struct-types).</span><span class="sxs-lookup"><span data-stu-id="b7a54-112">For more information, see [ref struct types](#ref-struct-types).</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="b7a54-113">Předání argumentu odkazem</span><span class="sxs-lookup"><span data-stu-id="b7a54-113">Passing an argument by reference</span></span>

<span data-ttu-id="b7a54-114">Při použití v seznamu `ref` parametrů metody označuje klíčové slovo, že argument je předán odkazem, nikoli hodnotou.</span><span class="sxs-lookup"><span data-stu-id="b7a54-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="b7a54-115">`ref` Klíčové slovo nastaví formální parametr jako alias pro argument, který musí být proměnná.</span><span class="sxs-lookup"><span data-stu-id="b7a54-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="b7a54-116">Jinými slovy, každá operace s parametrem je provedena na argumentu.</span><span class="sxs-lookup"><span data-stu-id="b7a54-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="b7a54-117">Například pokud volající předává výraz místní proměnné nebo výraz přístupu k elementu pole a volaná metoda nahradí objekt, na který odkazuje parametr ref, pak místní proměnná volajícího nebo prvek pole nyní odkazuje na nový objekt, když Metoda vrací.</span><span class="sxs-lookup"><span data-stu-id="b7a54-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="b7a54-118">Nepleťte si koncept předávání odkazem s konceptem typů odkazů.</span><span class="sxs-lookup"><span data-stu-id="b7a54-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="b7a54-119">Tyto dvě koncepce nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="b7a54-119">The two concepts are not the same.</span></span> <span data-ttu-id="b7a54-120">Parametr metody lze změnit `ref` bez ohledu na to, zda se jedná o typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="b7a54-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="b7a54-121">Pokud je předána odkazem, není k dispozici žádný zabalení typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b7a54-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="b7a54-122">Chcete-li `ref` použít parametr, definice metody a volající metoda musí explicitně `ref` používat klíčové slovo, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b7a54-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="b7a54-123">Argument, který je předán `ref` parametru nebo `in` , musí být inicializován před předáním.</span><span class="sxs-lookup"><span data-stu-id="b7a54-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="b7a54-124">To se liší od parametrů [out](out-parameter-modifier.md) , jejichž argumenty není nutné před předáním explicitně inicializovat.</span><span class="sxs-lookup"><span data-stu-id="b7a54-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="b7a54-125">Členové třídy nemohou mít signatury, které se liší pouze `ref`pomocí `in`, nebo `out`.</span><span class="sxs-lookup"><span data-stu-id="b7a54-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="b7a54-126">K chybě kompilátoru dojde, pokud jediným rozdílem mezi dvěma členy typu je, že jeden z nich má `ref` parametr a druhý `out`má parametr, nebo `in` .</span><span class="sxs-lookup"><span data-stu-id="b7a54-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="b7a54-127">Následující kód například není zkompilován.</span><span class="sxs-lookup"><span data-stu-id="b7a54-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="b7a54-128">Nicméně metody mohou být přetíženy v případě `ref`, že jedna metoda má parametr, `in`nebo `out` a druhá má parametr hodnoty, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b7a54-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="b7a54-129">V jiných situacích, které vyžadují porovnávání signatur, jako je například skrytí nebo `in`přepsání `ref`,, `out` a jsou součástí podpisu a vzájemně se neshodují.</span><span class="sxs-lookup"><span data-stu-id="b7a54-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="b7a54-130">Vlastnosti nejsou proměnné.</span><span class="sxs-lookup"><span data-stu-id="b7a54-130">Properties are not variables.</span></span> <span data-ttu-id="b7a54-131">Jsou to metody a nelze je předat `ref` parametrům.</span><span class="sxs-lookup"><span data-stu-id="b7a54-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="b7a54-132">Klíčová slova `ref`, `in`a `out` nelze použít pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="b7a54-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="b7a54-133">Asynchronní metody, které definujete pomocí modifikátoru [Async](async.md) .</span><span class="sxs-lookup"><span data-stu-id="b7a54-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="b7a54-134">Metody iterátoru, které zahrnují [návratový návrat](yield.md) nebo `yield break` příkaz yield.</span><span class="sxs-lookup"><span data-stu-id="b7a54-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="b7a54-135">Předání argumentu odkazem: Příklad</span><span class="sxs-lookup"><span data-stu-id="b7a54-135">Passing an argument by reference: An example</span></span>

<span data-ttu-id="b7a54-136">Předchozí příklady přecházejí typu hodnoty odkazem.</span><span class="sxs-lookup"><span data-stu-id="b7a54-136">The previous examples pass value types by reference.</span></span> <span data-ttu-id="b7a54-137">Můžete také použít `ref` klíčové slovo k předání typu odkazu odkazem.</span><span class="sxs-lookup"><span data-stu-id="b7a54-137">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="b7a54-138">Předání typu odkazu odkazem umožňuje volané metodě nahradit objekt, na který odkazuje parametr reference v volajícím.</span><span class="sxs-lookup"><span data-stu-id="b7a54-138">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="b7a54-139">Umístění úložiště objektu je předáno metodě jako hodnota referenčního parametru.</span><span class="sxs-lookup"><span data-stu-id="b7a54-139">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="b7a54-140">Změníte-li hodnotu v umístění úložiště parametru (aby odkazovala na nový objekt), můžete také změnit umístění úložiště, do kterého se volající odkazuje.</span><span class="sxs-lookup"><span data-stu-id="b7a54-140">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="b7a54-141">Následující příklad předává instanci typu odkazu jako `ref` parametr.</span><span class="sxs-lookup"><span data-stu-id="b7a54-141">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="b7a54-142">Další informace o tom, jak předat typy odkazů podle hodnoty a odkazu, naleznete v tématu [předávání parametrů typu odkazu](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b7a54-142">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="b7a54-143">Referenční návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="b7a54-143">Reference return values</span></span>

<span data-ttu-id="b7a54-144">Návratové hodnoty odkazu (nebo ref vrátí) jsou hodnoty, které metoda vrátí odkazem na volajícího.</span><span class="sxs-lookup"><span data-stu-id="b7a54-144">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="b7a54-145">To znamená, že volající může změnit hodnotu vrácenou metodou a tato změna se projeví ve stavu objektu, který obsahuje metodu.</span><span class="sxs-lookup"><span data-stu-id="b7a54-145">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="b7a54-146">Návratová hodnota odkazu je definována pomocí `ref` klíčového slova:</span><span class="sxs-lookup"><span data-stu-id="b7a54-146">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="b7a54-147">V signatuře metody.</span><span class="sxs-lookup"><span data-stu-id="b7a54-147">In the method signature.</span></span> <span data-ttu-id="b7a54-148">Například následující signatura metody označuje, že `GetCurrentPrice` metoda <xref:System.Decimal> vrací hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="b7a54-148">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="b7a54-149">Mezi tokenem a proměnnou vrácenou `return` v příkazu v metodě. `return`</span><span class="sxs-lookup"><span data-stu-id="b7a54-149">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="b7a54-150">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b7a54-150">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="b7a54-151">Aby mohl volající změnit stav objektu, návratová hodnota odkazu musí být uložena do proměnné, která je explicitně definována jako [místní referenční](#ref-locals)číslo.</span><span class="sxs-lookup"><span data-stu-id="b7a54-151">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="b7a54-152">Volaná metoda může také deklarovat návratovou hodnotu `ref readonly` tak, aby vracela hodnotu odkazem a vynutila, že volající kód nemůže změnit vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b7a54-152">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="b7a54-153">Volající metoda se může vyhnout zkopírování vracené hodnoty tím, že uloží hodnotu v proměnné s [parametrem ReadOnly](#ref-readonly-locals) .</span><span class="sxs-lookup"><span data-stu-id="b7a54-153">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="b7a54-154">Příklad naleznete v části [ref Returns a lokální hodnoty REF](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="b7a54-154">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="b7a54-155">Lokální hodnoty REF</span><span class="sxs-lookup"><span data-stu-id="b7a54-155">Ref locals</span></span>

<span data-ttu-id="b7a54-156">Lokální proměnná ref slouží k odkazování na hodnoty vrácené pomocí `return ref`.</span><span class="sxs-lookup"><span data-stu-id="b7a54-156">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="b7a54-157">Lokální proměnnou ref nelze inicializovat pro návratovou hodnotu, která není ref.</span><span class="sxs-lookup"><span data-stu-id="b7a54-157">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="b7a54-158">Jinými slovy, pravé straně inicializace musí být odkaz.</span><span class="sxs-lookup"><span data-stu-id="b7a54-158">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="b7a54-159">Jakékoli úpravy hodnoty lokálního odkazu se projeví ve stavu objektu, jehož metoda vrátila hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="b7a54-159">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="b7a54-160">Místní odkaz definujete pomocí `ref` klíčového slova před deklaraci proměnné, stejně jako bezprostředně před voláním metody, která vrací hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="b7a54-160">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="b7a54-161">Například následující příkaz definuje místní hodnotu REF, která je vrácena metodou s názvem `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="b7a54-161">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="b7a54-162">K hodnotě můžete přistupovat stejným způsobem pomocí odkazu.</span><span class="sxs-lookup"><span data-stu-id="b7a54-162">You can access a value by reference in the same way.</span></span> <span data-ttu-id="b7a54-163">V některých případech přístup k hodnotě pomocí odkazu zvyšuje výkon tím, že se vyhne potenciálně nákladné operaci kopírování.</span><span class="sxs-lookup"><span data-stu-id="b7a54-163">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="b7a54-164">Například následující příkaz ukazuje, jak může jeden definovat místní hodnotu REF, která se používá k odkazování na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b7a54-164">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="b7a54-165">Všimněte si, že v obou `ref` příkladech je klíčové slovo nutné použít na obou místech, nebo kompilátor generuje chybu CS8172, "" nemůže inicializovat proměnnou podle odkazu s hodnotou. "</span><span class="sxs-lookup"><span data-stu-id="b7a54-165">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="b7a54-166">Počínaje C# 7,3 se proměnná `foreach` iterace příkazu může jednat o místní proměnnou ref nebo ref jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="b7a54-166">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="b7a54-167">Další informace naleznete v článku o [příkazu foreach](foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="b7a54-167">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="b7a54-168">Místní referenční hodnoty jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b7a54-168">Ref readonly locals</span></span>

<span data-ttu-id="b7a54-169">Místní odkaz jen pro čtení se používá k odkazování na hodnoty vracené metodou nebo vlastností, `ref readonly` která má jeho signaturu `return ref`a používá.</span><span class="sxs-lookup"><span data-stu-id="b7a54-169">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="b7a54-170">Proměnná kombinuje vlastnosti `ref` místní proměnné s `readonly` proměnnou: Jedná se o alias úložiště, ke kterému je přiřazený, a nedá se změnit. `ref readonly`</span><span class="sxs-lookup"><span data-stu-id="b7a54-170">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span> 

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="b7a54-171">Příklad odkazů vrátí a místní hodnoty REF</span><span class="sxs-lookup"><span data-stu-id="b7a54-171">A ref returns and ref locals example</span></span>

<span data-ttu-id="b7a54-172">Následující příklad definuje `Book` třídu, která má dvě <xref:System.String> pole `Title` a `Author`.</span><span class="sxs-lookup"><span data-stu-id="b7a54-172">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="b7a54-173">Definuje `BookCollection` také třídu, která obsahuje soukromé `Book` pole objektů.</span><span class="sxs-lookup"><span data-stu-id="b7a54-173">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="b7a54-174">Jednotlivé objekty knihy jsou vráceny odkazem voláním její `GetBookByTitle` metody.</span><span class="sxs-lookup"><span data-stu-id="b7a54-174">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="b7a54-175">Když volající ukládá hodnotu vrácenou `GetBookByTitle` metodou jako místní referenční číslo, změny, které volající provede na vrácenou hodnotu, se projeví `BookCollection` v objektu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="b7a54-175">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a><span data-ttu-id="b7a54-176">Typy referenční struktury</span><span class="sxs-lookup"><span data-stu-id="b7a54-176">Ref struct types</span></span>

<span data-ttu-id="b7a54-177">Přidání modifikátoru `struct` k deklaraci definuje, že instance daného typu musí být přiděleny zásobníku. `ref`</span><span class="sxs-lookup"><span data-stu-id="b7a54-177">Adding the `ref` modifier to a `struct` declaration defines that instances of that type must be stack allocated.</span></span> <span data-ttu-id="b7a54-178">Jinými slovy, instance těchto typů nelze nikdy vytvořit v haldě jako člen jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="b7a54-178">In other words, instances of these types can never be created on the heap as a member of another class.</span></span> <span data-ttu-id="b7a54-179">Primární motivace pro tuto funkci byla <xref:System.Span%601> a související struktury.</span><span class="sxs-lookup"><span data-stu-id="b7a54-179">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span>

<span data-ttu-id="b7a54-180">Cílem zachování `ref struct` typu jako proměnné přidělené zásobníku je několik pravidel, která kompilátor vynutil pro všechny `ref struct` typy.</span><span class="sxs-lookup"><span data-stu-id="b7a54-180">The goal of keeping a `ref struct` type as a stack-allocated variable introduces several rules that the compiler enforces for all `ref struct` types.</span></span>

- <span data-ttu-id="b7a54-181">Nemůžete pole `ref struct`a.</span><span class="sxs-lookup"><span data-stu-id="b7a54-181">You can't box a `ref struct`.</span></span> <span data-ttu-id="b7a54-182">Nelze přiřadit `ref struct` typ k proměnné typu `object`, `dynamic`nebo žádnému typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b7a54-182">You cannot assign a `ref struct` type to a variable of type `object`, `dynamic`, or any interface type.</span></span>
- <span data-ttu-id="b7a54-183">`ref struct`typy nemohou implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b7a54-183">`ref struct` types cannot implement interfaces.</span></span>
- <span data-ttu-id="b7a54-184">Nelze deklarovat `ref struct` jako člena pole třídy nebo normální struktury.</span><span class="sxs-lookup"><span data-stu-id="b7a54-184">You can't declare a `ref struct` as a field member of a class or a normal struct.</span></span> <span data-ttu-id="b7a54-185">To zahrnuje deklaraci automaticky implementované vlastnosti, která vytvoří pole pro zálohování generované kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="b7a54-185">This includes declaring an auto-implemented property, which creates a compiler generated backing field.</span></span> 
- <span data-ttu-id="b7a54-186">Nelze deklarovat lokální proměnné, které jsou `ref struct` typy v asynchronních metodách.</span><span class="sxs-lookup"><span data-stu-id="b7a54-186">You cannot declare local variables that are `ref struct` types in async methods.</span></span> <span data-ttu-id="b7a54-187">Můžete je deklarovat v synchronních metodách, <xref:System.Threading.Tasks.Task>které <xref:System.Threading.Tasks.Task%601> vracejí `Task`nebo jako typy.</span><span class="sxs-lookup"><span data-stu-id="b7a54-187">You can declare them in synchronous methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> or `Task`-like types.</span></span>
- <span data-ttu-id="b7a54-188">V iterátorech `ref struct` nelze deklarovat lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="b7a54-188">You cannot declare `ref struct` local variables in iterators.</span></span>
- <span data-ttu-id="b7a54-189">Nemůžete `ref struct` zachytit proměnné ve výrazech lambda nebo místních funkcích.</span><span class="sxs-lookup"><span data-stu-id="b7a54-189">You cannot capture `ref struct` variables in lambda expressions or local functions.</span></span>

<span data-ttu-id="b7a54-190">Tato omezení zajišťují, že nechtěně nepoužíváte `ref struct` způsobem, který by ho mohl zvýšit na spravovanou haldu.</span><span class="sxs-lookup"><span data-stu-id="b7a54-190">These restrictions ensure you don't accidentally use a `ref struct` in a manner that could promote it to the managed heap.</span></span>

<span data-ttu-id="b7a54-191">Můžete kombinovat modifikátory a deklarovat strukturu jako `readonly ref`.</span><span class="sxs-lookup"><span data-stu-id="b7a54-191">You can combine modifiers to declare a struct as `readonly ref`.</span></span> <span data-ttu-id="b7a54-192">Kombinuje výhody a `ref struct` omezení a `readonly struct` deklarace. `readonly ref struct`</span><span class="sxs-lookup"><span data-stu-id="b7a54-192">A `readonly ref struct` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b7a54-193">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b7a54-193">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b7a54-194">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7a54-194">See also</span></span>

- [<span data-ttu-id="b7a54-195">Zapisovat bezpečný efektivní kód</span><span class="sxs-lookup"><span data-stu-id="b7a54-195">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="b7a54-196">Návratové a místní referenční hodnoty</span><span class="sxs-lookup"><span data-stu-id="b7a54-196">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="b7a54-197">Podmíněný výraz ref</span><span class="sxs-lookup"><span data-stu-id="b7a54-197">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="b7a54-198">operátor přiřazení ref</span><span class="sxs-lookup"><span data-stu-id="b7a54-198">ref assignment operator</span></span>](../operators/assignment-operator.md#ref-assignment-operator)
- [<span data-ttu-id="b7a54-199">Předávání parametrů</span><span class="sxs-lookup"><span data-stu-id="b7a54-199">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="b7a54-200">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="b7a54-200">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="b7a54-201">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="b7a54-201">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b7a54-202">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b7a54-202">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b7a54-203">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b7a54-203">C# Keywords</span></span>](index.md)
