---
title: Sestavení příkazového řádku pomocí csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 3cd49a17991f3d7606b0364a83be2b2e30ba0cce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218056"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="2a1e2-102">Sestavení příkazového řádku pomocí csc.exe</span><span class="sxs-lookup"><span data-stu-id="2a1e2-102">Command-line build with csc.exe</span></span>
<span data-ttu-id="2a1e2-103">Kompilátor jazyka C# můžete vyvolat zadáním názvu jeho spustitelného souboru (*csc.exe*) na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="2a1e2-104">Pokud použijete **příkazový řádek vývojáře pro sadu Visual Studio** okně všechny nezbytné proměnné prostředí jsou nastavené pro vás.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="2a1e2-105">Informace o tom, jak získat přístup k tento nástroj najdete v tématu [příkazový řádek vývojáře pro sadu Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span> 

<span data-ttu-id="2a1e2-106">Pokud chcete použít standardní okno příkazového řádku, je nutné upravit cestu k, než můžete vyvolat *csc.exe* z libovolného adresáře v počítači.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="2a1e2-107">Také musíte spustit *vsvars32.bat* nastavit příslušné proměnné prostředí pro podporu sestavení příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="2a1e2-108">Další informace o *vsvars32.bat*, včetně pokyny, jak najít a spustit ji, najdete v článku [postupy: nastavení proměnných prostředí pro Visual Studio v příkazovém řádku](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="2a1e2-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="2a1e2-109">Pokud pracujete na počítač, který je k dispozici pouze [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], můžete kompilátor jazyka C# na **SDK – příkazový řádek**, které otevřete z **Microsoft .NET Framework SDK** možnost nabídky.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-109">If you're working on a computer that has only the [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="2a1e2-110">MSBuild můžete také použít k sestavení C# programy prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="2a1e2-111">Další informace najdete v tématu [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="2a1e2-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="2a1e2-112">*Csc.exe* spustitelný soubor je obvykle uložen ve Microsoft.NET\Framework\\*\<verze >* ve složce *Windows* adresář.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="2a1e2-113">Umístění, kde se můžou lišit v závislosti na přesnou konfiguraci určitého počítače.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="2a1e2-114">Pokud ve vašem počítači je nainstalovaná více než jedna verze rozhraní .NET Framework, zjistíte více verzí tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="2a1e2-115">Další informace o těchto instalacích najdete v tématu [postupy: zjištění nainstalovaných verzí rozhraní .NET Framework](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="2a1e2-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
>  <span data-ttu-id="2a1e2-116">Při sestavování projektu pomocí prostředí Visual Studio IDE, můžete zobrazit **csc** příkaz a její přidružené kompilátoru možnosti v **výstup** okno.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="2a1e2-117">Chcete-li zobrazit tyto informace, postupujte podle pokynů v [postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) chcete změnit úroveň podrobností dat protokolu **normální** nebo **podrobné**.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="2a1e2-118">Po opětovném sestavení projektu, vyhledávání **výstup** okna pro **csc** najít volání do kompilátoru jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="2a1e2-119">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="2a1e2-119">**In this topic**</span></span>

- [<span data-ttu-id="2a1e2-120">Pravidla pro syntaxe příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2a1e2-120">Rules for command-line syntax</span></span>](#-rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="2a1e2-121">Příkazové řádky ukázkové</span><span class="sxs-lookup"><span data-stu-id="2a1e2-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="2a1e2-122">Rozdíly mezi kompilátor jazyka C# a výstup kompilátoru C++</span><span class="sxs-lookup"><span data-stu-id="2a1e2-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="2a1e2-123">Pravidla pro syntaxe příkazového řádku pro kompilátor jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2a1e2-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="2a1e2-124">Kompilátor jazyka C# používá následující pravidla při interpretaci argumentů zadána na příkazovém řádku operačního systému:</span><span class="sxs-lookup"><span data-stu-id="2a1e2-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="2a1e2-125">Argumenty jsou odděleny prázdný znak, který je mezeru nebo na kartě.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="2a1e2-126">Znak pomocí kurzoru (^) není rozpoznán jako řídicí znak nebo oddělovač.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="2a1e2-127">Znak je zpracován analyzátorem příkazového řádku v operačním systému, než je předán do `argv` pole v programu.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="2a1e2-128">Řetězec v uvozovkách ("řetězec") interpretována jako jeden argument, bez ohledu na to prázdný znak, který je součástí.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="2a1e2-129">Řetězec v uvozovkách, lze jej vkládat v argumentu.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="2a1e2-130">Uvozovky uvedené zpětným lomítkem (\\") je interpretován jako znak dvojitých uvozovek (").</span><span class="sxs-lookup"><span data-stu-id="2a1e2-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="2a1e2-131">Zpětná lomítka se interpretují oznámena, pokud se okamžitě předcházet uvozovky.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="2a1e2-132">Pokud sudý počet zpětná lomítka následuje uvozovky, jeden zpětné lomítko uveden `argv` pole pro každý pár zpětná lomítka a dvojité uvozovky se interpretuje jako oddělovač řetězec.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="2a1e2-133">Pokud lichý počet zpětná lomítka následuje uvozovky, jeden zpětné lomítko uveden `argv` pole pro každý pár zpětná lomítka a dvojité uvozovky se "escape" ve zbývajících zpětné lomítko.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="2a1e2-134">To způsobí, že literálu uvozovky (") k přidání do `argv`.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="2a1e2-135">Příkazové řádky ukázkové pro kompilátor jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2a1e2-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="2a1e2-136">Zkompiluje *File.cs* generovala *File.exe*:</span><span class="sxs-lookup"><span data-stu-id="2a1e2-136">Compiles *File.cs* producing *File.exe*:</span></span>

```console
csc File.cs 
```

- <span data-ttu-id="2a1e2-137">Zkompiluje *File.cs* generovala *souboru File.dll*:</span><span class="sxs-lookup"><span data-stu-id="2a1e2-137">Compiles *File.cs* producing *File.dll*:</span></span>

```console
csc -target:library File.cs
```

- <span data-ttu-id="2a1e2-138">Zkompiluje *File.cs* a vytvoří *My.exe*:</span><span class="sxs-lookup"><span data-stu-id="2a1e2-138">Compiles *File.cs* and creates *My.exe*:</span></span>

```console
csc -out:My.exe File.cs
```

- <span data-ttu-id="2a1e2-139">Kompiluje všechny C# soubory v aktuálním adresáři s povolenými optimalizacemi a definuje symboly pro ladění.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="2a1e2-140">Výstupem je *File2.exe*:</span><span class="sxs-lookup"><span data-stu-id="2a1e2-140">The output is *File2.exe*:</span></span>

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- <span data-ttu-id="2a1e2-141">Kompiluje všechny C# soubory v aktuálním adresáři ladicí verze *File2.dll pro ladění*.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="2a1e2-142">Zobrazí se žádná upozornění ani logo:</span><span class="sxs-lookup"><span data-stu-id="2a1e2-142">No logo and no warnings are displayed:</span></span>

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- <span data-ttu-id="2a1e2-143">Kompiluje všechny C# soubory v aktuálním adresáři na *Something.xyz* (DLL):</span><span class="sxs-lookup"><span data-stu-id="2a1e2-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="2a1e2-144">Rozdíly mezi kompilátor jazyka C# a výstup kompilátoru C++</span><span class="sxs-lookup"><span data-stu-id="2a1e2-144">Differences between C# compiler and C++ compiler output</span></span>
<span data-ttu-id="2a1e2-145">Neexistují žádné objektu (*.obj*) v důsledku volání do kompilátoru jazyka C# vytvoří soubory; výstupní soubory vytvářené přímo.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="2a1e2-146">V důsledku toho nemusí kompilátor jazyka C# linkeru.</span><span class="sxs-lookup"><span data-stu-id="2a1e2-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a1e2-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a1e2-147">See also</span></span>
 [<span data-ttu-id="2a1e2-148">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2a1e2-148">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="2a1e2-149">Možnosti kompilátoru jazyka C# (abecední pořadí)</span><span class="sxs-lookup"><span data-stu-id="2a1e2-149">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [<span data-ttu-id="2a1e2-150">Možnosti kompilátoru jazyka C# uvedené podle kategorie</span><span class="sxs-lookup"><span data-stu-id="2a1e2-150">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 [<span data-ttu-id="2a1e2-151">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2a1e2-151">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="2a1e2-152">Argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2a1e2-152">Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
 [<span data-ttu-id="2a1e2-153">Postupy: Zobrazení argumentů příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2a1e2-153">How to: Display Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [<span data-ttu-id="2a1e2-154">Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach</span><span class="sxs-lookup"><span data-stu-id="2a1e2-154">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [<span data-ttu-id="2a1e2-155">Návratové hodnoty Main()</span><span class="sxs-lookup"><span data-stu-id="2a1e2-155">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
