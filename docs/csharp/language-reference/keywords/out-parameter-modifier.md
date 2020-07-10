---
title: out – modifikátor parametrů – reference jazyka C#
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 30946c85d2b64ead3f42e03da61108fa5b367779
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174806"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="2d9dc-102">out – modifikátor parametrů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2d9dc-102">out parameter modifier (C# Reference)</span></span>

<span data-ttu-id="2d9dc-103">`out`Klíčové slovo způsobuje argumenty předávané odkazem.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="2d9dc-104">Nastaví formální parametr jako alias pro argument, který musí být proměnná.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="2d9dc-105">Jinými slovy, každá operace s parametrem je provedena na argumentu.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="2d9dc-106">Je podobně jako klíčové slovo [ref](ref.md) , s výjimkou, že `ref` vyžaduje, aby byla proměnná inicializována předtím, než je předána.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="2d9dc-107">Je také podobně jako klíčové slovo [in](in-parameter-modifier.md) , s výjimkou, která `in` neumožňuje volané metodě upravovat hodnotu argumentu.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="2d9dc-108">Chcete-li použít `out` parametr, definice metody a volající metoda musí explicitně použít `out` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="2d9dc-109">Zde je příklad:</span><span class="sxs-lookup"><span data-stu-id="2d9dc-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> <span data-ttu-id="2d9dc-110">`out`Klíčové slovo lze také použít s parametrem obecného typu k určení toho, že parametr typu je kovariantní.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="2d9dc-111">Další informace o použití `out` klíčového slova v tomto kontextu naleznete v tématu [out (Generic modifikátor)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="2d9dc-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="2d9dc-112">Proměnné předané jako `out` argumenty není nutné inicializovat před předáním volání metody.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="2d9dc-113">Nicméně volaná metoda je vyžadována pro přiřazení hodnoty před vrácením metody.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="2d9dc-114">`in` `ref` `out` Klíčová slova, a nejsou považována za součást signatury metody pro účely řešení přetížení.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="2d9dc-115">Proto metody nemohou být přetíženy, pokud jediným rozdílem je, že jedna metoda přebírá `ref` `in` argument or a druhý přebírá `out` argument.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="2d9dc-116">Následující kód například nebude zkompilován:</span><span class="sxs-lookup"><span data-stu-id="2d9dc-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="2d9dc-117">Přetížení je právní, ale pokud jedna metoda přebírá `ref` `in` argument, nebo `out` a druhý nemá žádný z těchto modifikátorů, jako je:</span><span class="sxs-lookup"><span data-stu-id="2d9dc-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="2d9dc-118">Kompilátor zvolí nejlepší přetížení porovnáním modifikátorů parametrů na webu volání s modifikátory parametru použitými ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>

<span data-ttu-id="2d9dc-119">Vlastnosti nejsou proměnné a proto je nelze předat jako `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="2d9dc-120">`in` `ref` Klíčová slova, a nelze použít `out` pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="2d9dc-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="2d9dc-121">Asynchronní metody, které definujete pomocí modifikátoru [Async](./async.md) .</span><span class="sxs-lookup"><span data-stu-id="2d9dc-121">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="2d9dc-122">Metody iterátoru, které zahrnují [návratový návrat](./yield.md) nebo `yield break` příkaz yield.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-122">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="2d9dc-123">Kromě toho [rozšiřující metody](../../programming-guide/classes-and-structs/extension-methods.md) mají následující omezení:</span><span class="sxs-lookup"><span data-stu-id="2d9dc-123">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="2d9dc-124">`out`Klíčové slovo nelze použít pro první argument metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-124">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="2d9dc-125">`ref`Klíčové slovo nelze použít u prvního argumentu metody rozšíření, pokud argument není struct nebo obecný typ, který není omezen na strukturu.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-125">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="2d9dc-126">`in`Klíčové slovo nelze použít, pokud první argument není struktura.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-126">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="2d9dc-127">`in`Klíčové slovo nelze použít pro žádný obecný typ, ani v případě, že je omezení typu struct.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-127">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="declaring-out-parameters"></a><span data-ttu-id="2d9dc-128">Deklarace `out` parametrů</span><span class="sxs-lookup"><span data-stu-id="2d9dc-128">Declaring `out` parameters</span></span>

<span data-ttu-id="2d9dc-129">Deklarace metody s `out` argumenty je klasické alternativní řešení, které vrací více hodnot.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-129">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="2d9dc-130">Počínaje jazykem C# 7,0 zvažte u podobných scénářů [hodnoty řazené kolekce členů](../builtin-types/value-tuples.md) .</span><span class="sxs-lookup"><span data-stu-id="2d9dc-130">Beginning with C# 7.0, consider [value tuples](../builtin-types/value-tuples.md) for similar scenarios.</span></span> <span data-ttu-id="2d9dc-131">Následující příklad používá `out` k vrácení tří proměnných s jedním voláním metody.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-131">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="2d9dc-132">Třetí argument je přiřazen null.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-132">The third argument is assigned to null.</span></span> <span data-ttu-id="2d9dc-133">To umožňuje metodám vracet hodnoty volitelně.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-133">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="2d9dc-134">Volání metody s `out` argumentem</span><span class="sxs-lookup"><span data-stu-id="2d9dc-134">Calling a method with an `out` argument</span></span>

<span data-ttu-id="2d9dc-135">V jazyce C# 6 a starší je nutné deklarovat proměnnou v samostatném příkazu před tím, než je předáte jako `out` argument.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-135">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="2d9dc-136">Následující příklad deklaruje proměnnou s názvem předtím, `number` než je předána metodě [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) , která se pokusí převést řetězec na číslo.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-136">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="2d9dc-137">Počínaje jazykem C# 7,0 můžete deklarovat `out` proměnnou v seznamu argumentů volání metody, nikoli v deklaraci samostatné proměnné.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-137">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="2d9dc-138">Tím se vytvoří více kompaktní, čitelný kód a také neúmyslně přiřadíte hodnotu proměnné před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-138">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="2d9dc-139">Následující příklad je podobný předchozímu příkladu s tím rozdílem, že definuje `number` proměnnou ve volání metody [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) .</span><span class="sxs-lookup"><span data-stu-id="2d9dc-139">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

<span data-ttu-id="2d9dc-140">V předchozím příkladu `number` je proměnná silně typu jako `int` .</span><span class="sxs-lookup"><span data-stu-id="2d9dc-140">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="2d9dc-141">Můžete také deklarovat implicitní typovou místní proměnnou, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2d9dc-141">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="2d9dc-142">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d9dc-142">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2d9dc-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d9dc-143">See also</span></span>

- [<span data-ttu-id="2d9dc-144">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d9dc-144">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2d9dc-145">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="2d9dc-145">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2d9dc-146">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d9dc-146">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="2d9dc-147">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="2d9dc-147">Method Parameters</span></span>](./method-parameters.md)
