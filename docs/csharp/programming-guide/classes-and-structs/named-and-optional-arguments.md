---
title: "Pojmenované a nepovinné argumenty (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e6fceb569a79b5988171f06ae6c09d86b5fc667d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="9fc0e-102">Pojmenované a nepovinné argumenty (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9fc0e-102">Named and Optional Arguments (C# Programming Guide)</span></span>
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]<span data-ttu-id="9fc0e-103">představuje pojmenované a nepovinné argumenty.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-103"> introduces named and optional arguments.</span></span> <span data-ttu-id="9fc0e-104">*Pojmenované argumenty* vám umožní zadat argument pro konkrétní parametr tím, že přidružíte argument s názvem parametru a nikoli s parametru pozici v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="9fc0e-105">*Nepovinné argumenty* umožňují vynechejte argumenty pro některé parametry.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="9fc0e-106">Obě tyto metody lze pomocí metody, indexery, konstruktory a delegáti.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="9fc0e-107">Při použití pojmenovaných a nepovinných argumentů argumenty, které jsou vyhodnocovány v pořadí, v jakém jsou uvedeny v seznamu argumentů není seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="9fc0e-108">Pojmenované a nepovinné parametry, při použití společně, umožňují zadat argumenty pro pouze několik parametrů ze seznamu volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="9fc0e-109">Tato funkce výrazně usnadňuje volání do rozhraní COM, jako je například rozhraní API automatizace Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="9fc0e-110">Pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="9fc0e-110">Named Arguments</span></span>  
 <span data-ttu-id="9fc0e-111">Pojmenované argumenty vás zbaví nutnosti mějte na paměti, nebo k vyhledání pořadí parametrů v seznamu parametrů vyvolání metod.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="9fc0e-112">Parametr pro každý argument může být určena název parametru.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="9fc0e-113">Například funkci, která zobrazí podrobnosti o pořadí (jako je třeba název prodejce, název pořadí číslo & produktu) může být volán v standardním způsobem odesláním argumentů podle pozice v pořadí definované funkce.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-113">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="9fc0e-114">Pokud pořadí parametrů nepamatujete, ale znáte jejich názvy, můžete odeslat argumenty v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-114">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="9fc0e-115">Pojmenované argumenty taky aby zlepšila čitelnost kódu tím, že určíte, co představuje všechny argumenty.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="9fc0e-116">V metodě v příkladu níže `sellerName` nesmí být null ani prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-116">In the example method below, the `sellerName` cannot be null or whitespace.</span></span> <span data-ttu-id="9fc0e-117">Jako obě `sellerName` a `productName` jsou typy řetězce, místo abyste odesílali argumentů podle pozice, má smysl pojmenované argumenty použít k rozlišení dvou a snížit nedorozuměním pro každý, kdo čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-117">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="9fc0e-118">Pojmenované argumenty, pokud se používá s poziční parametry, jsou platné, dokud</span><span class="sxs-lookup"><span data-stu-id="9fc0e-118">Named arguments, when used with positional arguments, are valid as long as</span></span> 

- <span data-ttu-id="9fc0e-119">nejsou následuje argumentů podle pozice, nebo</span><span class="sxs-lookup"><span data-stu-id="9fc0e-119">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="9fc0e-120">_od verze jazyka C# 7.2_, jejich použití ve správné pozici.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-120">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="9fc0e-121">V příkladu níže parametr `orderNum` je ve správné pozici, ale není explicitně s názvem.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-121">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="9fc0e-122">Pojmenované argumenty pořadí se na více systémů jsou však neplatný, pokud jste postupovali podle poziční argumenty.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-122">However, out-of-order named arguments are invalid if they're followed by positional arguments.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="9fc0e-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="9fc0e-123">Example</span></span>  
 <span data-ttu-id="9fc0e-124">Následující kód implementuje příklady z této části společně s ty, které jsou některé další.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-124">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="9fc0e-125">Nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="9fc0e-125">Optional Arguments</span></span>  
 <span data-ttu-id="9fc0e-126">Definice metoda, konstruktor, indexer nebo delegáta můžete určit, že jeho parametry jsou povinné a že jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-126">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="9fc0e-127">Žádném volání, musíte zadat argumenty pro všechny požadované parametry, ale můžete vynechat argumenty pro volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-127">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="9fc0e-128">Každý volitelný parametr má výchozí hodnotu v rámci jeho definice.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-128">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="9fc0e-129">Pokud se pro tento parametr je odeslat žádný argument, je použita výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-129">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="9fc0e-130">Výchozí hodnota musí být jedna z následujících typů výrazů:</span><span class="sxs-lookup"><span data-stu-id="9fc0e-130">A default value must be one of the following types of expressions:</span></span>  
  
-   <span data-ttu-id="9fc0e-131">konstantní výraz;</span><span class="sxs-lookup"><span data-stu-id="9fc0e-131">a constant expression;</span></span>  
  
-   <span data-ttu-id="9fc0e-132">výraz ve tvaru `new ValType()`, kde `ValType` je hodnota typu, například [výčtu](../../../csharp/language-reference/keywords/enum.md) nebo [struktura](../../../csharp/programming-guide/classes-and-structs/structs.md);</span><span class="sxs-lookup"><span data-stu-id="9fc0e-132">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../../csharp/language-reference/keywords/enum.md) or a [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span></span>  
  
-   <span data-ttu-id="9fc0e-133">výraz, který formulář [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), kde `ValType` je typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-133">an expression of the form [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="9fc0e-134">Volitelné parametry jsou definovány na konci seznamu parametrů po požadované parametry.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-134">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="9fc0e-135">Pokud má volající poskytuje argument pro každý z postupným volitelné parametry, je nutné zadat argumenty pro všechny předchozí volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-135">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="9fc0e-136">Textový soubor s oddělovači mezery v seznamu argumentů nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-136">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="9fc0e-137">Například v následujícím kódu metodu instance `ExampleMethod` je definovaná pomocí jednu požadované a volitelné dva parametry.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-137">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]  
  
 <span data-ttu-id="9fc0e-138">Následující volání do `ExampleMethod` způsobí chybu kompilátoru, protože argument je k dispozici pro třetí parametr, ale ne pro druhý.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-138">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="9fc0e-139">Ale pokud znáte název třetí parametr, můžete s názvem argument provedení úkolu.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-139">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="9fc0e-140">IntelliSense pomocí závorek označuje volitelné parametry, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-140">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="9fc0e-141">![Rychlé informace technologie IntelliSense pro metodu ExampleMethod. ] (../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span><span class="sxs-lookup"><span data-stu-id="9fc0e-141">![IntelliSense Quick Info for method ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span></span>  
<span data-ttu-id="9fc0e-142">Volitelné parametry v ExampleMethod</span><span class="sxs-lookup"><span data-stu-id="9fc0e-142">Optional parameters in ExampleMethod</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fc0e-143">Volitelné parametry můžete také deklarovat s použitím .NET <xref:System.Runtime.InteropServices.OptionalAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-143">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="9fc0e-144">`OptionalAttribute`Parametry nevyžadují výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-144">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fc0e-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="9fc0e-145">Example</span></span>  
 <span data-ttu-id="9fc0e-146">V následujícím příkladu v konstruktoru pro `ExampleClass` má jeden parametr, který je volitelné.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-146">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="9fc0e-147">Metodu instance `ExampleMethod` má jeden požadovaný parametr `required`a dva volitelné parametry, `optionalstr` a `optionalint`.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-147">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="9fc0e-148">Kód v `Main` ukazuje různé způsoby, ve kterém můžete vyvolat konstruktor a metoda.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-148">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="9fc0e-149">COM – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fc0e-149">COM Interfaces</span></span>  
 <span data-ttu-id="9fc0e-150">Pojmenované a nepovinné argumenty, společně s podporou pro dynamické objekty a další rozšíření dojít k výraznému zlepšení spolupráce se rozhraní API modelu COM, jako je například Office automatizace rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-150">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="9fc0e-151">Například [automatický formát](http://go.microsoft.com/fwlink/?LinkId=148201) metoda v aplikaci Microsoft Office Excel [rozsah](http://go.microsoft.com/fwlink/?LinkId=148196) rozhraní má sedm parametry, které jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-151">For example, the [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) method in the Microsoft Office Excel [Range](http://go.microsoft.com/fwlink/?LinkId=148196) interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="9fc0e-152">Tyto parametry se zobrazí na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-152">These parameters are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="9fc0e-153">![Rychlé informace technologie IntelliSense pro metodu automatické formátování. ] (../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span><span class="sxs-lookup"><span data-stu-id="9fc0e-153">![IntelliSense Quick Info for the AutoFormat method.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span></span>  
<span data-ttu-id="9fc0e-154">Automatický formát parametrů</span><span class="sxs-lookup"><span data-stu-id="9fc0e-154">AutoFormat parameters</span></span>  
  
 <span data-ttu-id="9fc0e-155">V C# 3.0 a starší verze je potřebná pro každý parametr argument, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-155">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]  
  
 <span data-ttu-id="9fc0e-156">Však může výrazně zjednodušit volání `AutoFormat` pomocí pojmenovaných a nepovinných argumentů, zavedená v C# 4.0.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-156">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="9fc0e-157">Pojmenované a nepovinné argumenty umožňují vynechejte argument pro volitelný parametr, pokud nechcete změnit výchozí hodnoty parametru.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-157">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="9fc0e-158">V následující volání je zadaná hodnota jenom pro jednu ze sedmi parametry.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-158">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]  
  
 <span data-ttu-id="9fc0e-159">Další informace a příklady naleznete v tématu [postup: pomocí pojmenovaných a nepovinných argumentů v programování Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) a [postupy: přístup k objektům zprostředkovatel komunikace s objekty Office pomocí Visual C# funkce](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="9fc0e-159">For more information and examples, see [How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="9fc0e-160">Rozlišení přetěžování</span><span class="sxs-lookup"><span data-stu-id="9fc0e-160">Overload Resolution</span></span>  
 <span data-ttu-id="9fc0e-161">Použití pojmenovaných a nepovinných argumentů ovlivňuje rozlišení přetížení následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="9fc0e-161">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
-   <span data-ttu-id="9fc0e-162">Metoda, indexer nebo konstruktor je kandidátem na spuštění, pokud všechny její parametry je volitelný nebo odpovídá podle názvu nebo podle pozici, na jeden argument příkazu volání a který argument lze převést na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-162">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
-   <span data-ttu-id="9fc0e-163">Pokud je nalezen více než jeden candidate, přetížení řešení pro upřednostňované převody pravidla argumenty, které jsou explicitně určena.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-163">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="9fc0e-164">Vynechání argumenty pro volitelné parametry jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-164">Omitted arguments for optional parameters are ignored.</span></span>  
  
-   <span data-ttu-id="9fc0e-165">Pokud dva kandidáty jsou považovány za být stejně dobrý, předvoleb přejde na candidate, který nemá volitelné parametry, pro které byly vynechány argumenty ve volání.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-165">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="9fc0e-166">Toto je důsledkem Obecné předvolby rozlišení přetížení pro kandidáty, které mají méně parametry.</span><span class="sxs-lookup"><span data-stu-id="9fc0e-166">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9fc0e-167">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9fc0e-167">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9fc0e-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="9fc0e-168">See Also</span></span>  
 [<span data-ttu-id="9fc0e-169">Postupy: použití pojmenovaných a nepovinných argumentů v programování pro Office</span><span class="sxs-lookup"><span data-stu-id="9fc0e-169">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [<span data-ttu-id="9fc0e-170">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="9fc0e-170">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [<span data-ttu-id="9fc0e-171">Použití konstruktorů</span><span class="sxs-lookup"><span data-stu-id="9fc0e-171">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
 [<span data-ttu-id="9fc0e-172">Použití indexerů</span><span class="sxs-lookup"><span data-stu-id="9fc0e-172">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)
