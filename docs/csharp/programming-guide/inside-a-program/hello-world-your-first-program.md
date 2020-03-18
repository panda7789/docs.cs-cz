---
title: Hello World – Váš první program používající Visual Studio ve Windows nebo Macu – Průvodce programováním v Jazyce C#
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 910fa4af1b4e45ce627b589a06910dc168490047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712140"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="c5749-102">Hello World - Váš první program</span><span class="sxs-lookup"><span data-stu-id="c5749-102">Hello World -- Your first program</span></span>

<span data-ttu-id="c5749-103">V tomto článku použijete Visual Studio k vytvoření tradičního "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c5749-103">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="c5749-104">Program.</span><span class="sxs-lookup"><span data-stu-id="c5749-104">program.</span></span> <span data-ttu-id="c5749-105">Visual Studio je profesionální integrované vývojové prostředí (IDE) s mnoha funkcemi určenými pro vývoj rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="c5749-105">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="c5749-106">K vytvoření tohoto programu použijete pouze několik funkcí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5749-106">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="c5749-107">Další informace o sadě Visual Studio najdete [v tématu Začínáme s visual c#](/visualstudio/ide/quickstart-csharp-console).</span><span class="sxs-lookup"><span data-stu-id="c5749-107">To learn more about Visual Studio, see [Getting Started with Visual C#](/visualstudio/ide/quickstart-csharp-console).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="c5749-108">Vytvoření nové aplikace</span><span class="sxs-lookup"><span data-stu-id="c5749-108">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="c5749-109">Windows</span><span class="sxs-lookup"><span data-stu-id="c5749-109">Windows</span></span>](#tab/windows)

<span data-ttu-id="c5749-110">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5749-110">Start Visual Studio.</span></span> <span data-ttu-id="c5749-111">Ve Windows se zobrazí následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="c5749-111">You'll see the following image on Windows:</span></span>

![Úvodní obrazovka Visual Studia ve Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="c5749-113">Vyberte **Vytvořit nový projekt** v pravém dolním rohu obrazu.</span><span class="sxs-lookup"><span data-stu-id="c5749-113">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="c5749-114">Visual Studio zobrazí dialogové okno **Nový projekt:**</span><span class="sxs-lookup"><span data-stu-id="c5749-114">Visual Studio displays the **New Project** dialog:</span></span>

![Obrazovka nového projektu Visual Studia ve Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="c5749-116">Pokud je to poprvé, co jste spustili Visual Studio, seznam **šablony posledních projektů** je prázdný.</span><span class="sxs-lookup"><span data-stu-id="c5749-116">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="c5749-117">V novém dialogovém okně projektu zvolte "Console App (.NET Core)" a stiskněte **tlačítko Další**.</span><span class="sxs-lookup"><span data-stu-id="c5749-117">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="c5749-118">Pojmenujte projekt, například "HelloWorld", a stiskněte **klávesu Create**.</span><span class="sxs-lookup"><span data-stu-id="c5749-118">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="c5749-119">Visual Studio otevře projekt.</span><span class="sxs-lookup"><span data-stu-id="c5749-119">Visual Studio opens your project.</span></span> <span data-ttu-id="c5749-120">Je to již základní "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c5749-120">It's already a basic "Hello World!"</span></span> <span data-ttu-id="c5749-121">Příklad.</span><span class="sxs-lookup"><span data-stu-id="c5749-121">example.</span></span> <span data-ttu-id="c5749-122">`Ctrl`  +  Stisknutím `F5` spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="c5749-122">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="c5749-123">Visual Studio vytvoří váš projekt a převede zdrojový kód na spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="c5749-123">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="c5749-124">Potom spustí příkazové okno, ve které je spuštěna nová aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5749-124">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="c5749-125">V okně by se měl zobrazit následující text:</span><span class="sxs-lookup"><span data-stu-id="c5749-125">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="c5749-126">Zavřete okno stisknutím klávesy.</span><span class="sxs-lookup"><span data-stu-id="c5749-126">Press a key to close the window.</span></span>

# <a name="macos"></a>[<span data-ttu-id="c5749-127">Macos</span><span class="sxs-lookup"><span data-stu-id="c5749-127">macOS</span></span>](#tab/macos)

<span data-ttu-id="c5749-128">Spusťte Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="c5749-128">Start Visual Studio for Mac.</span></span> <span data-ttu-id="c5749-129">Na Macu se zobrazí následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="c5749-129">You'll see the following image on Mac:</span></span>

![Úvodní obrazovka Visual Studia na Macu](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="c5749-131">Pokud je to poprvé, co jste spustili Visual Studio pro Mac, seznam **Nedávné projekty** je prázdný.</span><span class="sxs-lookup"><span data-stu-id="c5749-131">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="c5749-132">V pravém horním rohu obrazu vyberte **Nový.**</span><span class="sxs-lookup"><span data-stu-id="c5749-132">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="c5749-133">Visual Studio pro Mac zobrazí dialogové okno **Nový projekt:**</span><span class="sxs-lookup"><span data-stu-id="c5749-133">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Visual Studio nový projekt obrazovky na Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="c5749-135">V novém dialogovém okně projektu zvolte ".NET Core" a "Console App" a stiskněte **tlačítko Další**.</span><span class="sxs-lookup"><span data-stu-id="c5749-135">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="c5749-136">Budete muset vybrat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="c5749-136">You'll need to select the target framework.</span></span> <span data-ttu-id="c5749-137">Výchozí nastavení je v pořádku, takže stiskněte další.</span><span class="sxs-lookup"><span data-stu-id="c5749-137">The default is fine, so press next.</span></span> <span data-ttu-id="c5749-138">Pojmenujte projekt, například "HelloWorld", a stiskněte **klávesu Create**.</span><span class="sxs-lookup"><span data-stu-id="c5749-138">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="c5749-139">Můžete použít výchozí umístění projektu.</span><span class="sxs-lookup"><span data-stu-id="c5749-139">You can use the default project location.</span></span> <span data-ttu-id="c5749-140">Nepřidávejte tento projekt do správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="c5749-140">Don't add this project to source control.</span></span>

<span data-ttu-id="c5749-141">Visual Studio pro Mac otevře váš projekt.</span><span class="sxs-lookup"><span data-stu-id="c5749-141">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="c5749-142">Je to již základní "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c5749-142">It's already a basic "Hello World!"</span></span> <span data-ttu-id="c5749-143">Příklad.</span><span class="sxs-lookup"><span data-stu-id="c5749-143">example.</span></span> <span data-ttu-id="c5749-144">`Ctrl`  +  Stisknutím `Fn`  +  spusťte `F5` projekt.</span><span class="sxs-lookup"><span data-stu-id="c5749-144">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="c5749-145">Visual Studio pro Mac vytvoří váš projekt a převede zdrojový kód na spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="c5749-145">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="c5749-146">Potom spustí příkazové okno, ve které je spuštěna nová aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5749-146">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="c5749-147">V okně by se měl zobrazit následující text:</span><span class="sxs-lookup"><span data-stu-id="c5749-147">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="c5749-148">Stisknutím klávesy ukončíte relaci.</span><span class="sxs-lookup"><span data-stu-id="c5749-148">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="c5749-149">Prvky programu Jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c5749-149">Elements of a C# program</span></span>

<span data-ttu-id="c5749-150">Podívejme se na důležité části tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="c5749-150">Let's examine the important parts of this program.</span></span> <span data-ttu-id="c5749-151">První řádek obsahuje komentář.</span><span class="sxs-lookup"><span data-stu-id="c5749-151">The first line contains a comment.</span></span> <span data-ttu-id="c5749-152">Znaky `//` převedou zbytek řádku na komentář.</span><span class="sxs-lookup"><span data-stu-id="c5749-152">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="c5749-153">Můžete také zakomentovat blok textu tím, `/*` že `*/` jej uzavřete mezi znaky a.</span><span class="sxs-lookup"><span data-stu-id="c5749-153">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="c5749-154">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c5749-154">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="c5749-155">Aplikace konzoly Jazyka C# musí obsahovat metodu, `Main` ve které ovládací prvek začíná a končí.</span><span class="sxs-lookup"><span data-stu-id="c5749-155">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="c5749-156">Metoda `Main` je místo, kde můžete vytvořit objekty a spustit jiné metody.</span><span class="sxs-lookup"><span data-stu-id="c5749-156">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="c5749-157">Metoda `Main` je [statická](../../language-reference/keywords/static.md) metoda, která se nachází uvnitř třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="c5749-157">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="c5749-158">V předchozím "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c5749-158">In the previous "Hello World!"</span></span> <span data-ttu-id="c5749-159">například je umístěn ve `Hello`třídě s názvem .</span><span class="sxs-lookup"><span data-stu-id="c5749-159">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="c5749-160">Metodu můžete `Main` deklarovat jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="c5749-160">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="c5749-161">Může se `void`vrátit .</span><span class="sxs-lookup"><span data-stu-id="c5749-161">It can return `void`.</span></span> <span data-ttu-id="c5749-162">To znamená, že váš program nevrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c5749-162">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="c5749-163">Může také vrátit celé číslo.</span><span class="sxs-lookup"><span data-stu-id="c5749-163">It can also return an integer.</span></span> <span data-ttu-id="c5749-164">Celé číslo je **ukončovací kód** pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c5749-164">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="c5749-165">S jedním z návratových typů může trvat argumenty.</span><span class="sxs-lookup"><span data-stu-id="c5749-165">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="c5749-166">-nebo-</span><span class="sxs-lookup"><span data-stu-id="c5749-166">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="c5749-167">Parametr `Main` metody , `args`je `string` pole, které obsahuje argumenty příkazového řádku použité k vyvolání programu.</span><span class="sxs-lookup"><span data-stu-id="c5749-167">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="c5749-168">Další informace o použití argumentů příkazového řádku naleznete v příkladech v [části Main() a Argumenty příkazového řádku](../main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="c5749-168">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="c5749-169">Vstup a výstup</span><span class="sxs-lookup"><span data-stu-id="c5749-169">Input and output</span></span>

<span data-ttu-id="c5749-170">Programy jazyka C# obecně používají vstupní a výstupní služby poskytované knihovnou run-time rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5749-170">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="c5749-171">Příkaz `System.Console.WriteLine("Hello World!");` používá <xref:System.Console.WriteLine%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="c5749-171">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="c5749-172">Toto je jedna z <xref:System.Console> výstupních metod třídy v knihovně za běhu.</span><span class="sxs-lookup"><span data-stu-id="c5749-172">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="c5749-173">Zobrazí svůj parametr řetězce ve standardním výstupním datovém proudu následovaném novým řádkem.</span><span class="sxs-lookup"><span data-stu-id="c5749-173">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="c5749-174">Jiné <xref:System.Console> metody jsou k dispozici pro různé vstupní a výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="c5749-174">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="c5749-175">Pokud zahrnete `using System;` směrnice na začátku programu, <xref:System> můžete přímo použít třídy a metody bez jejich plné kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="c5749-175">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="c5749-176">Můžete například volat `Console.WriteLine` místo `System.Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="c5749-176">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="c5749-177">Další informace o metodách vstupu <xref:System.IO>a výstupu naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="c5749-177">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5749-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5749-178">See also</span></span>

- [<span data-ttu-id="c5749-179">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c5749-179">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c5749-180">Ukázky a výukové programy</span><span class="sxs-lookup"><span data-stu-id="c5749-180">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="c5749-181">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="c5749-181">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="c5749-182">Začínáme s visual c #</span><span class="sxs-lookup"><span data-stu-id="c5749-182">Getting Started with Visual C#</span></span>](/visualstudio/ide/quickstart-csharp-console)
