---
title: /vbruntime
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbruntime
- /vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dda8ea7285a748bac53e30af8bd7a60099fe7411
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="vbruntime"></a><span data-ttu-id="5d8d5-102">/vbruntime</span><span class="sxs-lookup"><span data-stu-id="5d8d5-102">/vbruntime</span></span>
<span data-ttu-id="5d8d5-103">Určuje, že by měl kompilátor kompilovat bez odkaz na Visual Basic Runtime Library nebo s odkazem na knihovnu konkrétní runtime.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d8d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d8d5-104">Syntax</span></span>  
  
```  
/vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="5d8d5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5d8d5-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="5d8d5-106">Kompilovat bez odkaz na Visual Basic Runtime Library.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="5d8d5-107">Kompilace s odkazem na výchozí hodnoty jazyka Visual Basic Runtime Library.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="5d8d5-108">Kompilovat bez odkazu na Visual Basic Runtime Library a vložit základní funkce z Visual Basic Runtime Library do sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="5d8d5-109">Kompilovat s odkazem na uvedené knihovny (DLL).</span><span class="sxs-lookup"><span data-stu-id="5d8d5-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d8d5-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d8d5-110">Remarks</span></span>  
 <span data-ttu-id="5d8d5-111">`/vbruntime` – Možnost kompilátoru umožňuje určit, že by měl kompilátor kompilovat bez odkazu na Visual Basic Runtime Library.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-111">The `/vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="5d8d5-112">Pokud zkompilujete bez odkazu na Visual Basic Runtime Library, chyby nebo upozornění kód nebo jazyk konstrukce, které generují volání pomocné rutiny modulu runtime jazyka Visual Basic přihlášeni.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="5d8d5-113">(A *jazyka Visual Basic runtime pomocná* je funkci definovanou v souboru Microsoft.VisualBasic.dll, která je volána v době běhu k provedení sémantického konkrétní jazyk.)</span><span class="sxs-lookup"><span data-stu-id="5d8d5-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="5d8d5-114">`/vbruntime+` Možnost vytváří stejné chování, k níž dojde, pokud žádné `/vbruntime` je zadán přepínač.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-114">The `/vbruntime+` option produces the same behavior that occurs if no `/vbruntime` switch is specified.</span></span> <span data-ttu-id="5d8d5-115">Můžete použít `/vbruntime+` možnost přepsat předchozí `/vbruntime` přepínače.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-115">You can use the `/vbruntime+` option to override previous `/vbruntime` switches.</span></span>  
  
 <span data-ttu-id="5d8d5-116">Většina objekty `My` typu nejsou k dispozici při použití `/vbruntime-` nebo `vbruntime:``path` možnosti.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-116">Most objects of the `My` type are unavailable when you use the `/vbruntime-` or `vbruntime:``path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="5d8d5-117">Vložení základní funkce Runtime jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d8d5-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="5d8d5-118">`/vbruntime*` Možnost umožňuje kompilovat bez odkaz na knihovnu runtime.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-118">The `/vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="5d8d5-119">Místo toho základní funkce z Visual Basic Runtime Library vložené v sestavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="5d8d5-120">Tuto možnost můžete použít, pokud vaše aplikace běží na platformách, které neobsahují runtime jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="5d8d5-121">Následující členy runtime jsou vloženy:</span><span class="sxs-lookup"><span data-stu-id="5d8d5-121">The following runtime members are embedded:</span></span>  
  
-   <span data-ttu-id="5d8d5-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions>– Třída</span><span class="sxs-lookup"><span data-stu-id="5d8d5-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
-   <span data-ttu-id="5d8d5-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>– Metoda</span><span class="sxs-lookup"><span data-stu-id="5d8d5-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
-   <span data-ttu-id="5d8d5-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>– Metoda</span><span class="sxs-lookup"><span data-stu-id="5d8d5-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
-   <span data-ttu-id="5d8d5-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>– Metoda</span><span class="sxs-lookup"><span data-stu-id="5d8d5-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
-   <span data-ttu-id="5d8d5-126"><xref:Microsoft.VisualBasic.Constants.vbBack>Konstanta</span><span class="sxs-lookup"><span data-stu-id="5d8d5-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
-   <span data-ttu-id="5d8d5-127"><xref:Microsoft.VisualBasic.Constants.vbCr>Konstanta</span><span class="sxs-lookup"><span data-stu-id="5d8d5-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
-   <span data-ttu-id="5d8d5-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf>Konstanta</span><span class="sxs-lookup"><span data-stu-id="5d8d5-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
-   <span data-ttu-id="5d8d5-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed>Konstanta</span><span class="sxs-lookup"><span data-stu-id="5d8d5-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
-   <span data-ttu-id="5d8d5-130"><xref:Microsoft.VisualBasic.Constants.vbLf>Konstanta</span><span class="sxs-lookup"><span data-stu-id="5d8d5-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
-   <span data-ttu-id="5d8d5-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine>Konstanta</span><span class="sxs-lookup"><span data-stu-id="5d8d5-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
-   <span data-ttu-id="5d8d5-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar>Konstanta</span><span class="sxs-lookup"><span data-stu-id="5d8d5-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
-   <span data-ttu-id="5d8d5-133"><xref:Microsoft.VisualBasic.Constants.vbNullString>Konstanta</span><span class="sxs-lookup"><span data-stu-id="5d8d5-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
-   <span data-ttu-id="5d8d5-134"><xref:Microsoft.VisualBasic.Constants.vbTab>Konstanta</span><span class="sxs-lookup"><span data-stu-id="5d8d5-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
-   <span data-ttu-id="5d8d5-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab>Konstanta</span><span class="sxs-lookup"><span data-stu-id="5d8d5-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
-   <span data-ttu-id="5d8d5-136">Některé objekty `My` typu</span><span class="sxs-lookup"><span data-stu-id="5d8d5-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="5d8d5-137">Pokud zkompilujete pomocí `/vbruntime*` možnost a váš kód odkazuje na člena z Visual Basic Runtime Library, který není vložených s základní funkce, kompilátor vrátí chybu, která určuje, že člen není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-137">If you compile using the `/vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="5d8d5-138">Odkazování na uvedené knihovny</span><span class="sxs-lookup"><span data-stu-id="5d8d5-138">Referencing a specified library</span></span>  
 <span data-ttu-id="5d8d5-139">Můžete použít `path` argument zkompilovat s odkazem na knihovnu vlastní runtime místo výchozího Visual Basic Runtime Library.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="5d8d5-140">Pokud hodnota `path` argument je plně kvalifikovanou cestu ke knihovně DLL, kompilátor použije tento soubor jako knihovna runtime.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="5d8d5-141">Pokud hodnota `path` argument není plně kvalifikovaná cesta ke knihovně DLL, Visual Basic – kompilátor bude hledat identifikovaných DLL v aktuální složce nejdřív.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="5d8d5-142">Bude poté hledat v cestě, která jste zadali pomocí [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-142">It will then search in the path that you have specified by using the [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="5d8d5-143">Pokud `/sdkpath` – možnost kompilátoru nepoužívá, kompilátor bude hledat identifikovaných knihovny DLL ve složce rozhraní .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span><span class="sxs-lookup"><span data-stu-id="5d8d5-143">If the `/sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d8d5-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d8d5-144">Example</span></span>  
 <span data-ttu-id="5d8d5-145">Následující příklad ukazuje způsob použití `/vbruntime` kompilovat s odkazem na knihovnu vlastní možnost.</span><span class="sxs-lookup"><span data-stu-id="5d8d5-145">The following example shows how to use the `/vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```  
vbc /vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d8d5-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d8d5-146">See Also</span></span>  
 [<span data-ttu-id="5d8d5-147">Základní jazyka Visual Basic – nový režim kompilace v sadě Visual Studio 2010 SP1</span><span class="sxs-lookup"><span data-stu-id="5d8d5-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)  
 [<span data-ttu-id="5d8d5-148">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="5d8d5-148">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="5d8d5-149">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="5d8d5-149">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="5d8d5-150">/ sdkpath</span><span class="sxs-lookup"><span data-stu-id="5d8d5-150">/sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
