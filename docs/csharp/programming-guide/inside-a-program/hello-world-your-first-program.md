---
title: Hello World!--Váš první program - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 7ff65867f9f81118cad30852c439f8b3491bf1aa
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969723"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="3da7f-102">Hello World!--Váš první program (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="3da7f-102">Hello World -- Your first program (C# Programming Guide)</span></span>

<span data-ttu-id="3da7f-103">Následující postup vytvoří verzi C# tradiční "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3da7f-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="3da7f-104">program.</span><span class="sxs-lookup"><span data-stu-id="3da7f-104">program.</span></span> <span data-ttu-id="3da7f-105">Program zobrazí řetězec `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="3da7f-105">The program displays the string `Hello World!`</span></span>

<span data-ttu-id="3da7f-106">Další příklady úvodních konceptů viz [Začínáme s Visual C# a Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3da7f-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="3da7f-107">Vytvoření a spuštění konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="3da7f-107">To create and run a console application</span></span>

1. <span data-ttu-id="3da7f-108">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3da7f-108">Start Visual Studio.</span></span>

2. <span data-ttu-id="3da7f-109">V panelu nabídky zvolte **souboru**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="3da7f-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="3da7f-110">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="3da7f-110">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="3da7f-111">Rozbalte **nainstalováno**, rozbalte **šablony**, rozbalte **Visual C#** a klikněte na tlačítko **konzolovou aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="3da7f-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>

4. <span data-ttu-id="3da7f-112">V **název** pole, zadejte název pro váš projekt a klikněte na tlačítko **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="3da7f-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="3da7f-113">Nový projekt se zobrazí v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="3da7f-113">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="3da7f-114">Pokud Program.cs není otevřen v **Editor kódu**, otevřete místní nabídku pro **Program.cs** v **Průzkumníka řešení**a klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="3da7f-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="3da7f-115">Nahraďte obsah Program.cs následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="3da7f-115">Replace the contents of Program.cs with the following code.</span></span>

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. <span data-ttu-id="3da7f-116">Stiskněte klávesu F5 ke spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="3da7f-116">Choose the F5 key to run the project.</span></span> <span data-ttu-id="3da7f-117">Zobrazí se okno příkazového řádku, která obsahuje řádek `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="3da7f-117">A Command Prompt window appears that contains the line `Hello World!`</span></span>

<span data-ttu-id="3da7f-118">Dále jsou zkoumány důležité části tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="3da7f-118">Next, the important parts of this program are examined.</span></span>

## <a name="comments"></a><span data-ttu-id="3da7f-119">Komentáře</span><span class="sxs-lookup"><span data-stu-id="3da7f-119">Comments</span></span>

<span data-ttu-id="3da7f-120">První řádek obsahuje komentář.</span><span class="sxs-lookup"><span data-stu-id="3da7f-120">The first line contains a comment.</span></span> <span data-ttu-id="3da7f-121">Znaky `//` převést zbytek řádku na poznámku.</span><span class="sxs-lookup"><span data-stu-id="3da7f-121">The characters `//` convert the rest of the line to a comment.</span></span>

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="3da7f-122">Můžete také můžete Zakomentovat blok textu jeho uzavřením mezi `/*` a `*/` znaků.</span><span class="sxs-lookup"><span data-stu-id="3da7f-122">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="3da7f-123">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3da7f-123">This is shown in the following example.</span></span>

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a><span data-ttu-id="3da7f-124">main – metoda</span><span class="sxs-lookup"><span data-stu-id="3da7f-124">Main method</span></span>

<span data-ttu-id="3da7f-125">Musí obsahovat konzolovou aplikaci C# `Main` metody, ve kterém ovládací prvek začíná a končí.</span><span class="sxs-lookup"><span data-stu-id="3da7f-125">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="3da7f-126">`Main` Je metoda, ve kterém se vytváří objekty a spouštějí jiné metody.</span><span class="sxs-lookup"><span data-stu-id="3da7f-126">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="3da7f-127">`Main` Je metoda [statické](../../../csharp/language-reference/keywords/static.md) metodu, která se nachází uvnitř třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3da7f-127">The `Main` method is a [static](../../../csharp/language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="3da7f-128">V předchozí "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3da7f-128">In the previous "Hello World!"</span></span> <span data-ttu-id="3da7f-129">například se nachází ve třídě s názvem `Hello`.</span><span class="sxs-lookup"><span data-stu-id="3da7f-129">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="3da7f-130">Lze deklarovat `Main` metody v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="3da7f-130">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="3da7f-131">Může vrátit `void`.</span><span class="sxs-lookup"><span data-stu-id="3da7f-131">It can return `void`.</span></span>

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="3da7f-132">Také může vrátit celé číslo.</span><span class="sxs-lookup"><span data-stu-id="3da7f-132">It can also return an integer.</span></span>

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="3da7f-133">Pomocí některé z návratových typů můžete převzít argumenty.</span><span class="sxs-lookup"><span data-stu-id="3da7f-133">With either of the return types, it can take arguments.</span></span>

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     <span data-ttu-id="3da7f-134">-nebo-</span><span class="sxs-lookup"><span data-stu-id="3da7f-134">-or-</span></span>

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="3da7f-135">Parametr `Main` metody `args`, je `string` pole obsahující argumenty příkazového řádku používané k vyvolání programu.</span><span class="sxs-lookup"><span data-stu-id="3da7f-135">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="3da7f-136">Na rozdíl od v jazyce C++ pole neobsahuje název souboru spustitelný soubor (exe).</span><span class="sxs-lookup"><span data-stu-id="3da7f-136">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>

<span data-ttu-id="3da7f-137">Další informace o tom, jak používat argumenty příkazového řádku, podívejte se na příklady v [Main() a argumenty příkazového řádku](../../../csharp/programming-guide/main-and-command-args/index.md) a [jak: Vytvoření a použití sestavení s pomocí příkazového řádku](../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="3da7f-137">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>

<span data-ttu-id="3da7f-138">Volání <xref:System.Console.ReadKey%2A> na konci `Main` metody zabrání v okně konzoly se ukončit dříve, než máte možnost si přečíst výstup při spuštění programu v režimu ladění, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="3da7f-138">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>

## <a name="input-and-output"></a><span data-ttu-id="3da7f-139">Vstup a výstup</span><span class="sxs-lookup"><span data-stu-id="3da7f-139">Input and output</span></span>

<span data-ttu-id="3da7f-140">C# obvykle používají vstupní a výstupní služby poskytované knihovny run-time rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3da7f-140">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="3da7f-141">Příkaz `System.Console.WriteLine("Hello World!");` používá <xref:System.Console.WriteLine%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3da7f-141">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="3da7f-142">Toto je jedna z metod výstupu <xref:System.Console> třídy do knihovny run-time.</span><span class="sxs-lookup"><span data-stu-id="3da7f-142">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="3da7f-143">Zobrazuje svůj parametr řetězce v datovém proudu standardního výstupu následovaný novým řádkem.</span><span class="sxs-lookup"><span data-stu-id="3da7f-143">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="3da7f-144">Další <xref:System.Console> metody jsou k dispozici pro různé vstupní a výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="3da7f-144">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="3da7f-145">Pokud zahrnete `using System;` direktiv na začátku programu, můžete přímo použít <xref:System> třídy a metody bez jejich plné kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="3da7f-145">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="3da7f-146">Například můžete volat `Console.WriteLine` místo `System.Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="3da7f-146">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="3da7f-147">Další informace o vstupních/výstupních metodách naleznete v tématu <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="3da7f-147">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="3da7f-148">Příkazový řádek kompilace a spuštění</span><span class="sxs-lookup"><span data-stu-id="3da7f-148">Command-line compilation and execution</span></span>

<span data-ttu-id="3da7f-149">Můžete kompilovat "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3da7f-149">You can compile the "Hello World!"</span></span> <span data-ttu-id="3da7f-150">program pomocí příkazového řádku namísto Visual Studio integrované vývojové prostředí (IDE).</span><span class="sxs-lookup"><span data-stu-id="3da7f-150">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>

### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="3da7f-151">Kompilace a spuštění z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="3da7f-151">To compile and run from a command prompt</span></span>

1. <span data-ttu-id="3da7f-152">Vložte kód z předchozího postupu do libovolného textového editoru a uložte soubor jako textový soubor.</span><span class="sxs-lookup"><span data-stu-id="3da7f-152">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="3da7f-153">Pojmenujte soubor `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="3da7f-153">Name the file `Hello.cs`.</span></span> <span data-ttu-id="3da7f-154">Soubory zdrojového kódu jazyka C# používají příponu `.cs`.</span><span class="sxs-lookup"><span data-stu-id="3da7f-154">C# source code files use the extension `.cs`.</span></span>

2. <span data-ttu-id="3da7f-155">Proveďte jeden z následujících kroků a otevřete okno příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="3da7f-155">Perform one of the following steps to open a command-prompt window:</span></span>

    - <span data-ttu-id="3da7f-156">Ve Windows 10 na **Start** nabídky, vyhledejte `Developer Command Prompt`a potom klepněte nebo vyberte možnost **Developer Command Prompt for VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="3da7f-156">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="3da7f-157">Zobrazí se okno příkazového řádku pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="3da7f-157">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="3da7f-158">Ve Windows 7, otevřete **Start** nabídka, rozbalte složku pro aktuální verzi sady Visual Studio, otevřete místní nabídku pro **Visual Studio Tools**a klikněte na tlačítko **Developer Command Prompt pro sady VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="3da7f-158">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="3da7f-159">Zobrazí se okno příkazového řádku pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="3da7f-159">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="3da7f-160">Povolte sestavení příkazového řádku ze standardního okna příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="3da7f-160">Enable command-line builds from a standard Command Prompt window.</span></span>

         <span data-ttu-id="3da7f-161">Zobrazit [jak: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="3da7f-161">See [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

3. <span data-ttu-id="3da7f-162">V okně příkazového řádku přejděte do složky, která obsahuje vaše `Hello.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="3da7f-162">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>

4. <span data-ttu-id="3da7f-163">Zadejte následující příkaz pro kompilaci `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="3da7f-163">Enter the following command to compile `Hello.cs`.</span></span>

     `csc Hello.cs`

     <span data-ttu-id="3da7f-164">Pokud program neobsahuje žádné chyby během kompilace, spustitelný soubor, který je pojmenován `Hello.exe` se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="3da7f-164">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>

5. <span data-ttu-id="3da7f-165">V okně příkazového řádku zadejte následující příkaz pro spuštění programu:</span><span class="sxs-lookup"><span data-stu-id="3da7f-165">In the command-prompt window, enter the following command to run the program:</span></span>

     `Hello`

 <span data-ttu-id="3da7f-166">Další informace o kompilátoru C# a jeho možnostech naleznete v tématu [možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md).</span><span class="sxs-lookup"><span data-stu-id="3da7f-166">For more information about the C# compiler and its options, see [C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3da7f-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3da7f-167">See also</span></span>

- [<span data-ttu-id="3da7f-168">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3da7f-168">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3da7f-169">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3da7f-169">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)
- [<span data-ttu-id="3da7f-170">Řetězce</span><span class="sxs-lookup"><span data-stu-id="3da7f-170">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
- [<span data-ttu-id="3da7f-171">Ukázky a kurzy</span><span class="sxs-lookup"><span data-stu-id="3da7f-171">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="3da7f-172">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3da7f-172">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="3da7f-173">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="3da7f-173">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="3da7f-174">Začínáme s jazykem Visual C# a Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3da7f-174">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)