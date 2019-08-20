---
title: Hello World – první programový průvodce C# programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 9a50de0bb583a1dfccfa609be1cca732868505ba
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589371"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="e810e-102">Hello World – první program (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="e810e-102">Hello World -- Your first program (C# Programming Guide)</span></span>

<span data-ttu-id="e810e-103">Následující postup vytvoří C# verzi tradičního "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e810e-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="e810e-104">editoru.</span><span class="sxs-lookup"><span data-stu-id="e810e-104">program.</span></span> <span data-ttu-id="e810e-105">Program zobrazí řetězec`Hello World!`</span><span class="sxs-lookup"><span data-stu-id="e810e-105">The program displays the string `Hello World!`</span></span>

<span data-ttu-id="e810e-106">Další příklady úvodních konceptů naleznete v tématu [Začínáme with C# Visual and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e810e-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="e810e-107">Vytvoření a spuštění konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="e810e-107">To create and run a console application</span></span>

1. <span data-ttu-id="e810e-108">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e810e-108">Start Visual Studio.</span></span>

2. <span data-ttu-id="e810e-109">V panelu nabídky zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="e810e-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="e810e-110">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e810e-110">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="e810e-111">Rozbalte položku **nainstalované**, rozbalte **šablony**, rozbalte položku **C#vizuál**a pak zvolte možnost konzolová **aplikace**.</span><span class="sxs-lookup"><span data-stu-id="e810e-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>

4. <span data-ttu-id="e810e-112">Do pole **název** zadejte název projektu a pak klikněte na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="e810e-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="e810e-113">Nový projekt se zobrazí v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="e810e-113">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="e810e-114">Pokud Program.cs není otevřen v **editoru kódu**, otevřete místní nabídku pro **program.cs** v **Průzkumník řešení**a pak zvolte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="e810e-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="e810e-115">Obsah Program.cs nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="e810e-115">Replace the contents of Program.cs with the following code.</span></span>

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. <span data-ttu-id="e810e-116">Kliknutím na klávesu F5 spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="e810e-116">Choose the F5 key to run the project.</span></span> <span data-ttu-id="e810e-117">Zobrazí se okno příkazového řádku, které obsahuje řádek.`Hello World!`</span><span class="sxs-lookup"><span data-stu-id="e810e-117">A Command Prompt window appears that contains the line `Hello World!`</span></span>

<span data-ttu-id="e810e-118">V dalším kroku se zkontrolují důležité části tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="e810e-118">Next, the important parts of this program are examined.</span></span>

## <a name="comments"></a><span data-ttu-id="e810e-119">Komentáře</span><span class="sxs-lookup"><span data-stu-id="e810e-119">Comments</span></span>

<span data-ttu-id="e810e-120">První řádek obsahuje komentář.</span><span class="sxs-lookup"><span data-stu-id="e810e-120">The first line contains a comment.</span></span> <span data-ttu-id="e810e-121">Znaky `//` převedou zbytek čáry na komentář.</span><span class="sxs-lookup"><span data-stu-id="e810e-121">The characters `//` convert the rest of the line to a comment.</span></span>

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="e810e-122">Můžete také odkomentovat blok textu uzavřením mezi `/*` znaky a. `*/`</span><span class="sxs-lookup"><span data-stu-id="e810e-122">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="e810e-123">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e810e-123">This is shown in the following example.</span></span>

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a><span data-ttu-id="e810e-124">main – metoda</span><span class="sxs-lookup"><span data-stu-id="e810e-124">Main method</span></span>

<span data-ttu-id="e810e-125">C# Konzolová aplikace musí obsahovat `Main` metodu, ve které ovládací prvek začíná a končí.</span><span class="sxs-lookup"><span data-stu-id="e810e-125">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="e810e-126">`Main` Metoda je místo, kde vytvoříte objekty a spustíte jiné metody.</span><span class="sxs-lookup"><span data-stu-id="e810e-126">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="e810e-127">Metoda je statická metoda, která se nachází uvnitř třídy nebo struktury. [](../../language-reference/keywords/static.md) `Main`</span><span class="sxs-lookup"><span data-stu-id="e810e-127">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="e810e-128">V předchozím "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e810e-128">In the previous "Hello World!"</span></span> <span data-ttu-id="e810e-129">například se nachází ve třídě s názvem `Hello`.</span><span class="sxs-lookup"><span data-stu-id="e810e-129">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="e810e-130">`Main` Metodu lze deklarovat jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="e810e-130">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="e810e-131">Může vracet `void`.</span><span class="sxs-lookup"><span data-stu-id="e810e-131">It can return `void`.</span></span>

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="e810e-132">Může také vracet celé číslo.</span><span class="sxs-lookup"><span data-stu-id="e810e-132">It can also return an integer.</span></span>

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="e810e-133">U obou návratových typů může vzít v úvahu argumenty.</span><span class="sxs-lookup"><span data-stu-id="e810e-133">With either of the return types, it can take arguments.</span></span>

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     <span data-ttu-id="e810e-134">-nebo-</span><span class="sxs-lookup"><span data-stu-id="e810e-134">-or-</span></span>

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="e810e-135">Parametr `Main` metody, `args`, je `string` pole, které obsahuje argumenty příkazového řádku, které se používají k vyvolání programu.</span><span class="sxs-lookup"><span data-stu-id="e810e-135">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="e810e-136">Na rozdíl od C++, pole nezahrnuje název spustitelného souboru (exe).</span><span class="sxs-lookup"><span data-stu-id="e810e-136">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>

<span data-ttu-id="e810e-137">Další informace o tom, jak používat argumenty příkazového řádku, naleznete v příkladech v části [Main () a argumenty příkazového řádku](../main-and-command-args/index.md) a [How to: Vytvořte a použijte sestavení pomocí příkazového řádku](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="e810e-137">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>

<span data-ttu-id="e810e-138">Volání <xref:System.Console.ReadKey%2A> na konci `Main` metody zabraňuje oknu v zavření okna konzoly před tím, než budete mít možnost číst výstup při spuštění programu v režimu ladění, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="e810e-138">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>

## <a name="input-and-output"></a><span data-ttu-id="e810e-139">Vstup a výstup</span><span class="sxs-lookup"><span data-stu-id="e810e-139">Input and output</span></span>

<span data-ttu-id="e810e-140">C#programy obecně používají vstupní a výstupní služby, které poskytuje knihovna run-time .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e810e-140">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="e810e-141">`System.Console.WriteLine("Hello World!");` Příkaz<xref:System.Console.WriteLine%2A> používá metodu.</span><span class="sxs-lookup"><span data-stu-id="e810e-141">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="e810e-142">Toto je jedna z výstupních metod <xref:System.Console> třídy v knihovně run-time.</span><span class="sxs-lookup"><span data-stu-id="e810e-142">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="e810e-143">Zobrazuje parametr řetězce na standardním výstupním streamu následovaný novým řádkem.</span><span class="sxs-lookup"><span data-stu-id="e810e-143">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="e810e-144">Další <xref:System.Console> metody jsou k dispozici pro různé vstupní a výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="e810e-144">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="e810e-145">Pokud zadáte <xref:System>direktivu na začátku programu, můžete přímo použít třídy a metody bez jejich úplného zařazení. `using System;`</span><span class="sxs-lookup"><span data-stu-id="e810e-145">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="e810e-146">Například můžete volat `Console.WriteLine` `System.Console.WriteLine`místo:</span><span class="sxs-lookup"><span data-stu-id="e810e-146">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="e810e-147">Další informace o metodách vstupu a výstupu naleznete v <xref:System.IO>tématu.</span><span class="sxs-lookup"><span data-stu-id="e810e-147">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="e810e-148">Kompilace a provádění příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="e810e-148">Command-line compilation and execution</span></span>

<span data-ttu-id="e810e-149">Můžete zkompilovat "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e810e-149">You can compile the "Hello World!"</span></span> <span data-ttu-id="e810e-150">program pomocí příkazového řádku namísto integrovaného vývojového prostředí (IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e810e-150">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>

### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="e810e-151">Kompilace a spuštění z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="e810e-151">To compile and run from a command prompt</span></span>

1. <span data-ttu-id="e810e-152">Vložte kód z předchozího postupu do libovolného textového editoru a pak soubor uložte jako textový soubor.</span><span class="sxs-lookup"><span data-stu-id="e810e-152">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="e810e-153">Pojmenujte soubor `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="e810e-153">Name the file `Hello.cs`.</span></span> <span data-ttu-id="e810e-154">C#soubory zdrojového kódu používají rozšíření `.cs`.</span><span class="sxs-lookup"><span data-stu-id="e810e-154">C# source code files use the extension `.cs`.</span></span>

2. <span data-ttu-id="e810e-155">K otevření okna příkazového řádku proveďte jeden z následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="e810e-155">Perform one of the following steps to open a command-prompt window:</span></span>

    - <span data-ttu-id="e810e-156">Ve Windows 10 v nabídce **Start** vyhledejte `Developer Command Prompt`a potom klepněte nebo zvolte **Developer Command Prompt pro vs 2017**.</span><span class="sxs-lookup"><span data-stu-id="e810e-156">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="e810e-157">Zobrazí se okno Developer Command Prompt.</span><span class="sxs-lookup"><span data-stu-id="e810e-157">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="e810e-158">V systému Windows 7 otevřete nabídku **Start** , rozbalte složku pro aktuální verzi sady Visual Studio, otevřete místní nabídku pro **Visual Studio Tools**a zvolte možnost **Developer Command Prompt pro vs 2017**.</span><span class="sxs-lookup"><span data-stu-id="e810e-158">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="e810e-159">Zobrazí se okno Developer Command Prompt.</span><span class="sxs-lookup"><span data-stu-id="e810e-159">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="e810e-160">Povolit buildy z příkazového řádku ze standardního okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e810e-160">Enable command-line builds from a standard Command Prompt window.</span></span>

         <span data-ttu-id="e810e-161">Viz [jak: Nastavení proměnných prostředí pro příkazový řádek](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e810e-161">See [How to: Set Environment Variables for the Visual Studio Command Line](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

3. <span data-ttu-id="e810e-162">V okně příkazového řádku přejděte do složky, která obsahuje váš `Hello.cs` soubor.</span><span class="sxs-lookup"><span data-stu-id="e810e-162">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>

4. <span data-ttu-id="e810e-163">Zadejte následující příkaz, který se `Hello.cs`má zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="e810e-163">Enter the following command to compile `Hello.cs`.</span></span>

     `csc Hello.cs`

     <span data-ttu-id="e810e-164">Pokud program neobsahuje žádné chyby kompilace, je vytvořen spustitelný soubor s názvem `Hello.exe` .</span><span class="sxs-lookup"><span data-stu-id="e810e-164">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>

5. <span data-ttu-id="e810e-165">V okně příkazového řádku zadejte následující příkaz pro spuštění programu:</span><span class="sxs-lookup"><span data-stu-id="e810e-165">In the command-prompt window, enter the following command to run the program:</span></span>

     `Hello`

 <span data-ttu-id="e810e-166">Další informace o C# kompilátoru a jeho možnostech naleznete v tématu [ C# možnosti kompilátoru](../../language-reference/compiler-options/index.md).</span><span class="sxs-lookup"><span data-stu-id="e810e-166">For more information about the C# compiler and its options, see [C# Compiler Options](../../language-reference/compiler-options/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e810e-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e810e-167">See also</span></span>

- [<span data-ttu-id="e810e-168">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e810e-168">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e810e-169">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e810e-169">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="e810e-170">Řetězce</span><span class="sxs-lookup"><span data-stu-id="e810e-170">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="e810e-171">Ukázky a kurzy</span><span class="sxs-lookup"><span data-stu-id="e810e-171">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="e810e-172">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="e810e-172">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="e810e-173">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="e810e-173">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="e810e-174">Začínáme s jazykem Visual C# a Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e810e-174">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
