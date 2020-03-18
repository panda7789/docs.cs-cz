---
title: Pojmenované a volitelné argumenty – programovací příručka jazyka C#
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
ms.openlocfilehash: 15b685248730c1f742035612a201d97d180bbc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399810"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="a073c-102">Pojmenované a nepovinné argumenty (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="a073c-102">Named and Optional Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="a073c-103">C# 4 zavádí pojmenované a volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="a073c-103">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="a073c-104">*Pojmenované argumenty* umožňují zadat argument pro určitý parametr tak, že argument připojujete k názvu parametru, nikoli k umístění parametru v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="a073c-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="a073c-105">*Volitelné argumenty* umožňují vynechat argumenty pro některé parametry.</span><span class="sxs-lookup"><span data-stu-id="a073c-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="a073c-106">Obě techniky lze použít s metodami, indexery, konstruktory a delegáty.</span><span class="sxs-lookup"><span data-stu-id="a073c-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="a073c-107">Při použití pojmenované a volitelné argumenty argumenty jsou vyhodnoceny v pořadí, ve kterém se zobrazí v seznamu argumentů, nikoli seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="a073c-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="a073c-108">Pojmenované a volitelné parametry, pokud jsou použity společně, umožňují zadat argumenty pouze pro několik parametrů ze seznamu volitelných parametrů.</span><span class="sxs-lookup"><span data-stu-id="a073c-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="a073c-109">Tato funkce výrazně usnadňuje volání rozhraní MODELU COM, jako jsou rozhraní API automatizace sady Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="a073c-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="a073c-110">Pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="a073c-110">Named Arguments</span></span>  
 <span data-ttu-id="a073c-111">Pojmenované argumenty vás osvobozují od nutnosti pamatovat si nebo vyhledat pořadí parametrů v seznamech parametrů volaných metod.</span><span class="sxs-lookup"><span data-stu-id="a073c-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="a073c-112">Parametr pro každý argument lze zadat podle názvu parametru.</span><span class="sxs-lookup"><span data-stu-id="a073c-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="a073c-113">Například funkce, která tiskne podrobnosti objednávky (například jméno prodejce, číslo objednávky & název produktu), může být volána standardním způsobem odesláním argumentů podle pozice v pořadí definovaném funkcí.</span><span class="sxs-lookup"><span data-stu-id="a073c-113">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="a073c-114">Pokud si nepamatujete pořadí parametrů, ale znáte jejich názvy, můžete odeslat argumenty v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a073c-114">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="a073c-115">Pojmenované argumenty také zlepšit čitelnost kódu určením, co každý argument představuje.</span><span class="sxs-lookup"><span data-stu-id="a073c-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="a073c-116">V příkladu metody `sellerName` níže nemůže být null nebo prázdné místo.</span><span class="sxs-lookup"><span data-stu-id="a073c-116">In the example method below, the `sellerName` cannot be null or white space.</span></span> <span data-ttu-id="a073c-117">Jako `sellerName` oba `productName` a jsou typy řetězců, namísto odesílání argumentů podle pozice, má smysl použít pojmenované argumenty k rozdvojení dvou a snížit nejasnosti pro každého, kdo čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="a073c-117">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="a073c-118">Pojmenované argumenty, jsou-li použity s pozičními argumenty, jsou platné, pokud</span><span class="sxs-lookup"><span data-stu-id="a073c-118">Named arguments, when used with positional arguments, are valid as long as</span></span>

- <span data-ttu-id="a073c-119">nejsou následovány žádnými pozičními argumenty, nebo</span><span class="sxs-lookup"><span data-stu-id="a073c-119">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="a073c-120">_počínaje C# 7.2_, jsou používány ve správné poloze.</span><span class="sxs-lookup"><span data-stu-id="a073c-120">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="a073c-121">V níže uvedeném `orderNum` příkladu je parametr ve správné pozici, ale není explicitně pojmenován.</span><span class="sxs-lookup"><span data-stu-id="a073c-121">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="a073c-122">Poziční argumenty, které následují za všemi pojmenovaná argumenty mimo pořadí, jsou neplatné.</span><span class="sxs-lookup"><span data-stu-id="a073c-122">Positional arguments that follow any out-of-order named arguments are invalid.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="a073c-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="a073c-123">Example</span></span>  
 <span data-ttu-id="a073c-124">Následující kód implementuje příklady z této části spolu s některé další.</span><span class="sxs-lookup"><span data-stu-id="a073c-124">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="a073c-125">Volitelné argumenty</span><span class="sxs-lookup"><span data-stu-id="a073c-125">Optional Arguments</span></span>  
 <span data-ttu-id="a073c-126">Definice metody, konstruktoru, indexeru nebo delegáta může určit, že jsou požadovány jeho parametry nebo že jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="a073c-126">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="a073c-127">Každé volání musí poskytnout argumenty pro všechny požadované parametry, ale může vynechat argumenty pro volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="a073c-127">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="a073c-128">Každý volitelný parametr má jako součást své definice výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a073c-128">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="a073c-129">Pokud pro tento parametr není odeslán žádný argument, použije se výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="a073c-129">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="a073c-130">Výchozí hodnota musí být jeden z následujících typů výrazů:</span><span class="sxs-lookup"><span data-stu-id="a073c-130">A default value must be one of the following types of expressions:</span></span>  
  
- <span data-ttu-id="a073c-131">konstantní výraz;</span><span class="sxs-lookup"><span data-stu-id="a073c-131">a constant expression;</span></span>  
  
- <span data-ttu-id="a073c-132">výraz formuláře `new ValType()`, kde `ValType` je typ hodnoty, například [výčtnebo](../../language-reference/builtin-types/enum.md) [struktura](../../language-reference/builtin-types/struct.md);</span><span class="sxs-lookup"><span data-stu-id="a073c-132">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../language-reference/builtin-types/enum.md) or a [struct](../../language-reference/builtin-types/struct.md);</span></span>  
  
- <span data-ttu-id="a073c-133">výraz výchozího formuláře [(ValType),](../../language-reference/operators/default.md) `ValType` kde je typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a073c-133">an expression of the form [default(ValType)](../../language-reference/operators/default.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="a073c-134">Volitelné parametry jsou definovány na konci seznamu parametrů po všech požadovaných parametrech.</span><span class="sxs-lookup"><span data-stu-id="a073c-134">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="a073c-135">Pokud volající poskytuje argument pro některý z posloupnosti volitelných parametrů, musí poskytnout argumenty pro všechny předchozí volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="a073c-135">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="a073c-136">Mezery oddělené čárkami v seznamu argumentů nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="a073c-136">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="a073c-137">Například v následujícím kódu je `ExampleMethod` metoda instance definována s jedním povinným a dvěma volitelnými parametry.</span><span class="sxs-lookup"><span data-stu-id="a073c-137">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 <span data-ttu-id="a073c-138">Následující volání `ExampleMethod` způsobí chybu kompilátoru, protože argument je k dispozici pro třetí parametr, ale ne pro druhý.</span><span class="sxs-lookup"><span data-stu-id="a073c-138">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="a073c-139">Pokud však znáte název třetího parametru, můžete k provedení úkolu použít pojmenovaný argument.</span><span class="sxs-lookup"><span data-stu-id="a073c-139">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="a073c-140">Technologie IntelliSense používá závorky k označení volitelných parametrů, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="a073c-140">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>  
  
 ![Snímek obrazovky s rychlými informacemi intelliSense pro metodu ExampleMethod](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
> <span data-ttu-id="a073c-142">Volitelné parametry můžete také deklarovat pomocí třídy .NET. <xref:System.Runtime.InteropServices.OptionalAttribute></span><span class="sxs-lookup"><span data-stu-id="a073c-142">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="a073c-143">`OptionalAttribute`parametry nevyžadují výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a073c-143">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a073c-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="a073c-144">Example</span></span>  
 <span data-ttu-id="a073c-145">V následujícím příkladu má `ExampleClass` konstruktor pro jeden parametr, který je volitelný.</span><span class="sxs-lookup"><span data-stu-id="a073c-145">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="a073c-146">Metoda `ExampleMethod` instance má jeden `required`povinný parametr a `optionalstr` dva `optionalint`volitelné parametry a .</span><span class="sxs-lookup"><span data-stu-id="a073c-146">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="a073c-147">Kód v `Main` ukazuje různé způsoby, ve kterém konstruktor a metoda může být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="a073c-147">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="a073c-148">Rozhraní COM</span><span class="sxs-lookup"><span data-stu-id="a073c-148">COM Interfaces</span></span>  
 <span data-ttu-id="a073c-149">Pojmenované a volitelné argumenty spolu s podporou dynamických objektů a dalších vylepšení výrazně zlepšují interoperabilitu s rozhraními API com, jako jsou rozhraní API pro automatizaci office.</span><span class="sxs-lookup"><span data-stu-id="a073c-149">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="a073c-150">Například <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> metoda v rozhraní aplikace <xref:Microsoft.Office.Interop.Excel.Range> Microsoft Office Excel má sedm parametrů, z nichž všechny jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="a073c-150">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="a073c-151">Tyto parametry jsou znázorněny na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="a073c-151">These parameters are shown in the following illustration:</span></span>  
  
 ![Snímek obrazovky s rychlými informacemi technologie IntelliSense pro metodu automatického formátování](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 <span data-ttu-id="a073c-153">V C# 3.0 a starší verze argument je vyžadován pro každý parametr, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a073c-153">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 <span data-ttu-id="a073c-154">Však můžete výrazně zjednodušit `AutoFormat` volání pomocí pojmenované a volitelné argumenty, zavedené v C# 4.0.</span><span class="sxs-lookup"><span data-stu-id="a073c-154">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="a073c-155">Pojmenované a volitelné argumenty umožňují vynechat argument pro volitelný parametr, pokud nechcete změnit výchozí hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="a073c-155">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="a073c-156">V následujícím volání je zadána hodnota pouze pro jeden ze sedmi parametrů.</span><span class="sxs-lookup"><span data-stu-id="a073c-156">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 <span data-ttu-id="a073c-157">Další informace a příklady najdete [v tématu Použití pojmenovaných a volitelných argumentů v programování sady Office](./how-to-use-named-and-optional-arguments-in-office-programming.md) a Jak získat přístup k [objektům interop sady Office pomocí funkcí Jazyka C#](../interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="a073c-157">For more information and examples, see [How to use named and optional arguments in Office programming](./how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to access Office interop objects by using C# features](../interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="a073c-158">Rozlišení přetěžování</span><span class="sxs-lookup"><span data-stu-id="a073c-158">Overload Resolution</span></span>  
 <span data-ttu-id="a073c-159">Použití pojmenovaných a volitelných argumentů ovlivňuje řešení přetížení následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="a073c-159">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
- <span data-ttu-id="a073c-160">Metoda, indexer nebo konstruktor je kandidátem pro spuštění, pokud je každý z jeho parametrů volitelný nebo odpovídá podle názvu nebo pozice jednomu argumentu v příkazu volání a tento argument lze převést na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="a073c-160">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
- <span data-ttu-id="a073c-161">Pokud je nalezen více než jeden kandidát, pravidla řešení přetížení pro upřednostňované převody se použijí na argumenty, které jsou explicitně zadány.</span><span class="sxs-lookup"><span data-stu-id="a073c-161">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="a073c-162">Vynechané argumenty pro volitelné parametry jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="a073c-162">Omitted arguments for optional parameters are ignored.</span></span>  
  
- <span data-ttu-id="a073c-163">Pokud jsou dva kandidáti považováni za stejně dobré, upřednostňuje se kandidát, který nemá volitelné parametry, pro které byly argumenty ve výzvě vynechány.</span><span class="sxs-lookup"><span data-stu-id="a073c-163">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="a073c-164">To je důsledkem obecné preference v řešení přetížení pro kandidáty, kteří mají méně parametrů.</span><span class="sxs-lookup"><span data-stu-id="a073c-164">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a073c-165">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a073c-165">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a073c-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="a073c-166">See also</span></span>

- [<span data-ttu-id="a073c-167">Použití pojmenovaných a volitelných argumentů v programování sady Office</span><span class="sxs-lookup"><span data-stu-id="a073c-167">How to use named and optional arguments in Office programming</span></span>](./how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="a073c-168">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="a073c-168">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="a073c-169">Použití konstruktorů</span><span class="sxs-lookup"><span data-stu-id="a073c-169">Using Constructors</span></span>](./using-constructors.md)
- [<span data-ttu-id="a073c-170">Použití indexerů</span><span class="sxs-lookup"><span data-stu-id="a073c-170">Using Indexers</span></span>](../indexers/using-indexers.md)
