---
title: -platform (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec3a7e01e62b60688080fee95cf70e0ed38917f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656175"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="25857-102">-platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25857-102">-platform (Visual Basic)</span></span>
<span data-ttu-id="25857-103">Určuje, která verze modul common language runtime (CLR) platforma můžete spustit výstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="25857-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25857-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25857-104">Syntax</span></span>  
  
```  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="25857-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="25857-105">Arguments</span></span>  
  
|<span data-ttu-id="25857-106">Termín</span><span class="sxs-lookup"><span data-stu-id="25857-106">Term</span></span>|<span data-ttu-id="25857-107">Definice</span><span class="sxs-lookup"><span data-stu-id="25857-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="25857-108">Zkompiluje vaše sestavení ke spuštění x86 kompatibilní, 32bitová verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="25857-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="25857-109">Zkompiluje vaše sestavení pro 64bitové verze CLR spustit na počítači, který podporuje AMD64 nebo EM64T sada instrukcí.</span><span class="sxs-lookup"><span data-stu-id="25857-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="25857-110">Zkompiluje vaše sestavení pro 64bitové verze CLR spustit na počítači s procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="25857-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="25857-111">Zkompiluje vaše sestavení pro spouštění na počítači s procesorem ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="25857-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="25857-112">Zkompiluje vaše sestavení pro spouštěn na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="25857-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="25857-113">Aplikace se spustí jako 32bitová aplikace na 32bitové verze systému Windows a jako 64bitové aplikaci v 64bitových verzích systému Windows.</span><span class="sxs-lookup"><span data-stu-id="25857-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="25857-114">Tento příznak je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="25857-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="25857-115">Zkompiluje vaše sestavení pro spouštěn na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="25857-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="25857-116">Aplikace se spustí jako 32bitová aplikace na 32bitové a 64bitové verze systému Windows.</span><span class="sxs-lookup"><span data-stu-id="25857-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="25857-117">Tento příznak je platná pouze pro spustitelné soubory (. Soubor EXE) a vyžaduje [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25857-117">This flag is valid only for executables (.EXE) and requires [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25857-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25857-118">Remarks</span></span>  
 <span data-ttu-id="25857-119">Použití `-platform` můžete určit typ procesoru cílem výstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="25857-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="25857-120">Obecně platí sestavení rozhraní .NET Framework, které jsou napsané v jazyce Visual Basic se spustí stejný bez ohledu na platformu.</span><span class="sxs-lookup"><span data-stu-id="25857-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="25857-121">Existují však někdy s odlišným na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="25857-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="25857-122">Jsou tyto běžné případy:</span><span class="sxs-lookup"><span data-stu-id="25857-122">These common cases are:</span></span>  
  
-   <span data-ttu-id="25857-123">Struktury, které obsahují členy, kteří změnit velikost v závislosti na platformě, jako je například libovolného typu ukazatele.</span><span class="sxs-lookup"><span data-stu-id="25857-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
-   <span data-ttu-id="25857-124">Aritmetika ukazatele, který zahrnuje konstantní velikosti.</span><span class="sxs-lookup"><span data-stu-id="25857-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
-   <span data-ttu-id="25857-125">Nesprávný platformy vyvolání nebo COM deklarace, které používají `Integer` pro obslužné rutiny místo <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="25857-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
-   <span data-ttu-id="25857-126">Přetypování <xref:System.IntPtr> k `Integer`.</span><span class="sxs-lookup"><span data-stu-id="25857-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
-   <span data-ttu-id="25857-127">Pomocí platformy vyvolání nebo zprostředkovatel komunikace s objekty COM s součásti, které nejsou k dispozici na všech platformách.</span><span class="sxs-lookup"><span data-stu-id="25857-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="25857-128">**-Platformy** možnost bude zmírnit některé problémy, pokud víte, že jste provedli předpoklady o architektuře kódu se spustí na.</span><span class="sxs-lookup"><span data-stu-id="25857-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="25857-129">Konkrétně:</span><span class="sxs-lookup"><span data-stu-id="25857-129">Specifically:</span></span>  
  
-   <span data-ttu-id="25857-130">Pokud se rozhodnete platformu 64-bit a spuštění aplikace na počítač s 32bitovou, chybová zpráva obsahuje mnohem dříve a více cíleně problém než chybu, která nastane bez použití tohoto přepínače.</span><span class="sxs-lookup"><span data-stu-id="25857-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
-   <span data-ttu-id="25857-131">Pokud nastavíte `x86` příznak na možnosti a následné spuštění aplikace na počítači 64-bit, bude aplikace spuštěna v subsystému WOW namísto spuštění nativně.</span><span class="sxs-lookup"><span data-stu-id="25857-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="25857-132">64bitová verze operačního systému Windows:</span><span class="sxs-lookup"><span data-stu-id="25857-132">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="25857-133">Sestavení kompilovat s `-platform:x86` se spustí na 32bitová verze modulu CLR spuštěna pod WOW64.</span><span class="sxs-lookup"><span data-stu-id="25857-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="25857-134">Spustitelné soubory kompilovat s `-platform:anycpu` se spustí na 64-bit CLR.</span><span class="sxs-lookup"><span data-stu-id="25857-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="25857-135">Knihovny DLL kompilovat s `-platform:anycpu` se spustí na stejném modulu CLR jako proces, do kterého jej načíst.</span><span class="sxs-lookup"><span data-stu-id="25857-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
-   <span data-ttu-id="25857-136">Spustitelné soubory, které jsou kompilovat s `-platform:anycpu32bitpreferred` se spustí na 32bitová verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="25857-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="25857-137">Další informace o tom, jak vyvíjet aplikaci spustit v 64bitové verzi systému Windows najdete v tématu [64bitové aplikace](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="25857-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="25857-138">Chcete-li nastavit - platformy v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="25857-138">To set -platform in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="25857-139">V **Průzkumníku řešení**, zvolte projekt, otevřete **projektu** nabídce a pak klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="25857-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="25857-140">Na **zkompilovat** kartě, zaškrtněte nebo zrušte **raději 32bitové** zaškrtávací políčko, nebo v **cílový procesor** seznamu, vyberte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="25857-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="25857-141">Další informace najdete v tématu [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="25857-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="25857-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="25857-142">Example</span></span>  
 <span data-ttu-id="25857-143">Následující příklad ukazuje, jak používat `-platform` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="25857-143">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="25857-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="25857-144">See Also</span></span>  
 [<span data-ttu-id="25857-145">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25857-145">/target (Visual Basic)</span></span>](target.md)  
 [<span data-ttu-id="25857-146">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="25857-146">Visual Basic Command-Line Compiler</span></span>](index.md)  
 [<span data-ttu-id="25857-147">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="25857-147">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
