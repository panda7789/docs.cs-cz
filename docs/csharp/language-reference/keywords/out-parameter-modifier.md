---
title: out modifikátor parametrů - C# Reference
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: f963188d77685bb81f7dc9fb3794e343114fe3c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173559"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="8ef33-102">out – modifikátor parametrů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8ef33-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="8ef33-103">Klíčové `out` slovo způsobí, že argumenty, které mají být předány odkazem.</span><span class="sxs-lookup"><span data-stu-id="8ef33-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="8ef33-104">Vytvoří formální parametr alias pro argument, který musí být proměnná.</span><span class="sxs-lookup"><span data-stu-id="8ef33-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="8ef33-105">Jinými slovy, každá operace na parametr je provedena na argument.</span><span class="sxs-lookup"><span data-stu-id="8ef33-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="8ef33-106">Je to jako klíčové slovo `ref` [ref,](ref.md) s tím rozdílem, že vyžaduje, aby proměnná byla inicializována před předáním.</span><span class="sxs-lookup"><span data-stu-id="8ef33-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="8ef33-107">Je také jako [v](in-parameter-modifier.md) klíčové `in` slovo, s tím rozdílem, že neumožňuje volané metody změnit hodnotu argumentu.</span><span class="sxs-lookup"><span data-stu-id="8ef33-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="8ef33-108">Chcete-li `out` použít parametr, definice metody a volající `out` metoda musí explicitně použít klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="8ef33-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="8ef33-109">Například:</span><span class="sxs-lookup"><span data-stu-id="8ef33-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> <span data-ttu-id="8ef33-110">Klíčové `out` slovo lze také použít s parametrem obecného typu k určení, že parametr typu je kovariantní.</span><span class="sxs-lookup"><span data-stu-id="8ef33-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="8ef33-111">Další informace o použití `out` klíčového slova v tomto kontextu naleznete v [tématu out (Generic Modifikátor)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="8ef33-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="8ef33-112">Proměnné předané `out` jako argumenty nemusí být inicializovány před předáním ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="8ef33-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="8ef33-113">Volaná metoda je však nutné přiřadit hodnotu před metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="8ef33-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="8ef33-114">`in`, `ref`a `out` klíčová slova nejsou považovány za součást podpisu metody pro účely řešení přetížení.</span><span class="sxs-lookup"><span data-stu-id="8ef33-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="8ef33-115">Proto metody nelze přetížit, pokud jediný rozdíl `ref` je, že jedna metoda trvá nebo `in` argument a druhý trvá `out` argument.</span><span class="sxs-lookup"><span data-stu-id="8ef33-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="8ef33-116">Následující kód, například, nebude kompilovat:</span><span class="sxs-lookup"><span data-stu-id="8ef33-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="8ef33-117">Přetížení je však legální, pokud `ref`jedna `in`metoda `out` trvá , , nebo argument a druhý nemá žádný z těchto modifikátorů, jako je tento:</span><span class="sxs-lookup"><span data-stu-id="8ef33-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="8ef33-118">Kompilátor zvolí nejlepší přetížení porovnáním modifikátorů parametrů v lokalitě volání s modifikátory parametrů použitými ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="8ef33-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>

<span data-ttu-id="8ef33-119">Vlastnosti nejsou proměnné a proto `out` nelze předat jako parametry.</span><span class="sxs-lookup"><span data-stu-id="8ef33-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="8ef33-120">Klíčová `out` slova a `in`klíčová `ref`slova nelze použít pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="8ef33-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="8ef33-121">Asynchronní metody, které definujete pomocí [asynchronního](./async.md) modifikátoru.</span><span class="sxs-lookup"><span data-stu-id="8ef33-121">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="8ef33-122">Iterátor metody, které zahrnují výnos `yield break` výnos [return](./yield.md) nebo příkaz.</span><span class="sxs-lookup"><span data-stu-id="8ef33-122">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-parameters"></a><span data-ttu-id="8ef33-123">Deklarování `out` parametrů</span><span class="sxs-lookup"><span data-stu-id="8ef33-123">Declaring `out` parameters</span></span>

<span data-ttu-id="8ef33-124">Deklarování `out` metody s argumenty je klasické řešení vrátit více hodnot.</span><span class="sxs-lookup"><span data-stu-id="8ef33-124">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="8ef33-125">Počínaje C# 7.0, zvažte [řazené kolekce členů](../../tuples.md) pro podobné scénáře.</span><span class="sxs-lookup"><span data-stu-id="8ef33-125">Beginning with C# 7.0, consider [tuples](../../tuples.md) for similar scenarios.</span></span> <span data-ttu-id="8ef33-126">Následující příklad `out` používá k vrácení tři proměnné s voláním jedné metody.</span><span class="sxs-lookup"><span data-stu-id="8ef33-126">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="8ef33-127">Všimněte si, že třetí argument je přiřazen k hodnotě null.</span><span class="sxs-lookup"><span data-stu-id="8ef33-127">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="8ef33-128">To umožňuje metody vrátit hodnoty volitelně.</span><span class="sxs-lookup"><span data-stu-id="8ef33-128">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="8ef33-129">Volání metody s `out` argumentem</span><span class="sxs-lookup"><span data-stu-id="8ef33-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="8ef33-130">V C# 6 a starší, musíte deklarovat proměnnou `out` v samostatném příkazu před předáním jako argument.</span><span class="sxs-lookup"><span data-stu-id="8ef33-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="8ef33-131">Následující příklad deklaruje proměnnou pojmenovanou `number` před předáním metodě [Int32.TryParse,](xref:System.Int32.TryParse(System.String,System.Int32@)) která se pokusí převést řetězec na číslo.</span><span class="sxs-lookup"><span data-stu-id="8ef33-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="8ef33-132">Počínaje C# 7.0, můžete `out` deklarovat proměnnou v seznamu argument volání metody, nikoli v samostatné deklaraci proměnné.</span><span class="sxs-lookup"><span data-stu-id="8ef33-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="8ef33-133">To vytváří kompaktnější, čitelný kód a také zabraňuje nechtěnému přiřazení hodnoty proměnné před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="8ef33-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="8ef33-134">Následující příklad je jako v předchozím příkladu, `number` s tím rozdílem, že definuje proměnnou v volání [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metoda.</span><span class="sxs-lookup"><span data-stu-id="8ef33-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

<span data-ttu-id="8ef33-135">V předchozím příkladu `number` je proměnná silně `int`zadána jako .</span><span class="sxs-lookup"><span data-stu-id="8ef33-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="8ef33-136">Můžete také deklarovat implicitně zadávanou místní proměnnou, jako to dělá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="8ef33-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="8ef33-137">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8ef33-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8ef33-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ef33-138">See also</span></span>

- [<span data-ttu-id="8ef33-139">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8ef33-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8ef33-140">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8ef33-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8ef33-141">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8ef33-141">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="8ef33-142">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="8ef33-142">Method Parameters</span></span>](./method-parameters.md)
