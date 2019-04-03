---
title: -platform (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: 9657d9ec23b0e67625521ee595bc693eb7b992a4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843120"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="2b78d-102">-platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b78d-102">-platform (Visual Basic)</span></span>
<span data-ttu-id="2b78d-103">Určuje, jaké verze platformy common language runtime (CLR) můžete spustit výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="2b78d-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b78d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b78d-104">Syntax</span></span>  
  
```  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="2b78d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2b78d-105">Arguments</span></span>  
  
|<span data-ttu-id="2b78d-106">Termín</span><span class="sxs-lookup"><span data-stu-id="2b78d-106">Term</span></span>|<span data-ttu-id="2b78d-107">Definice</span><span class="sxs-lookup"><span data-stu-id="2b78d-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="2b78d-108">Kompiluje sestavení ke spuštění v 32 bitů, které je kompatibilní x86 CLR.</span><span class="sxs-lookup"><span data-stu-id="2b78d-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="2b78d-109">Kompiluje sestavení ke spuštění v 64bitovém modulu CLR na počítači, který podporuje AMD64 nebo EM64T instrukční sadu.</span><span class="sxs-lookup"><span data-stu-id="2b78d-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="2b78d-110">Kompiluje sestavení ke spuštění v 64bitovém modulu CLR na počítači s procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="2b78d-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="2b78d-111">Kompiluje sestavení ke spuštění v počítači s procesorem ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="2b78d-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="2b78d-112">Kompiluje sestavení pro spouštěn na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="2b78d-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="2b78d-113">Aplikace se spustí jako 32bitová aplikace ve 32bitové verze Windows a jako na 64bitovými verzemi Windows 64-bit aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b78d-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="2b78d-114">Výchozí hodnota je tento příznak.</span><span class="sxs-lookup"><span data-stu-id="2b78d-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="2b78d-115">Kompiluje sestavení pro spouštěn na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="2b78d-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="2b78d-116">Aplikace poběží jako 32bitová aplikace ve 32bitové a 64bitové verze Windows.</span><span class="sxs-lookup"><span data-stu-id="2b78d-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="2b78d-117">Tento příznak je platná pouze pro spustitelné soubory (. Soubor EXE) a vyžaduje [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b78d-117">This flag is valid only for executables (.EXE) and requires [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b78d-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b78d-118">Remarks</span></span>  
 <span data-ttu-id="2b78d-119">Použití `-platform` možnost určit typ procesoru cílem výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="2b78d-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="2b78d-120">Sestavení rozhraní .NET Framework, které jsou napsané v jazyce Visual Basic, poběží stejný bez ohledu na platformu.</span><span class="sxs-lookup"><span data-stu-id="2b78d-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="2b78d-121">Existují však případy, které se chovají jinak na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="2b78d-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="2b78d-122">Tyto běžné případy jsou:</span><span class="sxs-lookup"><span data-stu-id="2b78d-122">These common cases are:</span></span>  
  
-   <span data-ttu-id="2b78d-123">Struktury, které obsahují členy, které se mění velikost v závislosti na platformě, jako je například libovolný typ ukazatele.</span><span class="sxs-lookup"><span data-stu-id="2b78d-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
-   <span data-ttu-id="2b78d-124">Aritmetika ukazatele, který obsahuje konstantní velikostí.</span><span class="sxs-lookup"><span data-stu-id="2b78d-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
-   <span data-ttu-id="2b78d-125">Nesprávný platformu vyvolání nebo deklarace modelu COM, které používají `Integer` pro popisovače místo <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="2b78d-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
-   <span data-ttu-id="2b78d-126">Přetypování <xref:System.IntPtr> k `Integer`.</span><span class="sxs-lookup"><span data-stu-id="2b78d-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
-   <span data-ttu-id="2b78d-127">Pomocí platformy vyvolat nebo komunikace s objekty COM s komponentami, které neexistují na všech platformách.</span><span class="sxs-lookup"><span data-stu-id="2b78d-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="2b78d-128">**-Platform** možnost zmírnit některé problémy, pokud víte, že jste provedli předpoklady o architektuře váš kód poběží.</span><span class="sxs-lookup"><span data-stu-id="2b78d-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="2b78d-129">Konkrétně:</span><span class="sxs-lookup"><span data-stu-id="2b78d-129">Specifically:</span></span>  
  
-   <span data-ttu-id="2b78d-130">Pokud se rozhodnete cílit na 64bitové platformě a v 32bitovém počítači při spuštění aplikace, chybová zpráva obsahuje mnohem dříve a více zaměřuje se na problému než chybu, která probíhá, aniž by tento přepínač.</span><span class="sxs-lookup"><span data-stu-id="2b78d-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
-   <span data-ttu-id="2b78d-131">Pokud jste nastavili `x86` příznak na možnosti a následně při spuštění aplikace na 64bitovém počítači, bude aplikace spuštěna v subsystému WOW, místo spouštění nativně.</span><span class="sxs-lookup"><span data-stu-id="2b78d-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="2b78d-132">V operačním systému Windows 64-bit:</span><span class="sxs-lookup"><span data-stu-id="2b78d-132">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="2b78d-133">Sestavení zkompilovaná `-platform:x86` se spustí na 32-bit CLR spuštěna v modulu WOW64.</span><span class="sxs-lookup"><span data-stu-id="2b78d-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="2b78d-134">Spustitelné soubory zkompilovaná `-platform:anycpu` se spustí na 64bitový modul CLR.</span><span class="sxs-lookup"><span data-stu-id="2b78d-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="2b78d-135">Knihovna DLL zkompilovaná `-platform:anycpu` se spustí na stejném modulu CLR jako proces, do kterého ji načíst.</span><span class="sxs-lookup"><span data-stu-id="2b78d-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
-   <span data-ttu-id="2b78d-136">Spustitelné soubory, které jsou kompilovány pomocí `-platform:anycpu32bitpreferred` se spustí na 32-bit CLR.</span><span class="sxs-lookup"><span data-stu-id="2b78d-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="2b78d-137">Další informace o tom, jak vyvinout aplikaci v 64bitové verzi Windows, naleznete v tématu [64bitové aplikace](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="2b78d-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="2b78d-138">Chcete-li nastavit - platform v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2b78d-138">To set -platform in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="2b78d-139">V **Průzkumníka řešení**, vyberte projekt, otevřete **projektu** nabídky a pak klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="2b78d-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2b78d-140">Na **kompilaci** kartu, zaškrtněte nebo zrušte zaškrtnutí **preferovat 32bitovou verzi** zaškrtávací políčko, nebo v **cílový procesor** , zvolte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2b78d-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="2b78d-141">Další informace najdete v tématu [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2b78d-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b78d-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b78d-142">Example</span></span>  
 <span data-ttu-id="2b78d-143">Následující příklad ukazuje způsob použití `-platform` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2b78d-143">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b78d-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b78d-144">See also</span></span>

- [<span data-ttu-id="2b78d-145">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b78d-145">/target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="2b78d-146">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="2b78d-146">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="2b78d-147">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="2b78d-147">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
