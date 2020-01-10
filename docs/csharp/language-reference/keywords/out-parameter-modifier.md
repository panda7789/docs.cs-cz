---
title: modifikátor parametru out – C# referenční informace
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: bc3814b91ed4327f4af1a4a1bfbda632b0393bb8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713273"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="8bd13-102">out – modifikátor parametrů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8bd13-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="8bd13-103">Klíčové slovo `out` způsobí, že argumenty budou předány odkazem.</span><span class="sxs-lookup"><span data-stu-id="8bd13-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="8bd13-104">Nastaví formální parametr jako alias pro argument, který musí být proměnná.</span><span class="sxs-lookup"><span data-stu-id="8bd13-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="8bd13-105">Jinými slovy, každá operace s parametrem je provedena na argumentu.</span><span class="sxs-lookup"><span data-stu-id="8bd13-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="8bd13-106">Je podobně jako klíčové slovo [ref](ref.md) s tím rozdílem, že `ref` vyžaduje, aby byla proměnná inicializována před předáním.</span><span class="sxs-lookup"><span data-stu-id="8bd13-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="8bd13-107">Je také podobně jako klíčové slovo [in](in-parameter-modifier.md) , s výjimkou, že `in` nepovoluje, aby volaná metoda změnila hodnotu argumentu.</span><span class="sxs-lookup"><span data-stu-id="8bd13-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="8bd13-108">Chcete-li použít parametr `out`, musí definice metody a volající metoda explicitně používat klíčové slovo `out`.</span><span class="sxs-lookup"><span data-stu-id="8bd13-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="8bd13-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8bd13-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="8bd13-110">Klíčové slovo `out` lze také použít s parametrem obecného typu k určení toho, že parametr typu je kovariantní.</span><span class="sxs-lookup"><span data-stu-id="8bd13-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="8bd13-111">Další informace o použití klíčového slova `out` v tomto kontextu naleznete v tématu [out (Generic modifikátor)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="8bd13-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="8bd13-112">Proměnné předané jako argumenty `out` nemusejí být před předáním do volání metody inicializovány.</span><span class="sxs-lookup"><span data-stu-id="8bd13-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="8bd13-113">Nicméně volaná metoda je vyžadována pro přiřazení hodnoty před vrácením metody.</span><span class="sxs-lookup"><span data-stu-id="8bd13-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="8bd13-114">Klíčová slova `in`, `ref`a `out` nejsou považována za součást signatury metody pro účely překladu přetížení.</span><span class="sxs-lookup"><span data-stu-id="8bd13-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="8bd13-115">Proto metody nemohou být přetíženy, pokud jediným rozdílem je, že jedna metoda přebírá `ref` nebo `in` argument a druhý přebírá `out` argument.</span><span class="sxs-lookup"><span data-stu-id="8bd13-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="8bd13-116">Následující kód například nebude zkompilován:</span><span class="sxs-lookup"><span data-stu-id="8bd13-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="8bd13-117">Přetížení je právní, ale pokud jedna metoda přebírá `ref`, `in`nebo `out` argument a druhý nemá žádný z těchto modifikátorů, jako je:</span><span class="sxs-lookup"><span data-stu-id="8bd13-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="8bd13-118">Kompilátor zvolí nejlepší přetížení porovnáním modifikátorů parametrů na webu volání s modifikátory parametru použitými ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="8bd13-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="8bd13-119">Vlastnosti nejsou proměnné a proto je nelze předat jako parametry `out`.</span><span class="sxs-lookup"><span data-stu-id="8bd13-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="8bd13-120">Klíčová slova `in`, `ref`a `out` nelze použít pro následující typy metod:</span><span class="sxs-lookup"><span data-stu-id="8bd13-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="8bd13-121">Asynchronní metody, které definujete pomocí modifikátoru [Async](./async.md) .</span><span class="sxs-lookup"><span data-stu-id="8bd13-121">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="8bd13-122">Metody iterátoru, které zahrnují příkaz [yield return](./yield.md) nebo `yield break`.</span><span class="sxs-lookup"><span data-stu-id="8bd13-122">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-parameters"></a><span data-ttu-id="8bd13-123">Deklarace `out`ch parametrů</span><span class="sxs-lookup"><span data-stu-id="8bd13-123">Declaring `out` parameters</span></span>   

<span data-ttu-id="8bd13-124">Deklarace metody s argumenty `out` je klasické řešení, které vrací více hodnot.</span><span class="sxs-lookup"><span data-stu-id="8bd13-124">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="8bd13-125">Počínaje C# 7,0 zvažte [řazené kolekce členů](../../tuples.md) pro podobné scénáře.</span><span class="sxs-lookup"><span data-stu-id="8bd13-125">Beginning with C# 7.0, consider [tuples](../../tuples.md) for similar scenarios.</span></span> <span data-ttu-id="8bd13-126">Následující příklad používá `out` k vrácení tří proměnných s jedním voláním metody.</span><span class="sxs-lookup"><span data-stu-id="8bd13-126">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="8bd13-127">Všimněte si, že třetí argument je přiřazen null.</span><span class="sxs-lookup"><span data-stu-id="8bd13-127">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="8bd13-128">To umožňuje metodám vracet hodnoty volitelně.</span><span class="sxs-lookup"><span data-stu-id="8bd13-128">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="8bd13-129">Volání metody s argumentem `out`</span><span class="sxs-lookup"><span data-stu-id="8bd13-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="8bd13-130">V C# 6 a starších verzích musíte deklarovat proměnnou v samostatném příkazu předtím, než je předáte jako argument `out`.</span><span class="sxs-lookup"><span data-stu-id="8bd13-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="8bd13-131">Následující příklad deklaruje proměnnou s názvem `number` předtím, než je předána metodě [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) , která se pokusí převést řetězec na číslo.</span><span class="sxs-lookup"><span data-stu-id="8bd13-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="8bd13-132">Počínaje C# 7,0 můžete deklarovat `out` proměnnou v seznamu argumentů volání metody, nikoli v deklaraci samostatné proměnné.</span><span class="sxs-lookup"><span data-stu-id="8bd13-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="8bd13-133">Tím se vytvoří více kompaktní, čitelný kód a také neúmyslně přiřadíte hodnotu proměnné před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="8bd13-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="8bd13-134">Následující příklad je podobný předchozímu příkladu s tím rozdílem, že definuje `number` proměnnou ve volání metody [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) .</span><span class="sxs-lookup"><span data-stu-id="8bd13-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="8bd13-135">V předchozím příkladu je proměnná `number` silně typu jako `int`.</span><span class="sxs-lookup"><span data-stu-id="8bd13-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="8bd13-136">Můžete také deklarovat implicitní typovou místní proměnnou, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8bd13-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="8bd13-137">C# – jazyková specifikace</span><span class="sxs-lookup"><span data-stu-id="8bd13-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8bd13-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bd13-138">See also</span></span>

- [<span data-ttu-id="8bd13-139">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="8bd13-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8bd13-140">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8bd13-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8bd13-141">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8bd13-141">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="8bd13-142">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="8bd13-142">Method Parameters</span></span>](./method-parameters.md)
