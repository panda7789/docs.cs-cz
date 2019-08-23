---
title: 'Postupy: Podmíněná kompilace pomocí atributu Trace a Debug'
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: df1f1c7e28464781a73a0939c3413f4c9d620d7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942383"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="46124-102">Postupy: Podmíněná kompilace pomocí atributu Trace a Debug</span><span class="sxs-lookup"><span data-stu-id="46124-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="46124-103">Při ladění aplikace během vývoje přejde výstup trasování i ladění do okna výstup v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46124-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="46124-104">Chcete-li však do nasazené aplikace zahrnout funkce trasování, je nutné zkompilovat vaše instrumentované aplikace s povolenou direktivou překladače **trasování** .</span><span class="sxs-lookup"><span data-stu-id="46124-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="46124-105">To umožňuje zkompilovat kód pro vydanou verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="46124-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="46124-106">Pokud nepovolíte direktivu **Trace** , veškerý trasovací kód se během kompilace ignoruje a není zahrnutý do spustitelného kódu, který nasadíte.</span><span class="sxs-lookup"><span data-stu-id="46124-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="46124-107">Metody trasování i ladění mají přidružené podmíněné atributy.</span><span class="sxs-lookup"><span data-stu-id="46124-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="46124-108">Například pokud má podmíněný atribut pro trasování **hodnotu true**, všechny příkazy trasování jsou zahrnuty v rámci sestavení (zkompilovaného souboru. exe nebo. dll); Pokud má atribut **Trace** podmíněný **hodnotu false**, nejsou k dispozici příkazy TRACE.</span><span class="sxs-lookup"><span data-stu-id="46124-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="46124-109">Můžete mít pro sestavení zapnutý podmíněný atribut **trasování** nebo **ladění** , nebo ani jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="46124-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="46124-110">Proto existují čtyři typy sestavení: **Ladění**, **trasování**, obojí nebo ani jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="46124-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="46124-111">Některá sestavení vydaných verzí pro produkční nasazení mohou obsahovat ani jednu z těchto možností: Většina sestavení ladění obsahuje obě.</span><span class="sxs-lookup"><span data-stu-id="46124-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="46124-112">Nastavení kompilátoru pro aplikaci můžete zadat několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="46124-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="46124-113">Stránky vlastností</span><span class="sxs-lookup"><span data-stu-id="46124-113">The property pages</span></span>  
  
- <span data-ttu-id="46124-114">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="46124-114">The command line</span></span>  
  
- <span data-ttu-id="46124-115">**#CONST** (pro Visual Basic) a **#define** (pro C#)</span><span class="sxs-lookup"><span data-stu-id="46124-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="46124-116">Změna nastavení kompilace z dialogového okna stránky vlastností</span><span class="sxs-lookup"><span data-stu-id="46124-116">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="46124-117">Klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="46124-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="46124-118">V místní nabídce vyberte možnost **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="46124-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="46124-119">V Visual Basic klikněte v levém podokně stránky vlastností na kartu **kompilovat** a pak klikněte na tlačítko **Upřesnit možnosti kompilace** . zobrazí se dialogové okno **Upřesnit nastavení kompilátoru** .</span><span class="sxs-lookup"><span data-stu-id="46124-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="46124-120">Zaškrtněte políčka pro nastavení kompilátoru, které chcete povolit.</span><span class="sxs-lookup"><span data-stu-id="46124-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="46124-121">Zrušte zaškrtnutí políček u nastavení, které chcete zakázat.</span><span class="sxs-lookup"><span data-stu-id="46124-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="46124-122">V C#klikněte na kartu **sestavení** v levém podokně stránky vlastností a zaškrtněte políčka pro nastavení kompilátoru, která chcete povolit.</span><span class="sxs-lookup"><span data-stu-id="46124-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="46124-123">Zrušte zaškrtnutí políček u nastavení, které chcete zakázat.</span><span class="sxs-lookup"><span data-stu-id="46124-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="46124-124">Kompilace instrumentované kódu pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="46124-124">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="46124-125">Nastavte podmíněný přepínač kompilátoru na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="46124-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="46124-126">Kompilátor bude obsahovat kód trasování nebo ladění ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="46124-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="46124-127">Například následující instrukce kompilátoru, která je zadána v příkazovém řádku, by zahrnovala váš kód trasování ve zkompilovaném spustitelném souboru:</span><span class="sxs-lookup"><span data-stu-id="46124-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="46124-128">Pro Visual Basic: **Vbc-r:System.dll-d:TRACE = True-d:Debug = false MyApplication. vb**</span><span class="sxs-lookup"><span data-stu-id="46124-128">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="46124-129">Pro C#: **CSC-r:System.dll-d:Trace-d:Debug = false MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="46124-129">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="46124-130">Chcete-li zkompilovat více než jeden soubor aplikace, ponechte prázdné místo mezi názvy souborů, například **MyApplication1. vb MyApplication2. vb MyApplication3. vb** nebo **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="46124-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="46124-131">Význam direktiv podmíněné kompilace použitých ve výše uvedených příkladech je následující:</span><span class="sxs-lookup"><span data-stu-id="46124-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="46124-132">– Direktiva</span><span class="sxs-lookup"><span data-stu-id="46124-132">Directive</span></span>|<span data-ttu-id="46124-133">Význam</span><span class="sxs-lookup"><span data-stu-id="46124-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="46124-134">Visual Basic – kompilátor</span><span class="sxs-lookup"><span data-stu-id="46124-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="46124-135">C#přepínač</span><span class="sxs-lookup"><span data-stu-id="46124-135">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="46124-136">Odkazuje na externí sestavení (EXE nebo DLL).</span><span class="sxs-lookup"><span data-stu-id="46124-136">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="46124-137">Definuje symbol podmíněné kompilace.</span><span class="sxs-lookup"><span data-stu-id="46124-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="46124-138">Je nutné provést trasování nebo ladění velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="46124-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="46124-139">Další informace o příkazech podmíněné kompilace získáte zadáním `vbc /?` příkazu (pro Visual Basic) `csc /?` nebo ( C#pro) v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="46124-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="46124-140">Další informace naleznete v tématu [sestavování z příkazového řádku](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) nebo [vyvolání kompilátoru příkazového řádku](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="46124-140">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="46124-141">Provedení podmíněné kompilace pomocí #CONST nebo #define</span><span class="sxs-lookup"><span data-stu-id="46124-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="46124-142">Zadejte odpovídající příkaz pro programovací jazyk v horní části souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="46124-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="46124-143">Jazyk</span><span class="sxs-lookup"><span data-stu-id="46124-143">Language</span></span>|<span data-ttu-id="46124-144">Příkaz</span><span class="sxs-lookup"><span data-stu-id="46124-144">Statement</span></span>|<span data-ttu-id="46124-145">Výsledek</span><span class="sxs-lookup"><span data-stu-id="46124-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="46124-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="46124-146">**Visual Basic**</span></span>|<span data-ttu-id="46124-147">**#CONST TRACE = True**</span><span class="sxs-lookup"><span data-stu-id="46124-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="46124-148">Povolí trasování</span><span class="sxs-lookup"><span data-stu-id="46124-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="46124-149">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="46124-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="46124-150">Zakáže trasování</span><span class="sxs-lookup"><span data-stu-id="46124-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="46124-151">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="46124-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="46124-152">Povolí ladění</span><span class="sxs-lookup"><span data-stu-id="46124-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="46124-153">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="46124-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="46124-154">Zakáže ladění.</span><span class="sxs-lookup"><span data-stu-id="46124-154">Disables debugging</span></span>|  
    |<span data-ttu-id="46124-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="46124-155">**C#**</span></span>|<span data-ttu-id="46124-156">**TRASOVÁNÍ #define**</span><span class="sxs-lookup"><span data-stu-id="46124-156">**#define TRACE**</span></span>|<span data-ttu-id="46124-157">Povolí trasování</span><span class="sxs-lookup"><span data-stu-id="46124-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="46124-158">**TRASOVÁNÍ #undef**</span><span class="sxs-lookup"><span data-stu-id="46124-158">**#undef TRACE**</span></span>|<span data-ttu-id="46124-159">Zakáže trasování</span><span class="sxs-lookup"><span data-stu-id="46124-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="46124-160">**#define ladění**</span><span class="sxs-lookup"><span data-stu-id="46124-160">**#define DEBUG**</span></span>|<span data-ttu-id="46124-161">Povolí ladění</span><span class="sxs-lookup"><span data-stu-id="46124-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="46124-162">**#undef ladění**</span><span class="sxs-lookup"><span data-stu-id="46124-162">**#undef DEBUG**</span></span>|<span data-ttu-id="46124-163">Zakáže ladění.</span><span class="sxs-lookup"><span data-stu-id="46124-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="46124-164">Zakázání trasování nebo ladění</span><span class="sxs-lookup"><span data-stu-id="46124-164">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="46124-165">Odstraní direktivu kompilátoru ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="46124-165">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="46124-166">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="46124-166">\- or -</span></span>  
  
<span data-ttu-id="46124-167">Odkomentujte direktivu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="46124-167">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46124-168">Až budete připraveni kompilovat, můžete buď zvolit možnost **sestavit** z nabídky **sestavení** , nebo použít metodu příkazového řádku, ale bez zadání **d:** pro definování symbolů podmíněné kompilace.</span><span class="sxs-lookup"><span data-stu-id="46124-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46124-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46124-169">See also</span></span>

- [<span data-ttu-id="46124-170">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="46124-170">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="46124-171">Postupy: Vytváření, inicializace a konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="46124-171">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="46124-172">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="46124-172">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="46124-173">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="46124-173">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [<span data-ttu-id="46124-174">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="46124-174">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="46124-175">Postupy: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="46124-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="46124-176">Postupy: Volání kompilátoru příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="46124-176">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
