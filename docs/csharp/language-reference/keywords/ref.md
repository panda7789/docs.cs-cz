---
description: ref – klíčové slovo – Reference jazyka C#
title: ref – klíčové slovo – Reference jazyka C#
ms.date: 04/21/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 58a4ce30e11ca023b50e5e53b1f1554a30d44390
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137081"
---
# <a name="ref-c-reference"></a><span data-ttu-id="62a29-103">ref (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="62a29-103">ref (C# Reference)</span></span>

<span data-ttu-id="62a29-104">`ref`Klíčové slovo označuje hodnotu, která je předána odkazem.</span><span class="sxs-lookup"><span data-stu-id="62a29-104">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="62a29-105">Používá se ve čtyřech různých kontextech:</span><span class="sxs-lookup"><span data-stu-id="62a29-105">It is used in four different contexts:</span></span>

- <span data-ttu-id="62a29-106">V signatuře metody a ve volání metody předejte argument metodě odkazem.</span><span class="sxs-lookup"><span data-stu-id="62a29-106">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="62a29-107">Další informace naleznete v tématu [předání argumentu odkazem](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="62a29-107">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="62a29-108">V signatuře metody pro vrácení hodnoty volajícímu odkazem.</span><span class="sxs-lookup"><span data-stu-id="62a29-108">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="62a29-109">Další informace najdete v tématu [referenční návratové hodnoty](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="62a29-109">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="62a29-110">V těle člena, aby označoval, že návratová hodnota odkazu je uložená místně jako odkaz, který volající chce změnit, nebo obecně místní proměnná přistupuje k jiné hodnotě odkazem.</span><span class="sxs-lookup"><span data-stu-id="62a29-110">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="62a29-111">Další informace naleznete v tématu [místní hodnoty REF](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="62a29-111">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="62a29-112">V `struct` deklaraci pro deklaraci `ref struct` nebo `readonly ref struct` .</span><span class="sxs-lookup"><span data-stu-id="62a29-112">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="62a29-113">Další informace naleznete [ `ref` v části struktura v článku](../builtin-types/struct.md#ref-struct) [typy struktury](../builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="62a29-113">For more information, see the [`ref` struct](../builtin-types/struct.md#ref-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="62a29-114">Předání argumentu odkazem</span><span class="sxs-lookup"><span data-stu-id="62a29-114">Passing an argument by reference</span></span>

<span data-ttu-id="62a29-115">Při použití v seznamu parametrů metody `ref` označuje klíčové slovo, že argument je předán odkazem, nikoli hodnotou.</span><span class="sxs-lookup"><span data-stu-id="62a29-115">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="62a29-116">`ref`Klíčové slovo nastaví formální parametr jako alias pro argument, který musí být proměnná.</span><span class="sxs-lookup"><span data-stu-id="62a29-116">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="62a29-117">Jinými slovy, každá operace s parametrem je provedena na argumentu.</span><span class="sxs-lookup"><span data-stu-id="62a29-117">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="62a29-118">Například pokud volající předává výraz místní proměnné nebo výraz přístupu k elementu pole a volaná metoda nahradí objekt, na který odkazuje parametr ref, pak místní proměnná volajícího nebo prvek pole nyní odkazuje na nový objekt, když se metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="62a29-118">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller's local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="62a29-119">Nepleťte si koncept předávání odkazem s konceptem typů odkazů.</span><span class="sxs-lookup"><span data-stu-id="62a29-119">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="62a29-120">Tyto dvě koncepce nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="62a29-120">The two concepts are not the same.</span></span> <span data-ttu-id="62a29-121">Parametr metody lze změnit `ref` bez ohledu na to, zda se jedná o typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="62a29-121">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="62a29-122">Pokud je předána odkazem, není k dispozici žádný zabalení typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="62a29-122">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="62a29-123">Chcete-li použít `ref` parametr, definice metody a volající metoda musí explicitně používat `ref` klíčové slovo, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="62a29-123">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="62a29-124">Argument, který je předán `ref` parametru nebo, `in` musí být inicializován před předáním.</span><span class="sxs-lookup"><span data-stu-id="62a29-124">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="62a29-125">To se liší od parametrů [out](out-parameter-modifier.md) , jejichž argumenty není nutné před předáním explicitně inicializovat.</span><span class="sxs-lookup"><span data-stu-id="62a29-125">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="62a29-126">Členové třídy nemohou mít signatury, které se liší pouze pomocí `ref` , `in` nebo `out` .</span><span class="sxs-lookup"><span data-stu-id="62a29-126">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="62a29-127">K chybě kompilátoru dojde, pokud jediným rozdílem mezi dvěma členy typu je, že jeden z nich má `ref` parametr a druhý má `out` parametr, nebo `in` .</span><span class="sxs-lookup"><span data-stu-id="62a29-127">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="62a29-128">Následující kód například není zkompilován.</span><span class="sxs-lookup"><span data-stu-id="62a29-128">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="62a29-129">Nicméně metody mohou být přetíženy v případě, že jedna metoda má `ref` `in` parametr, nebo `out` a druhá má parametr hodnoty, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="62a29-129">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="62a29-130">V jiných situacích, které vyžadují porovnávání signatur, jako je například skrytí nebo přepsání,, `in` `ref` a `out` jsou součástí podpisu a vzájemně se neshodují.</span><span class="sxs-lookup"><span data-stu-id="62a29-130">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="62a29-131">Vlastnosti nejsou proměnné.</span><span class="sxs-lookup"><span data-stu-id="62a29-131">Properties are not variables.</span></span> <span data-ttu-id="62a29-132">Jsou to metody a nelze je předat `ref` parametrům.</span><span class="sxs-lookup"><span data-stu-id="62a29-132">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="62a29-133">`ref` `in` Klíčová slova, a nelze použít `out` pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="62a29-133">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="62a29-134">Asynchronní metody, které definujete pomocí modifikátoru [Async](async.md) .</span><span class="sxs-lookup"><span data-stu-id="62a29-134">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="62a29-135">Metody iterátoru, které zahrnují [návratový návrat](yield.md) nebo `yield break` příkaz yield.</span><span class="sxs-lookup"><span data-stu-id="62a29-135">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="62a29-136">Kromě toho [rozšiřující metody](../../programming-guide/classes-and-structs/extension-methods.md) mají následující omezení:</span><span class="sxs-lookup"><span data-stu-id="62a29-136">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="62a29-137">`out`Klíčové slovo nelze použít pro první argument metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="62a29-137">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="62a29-138">`ref`Klíčové slovo nelze použít u prvního argumentu metody rozšíření, pokud argument není struct nebo obecný typ, který není omezen na strukturu.</span><span class="sxs-lookup"><span data-stu-id="62a29-138">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="62a29-139">`in`Klíčové slovo nelze použít, pokud první argument není struktura.</span><span class="sxs-lookup"><span data-stu-id="62a29-139">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="62a29-140">`in`Klíčové slovo nelze použít pro žádný obecný typ, ani v případě, že je omezení typu struct.</span><span class="sxs-lookup"><span data-stu-id="62a29-140">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="62a29-141">Předání argumentu odkazem: příklad</span><span class="sxs-lookup"><span data-stu-id="62a29-141">Passing an argument by reference: An example</span></span>

<span data-ttu-id="62a29-142">Předchozí příklady přecházejí typu hodnoty odkazem.</span><span class="sxs-lookup"><span data-stu-id="62a29-142">The previous examples pass value types by reference.</span></span> <span data-ttu-id="62a29-143">Můžete také použít `ref` klíčové slovo k předání typu odkazu odkazem.</span><span class="sxs-lookup"><span data-stu-id="62a29-143">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="62a29-144">Předání typu odkazu odkazem umožňuje volané metodě nahradit objekt, na který odkazuje parametr reference v volajícím.</span><span class="sxs-lookup"><span data-stu-id="62a29-144">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="62a29-145">Umístění úložiště objektu je předáno metodě jako hodnota referenčního parametru.</span><span class="sxs-lookup"><span data-stu-id="62a29-145">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="62a29-146">Změníte-li hodnotu v umístění úložiště parametru (aby odkazovala na nový objekt), můžete také změnit umístění úložiště, do kterého se volající odkazuje.</span><span class="sxs-lookup"><span data-stu-id="62a29-146">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="62a29-147">Následující příklad předává instanci typu odkazu jako `ref` parametr.</span><span class="sxs-lookup"><span data-stu-id="62a29-147">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="62a29-148">Další informace o tom, jak předat typy odkazů podle hodnoty a odkazu, naleznete v tématu [předávání parametrů typu odkazu](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="62a29-148">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="62a29-149">Referenční návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="62a29-149">Reference return values</span></span>

<span data-ttu-id="62a29-150">Návratové hodnoty odkazu (nebo ref vrátí) jsou hodnoty, které metoda vrátí odkazem na volajícího.</span><span class="sxs-lookup"><span data-stu-id="62a29-150">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="62a29-151">To znamená, že volající může změnit hodnotu vrácenou metodou a tato změna se projeví ve stavu objektu v metodě volání.</span><span class="sxs-lookup"><span data-stu-id="62a29-151">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object in the calling method.</span></span>

<span data-ttu-id="62a29-152">Návratová hodnota odkazu je definována pomocí `ref` klíčového slova:</span><span class="sxs-lookup"><span data-stu-id="62a29-152">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="62a29-153">V signatuře metody.</span><span class="sxs-lookup"><span data-stu-id="62a29-153">In the method signature.</span></span> <span data-ttu-id="62a29-154">Například následující signatura metody označuje, že `GetCurrentPrice` metoda vrací <xref:System.Decimal> hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="62a29-154">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="62a29-155">Mezi `return` tokenem a proměnnou vrácenou v `return` příkazu v metodě.</span><span class="sxs-lookup"><span data-stu-id="62a29-155">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="62a29-156">Příklad:</span><span class="sxs-lookup"><span data-stu-id="62a29-156">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="62a29-157">Aby mohl volající změnit stav objektu, návratová hodnota odkazu musí být uložena do proměnné, která je explicitně definována jako [místní referenční](#ref-locals)číslo.</span><span class="sxs-lookup"><span data-stu-id="62a29-157">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="62a29-158">Zde je příklad uceleného návratového příkladu, který zobrazuje jak podpis metody, tak tělo metody.</span><span class="sxs-lookup"><span data-stu-id="62a29-158">Here is a more complete ref return example, showing both the method signature and method body.</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="62a29-159">Volaná metoda může také deklarovat návratovou hodnotu tak `ref readonly` , aby vracela hodnotu odkazem a vynutila, že volající kód nemůže změnit vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="62a29-159">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="62a29-160">Volající metoda se může vyhnout zkopírování vracené hodnoty tím, že uloží hodnotu v proměnné s [parametrem ReadOnly](#ref-readonly-locals) .</span><span class="sxs-lookup"><span data-stu-id="62a29-160">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="62a29-161">Příklad naleznete v části [ref Returns a lokální hodnoty REF](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="62a29-161">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="62a29-162">Lokální hodnoty REF</span><span class="sxs-lookup"><span data-stu-id="62a29-162">Ref locals</span></span>

<span data-ttu-id="62a29-163">Lokální proměnná ref slouží k odkazování na hodnoty vrácené pomocí `return ref` .</span><span class="sxs-lookup"><span data-stu-id="62a29-163">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="62a29-164">Lokální proměnnou ref nelze inicializovat pro návratovou hodnotu, která není ref.</span><span class="sxs-lookup"><span data-stu-id="62a29-164">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="62a29-165">Jinými slovy, pravá strana inicializace musí být odkazem.</span><span class="sxs-lookup"><span data-stu-id="62a29-165">In other words, the right-hand side of the initialization must be a reference.</span></span> <span data-ttu-id="62a29-166">Jakékoli úpravy hodnoty lokálního odkazu se projeví ve stavu objektu, jehož metoda vrátila hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="62a29-166">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="62a29-167">Místní odkaz definujete pomocí `ref` klíčového slova před deklaraci proměnné, stejně jako bezprostředně před voláním metody, která vrací hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="62a29-167">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="62a29-168">Například následující příkaz definuje místní hodnotu REF, která je vrácena metodou s názvem `GetEstimatedValue` :</span><span class="sxs-lookup"><span data-stu-id="62a29-168">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="62a29-169">K hodnotě můžete přistupovat stejným způsobem pomocí odkazu.</span><span class="sxs-lookup"><span data-stu-id="62a29-169">You can access a value by reference in the same way.</span></span> <span data-ttu-id="62a29-170">V některých případech přístup k hodnotě pomocí odkazu zvyšuje výkon tím, že se vyhne potenciálně nákladné operaci kopírování.</span><span class="sxs-lookup"><span data-stu-id="62a29-170">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="62a29-171">Například následující příkaz ukazuje, jak může jeden definovat místní hodnotu REF, která se používá k odkazování na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="62a29-171">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="62a29-172">V obou příkladech `ref` musí být klíčové slovo použito na obou místech, nebo kompilátor generuje chybu CS8172, "" nemůže inicializovat proměnnou podle odkazu s hodnotou. "</span><span class="sxs-lookup"><span data-stu-id="62a29-172">In both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="62a29-173">Počínaje jazykem C# 7,3 může být proměnná iterace `foreach` příkazu ref na místní proměnnou ref nebo ref jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="62a29-173">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="62a29-174">Další informace naleznete v článku o [příkazu foreach](foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="62a29-174">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="62a29-175">Počínaje jazykem C# 7,3 můžete znovu přiřadit místní proměnnou ref nebo ref jen pro čtení s [operátorem přiřazení ref](../operators/assignment-operator.md#ref-assignment-operator).</span><span class="sxs-lookup"><span data-stu-id="62a29-175">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="62a29-176">Místní referenční hodnoty jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="62a29-176">Ref readonly locals</span></span>

<span data-ttu-id="62a29-177">Místní odkaz jen pro čtení se používá k odkazování na hodnoty vracené metodou nebo vlastností, která má `ref readonly` jeho signaturu a používá `return ref` .</span><span class="sxs-lookup"><span data-stu-id="62a29-177">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="62a29-178">`ref readonly`Proměnná kombinuje vlastnosti `ref` místní proměnné s `readonly` proměnnou: Jedná se o alias úložiště, ke kterému je přiřazený, a nedá se změnit.</span><span class="sxs-lookup"><span data-stu-id="62a29-178">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="62a29-179">Příklad odkazů vrátí a místní hodnoty REF</span><span class="sxs-lookup"><span data-stu-id="62a29-179">A ref returns and ref locals example</span></span>

<span data-ttu-id="62a29-180">Následující příklad definuje `Book` třídu, která má dvě <xref:System.String> pole `Title` a `Author` .</span><span class="sxs-lookup"><span data-stu-id="62a29-180">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="62a29-181">Definuje také `BookCollection` třídu, která obsahuje soukromé pole `Book` objektů.</span><span class="sxs-lookup"><span data-stu-id="62a29-181">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="62a29-182">Jednotlivé objekty knihy jsou vráceny odkazem voláním její `GetBookByTitle` metody.</span><span class="sxs-lookup"><span data-stu-id="62a29-182">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="62a29-183">Když volající ukládá hodnotu vrácenou `GetBookByTitle` metodou jako místní referenční číslo, změny, které volající provede na vrácenou hodnotu, se projeví v `BookCollection` objektu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="62a29-183">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="62a29-184">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="62a29-184">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="62a29-185">Viz také</span><span class="sxs-lookup"><span data-stu-id="62a29-185">See also</span></span>

- [<span data-ttu-id="62a29-186">Zapisovat bezpečný efektivní kód</span><span class="sxs-lookup"><span data-stu-id="62a29-186">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="62a29-187">Návratové hodnoty podle odkazu a lokální proměnné podle odkazu</span><span class="sxs-lookup"><span data-stu-id="62a29-187">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="62a29-188">Podmíněný výraz ref</span><span class="sxs-lookup"><span data-stu-id="62a29-188">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="62a29-189">Předávání parametrů</span><span class="sxs-lookup"><span data-stu-id="62a29-189">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="62a29-190">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="62a29-190">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="62a29-191">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="62a29-191">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="62a29-192">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="62a29-192">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="62a29-193">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="62a29-193">C# Keywords</span></span>](index.md)
