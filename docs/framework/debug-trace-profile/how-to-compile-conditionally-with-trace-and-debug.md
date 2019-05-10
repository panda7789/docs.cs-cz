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
ms.openlocfilehash: c9b60cdef2af25ce712fcb2401b7f776d3add5b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64660402"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="0213a-102">Postupy: Podmíněná kompilace pomocí atributu Trace a Debug</span><span class="sxs-lookup"><span data-stu-id="0213a-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="0213a-103">Při ladění aplikace během vývoje, přejděte do okna výstup v sadě Visual Studio vaší trasování a ladění výstupu.</span><span class="sxs-lookup"><span data-stu-id="0213a-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="0213a-104">Ale musíte zahrnout funkce sledování nasazených aplikací, zkompilovat instrumentované aplikace s využitím **trasování** direktivy kompilátoru povolena.</span><span class="sxs-lookup"><span data-stu-id="0213a-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="0213a-105">To umožňuje trasování kódu se zkompiluje do verze vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="0213a-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="0213a-106">Pokud nepovolíte **trasování** direktiv, všechna trasování kódu je ignorována během kompilace a není součástí spustitelný kód, který nasadíte.</span><span class="sxs-lookup"><span data-stu-id="0213a-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="0213a-107">Trasování a ladění metody mají přiřazeny podmíněné atributy.</span><span class="sxs-lookup"><span data-stu-id="0213a-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="0213a-108">Například pokud podmíněný atribut pro trasování je **true**, všechny příkazy trasování jsou zahrnuty v rámci sestavení (soubor zkompilovaný .exe nebo .dll); Pokud **trasování** atribut conditional je **false**, příkazů trasování nejsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="0213a-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="0213a-109">Může mít buď **trasování** nebo **ladění** atribut conditional zapnuté pro sestavení, nebo obou nebo ani jeden.</span><span class="sxs-lookup"><span data-stu-id="0213a-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="0213a-110">Proto existují čtyři typy sestavení: **Ladění**, **trasování**obou nebo ani jedna.</span><span class="sxs-lookup"><span data-stu-id="0213a-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="0213a-111">Některé buildy vydaných verzí pro produkční nasazení mohou obsahovat ani; většinu ladicích sestavení obsahují.</span><span class="sxs-lookup"><span data-stu-id="0213a-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="0213a-112">Můžete zadat nastavení kompilátoru pro vaši aplikaci několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="0213a-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="0213a-113">Stránky vlastností</span><span class="sxs-lookup"><span data-stu-id="0213a-113">The property pages</span></span>  
  
- <span data-ttu-id="0213a-114">Příkazový řádek</span><span class="sxs-lookup"><span data-stu-id="0213a-114">The command line</span></span>  
  
- <span data-ttu-id="0213a-115">**#CONST** (pro jazyk Visual Basic) a **#define** (pro C#)</span><span class="sxs-lookup"><span data-stu-id="0213a-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="0213a-116">Chcete-li změnit nastavení kompilace z dialogového okna stránky vlastností</span><span class="sxs-lookup"><span data-stu-id="0213a-116">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="0213a-117">Klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="0213a-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="0213a-118">Zvolte **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="0213a-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="0213a-119">V jazyce Visual Basic, klikněte na tlačítko **kompilace** kartu v levém podokně na stránce vlastností a pak klikněte na tlačítko **Upřesnit možnosti kompilace** tlačítka pro zobrazení **pokročilé nastavení kompilátoru**dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="0213a-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="0213a-120">Zaškrtněte políčka pro nastavení kompilátoru, které chcete povolit.</span><span class="sxs-lookup"><span data-stu-id="0213a-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="0213a-121">Zrušte zaškrtnutí políček u nastavení, které chcete zakázat.</span><span class="sxs-lookup"><span data-stu-id="0213a-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="0213a-122">V C#, klikněte na tlačítko **sestavení** kartu v levém podokně na stránce vlastností a pak zaškrtněte políčka pro nastavení kompilátoru, které chcete povolit.</span><span class="sxs-lookup"><span data-stu-id="0213a-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="0213a-123">Zrušte zaškrtnutí políček u nastavení, které chcete zakázat.</span><span class="sxs-lookup"><span data-stu-id="0213a-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="0213a-124">Chcete-li zkompilovat instrumentované kódu pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="0213a-124">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="0213a-125">Nastavení přepínače podmíněné kompilátoru na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="0213a-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="0213a-126">Kompilátor bude zahrnovat trasování nebo ladění kódu ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="0213a-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="0213a-127">Například následující pokyn kompilátoru zadané na příkazovém řádku by zahrnout trasování kódu do zkompilovaného spustitelného souboru:</span><span class="sxs-lookup"><span data-stu-id="0213a-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="0213a-128">V jazyce Visual Basic: **Vbc –-r:System.dll -d: trasování = TRUE -d: DEBUG = FALSE MyApplication.vb**</span><span class="sxs-lookup"><span data-stu-id="0213a-128">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="0213a-129">Pro C#: **csc-r:System.dll -d: trasování -d: DEBUG = FALSE MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="0213a-129">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="0213a-130">Chcete-li zkompilovat více než jeden soubor aplikace, ponechte prázdné místo mezi názvy souborů, například **MyApplication1.vb MyApplication2.vb MyApplication3.vb** nebo **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="0213a-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="0213a-131">Význam direktivy podmíněné kompilace použité v předchozích příkladech je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0213a-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="0213a-132">– Direktiva</span><span class="sxs-lookup"><span data-stu-id="0213a-132">Directive</span></span>|<span data-ttu-id="0213a-133">Význam</span><span class="sxs-lookup"><span data-stu-id="0213a-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="0213a-134">Visual Basic – kompilátor</span><span class="sxs-lookup"><span data-stu-id="0213a-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="0213a-135">C#Kompilátor</span><span class="sxs-lookup"><span data-stu-id="0213a-135">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="0213a-136">Odkazuje na externí sestavení (EXE nebo DLL)</span><span class="sxs-lookup"><span data-stu-id="0213a-136">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="0213a-137">Definuje symbol podmíněné kompilace</span><span class="sxs-lookup"><span data-stu-id="0213a-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="0213a-138">Je nutné zadat trasování a ladění se velká písmena.</span><span class="sxs-lookup"><span data-stu-id="0213a-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="0213a-139">Další informace o příkazech podmíněné kompilace, zadejte `vbc /?` (pro jazyk Visual Basic) nebo `csc /?` (pro C#) na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="0213a-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="0213a-140">Další informace najdete v tématu [sestavení z příkazového řádku](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) nebo [volání kompilátoru příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0213a-140">For more information, see [Building from the Command Line](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="0213a-141">K provedení podmíněné kompilace pomocí #CONST nebo #define</span><span class="sxs-lookup"><span data-stu-id="0213a-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="0213a-142">Zadejte odpovídající příkaz pro svůj oblíbený programovací jazyk v horní části souboru se zdrojovým kódem.</span><span class="sxs-lookup"><span data-stu-id="0213a-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="0213a-143">Jazyk</span><span class="sxs-lookup"><span data-stu-id="0213a-143">Language</span></span>|<span data-ttu-id="0213a-144">Příkaz</span><span class="sxs-lookup"><span data-stu-id="0213a-144">Statement</span></span>|<span data-ttu-id="0213a-145">Výsledek</span><span class="sxs-lookup"><span data-stu-id="0213a-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="0213a-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="0213a-146">**Visual Basic**</span></span>|<span data-ttu-id="0213a-147">**#CONST trasování = true**</span><span class="sxs-lookup"><span data-stu-id="0213a-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="0213a-148">Umožňuje trasování</span><span class="sxs-lookup"><span data-stu-id="0213a-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="0213a-149">**#CONST trasování = false**</span><span class="sxs-lookup"><span data-stu-id="0213a-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="0213a-150">Zakáže trasování</span><span class="sxs-lookup"><span data-stu-id="0213a-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="0213a-151">**#CONST ladění = true**</span><span class="sxs-lookup"><span data-stu-id="0213a-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="0213a-152">Povolí ladění</span><span class="sxs-lookup"><span data-stu-id="0213a-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="0213a-153">**#CONST ladění = false**</span><span class="sxs-lookup"><span data-stu-id="0213a-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="0213a-154">Zakáže ladění</span><span class="sxs-lookup"><span data-stu-id="0213a-154">Disables debugging</span></span>|  
    |<span data-ttu-id="0213a-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="0213a-155">**C#**</span></span>|<span data-ttu-id="0213a-156">**#define trasování**</span><span class="sxs-lookup"><span data-stu-id="0213a-156">**#define TRACE**</span></span>|<span data-ttu-id="0213a-157">Umožňuje trasování</span><span class="sxs-lookup"><span data-stu-id="0213a-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="0213a-158">**#undef trasování**</span><span class="sxs-lookup"><span data-stu-id="0213a-158">**#undef TRACE**</span></span>|<span data-ttu-id="0213a-159">Zakáže trasování</span><span class="sxs-lookup"><span data-stu-id="0213a-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="0213a-160">**#define ladění**</span><span class="sxs-lookup"><span data-stu-id="0213a-160">**#define DEBUG**</span></span>|<span data-ttu-id="0213a-161">Povolí ladění</span><span class="sxs-lookup"><span data-stu-id="0213a-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="0213a-162">**#undef ladění**</span><span class="sxs-lookup"><span data-stu-id="0213a-162">**#undef DEBUG**</span></span>|<span data-ttu-id="0213a-163">Zakáže ladění</span><span class="sxs-lookup"><span data-stu-id="0213a-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="0213a-164">Chcete-li zakázat trasování a ladění</span><span class="sxs-lookup"><span data-stu-id="0213a-164">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="0213a-165">Direktivy kompilátoru odstraňte ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="0213a-165">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="0213a-166">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="0213a-166">\- or -</span></span>  
  
<span data-ttu-id="0213a-167">Okomentujte direktivy kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0213a-167">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0213a-168">Až budete připravení ke kompilaci, můžete buď zvolit **sestavení** z **sestavení** nabídce nebo pomocí příkazového řádku, ale bez zadání **d:** k definování podmíněné symboly kompilace.</span><span class="sxs-lookup"><span data-stu-id="0213a-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0213a-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0213a-169">See also</span></span>

- [<span data-ttu-id="0213a-170">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="0213a-170">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="0213a-171">Postupy: Vytváření, inicializace a konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="0213a-171">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="0213a-172">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="0213a-172">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="0213a-173">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="0213a-173">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [<span data-ttu-id="0213a-174">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="0213a-174">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="0213a-175">Postupy: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0213a-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="0213a-176">Postupy: Volání kompilátoru příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="0213a-176">How to: Invoke the Command-Line Compiler</span></span>](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
