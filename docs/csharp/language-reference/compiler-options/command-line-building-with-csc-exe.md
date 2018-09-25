---
title: Sestavení z příkazového řádku s csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 4b6dfdbce131371553fc729206de29794266bfbe
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "46710681"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="ae573-102">Sestavení z příkazového řádku s csc.exe</span><span class="sxs-lookup"><span data-stu-id="ae573-102">Command-line build with csc.exe</span></span>
<span data-ttu-id="ae573-103">Kompilátor jazyka C# můžete vyvolat zadáním názvu její spustitelný soubor (*csc.exe*) z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ae573-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="ae573-104">Pokud používáte **Developer Command Prompt pro sadu Visual Studio** okna, všechny nezbytné proměnné prostředí jsou nastaveny za vás.</span><span class="sxs-lookup"><span data-stu-id="ae573-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="ae573-105">Informace o tom, jak tento nástroj používat, najdete v článku [Developer Command Prompt pro sadu Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="ae573-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span> 

<span data-ttu-id="ae573-106">Pokud používáte standardního okna příkazového řádku, je nutné upravit cestu k, abyste mohli vyvolat *csc.exe* z libovolného adresáře v počítači.</span><span class="sxs-lookup"><span data-stu-id="ae573-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="ae573-107">Je také nutné spustit *vsvars32.bat* nastavit příslušné proměnné prostředí pro podporu sestavení příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ae573-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="ae573-108">Další informace o *vsvars32.bat*, včetně pokynů pro vyhledání a spusťte ho, naleznete v tématu [postupy: nastavení proměnných prostředí pro Visual Studio příkazového řádku](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="ae573-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="ae573-109">Pokud pracujete na počítači, který má pouze [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], můžete použít kompilátor jazyka C# na **příkazový řádek sady SDK**, které můžete otevřít z **Microsoft .NET Framework SDK** nabídky.</span><span class="sxs-lookup"><span data-stu-id="ae573-109">If you're working on a computer that has only the [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="ae573-110">Pomocí nástroje MSBuild můžete také programově vytvářet programy jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="ae573-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="ae573-111">Další informace najdete v tématu [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="ae573-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="ae573-112">*Csc.exe* spustitelný soubor je obvykle umístěn ve Microsoft.NET\Framework\\*\<verze >* ve složce *Windows* adresář.</span><span class="sxs-lookup"><span data-stu-id="ae573-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="ae573-113">Umístění, kde se může lišit v závislosti na přesnou konfiguraci určitého počítače.</span><span class="sxs-lookup"><span data-stu-id="ae573-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="ae573-114">Pokud více než jednu verzi rozhraní .NET Framework je nainstalována v počítači, zjistíte více verzí tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="ae573-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="ae573-115">Další informace o těchto zařízení najdete v tématu [postupy: zjištění nainstalovaných verzí rozhraní .NET Framework](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="ae573-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
>  <span data-ttu-id="ae573-116">Při vytváření projektu pomocí rozhraní IDE sady Visual Studio můžete zobrazit **csc** příkazu a jeho kompilátoru přidružené možností v **výstup** okna.</span><span class="sxs-lookup"><span data-stu-id="ae573-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="ae573-117">Chcete-li zobrazit tyto informace, postupujte podle pokynů v [postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) změnit úroveň podrobností dat protokolu do **normální** nebo **podrobné**.</span><span class="sxs-lookup"><span data-stu-id="ae573-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="ae573-118">Po opětovném sestavení projektu, hledání **výstup** okně **csc** najít vyvolání kompilátor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="ae573-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="ae573-119">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="ae573-119">**In this topic**</span></span>

- [<span data-ttu-id="ae573-120">Pravidla pro syntaxi příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ae573-120">Rules for command-line syntax</span></span>](#-rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="ae573-121">Ukázkové příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="ae573-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="ae573-122">Rozdíly mezi kompilátor jazyka C# a výstup kompilátoru C++</span><span class="sxs-lookup"><span data-stu-id="ae573-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="ae573-123">Pravidla pro syntaxi příkazového řádku pro kompilátor jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ae573-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="ae573-124">Kompilátor jazyka C# používá při interpretaci argumentů příkazového řádku operačního systému následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="ae573-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="ae573-125">Argumenty jsou odděleny prázdným znakem, který je mezera nebo tabulátor.</span><span class="sxs-lookup"><span data-stu-id="ae573-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="ae573-126">Znak stříšky (^) nebyl rozpoznán jako řídicí znak ani oddělovač.</span><span class="sxs-lookup"><span data-stu-id="ae573-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="ae573-127">Znak, který zařizuje služba analyzátor příkazového řádku v operačním systému předtím, než je předána `argv` pole v programu.</span><span class="sxs-lookup"><span data-stu-id="ae573-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="ae573-128">Řetězec uzavřen do dvojitých uvozovek ("string") je interpretován jako jeden argument, bez ohledu na prázdný znak, který je součástí.</span><span class="sxs-lookup"><span data-stu-id="ae573-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="ae573-129">Řetězec v uvozovkách, může být vložen do argumentu.</span><span class="sxs-lookup"><span data-stu-id="ae573-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="ae573-130">Znak dvojitých uvozovek předcházený zpětným lomítkem (\\") je interpretován jako znak dvojitých uvozovek (").</span><span class="sxs-lookup"><span data-stu-id="ae573-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="ae573-131">Zpětná lomítka jsou interpretovány literálně, pokud jsou bezprostředně předcházet dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="ae573-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="ae573-132">Pokud sudý počet zpětných lomítek následován znakem dvojitých uvozovek, je jedno zpětné lomítko ukládat `argv` pole pro každý pár zpětných lomítek a dvojitých uvozovek, je interpretován jako oddělovač řetězců.</span><span class="sxs-lookup"><span data-stu-id="ae573-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="ae573-133">Pokud lichý počet zpětných lomítek následován znakem dvojitých uvozovek, je jedno zpětné lomítko ukládat `argv` pole pro každý pár zpětných lomítek a dvojitá uvozovka není "uvozeno uvozovacím znakem" ve zbývajících zpětné lomítko.</span><span class="sxs-lookup"><span data-stu-id="ae573-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="ae573-134">To způsobí, že literálu uvozovky (") mají být přidány v `argv`.</span><span class="sxs-lookup"><span data-stu-id="ae573-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="ae573-135">Příkazové řádky ukázkové pro kompilátor jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ae573-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="ae573-136">Zkompiluje *File.cs* vytváření *File.exe*:</span><span class="sxs-lookup"><span data-stu-id="ae573-136">Compiles *File.cs* producing *File.exe*:</span></span>

```console
csc File.cs 
```

- <span data-ttu-id="ae573-137">Zkompiluje *File.cs* vytváření *soubor.dll*:</span><span class="sxs-lookup"><span data-stu-id="ae573-137">Compiles *File.cs* producing *File.dll*:</span></span>

```console
csc -target:library File.cs
```

- <span data-ttu-id="ae573-138">Zkompiluje *File.cs* a vytvoří *My.exe*:</span><span class="sxs-lookup"><span data-stu-id="ae573-138">Compiles *File.cs* and creates *My.exe*:</span></span>

```console
csc -out:My.exe File.cs
```

- <span data-ttu-id="ae573-139">Kompiluje všechny jazyka C# soubory v aktuálním adresáři s povolenou optimalizací a definuje DEBUG symbol.</span><span class="sxs-lookup"><span data-stu-id="ae573-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="ae573-140">Výstup je *File2.exe*:</span><span class="sxs-lookup"><span data-stu-id="ae573-140">The output is *File2.exe*:</span></span>

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- <span data-ttu-id="ae573-141">Kompiluje všechny jazyka C# soubory v aktuálním adresáři ladicí verzi *File2.dll pro ladění*.</span><span class="sxs-lookup"><span data-stu-id="ae573-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="ae573-142">Žádná upozornění ani logo se zobrazí:</span><span class="sxs-lookup"><span data-stu-id="ae573-142">No logo and no warnings are displayed:</span></span>

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- <span data-ttu-id="ae573-143">Kompiluje všechny jazyka C# soubory v aktuálním adresáři *Something.xyz* (DLL):</span><span class="sxs-lookup"><span data-stu-id="ae573-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="ae573-144">Rozdíly mezi kompilátor jazyka C# a výstup kompilátoru C++</span><span class="sxs-lookup"><span data-stu-id="ae573-144">Differences between C# compiler and C++ compiler output</span></span>
<span data-ttu-id="ae573-145">Neexistují žádné objektu (*.obj*) soubory vytvořené v důsledku volání kompilátor jazyka C#; výstupní soubory jsou vytvořeny přímo.</span><span class="sxs-lookup"><span data-stu-id="ae573-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="ae573-146">V důsledku toho nemusí kompilátor jazyka C# propojovacího programu.</span><span class="sxs-lookup"><span data-stu-id="ae573-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae573-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae573-147">See also</span></span>

- [<span data-ttu-id="ae573-148">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ae573-148">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="ae573-149">Možnosti kompilátoru jazyka C# (abecední pořadí)</span><span class="sxs-lookup"><span data-stu-id="ae573-149">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
- [<span data-ttu-id="ae573-150">Možnosti kompilátoru jazyka C# uvedené podle kategorie</span><span class="sxs-lookup"><span data-stu-id="ae573-150">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
- [<span data-ttu-id="ae573-151">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ae573-151">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [<span data-ttu-id="ae573-152">Argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ae573-152">Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
- [<span data-ttu-id="ae573-153">Postupy: Zobrazení argumentů příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ae573-153">How to: Display Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
- [<span data-ttu-id="ae573-154">Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach</span><span class="sxs-lookup"><span data-stu-id="ae573-154">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
- [<span data-ttu-id="ae573-155">Návratové hodnoty Main()</span><span class="sxs-lookup"><span data-stu-id="ae573-155">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
