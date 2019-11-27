---
title: -platform
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: a6226b73d5d5d4d48a71afe39e8a546019d4c0bc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352346"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="be8c2-102">– Platforma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be8c2-102">-platform (Visual Basic)</span></span>
<span data-ttu-id="be8c2-103">Určuje, která verze platformy modulu CLR (Common Language Runtime) může spustit výstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="be8c2-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be8c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be8c2-104">Syntax</span></span>  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="be8c2-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="be8c2-105">Arguments</span></span>  
  
|<span data-ttu-id="be8c2-106">Termín</span><span class="sxs-lookup"><span data-stu-id="be8c2-106">Term</span></span>|<span data-ttu-id="be8c2-107">Definice</span><span class="sxs-lookup"><span data-stu-id="be8c2-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="be8c2-108">Zkompiluje sestavení tak, aby bylo spuštěno pomocí 32 CLR kompatibilního s platformou x86.</span><span class="sxs-lookup"><span data-stu-id="be8c2-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="be8c2-109">Zkompiluje sestavení tak, aby bylo spuštěno pomocí 64 CLR na počítači, který podporuje instrukční sady AMD64 nebo EM64T.</span><span class="sxs-lookup"><span data-stu-id="be8c2-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="be8c2-110">Zkompiluje sestavení tak, aby bylo spuštěno pomocí 64 CLR v počítači s procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="be8c2-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="be8c2-111">Zkompiluje sestavení, které se má spustit na počítači s procesorem ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="be8c2-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="be8c2-112">Zkompiluje sestavení pro spuštění na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="be8c2-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="be8c2-113">Aplikace bude spuštěna jako 32ová aplikace v 32 verzích systému Windows a jako aplikace 64 64 v systému Windows v 16bitovém verzích.</span><span class="sxs-lookup"><span data-stu-id="be8c2-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="be8c2-114">Tento příznak je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="be8c2-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="be8c2-115">Zkompiluje sestavení pro spuštění na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="be8c2-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="be8c2-116">Aplikace bude spuštěna jako 32ová aplikace v 32 i v 64 bitových verzí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="be8c2-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="be8c2-117">Tento příznak je platný jenom pro spustitelné soubory (. EXE) a vyžaduje .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="be8c2-117">This flag is valid only for executables (.EXE) and requires .NET Framework 4.5.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be8c2-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be8c2-118">Remarks</span></span>  
 <span data-ttu-id="be8c2-119">Pomocí možnosti `-platform` určete typ procesoru, který je cílem výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="be8c2-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="be8c2-120">Obecně platí, .NET Framework sestavení zapsaných v Visual Basic budou spuštěna stejně bez ohledu na platformu.</span><span class="sxs-lookup"><span data-stu-id="be8c2-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="be8c2-121">Existují však některé případy, které se chovají odlišně na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="be8c2-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="be8c2-122">Tyto běžné případy:</span><span class="sxs-lookup"><span data-stu-id="be8c2-122">These common cases are:</span></span>  
  
- <span data-ttu-id="be8c2-123">Struktury, které obsahují členy, které mění velikost v závislosti na platformě, jako je například libovolný typ ukazatele.</span><span class="sxs-lookup"><span data-stu-id="be8c2-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
- <span data-ttu-id="be8c2-124">Aritmetický ukazatel, který obsahuje konstantní velikosti.</span><span class="sxs-lookup"><span data-stu-id="be8c2-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
- <span data-ttu-id="be8c2-125">Nesprávné vyvolání platformy nebo deklarace COM, které používají `Integer` pro popisovače místo <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="be8c2-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
- <span data-ttu-id="be8c2-126">Přetypování <xref:System.IntPtr> do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="be8c2-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
- <span data-ttu-id="be8c2-127">Použití volání platformy nebo zprostředkovatele komunikace s objekty COM s komponentami, které neexistují na všech platformách.</span><span class="sxs-lookup"><span data-stu-id="be8c2-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="be8c2-128">Pokud víte, že jste provedli předpoklady týkající se architektury, na které je váš kód spuštěný, možnost **-platformou** tyto problémy sníží.</span><span class="sxs-lookup"><span data-stu-id="be8c2-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="be8c2-129">Určen</span><span class="sxs-lookup"><span data-stu-id="be8c2-129">Specifically:</span></span>  
  
- <span data-ttu-id="be8c2-130">Pokud se rozhodnete cílit na 64 platformu a aplikace je spuštěná na 32 počítači, chybová zpráva je mnohem starší a cílená na problém je větší než chyba, ke které dojde bez použití tohoto přepínače.</span><span class="sxs-lookup"><span data-stu-id="be8c2-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
- <span data-ttu-id="be8c2-131">Pokud u možnosti nastavíte příznak `x86` a aplikace se následně spustí na 64ém počítači, aplikace se spustí v subsystému WOW namísto nativního spuštění.</span><span class="sxs-lookup"><span data-stu-id="be8c2-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="be8c2-132">V 64 operačním systému Windows:</span><span class="sxs-lookup"><span data-stu-id="be8c2-132">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="be8c2-133">Sestavení kompilována s `-platform:x86` budou spouštěna v 32 CLR spuštěném v modulu WOW64.</span><span class="sxs-lookup"><span data-stu-id="be8c2-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="be8c2-134">Spustitelné soubory kompilovány s `-platform:anycpu` budou spouštěny v 64 CLR.</span><span class="sxs-lookup"><span data-stu-id="be8c2-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="be8c2-135">Knihovna DLL kompilována s `-platform:anycpu` bude spuštěna ve stejném modulu CLR jako proces, do kterého byla načtena.</span><span class="sxs-lookup"><span data-stu-id="be8c2-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
- <span data-ttu-id="be8c2-136">Spustitelné soubory, které jsou kompilovány s `-platform:anycpu32bitpreferred`, budou spouštěny v 32 CLR.</span><span class="sxs-lookup"><span data-stu-id="be8c2-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="be8c2-137">Další informace o vývoji aplikace pro spuštění v 64 verze systému Windows naleznete v tématu [64-bitové aplikace](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="be8c2-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="be8c2-138">Nastavení platformy v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="be8c2-138">To set -platform in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="be8c2-139">V **Průzkumník řešení**zvolte projekt, otevřete nabídku **projekt** a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="be8c2-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="be8c2-140">Na kartě **kompilovat** zaškrtněte nebo zrušte zaškrtnutí políčka **preferovat 32** , nebo v seznamu **cílový procesor** zvolte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="be8c2-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="be8c2-141">Další informace naleznete v tématu [Kompilovat stránku, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="be8c2-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be8c2-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="be8c2-142">Example</span></span>  
 <span data-ttu-id="be8c2-143">Následující příklad ukazuje, jak použít možnost kompilátoru `-platform`.</span><span class="sxs-lookup"><span data-stu-id="be8c2-143">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="be8c2-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be8c2-144">See also</span></span>

- [<span data-ttu-id="be8c2-145">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be8c2-145">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="be8c2-146">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="be8c2-146">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="be8c2-147">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="be8c2-147">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
