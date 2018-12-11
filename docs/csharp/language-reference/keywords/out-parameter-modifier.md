---
title: out – modifikátor parametrů - C# odkaz
ms.custom: seodec18
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: f50490195344c488d264735f89e0107caba888c2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242058"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="8ddf9-102">out – modifikátor parametrů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8ddf9-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="8ddf9-103">`out` – Klíčové slovo způsobí, že argumenty, které mají být předány podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="8ddf9-104">Je třeba [ref](ref.md) – klíčové slovo, s výjimkou, že `ref` vyžaduje, aby před jeho předáním inicializovat proměnnou.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-104">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="8ddf9-105">Je také třeba [v](in-parameter-modifier.md) – klíčové slovo, s výjimkou, že `in` neumožňuje volané metody, chcete-li změnit hodnotu argumentu.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-105">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="8ddf9-106">Použití `out` parametr definici metody a volající metody musíte explicitně použít `out` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-106">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="8ddf9-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8ddf9-107">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="8ddf9-108">`out` – Klíčové slovo je také možné pomocí parametru obecného typu k určení, že parametr typu je kovariant.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-108">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="8ddf9-109">Další informace týkající se použití `out` – klíčové slovo v tomto kontextu, najdete v článku [out (generický modifikátor)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="8ddf9-109">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="8ddf9-110">Proměnné se předaly jako `out` argumenty nemusí být inicializován před předáním ve volání metody.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-110">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="8ddf9-111">Volané metody je však potřeba přiřadit hodnotu dříve, než metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-111">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="8ddf9-112">I když `in`, `ref`, a `out` klíčová slova způsobit různé chování za běhu, nejsou považovány za součást podpisu metody v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-112">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="8ddf9-113">Proto metody nemohou být přetíženy, pokud je jediným rozdílem je, že jedna metoda má `ref` nebo `in` argument a druhý bere `out` argument.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="8ddf9-114">Například následující kód, nebude kompilovat:</span><span class="sxs-lookup"><span data-stu-id="8ddf9-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="8ddf9-115">Přetěžování je právní, ale pokud jedna metoda má `ref`, `in`, nebo `out` argument a druhý nemá žádná z těchto parametrů, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="8ddf9-115">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="8ddf9-116">Kompilátor volí přetížení optimální to provede spárováním odpovídajících modifikátorech parametrů v lokalitě volání do modifikátorech parametrů používaných pro volání metody.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-116">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="8ddf9-117">Vlastnosti nejsou proměnné a proto ji nelze předat jako `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-117">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="8ddf9-118">Nelze použít `in`, `ref`, a `out` klíčová slova pro následující druhy metod:</span><span class="sxs-lookup"><span data-stu-id="8ddf9-118">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="8ddf9-119">Asynchronní metody, které definujete pomocí [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-119">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="8ddf9-120">Metody iterátorů, mezi které patří [yield return](../../../csharp/language-reference/keywords/yield.md) nebo `yield break` příkazu.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-120">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="8ddf9-121">Deklarování `out` argumenty</span><span class="sxs-lookup"><span data-stu-id="8ddf9-121">Declaring `out` arguments</span></span>   

 <span data-ttu-id="8ddf9-122">Deklarace metody s `out` argumentů je užitečné, pokud chcete, aby metoda vrátit více hodnot.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-122">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="8ddf9-123">Následující příklad používá `out` vrátit tří proměnných s stačí jediná metoda volání.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-123">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="8ddf9-124">Všimněte si, že třetí argument je přiřazená na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-124">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="8ddf9-125">To umožňuje volitelně návratové hodnoty metod.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-125">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 <span data-ttu-id="8ddf9-126">[Zkuste vzor](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods) zahrnuje vrácení `bool` označující, zda operace úspěšné nebo neúspěšné, a vrátí hodnotu, vytvořený při operaci v `out` argument.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-126">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods) involves returning a `bool` to indicate whether an operation succeeded or failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="8ddf9-127">Počet analýze metody, například [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) metoda, tento model se používá.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-127">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="8ddf9-128">Volání metody s `out` argument</span><span class="sxs-lookup"><span data-stu-id="8ddf9-128">Calling a method with an `out` argument</span></span>

<span data-ttu-id="8ddf9-129">V jazyce C# 6 a starší, před jeho předáním jako musíte deklarovat proměnnou v samostatné prohlášení `out` argument.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-129">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="8ddf9-130">Následující příklad deklaruje proměnnou s názvem `number` předtím, než je předána [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metodu, která se pokusí převést řetězec na číslo.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-130">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="8ddf9-131">Od verze C# 7.0, lze deklarovat `out` proměnné v seznamu argumentů volání metody, nikoli v samostatné deklarace proměnné.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-131">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="8ddf9-132">Vytvoří kód kompaktnějším a srozumitelné a také vám zabrání od nedopatřením přiřazení hodnoty proměnné před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-132">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="8ddf9-133">V následujícím příkladu je podobně jako v předchozím příkladu, s tím rozdílem, že definuje `number` proměnné ve volání [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-133">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="8ddf9-134">V předchozím příkladu `number` proměnná je silně typováno jako `int`.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-134">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="8ddf9-135">Implicitně typovaná lokální proměnná, můžete také deklarovat jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8ddf9-135">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="8ddf9-136">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8ddf9-136">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8ddf9-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ddf9-137">See Also</span></span>

- [<span data-ttu-id="8ddf9-138">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8ddf9-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="8ddf9-139">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8ddf9-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8ddf9-140">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8ddf9-140">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="8ddf9-141">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="8ddf9-141">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
