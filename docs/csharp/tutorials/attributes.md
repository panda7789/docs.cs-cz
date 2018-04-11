---
title: Atributy - C#
description: Zjistěte, jak fungují atributy v jazyce C#.
keywords: Rozhraní .NET, .NET core, C#, atributy
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: dad02c64d22fe0f127057202c082680f13261d7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-attributes-in-c"></a><span data-ttu-id="0ae6c-104">Pomocí atributů v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0ae6c-104">Using Attributes in C#</span></span> #

<span data-ttu-id="0ae6c-105">Atributy poskytují způsob přiřazení informace s kódem deklarativní způsobem.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-105">Attributes provide a way of associating information with code in a declarative way.</span></span> <span data-ttu-id="0ae6c-106">Můžete zadat taky opakovaně použitelné element, který lze použít na celou řadu cíle.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-106">They can also provide a reusable element that can be applied to a variety of targets.</span></span>

<span data-ttu-id="0ae6c-107">Vezměte v úvahu `[Obsolete]` atribut.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-107">Consider the `[Obsolete]` attribute.</span></span> <span data-ttu-id="0ae6c-108">Je možné použít pro třídy, struktury, metody, konstruktory a další.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-108">It can be applied to classes, structs, methods, constructors, and more.</span></span> <span data-ttu-id="0ae6c-109">Ho _deklaruje_ , že prvek je zastaralé.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-109">It _declares_ that the element is obsolete.</span></span> <span data-ttu-id="0ae6c-110">Pak je kompilátor jazyka C# vyhledejte tento atribut a provádět některé akce v odpovědi.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-110">It's then up to the C# compiler to look for this attribute, and do some action in response.</span></span>

<span data-ttu-id="0ae6c-111">V tomto kurzu se seznámíte k přidání atributů do vašeho kódu, jak vytvořit a používat vlastní atributy a použití některých atributů, které jsou součástí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-111">In this tutorial, you'll be introduced to how to add attributes to your code, how to create and use your own attributes, and how to use some attributes that are built into .NET Core.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0ae6c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ae6c-112">Prerequisites</span></span>
<span data-ttu-id="0ae6c-113">Budete potřebovat k nastavení vašeho počítače ke spuštění .NET core.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-113">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="0ae6c-114">Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-114">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="0ae6c-115">Tuto aplikaci můžete spustit v systému Windows, Ubuntu Linux, systému macOS nebo v kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-115">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="0ae6c-116">Budete muset nainstalovat editor vaše oblíbené kódu.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-116">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="0ae6c-117">Popisy níže použijte [Visual Studio Code](https://code.visualstudio.com/) který je typu open source pro různé platformy editor.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-117">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="0ae6c-118">Můžete však použít, ať nástroje umíte pracovat s.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-118">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="0ae6c-119">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="0ae6c-119">Create the Application</span></span>

<span data-ttu-id="0ae6c-120">Teď, když jste nainstalovali všechny nástroje, vytvořte novou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-120">Now that you've installed all the tools, create a new .NET Core application.</span></span> <span data-ttu-id="0ae6c-121">Pokud chcete používat generátor příkazového řádku, spusťte následující příkaz v své oblíbené prostředí:</span><span class="sxs-lookup"><span data-stu-id="0ae6c-121">To use the command line generator, execute the following command in your favorite shell:</span></span>

`dotnet new console`

<span data-ttu-id="0ae6c-122">Tento příkaz vytvoří jen nejzákladnější soubory projektu .NET core.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-122">This command will create barebones .NET core project files.</span></span> <span data-ttu-id="0ae6c-123">Budete muset provést `dotnet restore` Obnovit závislosti potřebné ke kompilaci tento projekt.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-123">You will need to execute `dotnet restore` to restore the dependencies needed to compile this project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="0ae6c-124">Spuštění programu, použijte `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-124">To execute the program, use `dotnet run`.</span></span> <span data-ttu-id="0ae6c-125">Měli byste vidět "Hello, World" výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-125">You should see "Hello, World" output to the console.</span></span>

## <a name="how-to-add-attributes-to-code"></a><span data-ttu-id="0ae6c-126">Postup přidání atributů do kódu</span><span class="sxs-lookup"><span data-stu-id="0ae6c-126">How to add attributes to code</span></span>

<span data-ttu-id="0ae6c-127">V jazyce C#, atributy jsou třídy, které dědí od `Attribute` základní třídy.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-127">In C#, attributes are classes that inherit from the `Attribute` base class.</span></span> <span data-ttu-id="0ae6c-128">Všechny třídy, která dědí z `Attribute` lze použít jako řazení "značky" v další části kódu.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-128">Any class that inherits from `Attribute` can be used as a sort of "tag" on other pieces of code.</span></span>
<span data-ttu-id="0ae6c-129">Například je atribut nazvaný `ObsoleteAttribute`.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-129">For instance, there is an attribute called `ObsoleteAttribute`.</span></span> <span data-ttu-id="0ae6c-130">Používá se signál, že kód je zastaralé a už by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-130">This is used to signal that code is obsolete and shouldn't be used anymore.</span></span> <span data-ttu-id="0ae6c-131">Tento atribut na třídu, můžete umístit například pomocí hranaté závorky.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-131">You can place this attribute on a class, for instance, by using square brackets.</span></span>

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]  

<span data-ttu-id="0ae6c-132">Všimněte si, že když je volána třída `ObsoleteAttribute`, pouze je nutné použít `[Obsolete]` v kódu.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-132">Note that while the class is called `ObsoleteAttribute`, it's only necessary to use `[Obsolete]` in the code.</span></span> <span data-ttu-id="0ae6c-133">Jedná se o konvenci, která následuje C#.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-133">This is a convention that C# follows.</span></span>
<span data-ttu-id="0ae6c-134">Můžete použít úplný název `[ObsoleteAttribute]` Pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-134">You can use the full name `[ObsoleteAttribute]` if you choose.</span></span>

<span data-ttu-id="0ae6c-135">Při označování třídu zastaralé, je vhodné zajistit nějaké informace, které jako *proč* je zastaralý, nebo *co* místo toho chcete použít.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-135">When marking a class obsolete, it's a good idea to provide some information as to *why* it's obsolete, and/or *what* to use instead.</span></span> <span data-ttu-id="0ae6c-136">To provedete v předávání do atribut zastaralý parametr řetězce.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-136">Do this by passing a string parameter to the Obsolete attribute.</span></span>

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

<span data-ttu-id="0ae6c-137">Řetězec je předávána jako argument pro `ObsoleteAttribute` konstruktoru, stejně, jako by byly zápis `var attr = new ObsoleteAttribute("some string")`.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-137">The string is being passed as an argument to an `ObsoleteAttribute` constructor, just as if you were writing `var attr = new ObsoleteAttribute("some string")`.</span></span>

<span data-ttu-id="0ae6c-138">Parametry, které atributu konstruktoru jsou omezeny na jednoduché typy nebo literály: `bool, int, double, string, Type, enums, etc` a pole těchto typů.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-138">Parameters to an attribute constructor are limited to simple types/literals: `bool, int, double, string, Type, enums, etc` and arrays of those types.</span></span>
<span data-ttu-id="0ae6c-139">Nelze použít výraz nebo proměnnou.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-139">You can not use an expression or a variable.</span></span> <span data-ttu-id="0ae6c-140">Budete používat poziční nebo pojmenované parametry.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-140">You are free to use positional or named parameters.</span></span>

## <a name="how-to-create-your-own-attribute"></a><span data-ttu-id="0ae6c-141">Jak vytvořit vlastní atribut</span><span class="sxs-lookup"><span data-stu-id="0ae6c-141">How to create your own attribute</span></span>

<span data-ttu-id="0ae6c-142">Vytváření atribut je jednoduché, která dědí z `Attribute` základní třídy.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-142">Creating an attribute is as simple as inheriting from the `Attribute` base class.</span></span>

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

<span data-ttu-id="0ae6c-143">Pomocí výše uvedeného I teď můžete použít `[MySpecial]` (nebo `[MySpecialAttribute]`) jako atribut jinde v základu kódu.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-143">With the above, I can now use `[MySpecial]` (or `[MySpecialAttribute]`) as an attribute elsewhere in the code base.</span></span>

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

<span data-ttu-id="0ae6c-144">Atributy v knihovně základní třídy rozhraní .NET, například `ObsoleteAttribute` aktivovat určitého chování v kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-144">Attributes in the .NET base class library like `ObsoleteAttribute` trigger certain behaviors within the compiler.</span></span> <span data-ttu-id="0ae6c-145">Ale všechny atributy, které vytvoříte slouží pouze jako metadata a nevede k žádný kód v rámci třídy atributů spouštěna.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-145">However, any attribute you create acts only as metadata, and doesn't result in any code within the attribute class being executed.</span></span> <span data-ttu-id="0ae6c-146">Je to na vám tak, aby fungoval na aby metadata někde v kódu (podrobnosti o této později v tomto kurzu).</span><span class="sxs-lookup"><span data-stu-id="0ae6c-146">It's up to you to act on that metadata elsewhere in your code (more on that later in the tutorial).</span></span>

<span data-ttu-id="0ae6c-147">Není gotcha zde sledujte.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-147">There is a 'gotcha' here to watch out for.</span></span> <span data-ttu-id="0ae6c-148">Jak je uvedeno nahoře, jsou povoleny pouze určité typy mají být předány jako argumenty, při použití atributů.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-148">As mentioned above, only certain types are allowed to be passed as arguments when using attributes.</span></span> <span data-ttu-id="0ae6c-149">Ale při vytváření typ atributu, kompilátor jazyka C# neukončí můžete z vytváření těchto parametrů.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-149">However, when creating an attribute type, the C# compiler won't stop you from creating those parameters.</span></span> <span data-ttu-id="0ae6c-150">V následujícím příkladu, vytvořili jste atribut s konstruktor, který se zkompiluje stejně dobře.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-150">In the below example, I've created an attribute with a constructor that compiles just fine.</span></span>

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

<span data-ttu-id="0ae6c-151">Však nebude možné použít tento konstruktor se syntaxí atributu.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-151">However, you will be unable to use this constructor with attribute syntax.</span></span>

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

<span data-ttu-id="0ae6c-152">Výše způsobí chybu kompilátoru jako`Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`</span><span class="sxs-lookup"><span data-stu-id="0ae6c-152">The above will cause a compiler error like `Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`</span></span>

## <a name="how-to-restrict-attribute-usage"></a><span data-ttu-id="0ae6c-153">Jak omezit použití atributu</span><span class="sxs-lookup"><span data-stu-id="0ae6c-153">How to restrict attribute usage</span></span>

<span data-ttu-id="0ae6c-154">Atributy lze použít na několika "cíle".</span><span class="sxs-lookup"><span data-stu-id="0ae6c-154">Attributes can be used on a number of "targets".</span></span> <span data-ttu-id="0ae6c-155">Příklady uvedené nahoře je pro třídy, ale můžete je také použít na:</span><span class="sxs-lookup"><span data-stu-id="0ae6c-155">The above examples show them on classes, but they can also be used on:</span></span>

* <span data-ttu-id="0ae6c-156">Assembly</span><span class="sxs-lookup"><span data-stu-id="0ae6c-156">Assembly</span></span>
* <span data-ttu-id="0ae6c-157">Třída</span><span class="sxs-lookup"><span data-stu-id="0ae6c-157">Class</span></span>
* <span data-ttu-id="0ae6c-158">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="0ae6c-158">Constructor</span></span>
* <span data-ttu-id="0ae6c-159">Delegát</span><span class="sxs-lookup"><span data-stu-id="0ae6c-159">Delegate</span></span>
* <span data-ttu-id="0ae6c-160">Výčet</span><span class="sxs-lookup"><span data-stu-id="0ae6c-160">Enum</span></span>
* <span data-ttu-id="0ae6c-161">Událost</span><span class="sxs-lookup"><span data-stu-id="0ae6c-161">Event</span></span>
* <span data-ttu-id="0ae6c-162">Pole</span><span class="sxs-lookup"><span data-stu-id="0ae6c-162">Field</span></span>
* <span data-ttu-id="0ae6c-163">GenericParameter</span><span class="sxs-lookup"><span data-stu-id="0ae6c-163">GenericParameter</span></span>
* <span data-ttu-id="0ae6c-164">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ae6c-164">Interface</span></span>
* <span data-ttu-id="0ae6c-165">Metoda</span><span class="sxs-lookup"><span data-stu-id="0ae6c-165">Method</span></span>
* <span data-ttu-id="0ae6c-166">Modul</span><span class="sxs-lookup"><span data-stu-id="0ae6c-166">Module</span></span>
* <span data-ttu-id="0ae6c-167">Parametr</span><span class="sxs-lookup"><span data-stu-id="0ae6c-167">Parameter</span></span>
* <span data-ttu-id="0ae6c-168">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="0ae6c-168">Property</span></span>
* <span data-ttu-id="0ae6c-169">ReturnValue</span><span class="sxs-lookup"><span data-stu-id="0ae6c-169">ReturnValue</span></span>
* <span data-ttu-id="0ae6c-170">Struktura</span><span class="sxs-lookup"><span data-stu-id="0ae6c-170">Struct</span></span>

<span data-ttu-id="0ae6c-171">Když vytvoříte třídy atributu, ve výchozím nastavení, C# vám umožní použít tento atribut na žádném z cíle možné atributů.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-171">When you create an attribute class, by default, C# will allow you to use that attribute on any of the possible attribute targets.</span></span> <span data-ttu-id="0ae6c-172">Pokud chcete omezit na určité cíle vaší atribut, můžete tak učinit pomocí `AttributeUsageAttribute` na vaší třídě atribut.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-172">If you want to restrict your attribute to certain targets, you can do so by using the `AttributeUsageAttribute` on your attribute class.</span></span> <span data-ttu-id="0ae6c-173">Který má pravým, atribut na atribut!</span><span class="sxs-lookup"><span data-stu-id="0ae6c-173">That's right, an attribute on an attribute!</span></span>

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

<span data-ttu-id="0ae6c-174">Pokud se pokusíte umístí výše uvedený atribut něco, co není třídu nebo struktury, zobrazí se chyba kompilátoru jako`Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`</span><span class="sxs-lookup"><span data-stu-id="0ae6c-174">If you attempt to put the above attribute on something that's not a class or a struct, you will get a compiler error like `Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`</span></span>

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a><span data-ttu-id="0ae6c-175">Jak používat atributy připojené k element kódu</span><span class="sxs-lookup"><span data-stu-id="0ae6c-175">How to use attributes attached to a code element</span></span>

<span data-ttu-id="0ae6c-176">Atributy fungují jako metadata.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-176">Attributes act as metadata.</span></span> <span data-ttu-id="0ae6c-177">Bez některé pasivního platnost se nebude nijak ve skutečnosti.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-177">Without some outward force, they won't actually do anything.</span></span>

<span data-ttu-id="0ae6c-178">K vyhledání a fungovat na atributy, [reflexe](../programming-guide/concepts/reflection.md) je obvykle potřeba.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-178">To find and act on attributes, [Reflection](../programming-guide/concepts/reflection.md) is generally needed.</span></span> <span data-ttu-id="0ae6c-179">I nebude pokrývat reflexe podrobný v tomto kurzu, ale Základní myšlenkou je, že reflexe umožňuje psaní kódu v C#, která hledá jiný kód.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-179">I won't cover Reflection in-depth in this tutorial, but the basic idea is that Reflection allows you to write code in C# that examines other code.</span></span>

<span data-ttu-id="0ae6c-180">Například můžete reflexe a získat informace o třídě:</span><span class="sxs-lookup"><span data-stu-id="0ae6c-180">For instance, you can use Reflection to get information about a class:</span></span> 

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

<span data-ttu-id="0ae6c-181">Ta vypíše se něco podobného jako:`The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="0ae6c-181">That will print out something like: `The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>

<span data-ttu-id="0ae6c-182">Jakmile máte `TypeInfo` objektu (nebo `MemberInfo`, `FieldInfo`atd), můžete použít `GetCustomAttributes` metoda.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-182">Once you have a `TypeInfo` object (or a `MemberInfo`, `FieldInfo`, etc), you can use the `GetCustomAttributes` method.</span></span> <span data-ttu-id="0ae6c-183">Tato možnost vrátí kolekci `Attribute` objekty.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-183">This will return a collection of `Attribute` objects.</span></span>
<span data-ttu-id="0ae6c-184">Můžete také použít `GetCustomAttribute` a zadejte typ atributu.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-184">You can also use `GetCustomAttribute` and specify an Attribute type.</span></span>

<span data-ttu-id="0ae6c-185">Tady je příklad použití `GetCustomAttributes` na `MemberInfo` instanci pro `MyClass` (které jsme viděli dříve došlo `[Obsolete]` atribut na něm).</span><span class="sxs-lookup"><span data-stu-id="0ae6c-185">Here's an example of using `GetCustomAttributes` on a `MemberInfo` instance for `MyClass` (which we saw earlier has an `[Obsolete]` attribute on it).</span></span>

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

<span data-ttu-id="0ae6c-186">Ta vypíše do konzoly: `Attribute on MyClass: ObsoleteAttribute`.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-186">That will print to console: `Attribute on MyClass: ObsoleteAttribute`.</span></span> <span data-ttu-id="0ae6c-187">Zkuste přidat další atributy, které mají `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-187">Try adding other attributes to `MyClass`.</span></span>

<span data-ttu-id="0ae6c-188">Je důležité si uvědomit, že tyto `Attribute` líné instance objektů.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-188">It's important to note that these `Attribute` objects are instantiated lazily.</span></span> <span data-ttu-id="0ae6c-189">To znamená, že nebude spuštěna dokud `GetCustomAttribute` nebo `GetCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-189">That is, they won't be instantiated until you use `GetCustomAttribute` or `GetCustomAttributes`.</span></span>
<span data-ttu-id="0ae6c-190">Pokaždé, když jsou také vytvořeny instance.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-190">They are also instantiated each time.</span></span> <span data-ttu-id="0ae6c-191">Volání metody `GetCustomAttributes` dvakrát v řádku vrátí dva různé instance `ObsoleteAttribute`.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-191">Calling `GetCustomAttributes` twice in a row will return two different instances of `ObsoleteAttribute`.</span></span>

## <a name="common-attributes-in-the-base-class-library-bcl"></a><span data-ttu-id="0ae6c-192">Běžné atributy v knihovně základní třídu (BCL)</span><span class="sxs-lookup"><span data-stu-id="0ae6c-192">Common attributes in the base class library (BCL)</span></span>

<span data-ttu-id="0ae6c-193">Atributy se používají tak, že mnoho nástroje a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-193">Attributes are used by many tools and frameworks.</span></span> <span data-ttu-id="0ae6c-194">NUnit používá atributů, například `[Test]` a `[TestFixture]` jsou používány nástroj test runner NUnit.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-194">NUnit uses attributes like `[Test]` and `[TestFixture]` that are used by the NUnit test runner.</span></span> <span data-ttu-id="0ae6c-195">ASP.NET MVC používá atributů, například `[Authorize]` a poskytuje rámec filtru akce k provedení mezi vyjímání obavy na akce MVC.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-195">ASP.NET MVC uses attributes like `[Authorize]` and provides an action filter framework to perform cross-cutting concerns on MVC actions.</span></span> <span data-ttu-id="0ae6c-196">[PostSharp](https://www.postsharp.net) používá syntaxi atribut umožňující aspekt orientované programování v C#.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-196">[PostSharp](https://www.postsharp.net) uses the attribute syntax to allow aspect-oriented programming in C#.</span></span>

<span data-ttu-id="0ae6c-197">Zde je několik významné atributy integrovaný do knihovny .NET Core základní třídy:</span><span class="sxs-lookup"><span data-stu-id="0ae6c-197">Here are a few notable attributes built into the .NET Core base class libraries:</span></span>

* <span data-ttu-id="0ae6c-198">`[Obsolete]`.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-198">`[Obsolete]`.</span></span> <span data-ttu-id="0ae6c-199">Tato byl použit v uvedených příkladech a je umístěn v `System` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-199">This one was used in the above examples, and it lives in the `System` namespace.</span></span> <span data-ttu-id="0ae6c-200">Je vhodné zajistit deklarativní dokumentaci o základní změny kódu.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-200">It is useful to provide declarative documentation about a changing code base.</span></span> <span data-ttu-id="0ae6c-201">Zprávu lze zadat v podobě řetězce a jiné logického parametru lze použít pro zvýšení z kompilátoru upozornění k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-201">A message can be provided in the form of a string, and another boolean parameter can be used to escalate from a compiler warning to a compiler error.</span></span>

* <span data-ttu-id="0ae6c-202">`[Conditional]`.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-202">`[Conditional]`.</span></span> <span data-ttu-id="0ae6c-203">Tento atribut je v `System.Diagnostics` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-203">This attribute is in the `System.Diagnostics` namespace.</span></span> <span data-ttu-id="0ae6c-204">Tento atribut lze použít metody (nebo třídy atributů).</span><span class="sxs-lookup"><span data-stu-id="0ae6c-204">This attribute can be applied to methods (or attribute classes).</span></span> <span data-ttu-id="0ae6c-205">Řetězec je nutné předat do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-205">You must pass a string to the constructor.</span></span>
<span data-ttu-id="0ae6c-206">Pokud se, řetězce odpovídá `#define` direktivy, pak všechny volání této metody (ale ne metoda sama) se odeberou kompilátorem C#.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-206">If that string matches a `#define` directive, then any calls to that method (but not the method itself) will be removed by the C# compiler.</span></span> <span data-ttu-id="0ae6c-207">Obvykle to se používá pro ladění (Diagnostika).</span><span class="sxs-lookup"><span data-stu-id="0ae6c-207">Typically this is used for debugging (diagnostics) purposes.</span></span>

* <span data-ttu-id="0ae6c-208">`[CallerMemberName]`.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-208">`[CallerMemberName]`.</span></span> <span data-ttu-id="0ae6c-209">Tento atribut lze použít na parametry a život v `System.Runtime.CompilerServices` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-209">This attribute can be used on parameters, and lives in the `System.Runtime.CompilerServices` namespace.</span></span> <span data-ttu-id="0ae6c-210">Toto je atribut, který slouží k vložení název metody, která volá jinou metodu.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-210">This is an attribute that is used to inject the name of the method that is calling another method.</span></span> <span data-ttu-id="0ae6c-211">Obvykle se používá jako způsob, jak eliminovat "kouzelná řetězce" při implementaci v různých architektury uživatelského rozhraní INotifyPropertyChanged.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-211">This is typically used as a way to eliminate 'magic strings' when implementing INotifyPropertyChanged in various UI frameworks.</span></span> <span data-ttu-id="0ae6c-212">Jako příklad:</span><span class="sxs-lookup"><span data-stu-id="0ae6c-212">As an example:</span></span>

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

<span data-ttu-id="0ae6c-213">Ve výše uvedeném kódu, nemusíte mít literál `"Name"` řetězec.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-213">In the above code, you don't have to have a literal `"Name"` string.</span></span> <span data-ttu-id="0ae6c-214">To pomáhá zabránit překlepem související chyby a také zajišťuje pro hladší refaktoring nebo přejmenování.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-214">This can help prevent typo-related bugs and also makes for smoother refactoring/renaming.</span></span>

## <a name="summary"></a><span data-ttu-id="0ae6c-215">Souhrn</span><span class="sxs-lookup"><span data-stu-id="0ae6c-215">Summary</span></span>

<span data-ttu-id="0ae6c-216">Atributy přepněte deklarativní power jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-216">Attributes bring declarative power to C#.</span></span> <span data-ttu-id="0ae6c-217">Ale nejsou formu kód jako metadata a není fungovat samostatně.</span><span class="sxs-lookup"><span data-stu-id="0ae6c-217">But they are a form of code as meta-data, and don't act by themselves.</span></span>
