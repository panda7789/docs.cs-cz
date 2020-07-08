---
title: 'Postupy: Podmíněná kompilace pomocí atributu Trace a Debug'
description: Přečtěte si, jak podmíněně kompilovat pomocí trasování a ladění podmíněné atributy při kompilování aplikace .NET.
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
ms.openlocfilehash: 8758b793866ec0317f91d636476d33bd001ddd78
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051217"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="10781-103">Postupy: Podmíněná kompilace pomocí atributu Trace a Debug</span><span class="sxs-lookup"><span data-stu-id="10781-103">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="10781-104">Při ladění aplikace během vývoje přejde výstup trasování i ladění do okna výstup v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="10781-104">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="10781-105">Chcete-li však do nasazené aplikace zahrnout funkce trasování, je nutné zkompilovat vaše instrumentované aplikace s povolenou direktivou překladače **trasování** .</span><span class="sxs-lookup"><span data-stu-id="10781-105">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="10781-106">To umožňuje zkompilovat kód pro vydanou verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="10781-106">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="10781-107">Pokud nepovolíte direktivu **Trace** , veškerý trasovací kód se během kompilace ignoruje a není zahrnutý do spustitelného kódu, který nasadíte.</span><span class="sxs-lookup"><span data-stu-id="10781-107">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="10781-108">Metody trasování i ladění mají přidružené podmíněné atributy.</span><span class="sxs-lookup"><span data-stu-id="10781-108">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="10781-109">Například pokud má podmíněný atribut pro trasování **hodnotu true**, všechny příkazy trasování jsou zahrnuty v rámci sestavení (zkompilovaného souboru. exe nebo. dll); Pokud má atribut **Trace** podmíněný **hodnotu false**, nejsou k dispozici příkazy TRACE.</span><span class="sxs-lookup"><span data-stu-id="10781-109">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="10781-110">Můžete mít pro sestavení zapnutý podmíněný atribut **trasování** nebo **ladění** , nebo ani jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="10781-110">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="10781-111">Proto existují čtyři typy sestavení: **Debug**, **Trace**, obojí nebo ani jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="10781-111">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="10781-112">Některá sestavení vydaných verzí pro produkční nasazení mohou obsahovat ani jednu z těchto možností: Většina sestavení ladění obsahuje obě.</span><span class="sxs-lookup"><span data-stu-id="10781-112">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="10781-113">Nastavení kompilátoru pro aplikaci můžete zadat několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="10781-113">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="10781-114">Stránky vlastností</span><span class="sxs-lookup"><span data-stu-id="10781-114">The property pages</span></span>  
  
- <span data-ttu-id="10781-115">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="10781-115">The command line</span></span>  
  
- <span data-ttu-id="10781-116">**#CONST** (pro Visual Basic) a **#define** (pro C#)</span><span class="sxs-lookup"><span data-stu-id="10781-116">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="10781-117">Změna nastavení kompilace z dialogového okna stránky vlastností</span><span class="sxs-lookup"><span data-stu-id="10781-117">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="10781-118">Klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="10781-118">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="10781-119">V místní nabídce vyberte možnost **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="10781-119">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="10781-120">V Visual Basic klikněte v levém podokně stránky vlastností na kartu **kompilovat** a pak klikněte na tlačítko **Upřesnit možnosti kompilace** . zobrazí se dialogové okno **Upřesnit nastavení kompilátoru** .</span><span class="sxs-lookup"><span data-stu-id="10781-120">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="10781-121">Zaškrtněte políčka pro nastavení kompilátoru, které chcete povolit.</span><span class="sxs-lookup"><span data-stu-id="10781-121">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="10781-122">Zrušte zaškrtnutí políček u nastavení, které chcete zakázat.</span><span class="sxs-lookup"><span data-stu-id="10781-122">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="10781-123">V jazyce C# klikněte v levém podokně stránky vlastností na kartu **sestavení** a potom zaškrtněte políčka pro nastavení kompilátoru, která chcete povolit.</span><span class="sxs-lookup"><span data-stu-id="10781-123">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="10781-124">Zrušte zaškrtnutí políček u nastavení, které chcete zakázat.</span><span class="sxs-lookup"><span data-stu-id="10781-124">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="10781-125">Kompilace instrumentované kódu pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="10781-125">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="10781-126">Nastavte podmíněný přepínač kompilátoru na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="10781-126">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="10781-127">Kompilátor bude obsahovat kód trasování nebo ladění ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="10781-127">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="10781-128">Například následující instrukce kompilátoru, která je zadána v příkazovém řádku, by zahrnovala váš kód trasování ve zkompilovaném spustitelném souboru:</span><span class="sxs-lookup"><span data-stu-id="10781-128">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="10781-129">Pro Visual Basic: **vbc -r:System.dll-d:TRACE = True-d:Debug = false MyApplication. vb**</span><span class="sxs-lookup"><span data-stu-id="10781-129">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="10781-130">Pro C#: **csc -r:System.dll-d:Trace-d:Debug = FALSE MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="10781-130">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="10781-131">Chcete-li zkompilovat více než jeden soubor aplikace, ponechte prázdné místo mezi názvy souborů, například **MyApplication1. vb MyApplication2. vb MyApplication3. vb** nebo **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="10781-131">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="10781-132">Význam direktiv podmíněné kompilace použitých ve výše uvedených příkladech je následující:</span><span class="sxs-lookup"><span data-stu-id="10781-132">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="10781-133">Směrnici</span><span class="sxs-lookup"><span data-stu-id="10781-133">Directive</span></span>|<span data-ttu-id="10781-134">Význam</span><span class="sxs-lookup"><span data-stu-id="10781-134">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="10781-135">Visual Basic – kompilátor</span><span class="sxs-lookup"><span data-stu-id="10781-135">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="10781-136">Kompilátor jazyka C#</span><span class="sxs-lookup"><span data-stu-id="10781-136">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="10781-137">Odkazuje na externí sestavení (EXE nebo DLL).</span><span class="sxs-lookup"><span data-stu-id="10781-137">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="10781-138">Definuje symbol podmíněné kompilace.</span><span class="sxs-lookup"><span data-stu-id="10781-138">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="10781-139">Je nutné provést trasování nebo ladění velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="10781-139">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="10781-140">Další informace o příkazech podmíněné kompilace získáte zadáním `vbc /?` příkazu (pro Visual Basic) nebo `csc /?` (pro jazyk C#) na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="10781-140">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="10781-141">Další informace naleznete v tématu [sestavování z příkazového řádku](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) nebo [vyvolání kompilátoru příkazového řádku](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="10781-141">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="10781-142">Provedení podmíněné kompilace pomocí #CONST nebo #define</span><span class="sxs-lookup"><span data-stu-id="10781-142">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="10781-143">Zadejte odpovídající příkaz pro programovací jazyk v horní části souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="10781-143">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="10781-144">Jazyk</span><span class="sxs-lookup"><span data-stu-id="10781-144">Language</span></span>|<span data-ttu-id="10781-145">Příkaz</span><span class="sxs-lookup"><span data-stu-id="10781-145">Statement</span></span>|<span data-ttu-id="10781-146">Výsledek</span><span class="sxs-lookup"><span data-stu-id="10781-146">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="10781-147">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="10781-147">**Visual Basic**</span></span>|<span data-ttu-id="10781-148">**#CONST TRACE = True**</span><span class="sxs-lookup"><span data-stu-id="10781-148">**#CONST TRACE = true**</span></span>|<span data-ttu-id="10781-149">Povolí trasování</span><span class="sxs-lookup"><span data-stu-id="10781-149">Enables tracing</span></span>|  
    ||<span data-ttu-id="10781-150">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="10781-150">**#CONST TRACE = false**</span></span>|<span data-ttu-id="10781-151">Zakáže trasování</span><span class="sxs-lookup"><span data-stu-id="10781-151">Disables tracing</span></span>|  
    ||<span data-ttu-id="10781-152">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="10781-152">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="10781-153">Povolí ladění</span><span class="sxs-lookup"><span data-stu-id="10781-153">Enables debugging</span></span>|  
    ||<span data-ttu-id="10781-154">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="10781-154">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="10781-155">Zakáže ladění.</span><span class="sxs-lookup"><span data-stu-id="10781-155">Disables debugging</span></span>|  
    |<span data-ttu-id="10781-156">**C#**</span><span class="sxs-lookup"><span data-stu-id="10781-156">**C#**</span></span>|<span data-ttu-id="10781-157">**TRASOVÁNÍ #define**</span><span class="sxs-lookup"><span data-stu-id="10781-157">**#define TRACE**</span></span>|<span data-ttu-id="10781-158">Povolí trasování</span><span class="sxs-lookup"><span data-stu-id="10781-158">Enables tracing</span></span>|  
    ||<span data-ttu-id="10781-159">**TRASOVÁNÍ #undef**</span><span class="sxs-lookup"><span data-stu-id="10781-159">**#undef TRACE**</span></span>|<span data-ttu-id="10781-160">Zakáže trasování</span><span class="sxs-lookup"><span data-stu-id="10781-160">Disables tracing</span></span>|  
    ||<span data-ttu-id="10781-161">**#define ladění**</span><span class="sxs-lookup"><span data-stu-id="10781-161">**#define DEBUG**</span></span>|<span data-ttu-id="10781-162">Povolí ladění</span><span class="sxs-lookup"><span data-stu-id="10781-162">Enables debugging</span></span>|  
    ||<span data-ttu-id="10781-163">**#undef ladění**</span><span class="sxs-lookup"><span data-stu-id="10781-163">**#undef DEBUG**</span></span>|<span data-ttu-id="10781-164">Zakáže ladění.</span><span class="sxs-lookup"><span data-stu-id="10781-164">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="10781-165">Zakázání trasování nebo ladění</span><span class="sxs-lookup"><span data-stu-id="10781-165">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="10781-166">Odstraní direktivu kompilátoru ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="10781-166">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="10781-167">\-ani</span><span class="sxs-lookup"><span data-stu-id="10781-167">\- or -</span></span>  
  
<span data-ttu-id="10781-168">Odkomentujte direktivu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="10781-168">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10781-169">Až budete připraveni kompilovat, můžete buď zvolit možnost **sestavit** z nabídky **sestavení** , nebo použít metodu příkazového řádku, ale bez zadání **d:** pro definování symbolů podmíněné kompilace.</span><span class="sxs-lookup"><span data-stu-id="10781-169">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10781-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="10781-170">See also</span></span>

- [<span data-ttu-id="10781-171">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="10781-171">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="10781-172">Postupy: Vytváření, inicializace a konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="10781-172">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="10781-173">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="10781-173">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="10781-174">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="10781-174">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="10781-175">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="10781-175">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="10781-176">Jak nastavit proměnné prostředí pro příkazový řádek sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10781-176">How to set environment variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="10781-177">Postupy: Volání kompilátoru příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="10781-177">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
