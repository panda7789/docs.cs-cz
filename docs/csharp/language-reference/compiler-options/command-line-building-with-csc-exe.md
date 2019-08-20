---
title: Sestavení příkazového řádku pomocí CSc. exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 54306c79bc2856996925756ee4261fbe67692aea
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606974"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="2c9d3-102">Sestavení příkazového řádku pomocí CSc. exe</span><span class="sxs-lookup"><span data-stu-id="2c9d3-102">Command-line build with csc.exe</span></span>
<span data-ttu-id="2c9d3-103">C# Kompilátor můžete vyvolat zadáním názvu spustitelného souboru (*CSc. exe*) na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="2c9d3-104">Použijete-li okno **Developer Command Prompt pro sadu Visual Studio** , jsou pro vás nastaveny všechny potřebné proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="2c9d3-105">Informace o tom, jak získat přístup k tomuto nástroji, naleznete v tématu [Developer Command Prompt pro Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) .</span><span class="sxs-lookup"><span data-stu-id="2c9d3-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span> 

<span data-ttu-id="2c9d3-106">Používáte-li standardní okno příkazového řádku, je nutné před spuštěním souboru *CSc. exe* z libovolného podadresáře v počítači upravit cestu.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="2c9d3-107">Také je nutné spustit *vsvars32. bat* pro nastavení příslušných proměnných prostředí pro podporu sestavení příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="2c9d3-108">Další informace o *vsvars32. bat*, včetně pokynů pro jeho vyhledání a spuštění, najdete v tématu [How to: Nastavení proměnných prostředí pro příkazový řádek](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to: Set Environment Variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="2c9d3-109">Pokud pracujete na počítači, který má pouze sadu Windows Software Development Kit (SDK), můžete použít C# kompilátor na **příkazovém řádku sady SDK**, který otevřete z možnosti nabídky **Microsoft .NET Framework SDK** .</span><span class="sxs-lookup"><span data-stu-id="2c9d3-109">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="2c9d3-110">Nástroj MSBuild můžete také použít k programovému sestavování C# programů.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="2c9d3-111">Další informace najdete v tématu [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="2c9d3-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="2c9d3-112">Spustitelný soubor *CSc. exe* je obvykle umístěný ve složce Microsoft. NET\Framework\\ *\<verze >* v adresáři *Windows* .</span><span class="sxs-lookup"><span data-stu-id="2c9d3-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="2c9d3-113">Jeho umístění se může lišit v závislosti na přesné konfiguraci konkrétního počítače.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="2c9d3-114">Pokud je v počítači nainstalována více než jedna verze .NET Framework, najdete více verzí tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="2c9d3-115">Další informace o těchto instalacích naleznete v tématu [How to: Určete, které verze .NET Framework jsou nainstalovány](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="2c9d3-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
>  <span data-ttu-id="2c9d3-116">Při sestavování projektu pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio můžete zobrazit příkaz **CSC** a jeho přidružené možnosti kompilátoru v okně **výstup** .</span><span class="sxs-lookup"><span data-stu-id="2c9d3-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="2c9d3-117">Chcete-li zobrazit tyto informace, postupujte podle [pokynů v tématu Postupy: Umožňuje zobrazit, Uložit a nakonfigurovat soubory](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) protokolu sestavení pro změnu úrovně podrobností dat protokolu na **normální** nebo **podrobné**.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="2c9d3-118">Po opětovném sestavení projektu vyhledejte v okně **výstup** pro **CSC** , abyste našli vyvolání C# kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="2c9d3-119">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="2c9d3-119">**In this topic**</span></span>

- [<span data-ttu-id="2c9d3-120">Pravidla pro syntaxi příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2c9d3-120">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="2c9d3-121">Ukázkové příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="2c9d3-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="2c9d3-122">Rozdíly mezi C# kompilátorem C++ a výstupem kompilátoru</span><span class="sxs-lookup"><span data-stu-id="2c9d3-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="2c9d3-123">Pravidla pro syntaxi příkazového řádku pro C# kompilátor</span><span class="sxs-lookup"><span data-stu-id="2c9d3-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="2c9d3-124">C# Kompilátor při interpretaci argumentů uvedených na příkazovém řádku operačního systému používá následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="2c9d3-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="2c9d3-125">Argumenty jsou odděleny prázdným znakem, což je mezera nebo karta.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="2c9d3-126">Znak stříšky (^) není rozpoznán jako řídicí znak nebo oddělovač.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="2c9d3-127">Znak je zpracován analyzátorem příkazového řádku v operačním systému předtím, než se předává do `argv` pole v programu.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="2c9d3-128">Řetězec uzavřený v dvojitých uvozovkách ("String") je interpretován jako jeden argument bez ohledu na prázdné znaky, které jsou obsaženy v.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="2c9d3-129">V argumentu může být vložen řetězec v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="2c9d3-130">Dvojitá uvozovka začínající zpětným lomítkem (\\") je interpretována jako literální znak dvojité uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="2c9d3-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="2c9d3-131">Zpětná lomítka jsou interpretována doslova, pokud bezprostředně nepředchází uvozovky.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="2c9d3-132">Je-li sudý počet zpětných lomítek následován znakem dvojitých uvozovek, jedno zpětné lomítko je vloženo do `argv` pole pro každý pár zpětných lomítek a Dvojitá uvozovka je interpretována jako oddělovač řetězců.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="2c9d3-133">Je-li lichý počet zpětných lomítek následován znakem dvojitých uvozovek, jedno zpětné lomítko je umístěno v `argv` poli pro každý pár zpětných lomítek a dvojité uvozovky je "Escape" pomocí zbývajícího zpětného lomítka.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="2c9d3-134">To způsobí, že se literální dvojité uvozovky (") přidají do `argv`.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="2c9d3-135">Ukázkové příkazové řádky pro C# kompilátor</span><span class="sxs-lookup"><span data-stu-id="2c9d3-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="2c9d3-136">Zkompiluje *File.cs* vytvářející *soubor. exe*:</span><span class="sxs-lookup"><span data-stu-id="2c9d3-136">Compiles *File.cs* producing *File.exe*:</span></span>

```console
csc File.cs 
```

- <span data-ttu-id="2c9d3-137">Zkompiluje *File.cs* produkující *soubor. dll*:</span><span class="sxs-lookup"><span data-stu-id="2c9d3-137">Compiles *File.cs* producing *File.dll*:</span></span>

```console
csc -target:library File.cs
```

- <span data-ttu-id="2c9d3-138">Zkompiluje *File.cs* a vytvoří *My. exe*:</span><span class="sxs-lookup"><span data-stu-id="2c9d3-138">Compiles *File.cs* and creates *My.exe*:</span></span>

```console
csc -out:My.exe File.cs
```

- <span data-ttu-id="2c9d3-139">Zkompiluje všechny C# soubory v aktuálním adresáři s povolenými optimalizacemi a definuje symbol ladění.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="2c9d3-140">Výstup je *Soubor2. exe*:</span><span class="sxs-lookup"><span data-stu-id="2c9d3-140">The output is *File2.exe*:</span></span>

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- <span data-ttu-id="2c9d3-141">Zkompiluje všechny C# soubory v aktuálním adresáři, ve kterém je vyprodukována ladicí verze souboru *Soubor2. dll*.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="2c9d3-142">Nezobrazují se žádné logo a žádná upozornění:</span><span class="sxs-lookup"><span data-stu-id="2c9d3-142">No logo and no warnings are displayed:</span></span>

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- <span data-ttu-id="2c9d3-143">Zkompiluje všechny C# soubory v aktuálním adresáři na *něco. xyz* (knihovna DLL):</span><span class="sxs-lookup"><span data-stu-id="2c9d3-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="2c9d3-144">Rozdíly mezi C# kompilátorem C++ a výstupem kompilátoru</span><span class="sxs-lookup"><span data-stu-id="2c9d3-144">Differences between C# compiler and C++ compiler output</span></span>
<span data-ttu-id="2c9d3-145">V důsledku vyvolání C# kompilátoru nejsou vytvořeny žádné soubory objektů ( *. obj*). výstupní soubory jsou vytvářeny přímo.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="2c9d3-146">V důsledku toho C# kompilátor nepotřebuje linker.</span><span class="sxs-lookup"><span data-stu-id="2c9d3-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c9d3-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c9d3-147">See also</span></span>

- [<span data-ttu-id="2c9d3-148">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2c9d3-148">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2c9d3-149">Možnosti kompilátoru jazyka C# (abecední pořadí)</span><span class="sxs-lookup"><span data-stu-id="2c9d3-149">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="2c9d3-150">Možnosti kompilátoru jazyka C# uvedené podle kategorie</span><span class="sxs-lookup"><span data-stu-id="2c9d3-150">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="2c9d3-151">Argumenty Main() a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2c9d3-151">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="2c9d3-152">Argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2c9d3-152">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="2c9d3-153">Postupy: Zobrazit argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2c9d3-153">How to: Display Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="2c9d3-154">Návratové hodnoty Main()</span><span class="sxs-lookup"><span data-stu-id="2c9d3-154">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
