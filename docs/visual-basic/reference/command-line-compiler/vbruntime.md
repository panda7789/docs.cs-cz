---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
ms.openlocfilehash: a1988fcd19c6629d85ae0e739681fd39fe033c0d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843861"
---
# <a name="-vbruntime"></a><span data-ttu-id="a050f-102">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="a050f-102">-vbruntime</span></span>
<span data-ttu-id="a050f-103">Určuje, že kompilátor by měl kompilovat bez odkazu do knihovny prostředí Runtime jazyka Visual Basic nebo s odkazem na knihovně modulu runtime specifické.</span><span class="sxs-lookup"><span data-stu-id="a050f-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a050f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a050f-104">Syntax</span></span>  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="a050f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a050f-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="a050f-106">Proveďte kompilaci bez odkazu na knihovnu Runtime jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a050f-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="a050f-107">Kompilovat s odkazem na výchozí knihovny prostředí Runtime jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a050f-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="a050f-108">Proveďte kompilaci bez odkazu na knihovnu Runtime jazyka Visual Basic a vložit základní funkce z knihovny Runtime jazyka Visual Basic do sestavení.</span><span class="sxs-lookup"><span data-stu-id="a050f-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="a050f-109">Kompilovat s odkazem na zadanou knihovnu (DLL).</span><span class="sxs-lookup"><span data-stu-id="a050f-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a050f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a050f-110">Remarks</span></span>  
 <span data-ttu-id="a050f-111">`-vbruntime` – Možnost kompilátoru umožňuje určit, že kompilátor by měl kompilovat bez odkazu na knihovnu Runtime jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a050f-111">The `-vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="a050f-112">Pokud kompilaci bez odkazu na knihovnu Runtime jazyka Visual Basic, chyby nebo varování jsou protokolovány v kódu nebo jazykové konstrukce, které generují volání pomocné rutiny modulu runtime jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a050f-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="a050f-113">(A *pomocné rutiny modulu runtime jazyka Visual Basic* je funkce definované v souboru Microsoft.VisualBasic.dll, která je volána v době běhu k provedení konkrétní jazyk sémantického.)</span><span class="sxs-lookup"><span data-stu-id="a050f-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="a050f-114">`-vbruntime+` Možnost produkuje stejné chování, který nastane, pokud žádné `-vbruntime` je zadán přepínač.</span><span class="sxs-lookup"><span data-stu-id="a050f-114">The `-vbruntime+` option produces the same behavior that occurs if no `-vbruntime` switch is specified.</span></span> <span data-ttu-id="a050f-115">Můžete použít `-vbruntime+` lze přepsat předchozí `-vbruntime` přepínače.</span><span class="sxs-lookup"><span data-stu-id="a050f-115">You can use the `-vbruntime+` option to override previous `-vbruntime` switches.</span></span>  
  
 <span data-ttu-id="a050f-116">Většina objektů `My` typu nejsou k dispozici při použití `-vbruntime-` nebo `-vbruntime:path` možnosti.</span><span class="sxs-lookup"><span data-stu-id="a050f-116">Most objects of the `My` type are unavailable when you use the `-vbruntime-` or `-vbruntime:path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="a050f-117">Vkládání základní funkce modulu Runtime jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a050f-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="a050f-118">`-vbruntime*` Možnost umožňuje proveďte kompilaci bez odkazu na knihovnu prostředí runtime.</span><span class="sxs-lookup"><span data-stu-id="a050f-118">The `-vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="a050f-119">Místo toho základní funkce z knihovny Runtime jazyka Visual Basic je vložen do sestavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="a050f-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="a050f-120">Tuto možnost můžete použít, pokud vaše aplikace běží na platformách, které neobsahují modulu runtime jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a050f-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="a050f-121">Následující členy modulu runtime jsou vloženy:</span><span class="sxs-lookup"><span data-stu-id="a050f-121">The following runtime members are embedded:</span></span>  
  
-   <span data-ttu-id="a050f-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> Třída</span><span class="sxs-lookup"><span data-stu-id="a050f-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
-   <span data-ttu-id="a050f-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> – Metoda</span><span class="sxs-lookup"><span data-stu-id="a050f-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
-   <span data-ttu-id="a050f-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> – Metoda</span><span class="sxs-lookup"><span data-stu-id="a050f-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
-   <span data-ttu-id="a050f-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> – Metoda</span><span class="sxs-lookup"><span data-stu-id="a050f-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
-   <span data-ttu-id="a050f-126"><xref:Microsoft.VisualBasic.Constants.vbBack> Konstanty</span><span class="sxs-lookup"><span data-stu-id="a050f-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
-   <span data-ttu-id="a050f-127"><xref:Microsoft.VisualBasic.Constants.vbCr> Konstanty</span><span class="sxs-lookup"><span data-stu-id="a050f-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
-   <span data-ttu-id="a050f-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> Konstanty</span><span class="sxs-lookup"><span data-stu-id="a050f-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
-   <span data-ttu-id="a050f-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> Konstanty</span><span class="sxs-lookup"><span data-stu-id="a050f-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
-   <span data-ttu-id="a050f-130"><xref:Microsoft.VisualBasic.Constants.vbLf> Konstanty</span><span class="sxs-lookup"><span data-stu-id="a050f-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
-   <span data-ttu-id="a050f-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> Konstanty</span><span class="sxs-lookup"><span data-stu-id="a050f-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
-   <span data-ttu-id="a050f-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> Konstanty</span><span class="sxs-lookup"><span data-stu-id="a050f-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
-   <span data-ttu-id="a050f-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> Konstanty</span><span class="sxs-lookup"><span data-stu-id="a050f-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
-   <span data-ttu-id="a050f-134"><xref:Microsoft.VisualBasic.Constants.vbTab> Konstanty</span><span class="sxs-lookup"><span data-stu-id="a050f-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
-   <span data-ttu-id="a050f-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> Konstanty</span><span class="sxs-lookup"><span data-stu-id="a050f-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
-   <span data-ttu-id="a050f-136">Některé objekty `My` typu</span><span class="sxs-lookup"><span data-stu-id="a050f-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="a050f-137">Pokud kompilujete pomocí `-vbruntime*` možnost a váš kód odkazuje na člena z knihovny Runtime jazyka Visual Basic, který není integrován s základní funkce, kompilátor chybovou zprávu, která označuje, že člen není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a050f-137">If you compile using the `-vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="a050f-138">Odkazuje na zadanou knihovnu</span><span class="sxs-lookup"><span data-stu-id="a050f-138">Referencing a specified library</span></span>  
 <span data-ttu-id="a050f-139">Můžete použít `path` argument pro kompilaci pomocí odkazu na knihovnu vlastního modulu runtime místo výchozí knihovny prostředí Runtime jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a050f-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="a050f-140">Pokud hodnota `path` argument je plně kvalifikovanou cestu ke knihovně DLL, kompilátor použije tento soubor jako knihovna prostředí runtime.</span><span class="sxs-lookup"><span data-stu-id="a050f-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="a050f-141">Pokud hodnota `path` argument není plně kvalifikovanou cestu ke knihovně DLL, kompilátor jazyka Visual Basic vyhledá identifikované knihovny DLL ve složce aktuální nejprve.</span><span class="sxs-lookup"><span data-stu-id="a050f-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="a050f-142">Pak bude hledat v cestě, kterou jste zadali pomocí [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="a050f-142">It will then search in the path that you have specified by using the [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="a050f-143">Pokud `-sdkpath` není použita možnost kompilátoru, kompilátor bude hledat identifikované knihovny DLL ve složce rozhraní .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span><span class="sxs-lookup"><span data-stu-id="a050f-143">If the `-sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a050f-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="a050f-144">Example</span></span>  
 <span data-ttu-id="a050f-145">Následující příklad ukazuje způsob použití `-vbruntime` možnost kompilace s odkazem na vlastní knihovny.</span><span class="sxs-lookup"><span data-stu-id="a050f-145">The following example shows how to use the `-vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="a050f-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a050f-146">See also</span></span>

- [<span data-ttu-id="a050f-147">Visual Basic Core – nová režim kompilace v aplikaci Visual Studio 2010 SP1</span><span class="sxs-lookup"><span data-stu-id="a050f-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [<span data-ttu-id="a050f-148">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="a050f-148">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a050f-149">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="a050f-149">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="a050f-150">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="a050f-150">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
