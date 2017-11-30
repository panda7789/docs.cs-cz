---
title: "Řetězec interpolace - C#"
description: "Zjistěte, jak funguje interpolace řetězce v jazyce C# 6"
keywords: "Rozhraní .NET, .NET core, C#, řetězec"
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8806f6b-3ac7-4ee6-9b3e-c524d5301ae9
ms.openlocfilehash: ac19d4208da4f8ee6dd3e071ab70dbc41a0cd065
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="4d0a8-104">Interpolace řetězce v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4d0a8-104">String Interpolation in C#</span></span> #

<span data-ttu-id="4d0a8-105">Řetězec interpolace je způsob zástupné symboly v řetězci se nahrazují hodnota proměnné řetězce.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-105">String Interpolation is the way that placeholders in a string are replaced by the value of a string variable.</span></span> <span data-ttu-id="4d0a8-106">Před C# 6, je tím způsobem, jak to udělat pomocí `System.String.Format`.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-106">Before C# 6, the way to do this is with `System.String.Format`.</span></span> <span data-ttu-id="4d0a8-107">Tento postup funguje v pořádku, ale protože ji používá číslem zástupné symboly, může být těžší ke čtení a podrobnější.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-107">This works okay, but since it uses numbered placeholders, it can be harder to read and more verbose.</span></span>

<span data-ttu-id="4d0a8-108">Jinými programovací jazyky předtím řetězec interpolace integrované do jazyka nějakou dobu.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-108">Other programming languages have had string interpolation built into the language for a while.</span></span> <span data-ttu-id="4d0a8-109">Například v jazyce PHP:</span><span class="sxs-lookup"><span data-stu-id="4d0a8-109">For instance, in PHP:</span></span>

```php
$name = "Jonas";
echo "My name is $name.";
// This will output "My name is Jonas."
```

<span data-ttu-id="4d0a8-110">V jazyce C# 6 máme nakonec tento styl interpolace řetězec.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-110">In C# 6, we finally have that style of string interpolation.</span></span> <span data-ttu-id="4d0a8-111">Můžete použít `$` před řetězec k označení, že ho měli nahraďte proměnné nebo výrazy pro jejich hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-111">You can use a `$` before a string to indicate that it should substitute variables/expressions for their values.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4d0a8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d0a8-112">Prerequisites</span></span>
<span data-ttu-id="4d0a8-113">Budete muset nastavit svůj počítač ke spuštění .NET core.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-113">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="4d0a8-114">Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-114">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="4d0a8-115">Tuto aplikaci můžete spustit v systému Windows, Ubuntu Linux, systému macOS nebo v kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-115">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="4d0a8-116">Budete muset nainstalovat editor vaše oblíbené kódu.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-116">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="4d0a8-117">Popisy níže použijte [Visual Studio Code](https://code.visualstudio.com/) který je typu open source pro různé platformy editor.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-117">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="4d0a8-118">Můžete však použít, ať nástroje umíte pracovat s.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-118">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="4d0a8-119">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="4d0a8-119">Create the Application</span></span>

<span data-ttu-id="4d0a8-120">Teď, když jste nainstalovali všechny nástroje, vytvořte novou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-120">Now that you've installed all the tools, create a new .NET Core application.</span></span> <span data-ttu-id="4d0a8-121">Pokud chcete použít Generátor příkazového řádku, vytvořit adresář pro svůj projekt `interpolated`a ve své oblíbené prostředí spustíte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="4d0a8-121">To use the command line generator, create a directory for your project, such as `interpolated`, and execute the following command in your favorite shell:</span></span>

```
dotnet new console
```

<span data-ttu-id="4d0a8-122">Tento příkaz vytvoří projektu jen nejzákladnější .NET core s soubor projektu *interpolated.csproj*a soubor zdrojového kódu *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-122">This command will create a barebones .NET core project with a project file, *interpolated.csproj*, and a source code file, *Program.cs*.</span></span> <span data-ttu-id="4d0a8-123">Budete muset provést `dotnet restore` Obnovit závislosti potřebné ke kompilaci tento projekt.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-123">You will need to execute `dotnet restore` to restore the dependencies needed to compile this project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="4d0a8-124">Spuštění programu, použijte `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-124">To execute the program, use `dotnet run`.</span></span> <span data-ttu-id="4d0a8-125">Měli byste vidět "Hello, World" výstup do konzoly.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-125">You should see "Hello, World" output to the console.</span></span>



## <a name="intro-to-string-interpolation"></a><span data-ttu-id="4d0a8-126">Úvod do řetězce interpolace</span><span class="sxs-lookup"><span data-stu-id="4d0a8-126">Intro to String Interpolation</span></span>

<span data-ttu-id="4d0a8-127">S `System.String.Format`, zadejte "zástupné symboly" řetězec, který se nahrazují následující řetězec parametry.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-127">With `System.String.Format`, you specify "placeholders" in a string that are replaced by the parameters following the string.</span></span> <span data-ttu-id="4d0a8-128">Například:</span><span class="sxs-lookup"><span data-stu-id="4d0a8-128">For instance:</span></span>

[!code-csharp[String.Format example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#StringFormatExample)]  

<span data-ttu-id="4d0a8-129">Který výstup "Moje název je Matt hájů".</span><span class="sxs-lookup"><span data-stu-id="4d0a8-129">That will output "My name is Matt Groves".</span></span>

<span data-ttu-id="4d0a8-130">V jazyce C# 6, místo použití `String.Format`, definujete interpolované řetězce je s předponou `$` symbolů a potom pomocí proměnné přímo v řetězci.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-130">In C# 6, instead of using `String.Format`, you define an interpolated string by prepending it with the `$` symbol, and then using the variables directly in the string.</span></span> <span data-ttu-id="4d0a8-131">Například:</span><span class="sxs-lookup"><span data-stu-id="4d0a8-131">For instance:</span></span>

[!code-csharp[Interpolation example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExample)]  

<span data-ttu-id="4d0a8-132">Nemusíte používat jenom proměnné.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-132">You don't have to use just variables.</span></span> <span data-ttu-id="4d0a8-133">Můžete použít libovolný výraz v hranatých závorkách.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-133">You can use any expression within the brackets.</span></span> <span data-ttu-id="4d0a8-134">Například:</span><span class="sxs-lookup"><span data-stu-id="4d0a8-134">For instance:</span></span>

[!code-csharp[Interpolation expression example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExpressionExample)]  

<span data-ttu-id="4d0a8-135">Které by výstup:</span><span class="sxs-lookup"><span data-stu-id="4d0a8-135">Which would output:</span></span>

```
This is line number 1
This is line number 2
This is line number 3
This is line number 4
This is line number 5
```

## <a name="how-string-interpolation-works"></a><span data-ttu-id="4d0a8-136">Jak funguje řetězec interpolace</span><span class="sxs-lookup"><span data-stu-id="4d0a8-136">How string interpolation works</span></span>

<span data-ttu-id="4d0a8-137">Na pozadí je tato syntaxe interpolace řetězec přeložit na String.Format kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-137">Behind the scenes, this string interpolation syntax is translated into String.Format by the compiler.</span></span> <span data-ttu-id="4d0a8-138">Ano, můžete provést [stejného typu, vy provedete krok před s String.Format](https://msdn.microsoft.com/en-us/library/dwhawy9k(v=vs.110).aspx).</span><span class="sxs-lookup"><span data-stu-id="4d0a8-138">So, you can do the [same type of stuff you've done before with String.Format](https://msdn.microsoft.com/en-us/library/dwhawy9k(v=vs.110).aspx).</span></span>

<span data-ttu-id="4d0a8-139">Můžete například přidat odsazení a formátování čísel:</span><span class="sxs-lookup"><span data-stu-id="4d0a8-139">For instance, you can add padding and numeric formatting:</span></span>

[!code-csharp[Interpolation formatting example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationFormattingExample)]  

<span data-ttu-id="4d0a8-140">Výše by výstup podobný:</span><span class="sxs-lookup"><span data-stu-id="4d0a8-140">The above would output something like:</span></span>

```
998        5,177.67
999        6,719.30
1000       9,910.61
1001       529.34
1002       1,349.86
1003       2,660.82
1004       6,227.77
```

<span data-ttu-id="4d0a8-141">Pokud název proměnné není nalezen, bude vygenerována chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-141">If a variable name is not found, then a compile time error will be generated.</span></span>

<span data-ttu-id="4d0a8-142">Například:</span><span class="sxs-lookup"><span data-stu-id="4d0a8-142">For instance:</span></span>

```csharp
var animal = "fox";
var localizeMe = $"The {adj} brown {animal} jumped over the lazy {otheranimal}";
var adj = "quick";
Console.WriteLine(localizeMe);
```

<span data-ttu-id="4d0a8-143">Pokud je kompilovat, bude docházet k chybám:</span><span class="sxs-lookup"><span data-stu-id="4d0a8-143">If you compile this, you'll get errors:</span></span>
 
* <span data-ttu-id="4d0a8-144">`Cannot use local variable 'adj' before it is declared`- `adj` proměnná nebyl deklarován dokud *po* interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-144">`Cannot use local variable 'adj' before it is declared` - the `adj` variable wasn't declared until *after* the interpolated string.</span></span>
* <span data-ttu-id="4d0a8-145">`The name 'otheranimal' does not exist in the current context`-názvem proměnné `otheranimal` nikdy i byla deklarována</span><span class="sxs-lookup"><span data-stu-id="4d0a8-145">`The name 'otheranimal' does not exist in the current context` - a variable called `otheranimal` was never even declared</span></span>

## <a name="localization-and-internationalization"></a><span data-ttu-id="4d0a8-146">Lokalizace a internacionalizace</span><span class="sxs-lookup"><span data-stu-id="4d0a8-146">Localization and Internationalization</span></span>

<span data-ttu-id="4d0a8-147">Interpolované řetězce podporuje `IFormattable` a `FormattableString`, což může být užitečné pro internacionalizace.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-147">An interpolated string supports `IFormattable` and `FormattableString`, which can be useful for internationalization.</span></span>

<span data-ttu-id="4d0a8-148">Interpolované řetězce ve výchozím nastavení používá aktuální jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-148">By default, an interpolated string uses the current culture.</span></span> <span data-ttu-id="4d0a8-149">Pokud chcete použít jinou jazykovou verzi, může ho jako přetypování`IFormattable`</span><span class="sxs-lookup"><span data-stu-id="4d0a8-149">To use a different culture, you could cast it as `IFormattable`</span></span>

<span data-ttu-id="4d0a8-150">Například:</span><span class="sxs-lookup"><span data-stu-id="4d0a8-150">For instance:</span></span>

[!code-csharp[Interpolation internationalization example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationInternationalizationExample)]  

## <a name="conclusion"></a><span data-ttu-id="4d0a8-151">Závěr</span><span class="sxs-lookup"><span data-stu-id="4d0a8-151">Conclusion</span></span> 

<span data-ttu-id="4d0a8-152">V tomto kurzu jste zjistili, jak používat funkce interpolace řetězec jazyka C# 6.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-152">In this tutorial, you learned how to use string interpolation features of C# 6.</span></span> <span data-ttu-id="4d0a8-153">Je v podstatě přesnější způsob jednoduché psaní `String.Format` příkazy se některých aspektů pro pokročilejší použití.</span><span class="sxs-lookup"><span data-stu-id="4d0a8-153">It's basically a more concise way of writing simple `String.Format` statements, with some caveats for more advanced uses of it.</span></span>
