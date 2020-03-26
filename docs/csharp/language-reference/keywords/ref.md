---
title: ref klíčové slovo - C# Reference
ms.date: 03/19/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 61ee0e320f85925e4d804a6032e01c0485a31451
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249328"
---
# <a name="ref-c-reference"></a><span data-ttu-id="2d192-102">ref (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2d192-102">ref (C# Reference)</span></span>

<span data-ttu-id="2d192-103">Klíčové `ref` slovo označuje hodnotu, která je předána odkazem.</span><span class="sxs-lookup"><span data-stu-id="2d192-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="2d192-104">Používá se ve čtyřech různých kontextech:</span><span class="sxs-lookup"><span data-stu-id="2d192-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="2d192-105">V podpisu metody a volání metody předat argument metodě odkazem.</span><span class="sxs-lookup"><span data-stu-id="2d192-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="2d192-106">Další informace naleznete [v tématu Předávání argument odkazem](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="2d192-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="2d192-107">V podpisu metody, chcete-li vrátit hodnotu volajícímu odkazem.</span><span class="sxs-lookup"><span data-stu-id="2d192-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="2d192-108">Další informace naleznete v [tématu Reference return values](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="2d192-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="2d192-109">V těle člena označuje, že referenční vrácená hodnota je uložena místně jako odkaz, který volající zamýšlí změnit, nebo obecně místní proměnná přistupuje k jiné hodnotě odkazem.</span><span class="sxs-lookup"><span data-stu-id="2d192-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="2d192-110">Další informace naleznete v tématu [Ref locals](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="2d192-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="2d192-111">V `struct` prohlášení o `ref struct` prohlášení `readonly ref struct`o prohlášení a nebo .</span><span class="sxs-lookup"><span data-stu-id="2d192-111">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="2d192-112">Další informace naleznete v tématu [ref struct types](#ref-struct-types).</span><span class="sxs-lookup"><span data-stu-id="2d192-112">For more information, see [ref struct types](#ref-struct-types).</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="2d192-113">Předání argumentu odkazem</span><span class="sxs-lookup"><span data-stu-id="2d192-113">Passing an argument by reference</span></span>

<span data-ttu-id="2d192-114">Při použití v seznamu parametrů metody `ref` klíčové slovo označuje, že argument je předán odkazem, nikoli hodnotou.</span><span class="sxs-lookup"><span data-stu-id="2d192-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="2d192-115">Klíčové `ref` slovo vytvoří formální parametr alias pro argument, který musí být proměnnou.</span><span class="sxs-lookup"><span data-stu-id="2d192-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="2d192-116">Jinými slovy, každá operace na parametr je provedena na argument.</span><span class="sxs-lookup"><span data-stu-id="2d192-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="2d192-117">Pokud například volající předá výraz místní proměnné nebo přístupový výraz prvku pole a volaná metoda nahradí objekt, na který odkazuje parametr ref, pak místní proměnná volajícího nebo element pole nyní odkazuje na nový objekt, když metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="2d192-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller's local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="2d192-118">Nepleťte si koncept předávání odkazem s pojmem typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="2d192-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="2d192-119">Tyto dva pojmy nejsou stejné.</span><span class="sxs-lookup"><span data-stu-id="2d192-119">The two concepts are not the same.</span></span> <span data-ttu-id="2d192-120">Parametr metody lze upravit `ref` bez ohledu na to, zda se jedná o typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="2d192-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="2d192-121">Neexistuje žádné zabalení typu hodnoty, pokud je předán odkazem.</span><span class="sxs-lookup"><span data-stu-id="2d192-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="2d192-122">Chcete-li `ref` použít parametr, definice metody a volající `ref` metoda musí explicitně použít klíčové slovo, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2d192-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="2d192-123">Argument, který je `ref` předán `in` nebo parametr musí být inicializován před předáním.</span><span class="sxs-lookup"><span data-stu-id="2d192-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="2d192-124">To se liší [od](out-parameter-modifier.md) out parametry, jejichž argumenty nemusí být explicitně inicializovány před jejich předáním.</span><span class="sxs-lookup"><span data-stu-id="2d192-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="2d192-125">Členové třídy nemohou mít podpisy, které `ref` `in`se `out`liší pouze podle , nebo .</span><span class="sxs-lookup"><span data-stu-id="2d192-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="2d192-126">K chybě kompilátoru dochází, pokud je jediným rozdílem mezi `ref` dvěma členy typu, že jeden z nich má parametr a druhý má parametr `out`nebo `in` parametr .</span><span class="sxs-lookup"><span data-stu-id="2d192-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="2d192-127">Následující kód, například nekompiluje.</span><span class="sxs-lookup"><span data-stu-id="2d192-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="2d192-128">Metody však mohou být přetíženy, `ref` `in`pokud `out` má jedna metoda , nebo parametr a druhá má parametr hodnoty, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2d192-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="2d192-129">V jiných situacích, které vyžadují porovnávání `in`podpisů, například skrytí nebo přepsání , , `ref`a `out` jsou součástí podpisu a vzájemně se neshodují.</span><span class="sxs-lookup"><span data-stu-id="2d192-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="2d192-130">Vlastnosti nejsou proměnné.</span><span class="sxs-lookup"><span data-stu-id="2d192-130">Properties are not variables.</span></span> <span data-ttu-id="2d192-131">Jsou to metody a nelze `ref` je předat parametrům.</span><span class="sxs-lookup"><span data-stu-id="2d192-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="2d192-132">Klíčová `out` slova a `ref`klíčová `in`slova nelze použít pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="2d192-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="2d192-133">Asynchronní metody, které definujete pomocí [asynchronního](async.md) modifikátoru.</span><span class="sxs-lookup"><span data-stu-id="2d192-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="2d192-134">Iterátor metody, které zahrnují výnos `yield break` výnos [return](yield.md) nebo příkaz.</span><span class="sxs-lookup"><span data-stu-id="2d192-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="2d192-135">Kromě toho mají [rozšiřující metody](../../programming-guide/classes-and-structs/extension-methods.md) následující omezení:</span><span class="sxs-lookup"><span data-stu-id="2d192-135">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="2d192-136">Keywoard `out` nelze použít na první argument metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="2d192-136">The `out` keywoard cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="2d192-137">Klíčové `ref` slovo nelze použít na první argument metody rozšíření, pokud argument není struktura, nebo obecný typ není omezena být struktura.</span><span class="sxs-lookup"><span data-stu-id="2d192-137">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="2d192-138">Klíčové `in` slovo nelze použít, pokud první argument není struktura.</span><span class="sxs-lookup"><span data-stu-id="2d192-138">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="2d192-139">Klíčové `in` slovo nelze použít u žádného obecného typu, a to ani v případě, že je omezeno na strukturu.</span><span class="sxs-lookup"><span data-stu-id="2d192-139">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="2d192-140">Předání argumentu odkazem: Příklad</span><span class="sxs-lookup"><span data-stu-id="2d192-140">Passing an argument by reference: An example</span></span>

<span data-ttu-id="2d192-141">Předchozí příklady předat typy hodnot odkazem.</span><span class="sxs-lookup"><span data-stu-id="2d192-141">The previous examples pass value types by reference.</span></span> <span data-ttu-id="2d192-142">Klíčové `ref` slovo můžete také použít k předání referenčních typů odkazem.</span><span class="sxs-lookup"><span data-stu-id="2d192-142">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="2d192-143">Předání typu odkazu odkazem umožňuje volané metodě nahradit objekt, na který odkazuje referenční parametr volajícího.</span><span class="sxs-lookup"><span data-stu-id="2d192-143">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="2d192-144">Umístění úložiště objektu je předáno metodě jako hodnota referenčního parametru.</span><span class="sxs-lookup"><span data-stu-id="2d192-144">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="2d192-145">Pokud změníte hodnotu v umístění úložiště parametru (chcete-li přejděte na nový objekt), změníte také umístění úložiště, na které volající odkazuje.</span><span class="sxs-lookup"><span data-stu-id="2d192-145">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="2d192-146">Následující příklad předá instanci typu `ref` odkazu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="2d192-146">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="2d192-147">Další informace o předávání typů odkazů podle hodnoty a odkazu naleznete [v tématu Předávání parametrů typu odkazu](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="2d192-147">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="2d192-148">Referenční návratové hodnoty</span><span class="sxs-lookup"><span data-stu-id="2d192-148">Reference return values</span></span>

<span data-ttu-id="2d192-149">Referenční vrácené hodnoty (nebo ref vrátí) jsou hodnoty, které metoda vrátí odkazem na volajícího.</span><span class="sxs-lookup"><span data-stu-id="2d192-149">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="2d192-150">To znamená, že volající může upravit hodnotu vrácenou metodou a tato změna se projeví ve stavu objektu, který obsahuje metodu.</span><span class="sxs-lookup"><span data-stu-id="2d192-150">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="2d192-151">Referenční vrácená hodnota je `ref` definována pomocí klíčového slova:</span><span class="sxs-lookup"><span data-stu-id="2d192-151">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="2d192-152">V podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="2d192-152">In the method signature.</span></span> <span data-ttu-id="2d192-153">Například následující podpis metody označuje, `GetCurrentPrice` že <xref:System.Decimal> metoda vrátí hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="2d192-153">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="2d192-154">Mezi `return` token a proměnná `return` vrácena v příkazu v metodě.</span><span class="sxs-lookup"><span data-stu-id="2d192-154">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="2d192-155">Například:</span><span class="sxs-lookup"><span data-stu-id="2d192-155">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="2d192-156">Aby volající mohl upravit stav objektu, musí být vrácená hodnota odkazu uložena do proměnné, která je explicitně definována jako [ref local](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="2d192-156">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="2d192-157">Volaná metoda může také `ref readonly` deklarovat vrácenou hodnotu, která vrací hodnotu odkazem, a vynutit, aby volající kód nemohl změnit vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2d192-157">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="2d192-158">Volající metoda se může vyhnout kopírování vrácené hodnoty uložením hodnoty v místní proměnné [pouze pro čtení ref.](#ref-readonly-locals)</span><span class="sxs-lookup"><span data-stu-id="2d192-158">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="2d192-159">Příklad viz [Ref returns a ref locals example](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="2d192-159">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="2d192-160">Ref místní obyvatelé</span><span class="sxs-lookup"><span data-stu-id="2d192-160">Ref locals</span></span>

<span data-ttu-id="2d192-161">Ref místní proměnná se používá k `return ref`odkazování na hodnoty vrácené pomocí .</span><span class="sxs-lookup"><span data-stu-id="2d192-161">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="2d192-162">Místní proměnnou ref nelze inicializovat na nevratnou hodnotu bez ref.</span><span class="sxs-lookup"><span data-stu-id="2d192-162">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="2d192-163">Jinými slovy, pravá strana inicializace musí být odkaz.</span><span class="sxs-lookup"><span data-stu-id="2d192-163">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="2d192-164">Všechny změny hodnoty ref local se projeví ve stavu objektu, jehož metoda vrátila hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="2d192-164">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="2d192-165">Definujete ref místní pomocí `ref` klíčového slova před deklarace proměnné, jakož i bezprostředně před volání metody, která vrací hodnotu odkazem.</span><span class="sxs-lookup"><span data-stu-id="2d192-165">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="2d192-166">Například následující příkaz definuje ref místní hodnotu, která `GetEstimatedValue`je vrácena metodou s názvem :</span><span class="sxs-lookup"><span data-stu-id="2d192-166">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="2d192-167">Můžete přistupovat k hodnotě odkazem stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="2d192-167">You can access a value by reference in the same way.</span></span> <span data-ttu-id="2d192-168">V některých případech přístup k hodnotě odkazem zvyšuje výkon tím, že se vyhne potenciálně nákladné operaci kopírování.</span><span class="sxs-lookup"><span data-stu-id="2d192-168">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="2d192-169">Například následující příkaz ukazuje, jak lze definovat ref místní hodnotu, která se používá k odkazu na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2d192-169">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="2d192-170">Všimněte si, že `ref` v obou příkladech musí být klíčové slovo použito na obou místech nebo kompilátor generuje chybu CS8172, "Nelze inicializovat proměnnou odkazu s hodnotou."</span><span class="sxs-lookup"><span data-stu-id="2d192-170">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="2d192-171">Počínaje C# 7.3, iterace `foreach` proměnná příkazu může být ref místní nebo ref pro čtení místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="2d192-171">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="2d192-172">Další informace naleznete v článku [foreach prohlášení.](foreach-in.md)</span><span class="sxs-lookup"><span data-stu-id="2d192-172">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="2d192-173">Také počínaje C# 7.3, můžete znovu přiřadit ref místní nebo ref pouze pro čtení místní proměnné s [operátorem přiřazení ref](../operators/assignment-operator.md#ref-assignment-operator).</span><span class="sxs-lookup"><span data-stu-id="2d192-173">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="2d192-174">Ref pouze pro čtení místních obyvatel</span><span class="sxs-lookup"><span data-stu-id="2d192-174">Ref readonly locals</span></span>

<span data-ttu-id="2d192-175">Ref pouze pro čtení místní se používá k odkazování `ref readonly` na hodnoty vrácené metodou nebo vlastností, která má ve svém podpisu a používá `return ref`.</span><span class="sxs-lookup"><span data-stu-id="2d192-175">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="2d192-176">Proměnná `ref readonly` kombinuje vlastnosti `ref` místní proměnné `readonly` s proměnnou: jedná se o alias k úložišti, ke kterým je přiřazena, a nelze ji změnit.</span><span class="sxs-lookup"><span data-stu-id="2d192-176">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="2d192-177">Ref vrátí a ref místní příklad</span><span class="sxs-lookup"><span data-stu-id="2d192-177">A ref returns and ref locals example</span></span>

<span data-ttu-id="2d192-178">Následující příklad definuje `Book` třídu, <xref:System.String> která `Title` má `Author`dvě pole a .</span><span class="sxs-lookup"><span data-stu-id="2d192-178">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="2d192-179">Definuje také třídu, `BookCollection` která obsahuje `Book` soukromé pole objektů.</span><span class="sxs-lookup"><span data-stu-id="2d192-179">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="2d192-180">Jednotlivé objekty knihy jsou vráceny odkazem voláním jeho `GetBookByTitle` metody.</span><span class="sxs-lookup"><span data-stu-id="2d192-180">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="2d192-181">Když volající uloží hodnotu `GetBookByTitle` vrácenou metodou jako ref local, změny, které volající provede `BookCollection` na vrácenou hodnotu, se projeví v objektu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="2d192-181">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a><span data-ttu-id="2d192-182">Typy struktury ref</span><span class="sxs-lookup"><span data-stu-id="2d192-182">Ref struct types</span></span>

<span data-ttu-id="2d192-183">Přidání `ref` modifikátoru `struct` do deklarace definuje, že instance tohoto typu musí být přiděleny.</span><span class="sxs-lookup"><span data-stu-id="2d192-183">Adding the `ref` modifier to a `struct` declaration defines that instances of that type must be stack allocated.</span></span> <span data-ttu-id="2d192-184">Jinými slovy instance těchto typů nelze nikdy vytvořit na haldě jako člen jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="2d192-184">In other words, instances of these types can never be created on the heap as a member of another class.</span></span> <span data-ttu-id="2d192-185">Primární motivací pro <xref:System.Span%601> tuto funkci byla a související struktury.</span><span class="sxs-lookup"><span data-stu-id="2d192-185">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span>

<span data-ttu-id="2d192-186">Cílem zachování `ref struct` typu jako proměnné přidělené zásobníku zavádí několik pravidel, která `ref struct` kompilátor vynucuje pro všechny typy.</span><span class="sxs-lookup"><span data-stu-id="2d192-186">The goal of keeping a `ref struct` type as a stack-allocated variable introduces several rules that the compiler enforces for all `ref struct` types.</span></span>

- <span data-ttu-id="2d192-187">Nemůžete box. `ref struct`</span><span class="sxs-lookup"><span data-stu-id="2d192-187">You can't box a `ref struct`.</span></span> <span data-ttu-id="2d192-188">Nelze přiřadit `ref struct` typ proměnné typu `object`, `dynamic`nebo typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d192-188">You cannot assign a `ref struct` type to a variable of type `object`, `dynamic`, or any interface type.</span></span>
- <span data-ttu-id="2d192-189">`ref struct`typy nelze implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d192-189">`ref struct` types cannot implement interfaces.</span></span>
- <span data-ttu-id="2d192-190">Nelze deklarovat `ref struct` jako člen pole třídy nebo normální struktury.</span><span class="sxs-lookup"><span data-stu-id="2d192-190">You can't declare a `ref struct` as a field member of a class or a normal struct.</span></span> <span data-ttu-id="2d192-191">To zahrnuje deklarování automaticky implementované vlastnosti, která vytvoří kompilátor generované doprovodné pole.</span><span class="sxs-lookup"><span data-stu-id="2d192-191">This includes declaring an auto-implemented property, which creates a compiler generated backing field.</span></span>
- <span data-ttu-id="2d192-192">Nelze deklarovat místní `ref struct` proměnné, které jsou typy v asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="2d192-192">You cannot declare local variables that are `ref struct` types in async methods.</span></span> <span data-ttu-id="2d192-193">Můžete deklarovat je v <xref:System.Threading.Tasks.Task>synchronní metody, které vracejí nebo <xref:System.Threading.Tasks.Task%601> `Task`-like typy.</span><span class="sxs-lookup"><span data-stu-id="2d192-193">You can declare them in synchronous methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> or `Task`-like types.</span></span>
- <span data-ttu-id="2d192-194">Nelze deklarovat `ref struct` místní proměnné v iterátorech.</span><span class="sxs-lookup"><span data-stu-id="2d192-194">You cannot declare `ref struct` local variables in iterators.</span></span>
- <span data-ttu-id="2d192-195">Proměnné nelze `ref struct` zachytit ve výrazech lambda nebo místních funkcích.</span><span class="sxs-lookup"><span data-stu-id="2d192-195">You cannot capture `ref struct` variables in lambda expressions or local functions.</span></span>

<span data-ttu-id="2d192-196">Tato omezení zajistí, že omylem `ref struct` nepoužijete způsobem, který by ji mohl propagovat na spravovanou haldu.</span><span class="sxs-lookup"><span data-stu-id="2d192-196">These restrictions ensure you don't accidentally use a `ref struct` in a manner that could promote it to the managed heap.</span></span>

<span data-ttu-id="2d192-197">Můžete kombinovat modifikátory deklarovat strukturu jako `readonly ref`.</span><span class="sxs-lookup"><span data-stu-id="2d192-197">You can combine modifiers to declare a struct as `readonly ref`.</span></span> <span data-ttu-id="2d192-198">A `readonly ref struct` kombinuje výhody a `ref struct` omezení `readonly struct` a prohlášení.</span><span class="sxs-lookup"><span data-stu-id="2d192-198">A `readonly ref struct` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2d192-199">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d192-199">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2d192-200">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d192-200">See also</span></span>

- [<span data-ttu-id="2d192-201">Zapisujte bezpečný efektivní kód</span><span class="sxs-lookup"><span data-stu-id="2d192-201">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="2d192-202">Návratové hodnoty podle odkazu a lokální proměnné podle odkazu</span><span class="sxs-lookup"><span data-stu-id="2d192-202">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="2d192-203">Podmíněný výraz ref</span><span class="sxs-lookup"><span data-stu-id="2d192-203">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="2d192-204">Předávání parametrů</span><span class="sxs-lookup"><span data-stu-id="2d192-204">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="2d192-205">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="2d192-205">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="2d192-206">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d192-206">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2d192-207">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d192-207">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2d192-208">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2d192-208">C# Keywords</span></span>](index.md)
