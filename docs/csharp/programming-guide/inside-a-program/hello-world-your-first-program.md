---
title: Hello World – první program využívající Visual Studio ve Windows nebo v prostředí Mac – Průvodce programováním v C#
description: Visual Studio je profesionální vývojové prostředí s řadou funkcí pro vývoj pro .NET. Pomocí sady Visual Studio vytvořte verzi Hello World jazyka C#.
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: b78937b8ba1c7d4718bfb6252dac705945336d2a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301824"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="e51fb-104">Hello World – první program</span><span class="sxs-lookup"><span data-stu-id="e51fb-104">Hello World -- Your first program</span></span>

<span data-ttu-id="e51fb-105">V tomto článku použijete Visual Studio k vytvoření tradičního "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e51fb-105">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="e51fb-106">editoru.</span><span class="sxs-lookup"><span data-stu-id="e51fb-106">program.</span></span> <span data-ttu-id="e51fb-107">Visual Studio je profesionální integrované vývojové prostředí (IDE) s řadou funkcí navržených pro vývoj pro .NET.</span><span class="sxs-lookup"><span data-stu-id="e51fb-107">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="e51fb-108">K vytvoření tohoto programu použijete pouze několik funkcí v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e51fb-108">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="e51fb-109">Další informace o aplikaci Visual Studio naleznete v tématu [Začínáme v jazyce Visual C#](/visualstudio/ide/quickstart-csharp-console).</span><span class="sxs-lookup"><span data-stu-id="e51fb-109">To learn more about Visual Studio, see [Getting Started with Visual C#](/visualstudio/ide/quickstart-csharp-console).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="e51fb-110">Vytvoření nové aplikace</span><span class="sxs-lookup"><span data-stu-id="e51fb-110">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="e51fb-111">Windows</span><span class="sxs-lookup"><span data-stu-id="e51fb-111">Windows</span></span>](#tab/windows)

<span data-ttu-id="e51fb-112">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e51fb-112">Start Visual Studio.</span></span> <span data-ttu-id="e51fb-113">Ve Windows se zobrazí následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="e51fb-113">You'll see the following image on Windows:</span></span>

![Úvodní obrazovka sady Visual Studio ve Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="e51fb-115">Vyberte **vytvořit nový projekt** v pravém dolním rohu obrázku.</span><span class="sxs-lookup"><span data-stu-id="e51fb-115">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="e51fb-116">Visual Studio zobrazí dialogové okno **Nový projekt** :</span><span class="sxs-lookup"><span data-stu-id="e51fb-116">Visual Studio displays the **New Project** dialog:</span></span>

![Obrazovka nového projektu v aplikaci Visual Studio ve Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="e51fb-118">Pokud jste spustili aplikaci Visual Studio poprvé, seznam **naposledy použitých šablon projektů** je prázdný.</span><span class="sxs-lookup"><span data-stu-id="e51fb-118">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="e51fb-119">V dialogovém okně Nový projekt zvolte možnost Konzolová aplikace (.NET Core) a potom stiskněte tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="e51fb-119">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="e51fb-120">Zadejte název vašeho projektu, například HelloWorld, a pak stiskněte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="e51fb-120">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="e51fb-121">Visual Studio otevře projekt.</span><span class="sxs-lookup"><span data-stu-id="e51fb-121">Visual Studio opens your project.</span></span> <span data-ttu-id="e51fb-122">Už je základní "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="e51fb-122">It's already a basic "Hello World!"</span></span> <span data-ttu-id="e51fb-123">případě.</span><span class="sxs-lookup"><span data-stu-id="e51fb-123">example.</span></span> <span data-ttu-id="e51fb-124">Stisknutím klávesy `Ctrl`  +  `F5` spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="e51fb-124">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="e51fb-125">Visual Studio sestaví projekt a převede zdrojový kód na spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="e51fb-125">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="e51fb-126">Potom spustí příkazové okno, které spustí vaši novou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e51fb-126">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="e51fb-127">V okně byste měli vidět následující text:</span><span class="sxs-lookup"><span data-stu-id="e51fb-127">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="e51fb-128">Stisknutím klávesy zavřete okno.</span><span class="sxs-lookup"><span data-stu-id="e51fb-128">Press a key to close the window.</span></span>

# <a name="macos"></a>[<span data-ttu-id="e51fb-129">macOS</span><span class="sxs-lookup"><span data-stu-id="e51fb-129">macOS</span></span>](#tab/macos)

<span data-ttu-id="e51fb-130">Spusťte Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="e51fb-130">Start Visual Studio for Mac.</span></span> <span data-ttu-id="e51fb-131">Na Macu se zobrazí následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="e51fb-131">You'll see the following image on Mac:</span></span>

![Úvodní obrazovka sady Visual Studio na Macu](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="e51fb-133">Pokud Visual Studio pro Macte poprvé, seznam **posledních projektů** je prázdný.</span><span class="sxs-lookup"><span data-stu-id="e51fb-133">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="e51fb-134">V pravém horním rohu obrázku vyberte **Nový** .</span><span class="sxs-lookup"><span data-stu-id="e51fb-134">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="e51fb-135">Visual Studio pro Mac zobrazí dialog **Nový projekt** :</span><span class="sxs-lookup"><span data-stu-id="e51fb-135">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Obrazovka nového projektu v aplikaci Visual Studio na Macu](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="e51fb-137">V dialogovém okně Nový projekt vyberte .NET Core a Konzolová aplikace a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="e51fb-137">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="e51fb-138">Bude nutné vybrat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="e51fb-138">You'll need to select the target framework.</span></span> <span data-ttu-id="e51fb-139">Ve výchozím nastavení je to v pořádku, takže stiskněte tlačítko Další.</span><span class="sxs-lookup"><span data-stu-id="e51fb-139">The default is fine, so press next.</span></span> <span data-ttu-id="e51fb-140">Zadejte název vašeho projektu, například HelloWorld, a pak stiskněte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="e51fb-140">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="e51fb-141">Můžete použít výchozí umístění projektu.</span><span class="sxs-lookup"><span data-stu-id="e51fb-141">You can use the default project location.</span></span> <span data-ttu-id="e51fb-142">Nepřidávat tento projekt do správy zdrojových kódů.</span><span class="sxs-lookup"><span data-stu-id="e51fb-142">Don't add this project to source control.</span></span>

<span data-ttu-id="e51fb-143">Visual Studio pro Mac otevře projekt.</span><span class="sxs-lookup"><span data-stu-id="e51fb-143">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="e51fb-144">Už je základní "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="e51fb-144">It's already a basic "Hello World!"</span></span> <span data-ttu-id="e51fb-145">případě.</span><span class="sxs-lookup"><span data-stu-id="e51fb-145">example.</span></span> <span data-ttu-id="e51fb-146">Stisknutím klávesy `Ctrl`  +  `Fn`  +  `F5` spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="e51fb-146">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="e51fb-147">Visual Studio pro Mac sestavit projekt a převod zdrojového kódu na spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="e51fb-147">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="e51fb-148">Potom spustí příkazové okno, které spustí vaši novou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e51fb-148">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="e51fb-149">V okně byste měli vidět následující text:</span><span class="sxs-lookup"><span data-stu-id="e51fb-149">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="e51fb-150">Ukončete relaci stisknutím klávesy.</span><span class="sxs-lookup"><span data-stu-id="e51fb-150">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="e51fb-151">Prvky programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e51fb-151">Elements of a C# program</span></span>

<span data-ttu-id="e51fb-152">Pojďme se podívat na důležité části tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="e51fb-152">Let's examine the important parts of this program.</span></span> <span data-ttu-id="e51fb-153">První řádek obsahuje komentář.</span><span class="sxs-lookup"><span data-stu-id="e51fb-153">The first line contains a comment.</span></span> <span data-ttu-id="e51fb-154">Znaky `//` převedou zbytek čáry na komentář.</span><span class="sxs-lookup"><span data-stu-id="e51fb-154">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="e51fb-155">Můžete také odkomentovat blok textu uzavřením mezi `/*` `*/` znaky a.</span><span class="sxs-lookup"><span data-stu-id="e51fb-155">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="e51fb-156">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e51fb-156">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="e51fb-157">Konzolová aplikace v jazyce C# musí obsahovat `Main` metodu, ve které ovládací prvek začíná a končí.</span><span class="sxs-lookup"><span data-stu-id="e51fb-157">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="e51fb-158">`Main`Metoda je místo, kde vytvoříte objekty a spustíte jiné metody.</span><span class="sxs-lookup"><span data-stu-id="e51fb-158">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="e51fb-159">`Main`Metoda je [statická](../../language-reference/keywords/static.md) metoda, která se nachází uvnitř třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="e51fb-159">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="e51fb-160">V předchozím "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e51fb-160">In the previous "Hello World!"</span></span> <span data-ttu-id="e51fb-161">například se nachází ve třídě s názvem `Hello` .</span><span class="sxs-lookup"><span data-stu-id="e51fb-161">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="e51fb-162">Metodu lze deklarovat `Main` jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="e51fb-162">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="e51fb-163">Může vracet `void` .</span><span class="sxs-lookup"><span data-stu-id="e51fb-163">It can return `void`.</span></span> <span data-ttu-id="e51fb-164">To znamená, že váš program nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e51fb-164">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="e51fb-165">Může také vracet celé číslo.</span><span class="sxs-lookup"><span data-stu-id="e51fb-165">It can also return an integer.</span></span> <span data-ttu-id="e51fb-166">Celé číslo je **ukončovací kód** vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e51fb-166">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="e51fb-167">U obou návratových typů může vzít v úvahu argumenty.</span><span class="sxs-lookup"><span data-stu-id="e51fb-167">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="e51fb-168">-nebo-</span><span class="sxs-lookup"><span data-stu-id="e51fb-168">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="e51fb-169">Parametr `Main` metody, `args` , je `string` pole, které obsahuje argumenty příkazového řádku, které se používají k vyvolání programu.</span><span class="sxs-lookup"><span data-stu-id="e51fb-169">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="e51fb-170">Další informace o tom, jak používat argumenty příkazového řádku, naleznete v příkladech v části [Main () a argumenty příkazového řádku](../main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="e51fb-170">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="e51fb-171">Vstup a výstup</span><span class="sxs-lookup"><span data-stu-id="e51fb-171">Input and output</span></span>

<span data-ttu-id="e51fb-172">Programy v jazyce C# obecně používají vstupní a výstupní služby, které poskytuje běhová knihovna rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="e51fb-172">C# programs generally use the input/output services provided by the run-time library of .NET.</span></span> <span data-ttu-id="e51fb-173">Příkaz `System.Console.WriteLine("Hello World!");` používá <xref:System.Console.WriteLine%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="e51fb-173">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="e51fb-174">Toto je jedna z výstupních metod <xref:System.Console> třídy v knihovně run-time.</span><span class="sxs-lookup"><span data-stu-id="e51fb-174">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="e51fb-175">Zobrazuje parametr řetězce na standardním výstupním streamu následovaný novým řádkem.</span><span class="sxs-lookup"><span data-stu-id="e51fb-175">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="e51fb-176">Další <xref:System.Console> metody jsou k dispozici pro různé vstupní a výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="e51fb-176">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="e51fb-177">Pokud zadáte `using System;` direktivu na začátku programu, můžete přímo použít <xref:System> třídy a metody bez jejich úplného zařazení.</span><span class="sxs-lookup"><span data-stu-id="e51fb-177">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="e51fb-178">Například můžete volat `Console.WriteLine` místo `System.Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="e51fb-178">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="e51fb-179">Další informace o metodách vstupu a výstupu naleznete v tématu <xref:System.IO> .</span><span class="sxs-lookup"><span data-stu-id="e51fb-179">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="e51fb-180">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e51fb-180">See also</span></span>

- [<span data-ttu-id="e51fb-181">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e51fb-181">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e51fb-182">Ukázky a kurzy</span><span class="sxs-lookup"><span data-stu-id="e51fb-182">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="e51fb-183">Argumenty Main () a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="e51fb-183">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="e51fb-184">Začínáme s Visual C #</span><span class="sxs-lookup"><span data-stu-id="e51fb-184">Getting Started with Visual C#</span></span>](/visualstudio/ide/quickstart-csharp-console)
