---
title: Pojmenované a nepovinné argumenty - C# Průvodce programováním
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
ms.openlocfilehash: 086b76fdc7a97f80fb0b93956b2ee3eef7036506
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583101"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="15c62-102">Pojmenované a nepovinné argumenty (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="15c62-102">Named and Optional Arguments (C# Programming Guide)</span></span>
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] <span data-ttu-id="15c62-103">představuje pojmenované a nepovinné argumenty.</span><span class="sxs-lookup"><span data-stu-id="15c62-103">introduces named and optional arguments.</span></span> <span data-ttu-id="15c62-104">*Pojmenované argumenty* vám umožní zadat argument pro parametr konkrétní tím, že přidružíte argument s názvem parametru místo parametru pozice v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="15c62-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="15c62-105">*Volitelné argumenty* umožňují vynechejte argumenty pro některé parametry.</span><span class="sxs-lookup"><span data-stu-id="15c62-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="15c62-106">Obě tyto metody lze pomocí metody, indexery, konstruktory a delegáti.</span><span class="sxs-lookup"><span data-stu-id="15c62-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="15c62-107">Při použití pojmenované a nepovinné argumenty jsou argumenty se vyhodnocují v pořadí, v jakém jsou uvedeny v seznamu argumentů, ne seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="15c62-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="15c62-108">Pojmenované a nepovinné parametry, pokud se použijí společně, umožňují zadat argumenty pouze několik parametrů ze seznamu nepovinných parametrů.</span><span class="sxs-lookup"><span data-stu-id="15c62-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="15c62-109">Tato funkce výrazně usnadňuje volání do rozhraní COM, jako je například rozhraní API automatizace Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="15c62-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="15c62-110">Pojmenované argumenty</span><span class="sxs-lookup"><span data-stu-id="15c62-110">Named Arguments</span></span>  
 <span data-ttu-id="15c62-111">Pojmenované argumenty vás zbaví nutnosti mějte na paměti, nebo k vyhledání pořadí parametrů v seznamech parametrů volané metody.</span><span class="sxs-lookup"><span data-stu-id="15c62-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="15c62-112">Parametr pro každý argument může být určeno název parametru.</span><span class="sxs-lookup"><span data-stu-id="15c62-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="15c62-113">Například funkce, která vytiskne OrderDetails (jako jsou například prodejce název, číslo & product název objednávky) mohou být volány v standardní způsob odesílání argumentů podle pozice v pořadí určeném parametrem funkce.</span><span class="sxs-lookup"><span data-stu-id="15c62-113">For example, a function that prints order details (such as, seller name, order number & product name) can be called in the standard way by sending arguments by position, in the order defined by the function.</span></span>
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 <span data-ttu-id="15c62-114">Pokud nepamatujete pořadí parametrů, ale znáte jejich názvy, můžete odeslat argumenty v libovolném pořadí.</span><span class="sxs-lookup"><span data-stu-id="15c62-114">If you do not remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 <span data-ttu-id="15c62-115">Pojmenované argumenty také zlepšit čitelnost kódu díky identifikaci, co každý argument představuje.</span><span class="sxs-lookup"><span data-stu-id="15c62-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="15c62-116">V následujícím příkladu metoda `sellerName` nesmí být null ani prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="15c62-116">In the example method below, the `sellerName` cannot be null or white space.</span></span> <span data-ttu-id="15c62-117">Obě `sellerName` a `productName` jsou typy řetězce, místo abyste odesílali argumentů podle pozice, je vhodné použít pojmenované argumenty k rozlišení dvou a redukovat nejasnosti pro každého, kdo čte kód.</span><span class="sxs-lookup"><span data-stu-id="15c62-117">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
 <span data-ttu-id="15c62-118">Pojmenované argumenty, při použití s poziční argumenty, jsou platné jako</span><span class="sxs-lookup"><span data-stu-id="15c62-118">Named arguments, when used with positional arguments, are valid as long as</span></span> 

- <span data-ttu-id="15c62-119">nejsou následovány poziční argumenty, nebo</span><span class="sxs-lookup"><span data-stu-id="15c62-119">they're not followed by any positional arguments, or</span></span>

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- <span data-ttu-id="15c62-120">_od verze C# 7.2_, jejich použití ve správné pozici.</span><span class="sxs-lookup"><span data-stu-id="15c62-120">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="15c62-121">V příkladu níže parametr `orderNum` je ve správné pozici, ale není explicitně s názvem.</span><span class="sxs-lookup"><span data-stu-id="15c62-121">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 <span data-ttu-id="15c62-122">Mimo pořadí pojmenované argumenty jsou však neplatná, pokud jste postupovali podle poziční argumenty.</span><span class="sxs-lookup"><span data-stu-id="15c62-122">However, out-of-order named arguments are invalid if they're followed by positional arguments.</span></span>

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a><span data-ttu-id="15c62-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="15c62-123">Example</span></span>  
 <span data-ttu-id="15c62-124">Následující kód implementuje příklady v této části spolu s některé další značky.</span><span class="sxs-lookup"><span data-stu-id="15c62-124">The following code implements the examples from this section along with some additional ones.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a><span data-ttu-id="15c62-125">Nepovinné argumenty.</span><span class="sxs-lookup"><span data-stu-id="15c62-125">Optional Arguments</span></span>  
 <span data-ttu-id="15c62-126">Definice metody, konstruktoru, indexeru nebo delegáta můžete určit, že její parametry jsou povinné a že jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="15c62-126">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="15c62-127">Každé volání musí zadat argumenty pro všechny požadované parametry, ale lze vynechat argumenty pro volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="15c62-127">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="15c62-128">Každý volitelný parametr má výchozí hodnotu jako součást jeho definici.</span><span class="sxs-lookup"><span data-stu-id="15c62-128">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="15c62-129">Pokud pro tento parametr je odeslán žádný argument, je použita výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="15c62-129">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="15c62-130">Výchozí hodnota musí být jedna z následujících typů výrazů:</span><span class="sxs-lookup"><span data-stu-id="15c62-130">A default value must be one of the following types of expressions:</span></span>  
  
- <span data-ttu-id="15c62-131">konstantní výraz;</span><span class="sxs-lookup"><span data-stu-id="15c62-131">a constant expression;</span></span>  
  
- <span data-ttu-id="15c62-132">výraz ve tvaru `new ValType()`, kde `ValType` , jako je typ hodnoty, [výčtu](../../../csharp/language-reference/keywords/enum.md) nebo [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md);</span><span class="sxs-lookup"><span data-stu-id="15c62-132">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../../csharp/language-reference/keywords/enum.md) or a [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span></span>  
  
- <span data-ttu-id="15c62-133">výraz ve tvaru [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), kde `ValType` je typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="15c62-133">an expression of the form [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="15c62-134">Volitelné parametry jsou definované na konci seznamu parametrů po požadované parametry.</span><span class="sxs-lookup"><span data-stu-id="15c62-134">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="15c62-135">Pokud volající zadá argument pro každý z sledu očekávání volitelné parametry, je nutné zadat argumenty pro všechny předchozí volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="15c62-135">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="15c62-136">Exportovaná mezery v seznamu argumentů nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="15c62-136">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="15c62-137">Například následující kód metodu instance `ExampleMethod` je definována s vyžadovaný a dva volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="15c62-137">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 <span data-ttu-id="15c62-138">Následující volání `ExampleMethod` způsobí chybu kompilátoru, protože argument je k dispozici pro třetí parametr, ale ne pro druhý.</span><span class="sxs-lookup"><span data-stu-id="15c62-138">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="15c62-139">Pokud znáte název třetí parametr, můžete ke splnění úkolu můžete použít pojmenovaný argument.</span><span class="sxs-lookup"><span data-stu-id="15c62-139">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="15c62-140">Technologie IntelliSense pomocí závorek k označení volitelné parametry, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="15c62-140">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>  
  
 ![Snímek obrazovky zobrazující rychlé informace technologie IntelliSense pro metodu ExampleMethod.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
>  <span data-ttu-id="15c62-142">Volitelné parametry můžete také deklarovat s použitím .NET <xref:System.Runtime.InteropServices.OptionalAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="15c62-142">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="15c62-143">`OptionalAttribute` Parametry nevyžadují, aby výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="15c62-143">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15c62-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="15c62-144">Example</span></span>  
 <span data-ttu-id="15c62-145">V následujícím příkladu se v konstruktoru pro `ExampleClass` má jeden parametr, který je volitelný.</span><span class="sxs-lookup"><span data-stu-id="15c62-145">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="15c62-146">Metodu instance `ExampleMethod` má jeden povinný parametr, `required`a dva volitelné parametry, `optionalstr` a `optionalint`.</span><span class="sxs-lookup"><span data-stu-id="15c62-146">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="15c62-147">Kód v `Main` ukazuje různé způsoby, ve kterém lze vyvolat konstruktor a metody.</span><span class="sxs-lookup"><span data-stu-id="15c62-147">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a><span data-ttu-id="15c62-148">Com – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15c62-148">COM Interfaces</span></span>  
 <span data-ttu-id="15c62-149">Pojmenované a nepovinné argumenty společně s podporou dynamických objektů a dalších vylepšení, výrazně zlepšit vzájemná funkční spolupráce s rozhraními API modelu COM, jako je například rozhraní API Office automatizace.</span><span class="sxs-lookup"><span data-stu-id="15c62-149">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="15c62-150">Například <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> metodu v aplikaci Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> rozhraní obsahuje sedm parametry, z nichž všechny jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="15c62-150">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="15c62-151">Tyto parametry můžete vidět na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="15c62-151">These parameters are shown in the following illustration:</span></span>  
  
 ![Snímek obrazovky zobrazující rychlé informace technologie IntelliSense pro metodu automatické formátování.](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 <span data-ttu-id="15c62-153">V jazyce C# 3.0 a starší verze je argument se vyžaduje pro každý parametr, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="15c62-153">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 <span data-ttu-id="15c62-154">Však může výrazně zjednodušit volání `AutoFormat` pomocí pojmenovaných a nepovinných argumentů zavedené v C# 4.0.</span><span class="sxs-lookup"><span data-stu-id="15c62-154">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="15c62-155">Pojmenované a nepovinné argumenty umožňují argument pro nepovinný parametr vynechat, pokud nechcete změnit výchozí hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="15c62-155">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="15c62-156">V následujícím volání je zadána hodnota jenom pro jednu ze sedmi parametry.</span><span class="sxs-lookup"><span data-stu-id="15c62-156">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 <span data-ttu-id="15c62-157">Další informace a příklady najdete v tématu [jak: Použití pojmenovaných a nepovinných argumentů v programování pro Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) a [jak: Přístup k objektům Interop sady Office pomocí Vizuálu C# funkce](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="15c62-157">For more information and examples, see [How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="15c62-158">Rozlišení přetěžování</span><span class="sxs-lookup"><span data-stu-id="15c62-158">Overload Resolution</span></span>  
 <span data-ttu-id="15c62-159">Použití pojmenovaných a nepovinných argumentů řešení přetížení ovlivňuje následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="15c62-159">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
- <span data-ttu-id="15c62-160">Metoda, indexer nebo konstruktor je kandidátem pro spuštění, pokud každý ze svých parametrů je nepovinný nebo odpovídá podle názvu nebo podle pozice jediný argument ve volání příkazu, a že argument lze převést na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="15c62-160">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
- <span data-ttu-id="15c62-161">Pokud je nalezen více než jeden Release candidate, pravidla rozlišení přetížení pro upřednostňované převody se aplikují na argumenty, které jsou explicitně zadány.</span><span class="sxs-lookup"><span data-stu-id="15c62-161">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="15c62-162">Vynechaný argumenty pro volitelné parametry jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="15c62-162">Omitted arguments for optional parameters are ignored.</span></span>  
  
- <span data-ttu-id="15c62-163">Pokud dvě kandidáty jsou považovány za stejnou měrou bezproblémový, předvoleb přejde na Release candidate, který nemá žádné volitelné parametry, které byly vynechány argumenty ve volání.</span><span class="sxs-lookup"><span data-stu-id="15c62-163">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="15c62-164">Toto je důsledkem obecné předvoleb v rozlišení přetížení pro kandidáty, které mají méně parametrů.</span><span class="sxs-lookup"><span data-stu-id="15c62-164">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="15c62-165">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="15c62-165">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="15c62-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15c62-166">See also</span></span>

- [<span data-ttu-id="15c62-167">Postupy: Použití pojmenovaných a nepovinných argumentů v programování pro Office</span><span class="sxs-lookup"><span data-stu-id="15c62-167">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="15c62-168">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="15c62-168">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="15c62-169">Použití konstruktorů</span><span class="sxs-lookup"><span data-stu-id="15c62-169">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)
- [<span data-ttu-id="15c62-170">Použití indexerů</span><span class="sxs-lookup"><span data-stu-id="15c62-170">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)
