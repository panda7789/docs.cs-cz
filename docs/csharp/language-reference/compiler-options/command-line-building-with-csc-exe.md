---
description: Sestavení příkazového řádku s csc.exe
title: Sestavení příkazového řádku s csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 9ffd164602862fce7f5e4f0982d3eda7cb403e60
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125927"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="a9338-103">Sestavení příkazového řádku s csc.exe</span><span class="sxs-lookup"><span data-stu-id="a9338-103">Command-line build with csc.exe</span></span>

<span data-ttu-id="a9338-104">Kompilátor jazyka C# lze vyvolat zadáním názvu spustitelného souboru (*csc.exe*) na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="a9338-104">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="a9338-105">Použijete-li okno **Developer Command Prompt pro sadu Visual Studio** , jsou pro vás nastaveny všechny potřebné proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="a9338-105">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="a9338-106">Informace o tom, jak získat přístup k tomuto nástroji, naleznete v tématu [Developer Command Prompt pro Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) .</span><span class="sxs-lookup"><span data-stu-id="a9338-106">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span>

<span data-ttu-id="a9338-107">Pokud používáte standardní okno příkazového řádku, musíte upravit cestu, abyste mohli *csc.exe* vyvolat z libovolného podadresáře v počítači.</span><span class="sxs-lookup"><span data-stu-id="a9338-107">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="a9338-108">Je také nutné spustit *VsDevCmd.bat* pro nastavení příslušných proměnných prostředí pro podporu sestavení příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a9338-108">You also must run *VsDevCmd.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="a9338-109">Další informace o *VsDevCmd.bat*, včetně pokynů pro vyhledání a spuštění, naleznete v tématu [jak nastavit proměnné prostředí pro příkazový řádek sady Visual Studio](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="a9338-109">For more information about *VsDevCmd.bat*, including instructions for how to find and run it, see [How to set environment variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="a9338-110">Pokud pracujete na počítači, který má pouze sadu Windows Software Development Kit (SDK), můžete použít kompilátor jazyka C# na příkazovém **řádku sady SDK**, který otevřete z možnosti nabídky **Microsoft .NET Framework SDK** .</span><span class="sxs-lookup"><span data-stu-id="a9338-110">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="a9338-111">Nástroj MSBuild můžete také použít k programovému sestavení programů v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="a9338-111">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="a9338-112">Další informace najdete v tématu [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="a9338-112">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="a9338-113">Spustitelný soubor *csc.exe* obvykle je umístěný ve složce Microsoft. NET\Framework \\ *\<Version>* v adresáři *Windows* .</span><span class="sxs-lookup"><span data-stu-id="a9338-113">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="a9338-114">Jeho umístění se může lišit v závislosti na přesné konfiguraci konkrétního počítače.</span><span class="sxs-lookup"><span data-stu-id="a9338-114">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="a9338-115">Pokud je v počítači nainstalována více než jedna verze .NET Framework, najdete více verzí tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="a9338-115">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="a9338-116">Další informace o těchto instalacích naleznete v tématu [How to: Určete, které verze .NET Framework jsou nainstalovány](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="a9338-116">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
> <span data-ttu-id="a9338-117">Při sestavování projektu pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio můžete zobrazit příkaz **CSC** a jeho přidružené možnosti kompilátoru v okně **výstup** .</span><span class="sxs-lookup"><span data-stu-id="a9338-117">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="a9338-118">Chcete-li zobrazit tyto informace, postupujte podle pokynů v tématu [Postup: zobrazení, uložení a konfigurace souborů protokolu sestavení](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) pro změnu úrovně podrobností dat protokolu na **normální** nebo **podrobné**.</span><span class="sxs-lookup"><span data-stu-id="a9338-118">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="a9338-119">Po opětovném sestavení projektu vyhledejte v okně **výstup** pro **CSC** , aby bylo nalezeno vyvolání kompilátoru jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="a9338-119">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="a9338-120">**V tomto tématu**</span><span class="sxs-lookup"><span data-stu-id="a9338-120">**In this topic**</span></span>

- [<span data-ttu-id="a9338-121">Pravidla pro syntaxi příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a9338-121">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="a9338-122">Ukázkové příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="a9338-122">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="a9338-123">Rozdíly mezi kompilátorem C# a výstupem kompilátoru C++</span><span class="sxs-lookup"><span data-stu-id="a9338-123">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="a9338-124">Pravidla pro syntaxi příkazového řádku pro kompilátor jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a9338-124">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="a9338-125">Kompilátor jazyka C# při interpretaci argumentů uvedených na příkazovém řádku operačního systému používá následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="a9338-125">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="a9338-126">Argumenty jsou odděleny prázdným znakem, což je mezera nebo karta.</span><span class="sxs-lookup"><span data-stu-id="a9338-126">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="a9338-127">Znak stříšky (^) není rozpoznán jako řídicí znak nebo oddělovač.</span><span class="sxs-lookup"><span data-stu-id="a9338-127">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="a9338-128">Znak je zpracován analyzátorem příkazového řádku v operačním systému předtím, než se předává do `argv` pole v programu.</span><span class="sxs-lookup"><span data-stu-id="a9338-128">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="a9338-129">Řetězec uzavřený v dvojitých uvozovkách ("String") je interpretován jako jeden argument bez ohledu na prázdné znaky, které jsou obsaženy v.</span><span class="sxs-lookup"><span data-stu-id="a9338-129">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="a9338-130">V argumentu může být vložen řetězec v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="a9338-130">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="a9338-131">Dvojitá uvozovka začínající zpětným lomítkem ( \\ ") je interpretována jako literální znak dvojité uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="a9338-131">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="a9338-132">Zpětná lomítka jsou interpretována doslova, pokud bezprostředně nepředchází uvozovky.</span><span class="sxs-lookup"><span data-stu-id="a9338-132">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="a9338-133">Je-li sudý počet zpětných lomítek následován znakem dvojitých uvozovek, jedno zpětné lomítko je vloženo do `argv` pole pro každý pár zpětných lomítek a Dvojitá uvozovka je interpretována jako oddělovač řetězců.</span><span class="sxs-lookup"><span data-stu-id="a9338-133">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="a9338-134">Je-li lichý počet zpětných lomítek následován znakem dvojitých uvozovek, jedno zpětné lomítko je umístěno v `argv` poli pro každý pár zpětných lomítek a dvojité uvozovky je "Escape" pomocí zbývajícího zpětného lomítka.</span><span class="sxs-lookup"><span data-stu-id="a9338-134">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="a9338-135">To způsobí, že se literální dvojité uvozovky (") přidají do `argv` .</span><span class="sxs-lookup"><span data-stu-id="a9338-135">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="a9338-136">Ukázkové příkazové řádky pro kompilátor jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a9338-136">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="a9338-137">Zkompiluje *File.cs* produkující *File.exe*:</span><span class="sxs-lookup"><span data-stu-id="a9338-137">Compiles *File.cs* producing *File.exe*:</span></span>

  ```console
  csc File.cs
  ```

- <span data-ttu-id="a9338-138">Zkompiluje *File.cs* produkující *File.dll*:</span><span class="sxs-lookup"><span data-stu-id="a9338-138">Compiles *File.cs* producing *File.dll*:</span></span>

  ```console
  csc -target:library File.cs
  ```

- <span data-ttu-id="a9338-139">Zkompiluje *File.cs* a vytvoří *My.exe*:</span><span class="sxs-lookup"><span data-stu-id="a9338-139">Compiles *File.cs* and creates *My.exe*:</span></span>

  ```console
  csc -out:My.exe File.cs
  ```

- <span data-ttu-id="a9338-140">Zkompiluje všechny soubory v jazyce C# v aktuálním adresáři s povolenými optimalizacemi a definuje symbol ladění.</span><span class="sxs-lookup"><span data-stu-id="a9338-140">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="a9338-141">Výstup je *File2.exe*:</span><span class="sxs-lookup"><span data-stu-id="a9338-141">The output is *File2.exe*:</span></span>

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- <span data-ttu-id="a9338-142">Zkompiluje všechny soubory v jazyce C# v aktuálním adresáři, ve kterém je vyprodukována ladicí verze *File2.dll*.</span><span class="sxs-lookup"><span data-stu-id="a9338-142">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="a9338-143">Nezobrazují se žádné logo a žádná upozornění:</span><span class="sxs-lookup"><span data-stu-id="a9338-143">No logo and no warnings are displayed:</span></span>

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- <span data-ttu-id="a9338-144">Zkompiluje všechny soubory v jazyce C# v aktuálním adresáři do souboru *. xyz* (knihovna DLL):</span><span class="sxs-lookup"><span data-stu-id="a9338-144">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="a9338-145">Rozdíly mezi kompilátorem C# a výstupem kompilátoru C++</span><span class="sxs-lookup"><span data-stu-id="a9338-145">Differences between C# compiler and C++ compiler output</span></span>

<span data-ttu-id="a9338-146">Neexistují žádné soubory objektů (*. obj*) vytvořené v důsledku vyvolání kompilátoru jazyka C#; výstupní soubory jsou vytvářeny přímo.</span><span class="sxs-lookup"><span data-stu-id="a9338-146">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="a9338-147">V důsledku toho kompilátor C# nepotřebuje linker.</span><span class="sxs-lookup"><span data-stu-id="a9338-147">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9338-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9338-148">See also</span></span>

- [<span data-ttu-id="a9338-149">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="a9338-149">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a9338-150">Možnosti kompilátoru C# (abecední pořadí)</span><span class="sxs-lookup"><span data-stu-id="a9338-150">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="a9338-151">Možnosti kompilátoru C# uvedené podle kategorie</span><span class="sxs-lookup"><span data-stu-id="a9338-151">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="a9338-152">Argumenty Main () a příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a9338-152">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="a9338-153">Argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a9338-153">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="a9338-154">Jak zobrazit argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a9338-154">How to display command-line arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="a9338-155">Návratové hodnoty Main()</span><span class="sxs-lookup"><span data-stu-id="a9338-155">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
