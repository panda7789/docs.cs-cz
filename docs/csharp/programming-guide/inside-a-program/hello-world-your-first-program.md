---
title: Hello World – první program využívající Visual Studio ve Windows nebo v prostředí Mac – Průvodce programováním v C#
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 6d78ec83fec72b30f5cee398af1816d0cac35886
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241861"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="3b6a1-102">Hello World – první program</span><span class="sxs-lookup"><span data-stu-id="3b6a1-102">Hello World -- Your first program</span></span>

<span data-ttu-id="3b6a1-103">V tomto článku použijete Visual Studio k vytvoření tradičního "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3b6a1-103">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="3b6a1-104">editoru.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-104">program.</span></span> <span data-ttu-id="3b6a1-105">Visual Studio je profesionální integrované vývojové prostředí (IDE) s řadou funkcí navržených pro vývoj pro .NET.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-105">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="3b6a1-106">K vytvoření tohoto programu použijete pouze několik funkcí v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-106">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="3b6a1-107">Další informace o aplikaci Visual Studio naleznete v tématu [Začínáme v jazyce Visual C#](/visualstudio/ide/quickstart-csharp-console).</span><span class="sxs-lookup"><span data-stu-id="3b6a1-107">To learn more about Visual Studio, see [Getting Started with Visual C#](/visualstudio/ide/quickstart-csharp-console).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="3b6a1-108">Vytvoření nové aplikace</span><span class="sxs-lookup"><span data-stu-id="3b6a1-108">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="3b6a1-109">Windows</span><span class="sxs-lookup"><span data-stu-id="3b6a1-109">Windows</span></span>](#tab/windows)

<span data-ttu-id="3b6a1-110">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-110">Start Visual Studio.</span></span> <span data-ttu-id="3b6a1-111">Ve Windows se zobrazí následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="3b6a1-111">You'll see the following image on Windows:</span></span>

![Úvodní obrazovka sady Visual Studio ve Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="3b6a1-113">Vyberte **vytvořit nový projekt** v pravém dolním rohu obrázku.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-113">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="3b6a1-114">Visual Studio zobrazí dialogové okno **Nový projekt** :</span><span class="sxs-lookup"><span data-stu-id="3b6a1-114">Visual Studio displays the **New Project** dialog:</span></span>

![Obrazovka nového projektu v aplikaci Visual Studio ve Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="3b6a1-116">Pokud jste spustili aplikaci Visual Studio poprvé, seznam **naposledy použitých šablon projektů** je prázdný.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-116">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="3b6a1-117">V dialogovém okně Nový projekt zvolte možnost Konzolová aplikace (.NET Core) a potom stiskněte tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-117">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="3b6a1-118">Zadejte název vašeho projektu, například HelloWorld, a pak stiskněte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-118">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="3b6a1-119">Visual Studio otevře projekt.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-119">Visual Studio opens your project.</span></span> <span data-ttu-id="3b6a1-120">Už je základní "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="3b6a1-120">It's already a basic "Hello World!"</span></span> <span data-ttu-id="3b6a1-121">případě.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-121">example.</span></span> <span data-ttu-id="3b6a1-122">Stisknutím klávesy `Ctrl`  +  `F5` spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-122">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="3b6a1-123">Visual Studio sestaví projekt a převede zdrojový kód na spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-123">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="3b6a1-124">Potom spustí příkazové okno, které spustí vaši novou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-124">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="3b6a1-125">V okně byste měli vidět následující text:</span><span class="sxs-lookup"><span data-stu-id="3b6a1-125">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="3b6a1-126">Stisknutím klávesy zavřete okno.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-126">Press a key to close the window.</span></span>

# <a name="macos"></a>[<span data-ttu-id="3b6a1-127">macOS</span><span class="sxs-lookup"><span data-stu-id="3b6a1-127">macOS</span></span>](#tab/macos)

<span data-ttu-id="3b6a1-128">Spusťte Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-128">Start Visual Studio for Mac.</span></span> <span data-ttu-id="3b6a1-129">Na Macu se zobrazí následující obrázek:</span><span class="sxs-lookup"><span data-stu-id="3b6a1-129">You'll see the following image on Mac:</span></span>

![Úvodní obrazovka sady Visual Studio na Macu](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="3b6a1-131">Pokud Visual Studio pro Macte poprvé, seznam **posledních projektů** je prázdný.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-131">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="3b6a1-132">V pravém horním rohu obrázku vyberte **Nový** .</span><span class="sxs-lookup"><span data-stu-id="3b6a1-132">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="3b6a1-133">Visual Studio pro Mac zobrazí dialog **Nový projekt** :</span><span class="sxs-lookup"><span data-stu-id="3b6a1-133">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Obrazovka nového projektu v aplikaci Visual Studio na Macu](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="3b6a1-135">V dialogovém okně Nový projekt vyberte .NET Core a Konzolová aplikace a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-135">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="3b6a1-136">Bude nutné vybrat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-136">You'll need to select the target framework.</span></span> <span data-ttu-id="3b6a1-137">Ve výchozím nastavení je to v pořádku, takže stiskněte tlačítko Další.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-137">The default is fine, so press next.</span></span> <span data-ttu-id="3b6a1-138">Zadejte název vašeho projektu, například HelloWorld, a pak stiskněte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-138">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="3b6a1-139">Můžete použít výchozí umístění projektu.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-139">You can use the default project location.</span></span> <span data-ttu-id="3b6a1-140">Nepřidávat tento projekt do správy zdrojových kódů.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-140">Don't add this project to source control.</span></span>

<span data-ttu-id="3b6a1-141">Visual Studio pro Mac otevře projekt.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-141">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="3b6a1-142">Už je základní "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="3b6a1-142">It's already a basic "Hello World!"</span></span> <span data-ttu-id="3b6a1-143">případě.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-143">example.</span></span> <span data-ttu-id="3b6a1-144">Stisknutím klávesy `Ctrl`  +  `Fn`  +  `F5` spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-144">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="3b6a1-145">Visual Studio pro Mac sestavit projekt a převod zdrojového kódu na spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-145">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="3b6a1-146">Potom spustí příkazové okno, které spustí vaši novou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-146">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="3b6a1-147">V okně byste měli vidět následující text:</span><span class="sxs-lookup"><span data-stu-id="3b6a1-147">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="3b6a1-148">Ukončete relaci stisknutím klávesy.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-148">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="3b6a1-149">Prvky programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3b6a1-149">Elements of a C# program</span></span>

<span data-ttu-id="3b6a1-150">Pojďme se podívat na důležité části tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-150">Let's examine the important parts of this program.</span></span> <span data-ttu-id="3b6a1-151">První řádek obsahuje komentář.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-151">The first line contains a comment.</span></span> <span data-ttu-id="3b6a1-152">Znaky `//` převedou zbytek čáry na komentář.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-152">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="3b6a1-153">Můžete také odkomentovat blok textu uzavřením mezi `/*` `*/` znaky a.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-153">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="3b6a1-154">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-154">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="3b6a1-155">Konzolová aplikace v jazyce C# musí obsahovat `Main` metodu, ve které ovládací prvek začíná a končí.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-155">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="3b6a1-156">`Main`Metoda je místo, kde vytvoříte objekty a spustíte jiné metody.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-156">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="3b6a1-157">`Main`Metoda je [statická](../../language-reference/keywords/static.md) metoda, která se nachází uvnitř třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-157">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="3b6a1-158">V předchozím "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3b6a1-158">In the previous "Hello World!"</span></span> <span data-ttu-id="3b6a1-159">například se nachází ve třídě s názvem `Hello` .</span><span class="sxs-lookup"><span data-stu-id="3b6a1-159">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="3b6a1-160">Metodu lze deklarovat `Main` jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="3b6a1-160">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="3b6a1-161">Může vracet `void` .</span><span class="sxs-lookup"><span data-stu-id="3b6a1-161">It can return `void`.</span></span> <span data-ttu-id="3b6a1-162">To znamená, že váš program nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-162">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="3b6a1-163">Může také vracet celé číslo.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-163">It can also return an integer.</span></span> <span data-ttu-id="3b6a1-164">Celé číslo je **ukončovací kód** vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-164">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="3b6a1-165">U obou návratových typů může vzít v úvahu argumenty.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-165">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="3b6a1-166">-nebo-</span><span class="sxs-lookup"><span data-stu-id="3b6a1-166">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="3b6a1-167">Parametr `Main` metody, `args` , je `string` pole, které obsahuje argumenty příkazového řádku, které se používají k vyvolání programu.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-167">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="3b6a1-168">Další informace o tom, jak používat argumenty příkazového řádku, naleznete v příkladech v části [Main () a argumenty příkazového řádku](../main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="3b6a1-168">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="3b6a1-169">Vstup a výstup</span><span class="sxs-lookup"><span data-stu-id="3b6a1-169">Input and output</span></span>

<span data-ttu-id="3b6a1-170">Programy v jazyce C# obecně používají vstupní a výstupní služby, které poskytuje běhová knihovna rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-170">C# programs generally use the input/output services provided by the run-time library of .NET.</span></span> <span data-ttu-id="3b6a1-171">Příkaz `System.Console.WriteLine("Hello World!");` používá <xref:System.Console.WriteLine%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-171">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="3b6a1-172">Toto je jedna z výstupních metod <xref:System.Console> třídy v knihovně run-time.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-172">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="3b6a1-173">Zobrazuje parametr řetězce na standardním výstupním streamu následovaný novým řádkem.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-173">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="3b6a1-174">Další <xref:System.Console> metody jsou k dispozici pro různé vstupní a výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-174">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="3b6a1-175">Pokud zadáte `using System;` direktivu na začátku programu, můžete přímo použít <xref:System> třídy a metody bez jejich úplného zařazení.</span><span class="sxs-lookup"><span data-stu-id="3b6a1-175">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="3b6a1-176">Například můžete volat `Console.WriteLine` místo `System.Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="3b6a1-176">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="3b6a1-177">Další informace o metodách vstupu a výstupu naleznete v tématu <xref:System.IO> .</span><span class="sxs-lookup"><span data-stu-id="3b6a1-177">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b6a1-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b6a1-178">See also</span></span>

- [<span data-ttu-id="3b6a1-179">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="3b6a1-179">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3b6a1-180">Ukázky a kurzy</span><span class="sxs-lookup"><span data-stu-id="3b6a1-180">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="3b6a1-181">Argumenty Main () a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="3b6a1-181">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="3b6a1-182">Začínáme s Visual C #</span><span class="sxs-lookup"><span data-stu-id="3b6a1-182">Getting Started with Visual C#</span></span>](/visualstudio/ide/quickstart-csharp-console)
