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
ms.openlocfilehash: 8c7789c6af7b82ecb40ecd73d09f64aa1da3fd4b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005056"
---
# <a name="-vbruntime"></a><span data-ttu-id="2d84d-102">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="2d84d-102">-vbruntime</span></span>
<span data-ttu-id="2d84d-103">Určuje, že má kompilátor kompilovat bez odkazu na knihovnu modulu runtime Visual Basic, nebo s odkazem na konkrétní běhovou knihovnu.</span><span class="sxs-lookup"><span data-stu-id="2d84d-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d84d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d84d-104">Syntax</span></span>  
  
```console  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="2d84d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2d84d-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="2d84d-106">Zkompilujte bez odkazu na knihovnu runtime Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2d84d-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="2d84d-107">Zkompiluje s odkazem na výchozí knihovnu runtime Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2d84d-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="2d84d-108">Zkompilujte bez odkazu na běhovou knihovnu Visual Basic a vložte základní funkce z knihovny modulu runtime Visual Basic do sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d84d-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="2d84d-109">Zkompiluje s odkazem na zadanou knihovnu (DLL).</span><span class="sxs-lookup"><span data-stu-id="2d84d-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d84d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d84d-110">Remarks</span></span>  
 <span data-ttu-id="2d84d-111">Možnost kompilátoru `-vbruntime` umožňuje určit, zda má být kompilátor zkompilován bez odkazu na knihovnu modulu runtime Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2d84d-111">The `-vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="2d84d-112">Pokud kompilujete bez odkazu na knihovnu prostředí Visual Basic runtime, chyby nebo upozornění jsou protokolovány v kódu nebo jazykových konstrukcích, které generují volání pomocníka modulu runtime Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2d84d-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="2d84d-113">( *Pomocník pro Visual Basic runtime* je funkce definovaná v souboru Microsoft. VisualBasic. dll, která je volána za běhu za účelem provedení konkrétní jazykové sémantiky.)</span><span class="sxs-lookup"><span data-stu-id="2d84d-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="2d84d-114">Možnost `-vbruntime+` vytváří stejné chování, které nastane, pokud není zadán žádný `-vbruntime` přepínač.</span><span class="sxs-lookup"><span data-stu-id="2d84d-114">The `-vbruntime+` option produces the same behavior that occurs if no `-vbruntime` switch is specified.</span></span> <span data-ttu-id="2d84d-115">Pomocí možnosti `-vbruntime+` můžete přepsat předchozí `-vbruntime` přepínače.</span><span class="sxs-lookup"><span data-stu-id="2d84d-115">You can use the `-vbruntime+` option to override previous `-vbruntime` switches.</span></span>  
  
 <span data-ttu-id="2d84d-116">Většina objektů `My`ho typu není při použití možností `-vbruntime-` nebo `-vbruntime:path` k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2d84d-116">Most objects of the `My` type are unavailable when you use the `-vbruntime-` or `-vbruntime:path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="2d84d-117">Vkládání Visual Basic základní funkce modulu runtime</span><span class="sxs-lookup"><span data-stu-id="2d84d-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="2d84d-118">Možnost `-vbruntime*` umožňuje kompilovat bez odkazu na běhovou knihovnu.</span><span class="sxs-lookup"><span data-stu-id="2d84d-118">The `-vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="2d84d-119">Místo toho je základní funkce z knihovny modulu runtime Visual Basic vložena do sestavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="2d84d-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="2d84d-120">Tuto možnost můžete použít, pokud vaše aplikace běží na platformách, které neobsahují modul runtime Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2d84d-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="2d84d-121">Následující členové modulu runtime jsou vloženi:</span><span class="sxs-lookup"><span data-stu-id="2d84d-121">The following runtime members are embedded:</span></span>  
  
- <span data-ttu-id="2d84d-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> – třída</span><span class="sxs-lookup"><span data-stu-id="2d84d-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
- <span data-ttu-id="2d84d-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> – metoda</span><span class="sxs-lookup"><span data-stu-id="2d84d-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
- <span data-ttu-id="2d84d-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> – metoda</span><span class="sxs-lookup"><span data-stu-id="2d84d-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
- <span data-ttu-id="2d84d-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> – metoda</span><span class="sxs-lookup"><span data-stu-id="2d84d-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
- <span data-ttu-id="2d84d-126"><xref:Microsoft.VisualBasic.Constants.vbBack> konstanta</span><span class="sxs-lookup"><span data-stu-id="2d84d-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
- <span data-ttu-id="2d84d-127"><xref:Microsoft.VisualBasic.Constants.vbCr> konstanta</span><span class="sxs-lookup"><span data-stu-id="2d84d-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
- <span data-ttu-id="2d84d-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> konstanta</span><span class="sxs-lookup"><span data-stu-id="2d84d-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
- <span data-ttu-id="2d84d-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> konstanta</span><span class="sxs-lookup"><span data-stu-id="2d84d-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
- <span data-ttu-id="2d84d-130"><xref:Microsoft.VisualBasic.Constants.vbLf> konstanta</span><span class="sxs-lookup"><span data-stu-id="2d84d-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
- <span data-ttu-id="2d84d-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> konstanta</span><span class="sxs-lookup"><span data-stu-id="2d84d-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
- <span data-ttu-id="2d84d-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> konstanta</span><span class="sxs-lookup"><span data-stu-id="2d84d-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
- <span data-ttu-id="2d84d-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> konstanta</span><span class="sxs-lookup"><span data-stu-id="2d84d-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
- <span data-ttu-id="2d84d-134"><xref:Microsoft.VisualBasic.Constants.vbTab> konstanta</span><span class="sxs-lookup"><span data-stu-id="2d84d-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
- <span data-ttu-id="2d84d-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> konstanta</span><span class="sxs-lookup"><span data-stu-id="2d84d-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
- <span data-ttu-id="2d84d-136">Některé objekty typu `My`</span><span class="sxs-lookup"><span data-stu-id="2d84d-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="2d84d-137">Pokud kompilujete pomocí možnosti `-vbruntime*` a váš kód odkazuje na člen z běhové knihovny Visual Basic, která není vložena se základní funkcí, kompilátor vrátí chybu, která označuje, že člen není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2d84d-137">If you compile using the `-vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="2d84d-138">Odkazování na zadanou knihovnu</span><span class="sxs-lookup"><span data-stu-id="2d84d-138">Referencing a specified library</span></span>  
 <span data-ttu-id="2d84d-139">Můžete použít argument `path` pro zkompilování s odkazem na vlastní běhovou knihovnu namísto výchozí knihovny prostředí runtime Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2d84d-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="2d84d-140">Pokud je hodnota argumentu `path` plně kvalifikovaná cesta k knihovně DLL, kompilátor použije tento soubor jako běhovou knihovnu.</span><span class="sxs-lookup"><span data-stu-id="2d84d-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="2d84d-141">Pokud hodnota argumentu `path` není úplná cesta k knihovně DLL, kompilátor Visual Basic v aktuální složce nejprve vyhledá identifikovanou knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="2d84d-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="2d84d-142">Pak bude hledat v cestě, kterou jste zadali pomocí možnosti kompilátoru [-SdkPath –](../../../visual-basic/reference/command-line-compiler/sdkpath.md) .</span><span class="sxs-lookup"><span data-stu-id="2d84d-142">It will then search in the path that you have specified by using the [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="2d84d-143">Pokud není použita možnost kompilátoru `-sdkpath`, kompilátor bude hledat identifikované knihovny DLL ve složce .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span><span class="sxs-lookup"><span data-stu-id="2d84d-143">If the `-sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d84d-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d84d-144">Example</span></span>  
 <span data-ttu-id="2d84d-145">Následující příklad ukazuje, jak použít možnost `-vbruntime` ke kompilaci s odkazem na vlastní knihovnu.</span><span class="sxs-lookup"><span data-stu-id="2d84d-145">The following example shows how to use the `-vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d84d-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d84d-146">See also</span></span>

- [<span data-ttu-id="2d84d-147">Visual Basic Core – nový režim kompilace v aplikaci Visual Studio 2010 SP1</span><span class="sxs-lookup"><span data-stu-id="2d84d-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [<span data-ttu-id="2d84d-148">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2d84d-148">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="2d84d-149">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="2d84d-149">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="2d84d-150">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="2d84d-150">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
