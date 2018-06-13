---
title: Hello World! -- váš první program (Průvodce programováním v C#)
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 904657175d87e0d78e518248ed89b3720227360f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339167"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="6e85f-102">Hello World! -- váš první program (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6e85f-102">Hello World -- Your First Program (C# Programming Guide)</span></span>
<span data-ttu-id="6e85f-103">Následující postup vytvoří C# verze tradiční "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="6e85f-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="6e85f-104">program.</span><span class="sxs-lookup"><span data-stu-id="6e85f-104">program.</span></span> <span data-ttu-id="6e85f-105">Program zobrazí řetězec `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="6e85f-105">The program displays the string `Hello World!`</span></span>  
  
 <span data-ttu-id="6e85f-106">Další příklady úvodní koncepty, najdete v části [Začínáme s Visual C# a Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6e85f-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="6e85f-107">Vytvoření a spuštění konzolové aplikace</span><span class="sxs-lookup"><span data-stu-id="6e85f-107">To create and run a console application</span></span>  
  
1.  <span data-ttu-id="6e85f-108">Spuštění sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e85f-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="6e85f-109">Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="6e85f-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="6e85f-110">**Nový projekt** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="6e85f-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="6e85f-111">Rozbalte položku **nainstalovaná**, rozbalte položku **šablony**, rozbalte položku **Visual C#** a potom zvolte **konzolové aplikace**.</span><span class="sxs-lookup"><span data-stu-id="6e85f-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="6e85f-112">V **název** pole, zadejte název pro svůj projekt a potom zvolte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="6e85f-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="6e85f-113">Nový projekt se zobrazí v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="6e85f-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="6e85f-114">Pokud není otevřen v souboru Program.cs **Editor kódu**, otevřete místní nabídku pro **Program.cs** v **Průzkumníku řešení**a potom zvolte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="6e85f-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="6e85f-115">Nahraďte obsah souboru Program.cs následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="6e85f-115">Replace the contents of Program.cs with the following code.</span></span>  
  
     [!code-csharp[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  <span data-ttu-id="6e85f-116">Zvolte klávesu F5 a spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="6e85f-116">Choose the F5 key to run the project.</span></span> <span data-ttu-id="6e85f-117">Zobrazí se okno příkazového řádku, která obsahuje řádek `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="6e85f-117">A Command Prompt window appears that contains the line `Hello World!`</span></span>  
  
 <span data-ttu-id="6e85f-118">V dalším kroku se zkontrolují důležité části tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="6e85f-118">Next, the important parts of this program are examined.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="6e85f-119">Komentáře</span><span class="sxs-lookup"><span data-stu-id="6e85f-119">Comments</span></span>  
 <span data-ttu-id="6e85f-120">První řádek obsahuje komentář.</span><span class="sxs-lookup"><span data-stu-id="6e85f-120">The first line contains a comment.</span></span> <span data-ttu-id="6e85f-121">Znaky `//` převést zbytek řádku na komentář.</span><span class="sxs-lookup"><span data-stu-id="6e85f-121">The characters `//` convert the rest of the line to a comment.</span></span>  
  
 [!code-csharp[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 <span data-ttu-id="6e85f-122">Můžete také Zakomentovat blok textu uveden mezi `/*` a `*/` znaků.</span><span class="sxs-lookup"><span data-stu-id="6e85f-122">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="6e85f-123">To je ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6e85f-123">This is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a><span data-ttu-id="6e85f-124">Main – metoda</span><span class="sxs-lookup"><span data-stu-id="6e85f-124">Main Method</span></span>  
 <span data-ttu-id="6e85f-125">Musí obsahovat konzolovou aplikaci C# `Main` metoda, ve kterém řízení spuštění a ukončení.</span><span class="sxs-lookup"><span data-stu-id="6e85f-125">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="6e85f-126">`Main` Je metoda, kde vytvářet objekty a provést další metody.</span><span class="sxs-lookup"><span data-stu-id="6e85f-126">The `Main` method is where you create objects and execute other methods.</span></span>  
  
 <span data-ttu-id="6e85f-127">`Main` Je metoda [statické](../../../csharp/language-reference/keywords/static.md) metoda, která se nachází uvnitř třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="6e85f-127">The `Main` method is a [static](../../../csharp/language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="6e85f-128">V předchozích "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="6e85f-128">In the previous "Hello World!"</span></span> <span data-ttu-id="6e85f-129">například se nachází v třídy s názvem `Hello`.</span><span class="sxs-lookup"><span data-stu-id="6e85f-129">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="6e85f-130">Je možné deklarovat `Main` metoda v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="6e85f-130">You can declare the `Main` method in one of the following ways:</span></span>  
  
-   <span data-ttu-id="6e85f-131">Může vrátit `void`.</span><span class="sxs-lookup"><span data-stu-id="6e85f-131">It can return `void`.</span></span>  
  
     [!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   <span data-ttu-id="6e85f-132">Také se může vrátit celé číslo.</span><span class="sxs-lookup"><span data-stu-id="6e85f-132">It can also return an integer.</span></span>  
  
     [!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   <span data-ttu-id="6e85f-133">Některým z návratové typy může trvat argumenty.</span><span class="sxs-lookup"><span data-stu-id="6e85f-133">With either of the return types, it can take arguments.</span></span>  
  
     [!code-csharp[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     <span data-ttu-id="6e85f-134">-nebo-</span><span class="sxs-lookup"><span data-stu-id="6e85f-134">-or-</span></span>  
  
     [!code-csharp[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 <span data-ttu-id="6e85f-135">Parametr `Main` metody `args`, je `string` pole, které obsahuje argumenty příkazového řádku, použije k vyvolání programu.</span><span class="sxs-lookup"><span data-stu-id="6e85f-135">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="6e85f-136">Na rozdíl od v jazyce C++ pole neobsahuje název souboru spustitelný soubor (exe).</span><span class="sxs-lookup"><span data-stu-id="6e85f-136">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>  
  
 <span data-ttu-id="6e85f-137">Další informace o tom, jak používat argumenty příkazového řádku, podívejte se na příklady v [Main() a příkazového řádku argumenty](../../../csharp/programming-guide/main-and-command-args/index.md) a [postupy: vytvoření a použití sestavení pomocí příkazu řádek](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).</span><span class="sxs-lookup"><span data-stu-id="6e85f-137">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).</span></span>  
  
 <span data-ttu-id="6e85f-138">Volání <xref:System.Console.ReadKey%2A> na konci `Main` metoda zabraňuje v okně konzoly zavřením předtím, než budete mít možnost číst výstup při spuštění programu v režimu ladění, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="6e85f-138">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>  
  
## <a name="input-and-output"></a><span data-ttu-id="6e85f-139">Vstup a výstup</span><span class="sxs-lookup"><span data-stu-id="6e85f-139">Input and Output</span></span>  
 <span data-ttu-id="6e85f-140">Programy C# obecně používat vstupu a výstupu služeb poskytovaných běhové knihovny rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6e85f-140">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="6e85f-141">Příkaz `System.Console.WriteLine("Hello World!");` používá <xref:System.Console.WriteLine%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="6e85f-141">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="6e85f-142">Toto je jedna z metod výstup <xref:System.Console> třídy v běhové knihovny.</span><span class="sxs-lookup"><span data-stu-id="6e85f-142">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="6e85f-143">Zobrazí jeho parametr řetězce na standardní výstupní datový proud, za nímž následuje nový řádek.</span><span class="sxs-lookup"><span data-stu-id="6e85f-143">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="6e85f-144">Další <xref:System.Console> metody jsou k dispozici pro jinou vstupní a výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="6e85f-144">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="6e85f-145">Pokud zahrnete `using System;` direktivy na začátku tohoto programu, můžete přímo použít <xref:System> třídy a metody bez plně kvalifikovaného je.</span><span class="sxs-lookup"><span data-stu-id="6e85f-145">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="6e85f-146">Například můžete volat `Console.WriteLine` místo `System.Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="6e85f-146">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-csharp[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 <span data-ttu-id="6e85f-147">Další informace o metodách vstupu a výstupu, najdete v části <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="6e85f-147">For more information about input/output methods, see <xref:System.IO>.</span></span>  
  
## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="6e85f-148">Kompilace a provádění na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="6e85f-148">Command-Line Compilation and Execution</span></span>  
 <span data-ttu-id="6e85f-149">Zkompilujete "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="6e85f-149">You can compile the "Hello World!"</span></span> <span data-ttu-id="6e85f-150">program pomocí příkazového řádku místo prostředí Visual Studio integrované vývoj prostředí (IDE).</span><span class="sxs-lookup"><span data-stu-id="6e85f-150">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="6e85f-151">Kompilace a spuštění z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="6e85f-151">To compile and run from a command prompt</span></span>  
  
1.  <span data-ttu-id="6e85f-152">Vložit do libovolného textového editoru kódu v předchozím postupu a pak soubor uložte jako textový soubor.</span><span class="sxs-lookup"><span data-stu-id="6e85f-152">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="6e85f-153">Název souboru `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="6e85f-153">Name the file `Hello.cs`.</span></span> <span data-ttu-id="6e85f-154">Soubory zdrojového kódu C# pomocí rozšíření `.cs`.</span><span class="sxs-lookup"><span data-stu-id="6e85f-154">C# source code files use the extension `.cs`.</span></span>  
  
2.  <span data-ttu-id="6e85f-155">Proveďte jeden z následujících kroků otevřete okno příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="6e85f-155">Perform one of the following steps to open a command-prompt window:</span></span>  
  
    -   <span data-ttu-id="6e85f-156">Ve Windows 10 na **spustit** nabídky, vyhledejte `Developer Command Prompt`a potom klepněte na nebo zvolte **příkazový řádek vývojáře pro VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="6e85f-156">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="6e85f-157">Zobrazí se okno příkazového řádku vývojáře.</span><span class="sxs-lookup"><span data-stu-id="6e85f-157">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="6e85f-158">V systému Windows 7, otevřete **spustit** nabídky, rozbalte složku s aktuální verzí sady Visual Studio, otevřete místní nabídku pro **nástroje sady Visual Studio**a potom zvolte **příkazový řádek vývojáře pro VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="6e85f-158">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="6e85f-159">Zobrazí se okno příkazového řádku vývojáře.</span><span class="sxs-lookup"><span data-stu-id="6e85f-159">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="6e85f-160">Povolte sestavení příkazového řádku z standardní okno příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6e85f-160">Enable command-line builds from a standard Command Prompt window.</span></span>  
  
         <span data-ttu-id="6e85f-161">V tématu [postupy: nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="6e85f-161">See [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>  
  
3.  <span data-ttu-id="6e85f-162">V okně příkazového řádku přejděte do složky, která obsahuje vaše `Hello.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="6e85f-162">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>  
  
4.  <span data-ttu-id="6e85f-163">Zadejte následující příkaz pro kompilaci `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="6e85f-163">Enter the following command to compile `Hello.cs`.</span></span>  
  
     `csc Hello.cs`  
  
     <span data-ttu-id="6e85f-164">Pokud váš program nejsou žádné chyby kompilace, spustitelný soubor, který je pojmenován `Hello.exe` je vytvořena.</span><span class="sxs-lookup"><span data-stu-id="6e85f-164">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>  
  
5.  <span data-ttu-id="6e85f-165">V okně příkazového řádku zadejte následující příkaz pro spuštění programu:</span><span class="sxs-lookup"><span data-stu-id="6e85f-165">In the command-prompt window, enter the following command to run the program:</span></span>  
  
     `Hello`  
  
 <span data-ttu-id="6e85f-166">Další informace o kompilátor jazyka C# a její možnosti najdete v tématu [možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md).</span><span class="sxs-lookup"><span data-stu-id="6e85f-166">For more information about the C# compiler and its options, see [C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6e85f-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e85f-167">See Also</span></span>  
 [<span data-ttu-id="6e85f-168">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6e85f-168">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6e85f-169">V programu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6e85f-169">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)  
 [<span data-ttu-id="6e85f-170">Řetězce</span><span class="sxs-lookup"><span data-stu-id="6e85f-170">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="6e85f-171">\<paveover > C# ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="6e85f-171">\<paveover>C# Sample Applications</span></span>](http://msdn.microsoft.com/library/9a9d7aaa-51d3-4224-b564-95409b0f3e15)  
 [<span data-ttu-id="6e85f-172">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6e85f-172">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6e85f-173">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="6e85f-173">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="6e85f-174">Začínáme s jazykem Visual C# a Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e85f-174">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
