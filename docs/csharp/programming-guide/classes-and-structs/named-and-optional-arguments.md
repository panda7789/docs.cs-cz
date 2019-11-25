---
title: Pojmenované a volitelné argumenty – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
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
ms.openlocfilehash: 30475b637202d3b614ac968897e467956bc78646
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970510"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="177ba-102">Pojmenované a nepovinné argumenty (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="177ba-102">Named and Optional Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="177ba-103">C#4 zavádí pojmenované a volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="177ba-103">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="177ba-104">*Pojmenované argumenty* umožňují zadat argument pro konkrétní parametr přiřazením argumentu s názvem parametru, nikoli zadáním pozice parametru v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="177ba-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="177ba-105">*Volitelné argumenty* umožňují vynechat argumenty pro některé parametry.</span><span class="sxs-lookup"><span data-stu-id="177ba-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="177ba-106">Oba postupy lze použít s metodami, indexery, konstruktory a delegáty.</span><span class="sxs-lookup"><span data-stu-id="177ba-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="177ba-107">Při použití pojmenovaných a volitelných argumentů jsou argumenty vyhodnocovány v pořadí, v jakém jsou uvedeny v seznamu argumentů, nikoli v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="177ba-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="177ba-108">Pojmenované a volitelné parametry – při použití společně vám umožní zadat argumenty jenom pro několik parametrů ze seznamu nepovinných parametrů.</span><span class="sxs-lookup"><span data-stu-id="177ba-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="177ba-109">Tato funkce významně usnadňuje volání rozhraní COM, jako jsou systém Microsoft Office rozhraní API pro automatizaci.</span><span class="sxs-lookup"><span data-stu-id="177ba-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="177ba-110">Pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="177ba-110">Named Arguments</span></span>  
 <span data-ttu-id="177ba-111">Pojmenované argumenty, které si zapamatujete, abyste si vyhledali pořadí parametrů v seznamech volaných metod.</span><span class="sxs-lookup"><span data-stu-id="177ba-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="177ba-112">Parametr pro každý argument lze zadat pomocí názvu parametru.</span><span class="sxs-lookup"><span data-stu-id="177ba-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="177ba-113">Například funkce, která tiskne podrobnosti objednávky (například, jméno prodejce, číslo objednávky & název produktu), může být volána standardním způsobem odesláním argumentů podle pozice v pořadí určeném funkcí.</span><span class="sxs-lookup"><span data-stu-id="177ba-113">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="177ba-114">Pokud si nepamatujete pořadí parametrů, ale znáte jejich názvy, můžete argumenty poslat v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="177ba-114">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="177ba-115">Pojmenované argumenty také zlepšují čitelnost kódu tím, že identifikují, co každý argument představuje.</span><span class="sxs-lookup"><span data-stu-id="177ba-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="177ba-116">V níže uvedené metodě příklad `sellerName` nemůže být null nebo prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="177ba-116">In the example method below, the `sellerName` cannot be null or white space.</span></span> <span data-ttu-id="177ba-117">Jak `sellerName` i `productName` jsou typy řetězců namísto odeslání argumentů podle pozice, má smysl použít pojmenované argumenty k jednoznačnému odstranění těchto dvou a omezení nejasností pro kohokoli, kdo čte kód.</span><span class="sxs-lookup"><span data-stu-id="177ba-117">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="177ba-118">Pojmenované argumenty, pokud se používají s pozičními argumenty, jsou platné, dokud</span><span class="sxs-lookup"><span data-stu-id="177ba-118">Named arguments, when used with positional arguments, are valid as long as</span></span> 

- <span data-ttu-id="177ba-119">nejsou následovány žádnými pozičními argumenty nebo</span><span class="sxs-lookup"><span data-stu-id="177ba-119">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="177ba-120">_počínaje C# 7,2_se používají ve správné pozici.</span><span class="sxs-lookup"><span data-stu-id="177ba-120">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="177ba-121">V následujícím příkladu je parametr `orderNum` ve správné pozici, ale není explicitně pojmenován.</span><span class="sxs-lookup"><span data-stu-id="177ba-121">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="177ba-122">Poziční argumenty, které následují za libovolnými pojmenovanými argumenty, jsou neplatné.</span><span class="sxs-lookup"><span data-stu-id="177ba-122">Positional arguments that follow any out-of-order named arguments are invalid.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="177ba-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="177ba-123">Example</span></span>  
 <span data-ttu-id="177ba-124">Následující kód implementuje příklady z této části spolu s dalšími dalšími.</span><span class="sxs-lookup"><span data-stu-id="177ba-124">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="177ba-125">Nepovinné argumenty</span><span class="sxs-lookup"><span data-stu-id="177ba-125">Optional Arguments</span></span>  
 <span data-ttu-id="177ba-126">Definice metody, konstruktoru, indexeru nebo delegáta může určit, že jeho parametry jsou povinné nebo že jsou nepovinné.</span><span class="sxs-lookup"><span data-stu-id="177ba-126">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="177ba-127">Jakékoli volání musí poskytnout argumenty pro všechny požadované parametry, ale může vynechat argumenty pro volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="177ba-127">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="177ba-128">Každý volitelný parametr má jako součást definice výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="177ba-128">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="177ba-129">Pokud není pro tento parametr odeslán žádný argument, je použita výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="177ba-129">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="177ba-130">Výchozí hodnota musí být jeden z následujících typů výrazů:</span><span class="sxs-lookup"><span data-stu-id="177ba-130">A default value must be one of the following types of expressions:</span></span>  
  
- <span data-ttu-id="177ba-131">konstantní výraz;</span><span class="sxs-lookup"><span data-stu-id="177ba-131">a constant expression;</span></span>  
  
- <span data-ttu-id="177ba-132">výraz `new ValType()` formuláře, kde `ValType` je hodnotový typ, jako je například [výčet](../../language-reference/keywords/enum.md) nebo [Struktura](./structs.md);</span><span class="sxs-lookup"><span data-stu-id="177ba-132">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../language-reference/keywords/enum.md) or a [struct](./structs.md);</span></span>  
  
- <span data-ttu-id="177ba-133">výraz výchozí hodnoty formuláře [(ValType)](../../language-reference/operators/default.md), kde `ValType` je hodnotový typ.</span><span class="sxs-lookup"><span data-stu-id="177ba-133">an expression of the form [default(ValType)](../../language-reference/operators/default.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="177ba-134">Volitelné parametry jsou definovány na konci seznamu parametrů po všech požadovaných parametrech.</span><span class="sxs-lookup"><span data-stu-id="177ba-134">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="177ba-135">Pokud volající poskytne argument pro jakékoli z úspěchu volitelných parametrů, musí zadat argumenty pro všechny předchozí volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="177ba-135">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="177ba-136">Mezery oddělené čárkami v seznamu argumentů nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="177ba-136">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="177ba-137">Například v následujícím kódu je metoda instance `ExampleMethod` definována s jedním vyžadovaným a dvěma nepovinnými parametry.</span><span class="sxs-lookup"><span data-stu-id="177ba-137">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 <span data-ttu-id="177ba-138">Následující volání `ExampleMethod` způsobí chybu kompilátoru, protože je k dispozici argument pro třetí parametr, ale ne pro druhý.</span><span class="sxs-lookup"><span data-stu-id="177ba-138">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="177ba-139">Pokud však znáte název třetího parametru, můžete k dokončení úkolu použít pojmenovaný argument.</span><span class="sxs-lookup"><span data-stu-id="177ba-139">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="177ba-140">Technologie IntelliSense používá hranaté závorky k označení volitelných parametrů, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="177ba-140">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>  
  
 ![Snímek obrazovky znázorňující rychlé informace technologie IntelliSense pro metodu ExampleMethod](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
> <span data-ttu-id="177ba-142">Můžete také deklarovat volitelné parametry pomocí třídy <xref:System.Runtime.InteropServices.OptionalAttribute> .NET.</span><span class="sxs-lookup"><span data-stu-id="177ba-142">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="177ba-143">parametry `OptionalAttribute` nevyžadují výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="177ba-143">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="177ba-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="177ba-144">Example</span></span>  
 <span data-ttu-id="177ba-145">V následujícím příkladu má konstruktor pro `ExampleClass` jeden parametr, který je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="177ba-145">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="177ba-146">Metoda instance `ExampleMethod` má jeden povinný parametr, `required` a dva volitelné parametry, `optionalstr` a `optionalint`.</span><span class="sxs-lookup"><span data-stu-id="177ba-146">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="177ba-147">Kód v `Main` ukazuje různé způsoby, jak lze vyvolat konstruktor a metodu.</span><span class="sxs-lookup"><span data-stu-id="177ba-147">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="177ba-148">Rozhraní COM</span><span class="sxs-lookup"><span data-stu-id="177ba-148">COM Interfaces</span></span>  
 <span data-ttu-id="177ba-149">Pojmenované a nepovinné argumenty, společně s podporou pro dynamické objekty a další vylepšení, významně zlepšují interoperabilitu s rozhraními API modelu COM, jako jsou třeba rozhraní API pro automatizaci Office.</span><span class="sxs-lookup"><span data-stu-id="177ba-149">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="177ba-150">Například metoda <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> v rozhraní systém Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> má sedm parametrů, z nichž všechny jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="177ba-150">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="177ba-151">Tyto parametry jsou uvedeny na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="177ba-151">These parameters are shown in the following illustration:</span></span>  
  
 ![Snímek obrazovky s rychlými informacemi technologie IntelliSense pro metodu automatického formátování](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 <span data-ttu-id="177ba-153">V C# 3,0 a starších verzích je pro každý parametr požadován argument, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="177ba-153">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 <span data-ttu-id="177ba-154">Můžete však výrazně zjednodušit volání `AutoFormat` pomocí pojmenovaných a nepovinných argumentů představených v C# 4,0.</span><span class="sxs-lookup"><span data-stu-id="177ba-154">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="177ba-155">Pojmenované a volitelné argumenty umožňují vynechat argument pro volitelný parametr, pokud nechcete změnit výchozí hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="177ba-155">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="177ba-156">V následujícím volání je hodnota zadána pouze pro jeden ze sedmi parametrů.</span><span class="sxs-lookup"><span data-stu-id="177ba-156">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 <span data-ttu-id="177ba-157">Další informace a příklady najdete v tématu [použití pojmenovaných a nepovinných argumentů v programování pro systém Office](./how-to-use-named-and-optional-arguments-in-office-programming.md) a [Postup: přístup k objektům C# Interop sady Office pomocí vizuálních funkcí](../interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="177ba-157">For more information and examples, see [How to use named and optional arguments in Office programming](./how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="177ba-158">Rozlišení přetěžování</span><span class="sxs-lookup"><span data-stu-id="177ba-158">Overload Resolution</span></span>  
 <span data-ttu-id="177ba-159">Použití pojmenovaných a nepovinných argumentů má vliv na rozlišení přetížení následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="177ba-159">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
- <span data-ttu-id="177ba-160">Metoda, indexer nebo konstruktor je kandidátem na provedení, pokud jsou jednotlivé parametry buď volitelné, nebo odpovídají, podle názvu nebo podle pozice, k jednomu argumentu v příkazu volání a tento argument lze převést na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="177ba-160">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
- <span data-ttu-id="177ba-161">Pokud je nalezen více než jeden kandidát, budou pravidla rozlišení přetížení pro preferované převody použita na argumenty, které jsou explicitně určeny.</span><span class="sxs-lookup"><span data-stu-id="177ba-161">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="177ba-162">Vynechané argumenty pro volitelné parametry jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="177ba-162">Omitted arguments for optional parameters are ignored.</span></span>  
  
- <span data-ttu-id="177ba-163">Pokud jsou dva kandidáty odůvodněné stejně dobré, preference směřuje k kandidátovi, který nemá nepovinné parametry pro to, které argumenty byly ve volání vynechány.</span><span class="sxs-lookup"><span data-stu-id="177ba-163">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="177ba-164">Jedná se o důsledek Obecné předvolby v řešení přetížení pro kandidáty, které mají méně parametrů.</span><span class="sxs-lookup"><span data-stu-id="177ba-164">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="177ba-165">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="177ba-165">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="177ba-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="177ba-166">See also</span></span>

- [<span data-ttu-id="177ba-167">Postupy: použití pojmenovaných a nepovinných argumentů v programování pro systém Office</span><span class="sxs-lookup"><span data-stu-id="177ba-167">How to: use named and optional arguments in Office programming</span></span>](./how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="177ba-168">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="177ba-168">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="177ba-169">Použití konstruktorů</span><span class="sxs-lookup"><span data-stu-id="177ba-169">Using Constructors</span></span>](./using-constructors.md)
- [<span data-ttu-id="177ba-170">Použití indexerů</span><span class="sxs-lookup"><span data-stu-id="177ba-170">Using Indexers</span></span>](../indexers/using-indexers.md)
