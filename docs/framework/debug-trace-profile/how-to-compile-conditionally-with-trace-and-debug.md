---
title: "Postupy: Podmíněná kompilace pomocí atributu Trace a Debug"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3907888ebcda9c5c6c498cbff39956391f7e213
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="d5e0a-102">Postupy: Podmíněná kompilace pomocí atributu Trace a Debug</span><span class="sxs-lookup"><span data-stu-id="d5e0a-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="d5e0a-103">Při ladění aplikace během vývoje, vaše trasování a ladění výstupu přejít do okna výstupu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="d5e0a-104">Zahrnout trasování funkce nasazené aplikace, musí však zkompilovat instrumentovaného aplikací s **trasování** kompilátoru direktiva povolena.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="d5e0a-105">To umožňuje trasování kódu ke kompilaci do verzi vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="d5e0a-106">Pokud nepovolíte **trasování** direktivy, všechny trasování kódu se ignoruje při kompilaci a není součástí spustitelného kódu, kterou chcete nasadit.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="d5e0a-107">Trasování a ladění metody přidruženy podmíněné atributy.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="d5e0a-108">Například pokud podmíněný atribut pro trasování je **true**, jsou součástí sestavení (Soubor kompilované .exe nebo .dll); všechny příkazy trasování, pokud **trasování** podmíněný atribut je **false**, nejsou zahrnuty trasovacích příkazů.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="d5e0a-109">Může mít buď **trasování** nebo **ladění** podmíněný atribut zapnuli pro sestavení, nebo obojí nebo ani jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="d5e0a-110">Proto existují čtyři typy sestavení: **ladění**, **trasování**, oba, nebo žádný z nich.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="d5e0a-111">Některé verze sestavení pro produkční nasazení může obsahovat ani; Většina ladění sestavení obsahovat obě.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="d5e0a-112">Můžete zadat nastavení kompilátoru pro vaši aplikaci několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="d5e0a-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
-   <span data-ttu-id="d5e0a-113">Stránky vlastností</span><span class="sxs-lookup"><span data-stu-id="d5e0a-113">The property pages</span></span>  
  
-   <span data-ttu-id="d5e0a-114">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="d5e0a-114">The command line</span></span>  
  
-   <span data-ttu-id="d5e0a-115">**#CONST** (pro Visual Basic) a **#define** (pro jazyk C#)</span><span class="sxs-lookup"><span data-stu-id="d5e0a-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="d5e0a-116">Chcete-li změnit nastavení kompilace z dialogového okna Vlastnosti stránky</span><span class="sxs-lookup"><span data-stu-id="d5e0a-116">To change compile settings from the property pages dialog box</span></span>  
  
1.  <span data-ttu-id="d5e0a-117">Klikněte pravým tlačítkem na uzel projektu v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="d5e0a-118">Zvolte **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    -   <span data-ttu-id="d5e0a-119">V jazyce Visual Basic, klikněte na tlačítko **zkompilovat** v levém podokně na stránku vlastností a potom klikněte na tlačítko **Upřesnit možnosti kompilace** tlačítko pro zobrazení **Upřesnit nastavení kompilátoru**dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="d5e0a-120">Zaškrtněte políčka pro kompilátor – nastavení, které chcete povolit.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="d5e0a-121">Zrušte zaškrtnutí políčka pro nastavení, které chcete zakázat.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    -   <span data-ttu-id="d5e0a-122">V jazyce C#, klikněte **sestavení** v levém podokně na stránku vlastností a potom zaškrtněte políčka pro kompilátor – nastavení, které chcete povolit.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="d5e0a-123">Zrušte zaškrtnutí políčka pro nastavení, které chcete zakázat.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="d5e0a-124">Ke kompilaci instrumentovány v kódu pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="d5e0a-124">To compile instrumented code using the command line</span></span>  
  
1.  <span data-ttu-id="d5e0a-125">Nastavte podmíněný kompilátoru přepínač na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="d5e0a-126">Kompilátor bude zahrnovat trasování nebo ladění kódu v spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="d5e0a-127">Například následující pokyn kompilátoru zadat na příkazovém řádku bude zahrnovat trasování kódu v kompilovaném spustitelný soubor:</span><span class="sxs-lookup"><span data-stu-id="d5e0a-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="d5e0a-128">V jazyce Visual Basic: **Vbc – /r:System.dll /d:TRACE = TRUE /d:DEBUG = FALSE MyApplication.vb**</span><span class="sxs-lookup"><span data-stu-id="d5e0a-128">For Visual Basic: **vbc /r:System.dll /d:TRACE=TRUE /d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="d5e0a-129">Pro jazyk C#: **csc /r:System.dll /d:TRACE /d:DEBUG = FALSE MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="d5e0a-129">For C#: **csc /r:System.dll /d:TRACE /d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d5e0a-130">Chcete-li kompilovat více než jeden soubor aplikace, ponechte prázdné místo mezi názvy souborů, například **MyApplication1.vb MyApplication2.vb MyApplication3.vb** nebo **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="d5e0a-131">Význam direktivy podmíněné kompilace použít v uvedených příkladech je následující:</span><span class="sxs-lookup"><span data-stu-id="d5e0a-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="d5e0a-132">– Direktiva</span><span class="sxs-lookup"><span data-stu-id="d5e0a-132">Directive</span></span>|<span data-ttu-id="d5e0a-133">Význam</span><span class="sxs-lookup"><span data-stu-id="d5e0a-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="d5e0a-134">Visual Basic – kompilátor</span><span class="sxs-lookup"><span data-stu-id="d5e0a-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="d5e0a-135">Kompilátor jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d5e0a-135">C# compiler</span></span>|  
    |`/r:`|<span data-ttu-id="d5e0a-136">Odkazuje na externí sestavení (EXE nebo DLL)</span><span class="sxs-lookup"><span data-stu-id="d5e0a-136">References an external assembly (EXE or DLL)</span></span>|  
    |`/d:`|<span data-ttu-id="d5e0a-137">Definuje symbol Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="d5e0a-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="d5e0a-138">Je nutné zadat trasování nebo ladění se velká písmena.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="d5e0a-139">Další informace o příkazech Podmíněná kompilace zadejte `vbc /?` (pro Visual Basic) nebo `csc /?` (pro jazyk C#) na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="d5e0a-140">Další informace najdete v tématu [sestavení z příkazového řádku](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) nebo [volání kompilátoru příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d5e0a-140">For more information, see [Building from the Command Line](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="d5e0a-141">K provedení Podmíněná kompilace pomocí #CONST nebo #define</span><span class="sxs-lookup"><span data-stu-id="d5e0a-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1.  <span data-ttu-id="d5e0a-142">Zadejte příkaz vhodné pro programovací jazyk v horní části souboru se zdrojovým kódem.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="d5e0a-143">Jazyk</span><span class="sxs-lookup"><span data-stu-id="d5e0a-143">Language</span></span>|<span data-ttu-id="d5e0a-144">Příkaz</span><span class="sxs-lookup"><span data-stu-id="d5e0a-144">Statement</span></span>|<span data-ttu-id="d5e0a-145">Výsledek</span><span class="sxs-lookup"><span data-stu-id="d5e0a-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="d5e0a-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="d5e0a-146">**Visual Basic**</span></span>|<span data-ttu-id="d5e0a-147">**#CONST trasování = true**</span><span class="sxs-lookup"><span data-stu-id="d5e0a-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="d5e0a-148">Umožňuje trasování</span><span class="sxs-lookup"><span data-stu-id="d5e0a-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="d5e0a-149">**#CONST trasování = false**</span><span class="sxs-lookup"><span data-stu-id="d5e0a-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="d5e0a-150">Zakáže trasování</span><span class="sxs-lookup"><span data-stu-id="d5e0a-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="d5e0a-151">**#CONST ladění = true**</span><span class="sxs-lookup"><span data-stu-id="d5e0a-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="d5e0a-152">Povolí režim ladění</span><span class="sxs-lookup"><span data-stu-id="d5e0a-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="d5e0a-153">**#CONST ladění = false**</span><span class="sxs-lookup"><span data-stu-id="d5e0a-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="d5e0a-154">Zakáže ladění</span><span class="sxs-lookup"><span data-stu-id="d5e0a-154">Disables debugging</span></span>|  
    |<span data-ttu-id="d5e0a-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="d5e0a-155">**C#**</span></span>|<span data-ttu-id="d5e0a-156">**#define trasování**</span><span class="sxs-lookup"><span data-stu-id="d5e0a-156">**#define TRACE**</span></span>|<span data-ttu-id="d5e0a-157">Umožňuje trasování</span><span class="sxs-lookup"><span data-stu-id="d5e0a-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="d5e0a-158">**#undef trasování**</span><span class="sxs-lookup"><span data-stu-id="d5e0a-158">**#undef TRACE**</span></span>|<span data-ttu-id="d5e0a-159">Zakáže trasování</span><span class="sxs-lookup"><span data-stu-id="d5e0a-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="d5e0a-160">**#define ladění**</span><span class="sxs-lookup"><span data-stu-id="d5e0a-160">**#define DEBUG**</span></span>|<span data-ttu-id="d5e0a-161">Povolí režim ladění</span><span class="sxs-lookup"><span data-stu-id="d5e0a-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="d5e0a-162">**#undef ladění**</span><span class="sxs-lookup"><span data-stu-id="d5e0a-162">**#undef DEBUG**</span></span>|<span data-ttu-id="d5e0a-163">Zakáže ladění</span><span class="sxs-lookup"><span data-stu-id="d5e0a-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="d5e0a-164">Chcete-li zakázat trasování nebo ladění</span><span class="sxs-lookup"><span data-stu-id="d5e0a-164">To disable tracing or debugging</span></span>  
  
1.  <span data-ttu-id="d5e0a-165">Direktivy kompilátoru odstraňte z vašeho zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-165">Delete the compiler directive from your source code.</span></span>  
  
     <span data-ttu-id="d5e0a-166">\-nebo –</span><span class="sxs-lookup"><span data-stu-id="d5e0a-166">\- or -</span></span>  
  
2.  <span data-ttu-id="d5e0a-167">Komentář – direktiva kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-167">Comment out the compiler directive.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d5e0a-168">Jakmile budete připraveni k sestavení, můžete buď zvolit **sestavení** z **sestavení** nabídky, nebo pomocí příkazového řádku, ale bez zadání **d:** k definování podmíněného kompilace symboly.</span><span class="sxs-lookup"><span data-stu-id="d5e0a-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e0a-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5e0a-169">See Also</span></span>  
 [<span data-ttu-id="d5e0a-170">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="d5e0a-170">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [<span data-ttu-id="d5e0a-171">Postupy: vytváření, inicializace a konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="d5e0a-171">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [<span data-ttu-id="d5e0a-172">Trasování – přepínače</span><span class="sxs-lookup"><span data-stu-id="d5e0a-172">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="d5e0a-173">Trasování – moduly naslouchání</span><span class="sxs-lookup"><span data-stu-id="d5e0a-173">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [<span data-ttu-id="d5e0a-174">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="d5e0a-174">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [<span data-ttu-id="d5e0a-175">Postupy: nastavení proměnných prostředí pro příkazový řádek sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d5e0a-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 [<span data-ttu-id="d5e0a-176">Postupy: volání kompilátoru příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="d5e0a-176">How to: Invoke the Command-Line Compiler</span></span>](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
