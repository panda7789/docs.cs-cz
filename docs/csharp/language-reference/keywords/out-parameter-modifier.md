---
title: out – modifikátor parametrů - C# odkaz
ms.custom: seodec18
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 769d1ac0b6266c87e99605c76a25e016f15eb11c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125739"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="551c7-102">out – modifikátor parametrů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="551c7-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="551c7-103">`out` – Klíčové slovo způsobí, že argumenty, které mají být předány podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="551c7-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="551c7-104">Formální parametr je alias pro argument, který musí být proměnná.</span><span class="sxs-lookup"><span data-stu-id="551c7-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="551c7-105">Jinými slovy všechny operace na parametr se provádí na argumentu.</span><span class="sxs-lookup"><span data-stu-id="551c7-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="551c7-106">Je třeba [ref](ref.md) – klíčové slovo, s výjimkou, že `ref` vyžaduje, aby před jeho předáním inicializovat proměnnou.</span><span class="sxs-lookup"><span data-stu-id="551c7-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="551c7-107">Je také třeba [v](in-parameter-modifier.md) – klíčové slovo, s výjimkou, že `in` neumožňuje volané metody, chcete-li změnit hodnotu argumentu.</span><span class="sxs-lookup"><span data-stu-id="551c7-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="551c7-108">Použití `out` parametr definici metody a volající metody musíte explicitně použít `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="551c7-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="551c7-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="551c7-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="551c7-110">`out` – Klíčové slovo je také možné pomocí parametru obecného typu k určení, že parametr typu je kovariant.</span><span class="sxs-lookup"><span data-stu-id="551c7-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="551c7-111">Další informace týkající se použití `out` – klíčové slovo v tomto kontextu, najdete v článku [out (generický modifikátor)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="551c7-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="551c7-112">Proměnné se předaly jako `out` argumenty nemusí být inicializován před předáním ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="551c7-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="551c7-113">Volané metody je však potřeba přiřadit hodnotu dříve, než metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="551c7-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="551c7-114">`in`, `ref`, A `out` klíčová slova nejsou považované za součást podpisu metody za účelem řešení přetížení.</span><span class="sxs-lookup"><span data-stu-id="551c7-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="551c7-115">Proto metody nemohou být přetíženy, pokud je jediným rozdílem je, že jedna metoda má `ref` nebo `in` argument a druhý bere `out` argument.</span><span class="sxs-lookup"><span data-stu-id="551c7-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="551c7-116">Například následující kód, nebude kompilovat:</span><span class="sxs-lookup"><span data-stu-id="551c7-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="551c7-117">Přetěžování je právní, ale pokud jedna metoda má `ref`, `in`, nebo `out` argument a druhý nemá žádná z těchto parametrů, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="551c7-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="551c7-118">Kompilátor volí přetížení optimální to provede spárováním odpovídajících modifikátorech parametrů v lokalitě volání do modifikátorech parametrů používaných pro volání metody.</span><span class="sxs-lookup"><span data-stu-id="551c7-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="551c7-119">Vlastnosti nejsou proměnné a proto ji nelze předat jako `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="551c7-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="551c7-120">Nelze použít `in`, `ref`, a `out` klíčová slova pro následující druhy metod:</span><span class="sxs-lookup"><span data-stu-id="551c7-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="551c7-121">Asynchronní metody, které definujete pomocí [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="551c7-121">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="551c7-122">Metody iterátorů, mezi které patří [yield return](../../../csharp/language-reference/keywords/yield.md) nebo `yield break` příkazu.</span><span class="sxs-lookup"><span data-stu-id="551c7-122">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-parameters"></a><span data-ttu-id="551c7-123">Deklarování `out` parametry</span><span class="sxs-lookup"><span data-stu-id="551c7-123">Declaring `out` parameters</span></span>   

<span data-ttu-id="551c7-124">Deklarace metody s `out` argumenty se klasické alternativní řešení Chcete-li vrátit více hodnot.</span><span class="sxs-lookup"><span data-stu-id="551c7-124">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="551c7-125">Počínaje C# 7.0, vezměte v úvahu [řazených kolekcí členů](../../tuples.md) pro podobné scénáře.</span><span class="sxs-lookup"><span data-stu-id="551c7-125">Beginning with C# 7.0, consider [tuples](../../tuples.md) for similar scenarios.</span></span> <span data-ttu-id="551c7-126">Následující příklad používá `out` vrátit tří proměnných s stačí jediná metoda volání.</span><span class="sxs-lookup"><span data-stu-id="551c7-126">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="551c7-127">Všimněte si, že třetí argument je přiřazená na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="551c7-127">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="551c7-128">To umožňuje volitelně návratové hodnoty metod.</span><span class="sxs-lookup"><span data-stu-id="551c7-128">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="551c7-129">Volání metody s `out` argument</span><span class="sxs-lookup"><span data-stu-id="551c7-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="551c7-130">V jazyce C# 6 a starší, před jeho předáním jako musíte deklarovat proměnnou v samostatné prohlášení `out` argument.</span><span class="sxs-lookup"><span data-stu-id="551c7-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="551c7-131">Následující příklad deklaruje proměnnou s názvem `number` předtím, než je předána [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metodu, která se pokusí převést řetězec na číslo.</span><span class="sxs-lookup"><span data-stu-id="551c7-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="551c7-132">Od verze C# 7.0, lze deklarovat `out` proměnné v seznamu argumentů volání metody, nikoli v samostatné deklarace proměnné.</span><span class="sxs-lookup"><span data-stu-id="551c7-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="551c7-133">Vytvoří kód kompaktnějším a srozumitelné a také vám zabrání od nedopatřením přiřazení hodnoty proměnné před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="551c7-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="551c7-134">V následujícím příkladu je podobně jako v předchozím příkladu, s tím rozdílem, že definuje `number` proměnné ve volání [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody.</span><span class="sxs-lookup"><span data-stu-id="551c7-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="551c7-135">V předchozím příkladu `number` proměnná je silně typováno jako `int`.</span><span class="sxs-lookup"><span data-stu-id="551c7-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="551c7-136">Implicitně typovaná lokální proměnná, můžete také deklarovat jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="551c7-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="551c7-137">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="551c7-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="551c7-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="551c7-138">See also</span></span>

- [<span data-ttu-id="551c7-139">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="551c7-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="551c7-140">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="551c7-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="551c7-141">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="551c7-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="551c7-142">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="551c7-142">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
