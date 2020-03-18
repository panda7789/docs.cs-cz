---
title: Sestavení příkazového řádku s csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: f692e66672b1804a309c6ac04c158af948a1b1ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789862"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="25e15-102">Sestavení příkazového řádku s csc.exe</span><span class="sxs-lookup"><span data-stu-id="25e15-102">Command-line build with csc.exe</span></span>

<span data-ttu-id="25e15-103">Kompilátor jazyka C# můžete vyvolat zadáním názvu jeho spustitelného souboru (*csc.exe*) na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="25e15-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="25e15-104">Pokud použijete **okno Příkazový řádek pro vývojáře pro sadu Visual Studio,** budou nastaveny všechny proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="25e15-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="25e15-105">Informace o tom, jak získat přístup k tomuto nástroji, naleznete v [tématu Vývojářský příkaz ový řádek pro sadu Visual Studio.](../../../framework/tools/developer-command-prompt-for-vs.md)</span><span class="sxs-lookup"><span data-stu-id="25e15-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span>

<span data-ttu-id="25e15-106">Pokud používáte standardní okno příkazového řádku, je nutné upravit cestu před vyvoláním *souboru csc.exe* z libovolného podadresáře v počítači.</span><span class="sxs-lookup"><span data-stu-id="25e15-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="25e15-107">Musíte také spustit *vsvars32.bat* nastavit příslušné proměnné prostředí pro podporu sestavení příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="25e15-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="25e15-108">Další informace o *vsvars32.bat*, včetně pokynů k vyhledání a spuštění, naleznete v tématu [Jak nastavit proměnné prostředí pro příkazový řádek sady Visual Studio](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="25e15-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to set environment variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="25e15-109">Pokud pracujete na počítači, který obsahuje pouze sadu Windows Software Development Kit (SDK), můžete použít kompilátor jazyka C# na **příkazovém řádku sady SDK**, který otevřete z nabídky sady **Microsoft .NET Framework SDK.**</span><span class="sxs-lookup"><span data-stu-id="25e15-109">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="25e15-110">MSBuild můžete také použít k vytvoření programů Jazyka C# programově.</span><span class="sxs-lookup"><span data-stu-id="25e15-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="25e15-111">Další informace naleznete v tématu [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="25e15-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="25e15-112">Spustitelný soubor *csc.exe* je obvykle umístěn ve\\složce Microsoft.NET\Framework*\<Version>* v adresáři *systému Windows.*</span><span class="sxs-lookup"><span data-stu-id="25e15-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="25e15-113">Jeho umístění se může lišit v závislosti na přesné konfiguraci konkrétního počítače.</span><span class="sxs-lookup"><span data-stu-id="25e15-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="25e15-114">Pokud je v počítači nainstalována více než jedna verze rozhraní .NET Framework, najdete více verzí tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="25e15-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="25e15-115">Další informace o těchto instalacích naleznete v [tématu How to: determine which version of the .NET Framework .](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)</span><span class="sxs-lookup"><span data-stu-id="25e15-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
> <span data-ttu-id="25e15-116">Při vytváření projektu pomocí ide sady Visual Studio můžete zobrazit příkaz **csc** a jeho přidružené možnosti kompilátoru v okně **Výstup.**</span><span class="sxs-lookup"><span data-stu-id="25e15-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="25e15-117">Chcete-li tyto informace zobrazit, postupujte podle pokynů v [části Postup: Zobrazení, uložení a konfigurace souborů protokolu sestavení](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) změňte úroveň podrobností dat protokolu na **normální** nebo **podrobnou**.</span><span class="sxs-lookup"><span data-stu-id="25e15-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="25e15-118">Po sestavení projektu vyhledejte vyvolání kompilátoru jazyka C#, vyhledejte v okně **Výstup** **csc** vyvolání kompilátoru jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="25e15-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="25e15-119">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="25e15-119">**In this topic**</span></span>

- [<span data-ttu-id="25e15-120">Pravidla pro syntaxi příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="25e15-120">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="25e15-121">Ukázkové příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="25e15-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="25e15-122">Rozdíly mezi kompilátorem jazyka C# a výstupem kompilátoru jazyka C++</span><span class="sxs-lookup"><span data-stu-id="25e15-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="25e15-123">Pravidla pro syntaxi příkazového řádku pro kompilátor jazyka C#</span><span class="sxs-lookup"><span data-stu-id="25e15-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="25e15-124">Kompilátor Jazyka C# používá následující pravidla, pokud interpretuje argumenty uvedené na příkazovém řádku operačního systému:</span><span class="sxs-lookup"><span data-stu-id="25e15-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="25e15-125">Argumenty jsou odděleny prázdné místo, což je mezera nebo karta.</span><span class="sxs-lookup"><span data-stu-id="25e15-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="25e15-126">Znak stříšky (^) není rozpoznán jako řídicí znak nebo oddělovač.</span><span class="sxs-lookup"><span data-stu-id="25e15-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="25e15-127">Znak je zpracován analyzátorem příkazového řádku v operačním systému před `argv` jeho předáním poli v programu.</span><span class="sxs-lookup"><span data-stu-id="25e15-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="25e15-128">Řetězec uzavřený v uvozovkách ("řetězec") je interpretován jako jeden argument, bez ohledu na prázdné místo, které je obsaženo uvnitř.</span><span class="sxs-lookup"><span data-stu-id="25e15-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="25e15-129">Řetězec v uvozovkách může být vložen do argumentu.</span><span class="sxs-lookup"><span data-stu-id="25e15-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="25e15-130">Dvojité uvozovky, před nimiž\\je zpětné lomítko ( ") interpretováno jako znak doslovné uvozovky ().</span><span class="sxs-lookup"><span data-stu-id="25e15-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="25e15-131">Zpětná lomítka jsou interpretována doslovně, pokud bezprostředně nepředcházejí před uvozovkou.</span><span class="sxs-lookup"><span data-stu-id="25e15-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="25e15-132">Pokud sudý počet zpětných lomítk následuje dvojité uvozovky, `argv` jedno zpětné lomítko je vložen do pole pro každý pár zpětných lomítka a dvojité uvozovky je interpretován jako řetězec oddělovač.</span><span class="sxs-lookup"><span data-stu-id="25e15-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="25e15-133">Pokud lichý počet zpětných lomítk následuje dvojité uvozovky, `argv` jedno zpětné lomítko je vložen do pole pro každý pár zpětných lomítka a dvojité uvozovky je "uvozena" zbývající zpětné lomítko.</span><span class="sxs-lookup"><span data-stu-id="25e15-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="25e15-134">To způsobí, že literál dvojité uvozovky (") které mají být přidány v `argv`.</span><span class="sxs-lookup"><span data-stu-id="25e15-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="25e15-135">Ukázkové příkazové řádky pro kompilátor jazyka C#</span><span class="sxs-lookup"><span data-stu-id="25e15-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="25e15-136">Zkompiluje *File.cs* produkující *soubor File.exe*:</span><span class="sxs-lookup"><span data-stu-id="25e15-136">Compiles *File.cs* producing *File.exe*:</span></span>

  ```console
  csc File.cs
  ```

- <span data-ttu-id="25e15-137">Zkompiluje *File.cs* produkci *souboru File.dll*:</span><span class="sxs-lookup"><span data-stu-id="25e15-137">Compiles *File.cs* producing *File.dll*:</span></span>

  ```console
  csc -target:library File.cs
  ```

- <span data-ttu-id="25e15-138">Zkompiluje *File.cs* a vytvoří *my.exe*:</span><span class="sxs-lookup"><span data-stu-id="25e15-138">Compiles *File.cs* and creates *My.exe*:</span></span>

  ```console
  csc -out:My.exe File.cs
  ```

- <span data-ttu-id="25e15-139">Zkompiluje všechny soubory Jazyka C# v aktuálním adresáři s povolenými optimalizacemi a definuje symbol LADĚNÍ.</span><span class="sxs-lookup"><span data-stu-id="25e15-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="25e15-140">Výstupem je *Soubor2.exe*:</span><span class="sxs-lookup"><span data-stu-id="25e15-140">The output is *File2.exe*:</span></span>

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- <span data-ttu-id="25e15-141">Zkompiluje všechny soubory Jazyka C# v aktuálním adresáři, který vytváří ladicí verzi *souboru File2.dll*.</span><span class="sxs-lookup"><span data-stu-id="25e15-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="25e15-142">Nezobrazuje se žádné logo ani varování:</span><span class="sxs-lookup"><span data-stu-id="25e15-142">No logo and no warnings are displayed:</span></span>

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- <span data-ttu-id="25e15-143">Zkompiluje všechny soubory Jazyka C# v aktuálním adresáři do *souboru Something.xyz* (dll):</span><span class="sxs-lookup"><span data-stu-id="25e15-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="25e15-144">Rozdíly mezi kompilátorem jazyka C# a výstupem kompilátoru jazyka C++</span><span class="sxs-lookup"><span data-stu-id="25e15-144">Differences between C# compiler and C++ compiler output</span></span>

<span data-ttu-id="25e15-145">Neexistují žádné soubory objektu (*obj*) vytvořené v důsledku vyvolání kompilátoru Jazyka C#; výstupní soubory jsou vytvářeny přímo.</span><span class="sxs-lookup"><span data-stu-id="25e15-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="25e15-146">V důsledku toho kompilátor jazyka C# nepotřebuje propojovací ho.</span><span class="sxs-lookup"><span data-stu-id="25e15-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="25e15-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="25e15-147">See also</span></span>

- [<span data-ttu-id="25e15-148">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="25e15-148">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="25e15-149">Možnosti kompilátoru C# (abecední pořadí)</span><span class="sxs-lookup"><span data-stu-id="25e15-149">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="25e15-150">Možnosti kompilátoru C# uvedené podle kategorie</span><span class="sxs-lookup"><span data-stu-id="25e15-150">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="25e15-151">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="25e15-151">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="25e15-152">Argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="25e15-152">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="25e15-153">Jak zobrazit argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="25e15-153">How to display command-line arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="25e15-154">Návratové hodnoty Main()</span><span class="sxs-lookup"><span data-stu-id="25e15-154">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
