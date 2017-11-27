---
title: "-langversion (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
caps.latest.revision: "33"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d034958b14c54540aa175a23067d47bd5d850bab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="langversion-c-compiler-options"></a><span data-ttu-id="cd57d-102">/langversion (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="cd57d-102">/langversion (C# Compiler Options)</span></span>
<span data-ttu-id="cd57d-103">Způsobí, že kompilátor tak, aby přijímal pouze syntaxi, která je součástí vybrané specifikace jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cd57d-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd57d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd57d-104">Syntax</span></span>  
  
```console  
/langversion:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="cd57d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="cd57d-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="cd57d-106">Platné jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="cd57d-106">The following values are valid:</span></span>  
  
|<span data-ttu-id="cd57d-107">Možnost</span><span class="sxs-lookup"><span data-stu-id="cd57d-107">Option</span></span>|<span data-ttu-id="cd57d-108">Význam</span><span class="sxs-lookup"><span data-stu-id="cd57d-108">Meaning</span></span>|  
|------------|-------------|  
|<span data-ttu-id="cd57d-109">default</span><span class="sxs-lookup"><span data-stu-id="cd57d-109">default</span></span>|<span data-ttu-id="cd57d-110">Kompilátor přijímá všechny platné syntaxe jazyka, jakou může podporovat.</span><span class="sxs-lookup"><span data-stu-id="cd57d-110">The compiler accepts all valid language syntax that it can support.</span></span> <span data-ttu-id="cd57d-111"><sup id="TDefault">[Výchozí](#FDefault)</sup></span><span class="sxs-lookup"><span data-stu-id="cd57d-111"><sup id="TDefault">[Default](#FDefault)</sup></span></span>| 
|<span data-ttu-id="cd57d-112">ISO-1</span><span class="sxs-lookup"><span data-stu-id="cd57d-112">ISO-1</span></span>|<span data-ttu-id="cd57d-113">Kompilátor přijímá pouze syntaxi, která je součástí ISO/IEC 23270: 2003 C# (1.0/1.1) <sup id="TISO1"> [ISO1](#FISO1)</sup></span><span class="sxs-lookup"><span data-stu-id="cd57d-113">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.1) <sup id="TISO1">[ISO1](#FISO1)</sup></span></span>|  
|<span data-ttu-id="cd57d-114">ISO-2</span><span class="sxs-lookup"><span data-stu-id="cd57d-114">ISO-2</span></span>|<span data-ttu-id="cd57d-115">Kompilátor přijímá pouze syntaxi, která je součástí ISO/IEC 23270: 2006 C# (2.0) <sup id="TISO2"> [ISO2](#FISO2)</sup></span><span class="sxs-lookup"><span data-stu-id="cd57d-115">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup></span></span>|
|<span data-ttu-id="cd57d-116">3</span><span class="sxs-lookup"><span data-stu-id="cd57d-116">3</span></span>|<span data-ttu-id="cd57d-117">Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 3.0 nebo nižší <sup id="TCS3"> [CS3](#FCS3)</sup></span><span class="sxs-lookup"><span data-stu-id="cd57d-117">The compiler accepts only syntax that is included in C# 3.0 or lower <sup id="TCS3">[CS3](#FCS3)</sup></span></span>|
|<span data-ttu-id="cd57d-118">4</span><span class="sxs-lookup"><span data-stu-id="cd57d-118">4</span></span>|<span data-ttu-id="cd57d-119">Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 4.0 nebo nižší <sup id="TCS4"> [CS4](#FCS4)</sup></span><span class="sxs-lookup"><span data-stu-id="cd57d-119">The compiler accepts only syntax that is included in C# 4.0 or lower <sup id="TCS4">[CS4](#FCS4)</sup></span></span>|
|<span data-ttu-id="cd57d-120">5</span><span class="sxs-lookup"><span data-stu-id="cd57d-120">5</span></span>|<span data-ttu-id="cd57d-121">Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 5.0 nebo nižší <sup id="TCS5"> [CS5](#FCS5)</sup></span><span class="sxs-lookup"><span data-stu-id="cd57d-121">The compiler accepts only syntax that is included in C# 5.0 or lower <sup id="TCS5">[CS5](#FCS5)</sup></span></span>|
|<span data-ttu-id="cd57d-122">6</span><span class="sxs-lookup"><span data-stu-id="cd57d-122">6</span></span>|<span data-ttu-id="cd57d-123">Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 6.0 nebo nižší <sup id="TCS6"> [CS6](#FCS6)</sup></span><span class="sxs-lookup"><span data-stu-id="cd57d-123">The compiler accepts only syntax that is included in C# 6.0 or lower <sup id="TCS6">[CS6](#FCS6)</sup></span></span>|
|<span data-ttu-id="cd57d-124">7</span><span class="sxs-lookup"><span data-stu-id="cd57d-124">7</span></span>|<span data-ttu-id="cd57d-125">Kompilátor přijímá pouze syntaxi, která je zahrnuta v C# 7.0 nebo nižší <sup id="TCS7"> [CS7](#FCS7)</sup></span><span class="sxs-lookup"><span data-stu-id="cd57d-125">The compiler accepts only syntax that is included in C# 7.0 or lower <sup id="TCS7">[CS7](#FCS7)</sup></span></span>|
|<span data-ttu-id="cd57d-126">Nejnovější</span><span class="sxs-lookup"><span data-stu-id="cd57d-126">latest</span></span>|<span data-ttu-id="cd57d-127">Kompilátor přijímá všechny platné syntaxe jazyka, jakou může podporovat.</span><span class="sxs-lookup"><span data-stu-id="cd57d-127">The compiler accepts all valid language syntax that it can support.</span></span> <span data-ttu-id="cd57d-128"><sup id="TLatest">[Nejnovější](#FLatest)</sup></span><span class="sxs-lookup"><span data-stu-id="cd57d-128"><sup id="TLatest">[Latest](#FLatest)</sup></span></span>|
<!--- Uncomment and move these above
|latest| once they're officially released
|7.1|The compiler accepts only syntax that is included in C# 7.1 or lower <sup id="TCS71">[CS71](#FCS71)</sup>|
|7.2|The compiler accepts only syntax that is included in C# 7.2 or lower <sup id="TCS71">[CS72](#FCS72)</sup>|
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS71">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a><span data-ttu-id="cd57d-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd57d-129">Remarks</span></span>  
 <span data-ttu-id="cd57d-130">Metadata odkazuje aplikace C# není podléhají **/langversion** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="cd57d-130">Metadata referenced by your C# application is not subject to **/langversion** compiler option.</span></span>  
  
 <span data-ttu-id="cd57d-131">Protože každá verze kompilátoru jazyka C# obsahuje rozšíření pro specifikaci jazyka **/langversion** nezískáte ekvivalentní funkce kompilátoru starší verze.</span><span class="sxs-lookup"><span data-stu-id="cd57d-131">Because each version of the C# compiler contains extensions to the language specification, **/langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>  
 
 <span data-ttu-id="cd57d-132">Kromě toho při aktualizace verzí jazyka C# obecně neshoduje se hlavní rozhraní .net Framework verze, nové syntaxe a funkce nejsou se nevztahuje na danou verzi konkrétní framework.</span><span class="sxs-lookup"><span data-stu-id="cd57d-132">Additionally, while C# version updates generally coincide with major .Net Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="cd57d-133">Při nových funkcí bude vyžadovat výborný nové aktualizace kompilátoru, která je také vydané spolu s revize C#, každou konkrétní funkci má svou vlastní minimální rozhraní API .net nebo běžné požadavky modulu runtime jazyka, které může povolit jeho spuštění v nižší úrovně rozhraní pomocí včetně balíčky NuGet, nebo jiné knihovny.</span><span class="sxs-lookup"><span data-stu-id="cd57d-133">While the new features will definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .Net API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>
  
 <span data-ttu-id="cd57d-134">Bez ohledu na to, které **/langversion** nastavení použijete, bude použita aktuální verzí common language runtime pro vytvoření .exe nebo .dll.</span><span class="sxs-lookup"><span data-stu-id="cd57d-134">Regardless of which **/langversion** setting you use, you will use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="cd57d-135">Jedinou výjimkou je přátelských sestavení a [/moduleassemblyname (možnost kompilátoru C#)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), které pracovní pod **/langversion:ISO-1**.</span><span class="sxs-lookup"><span data-stu-id="cd57d-135">One exception is friend assemblies and [/moduleassemblyname (C# Compiler Option)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), which work under **/langversion:ISO-1**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="cd57d-136">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cd57d-136">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="cd57d-137">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="cd57d-137">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="cd57d-138">Klikněte **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="cd57d-138">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="cd57d-139">Klikněte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="cd57d-139">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="cd57d-140">Změnit **jazyková verze** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cd57d-140">Modify the **Language Version** property.</span></span>  
  
 <span data-ttu-id="cd57d-141">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd57d-141">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="cd57d-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd57d-142">See Also</span></span>  
 [<span data-ttu-id="cd57d-143">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="cd57d-143">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="cd57d-144">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="cd57d-144">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a><span data-ttu-id="cd57d-145">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cd57d-145">C# Language Specification</span></span>
 <span data-ttu-id="cd57d-146">[Referenční dokumentace specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md) : Foundation rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="cd57d-146">[C# Language Specification Reference](../../../csharp/language-reference/language-specification/index.md) : .NET Foundation</span></span>  
 <span data-ttu-id="cd57d-147">C# 1.0/1.1 [ISO/IEC 23270: 2003](https://www.iso.org/standard/36768.html) informačních technologií – specifikace jazyka C#: ISO katalogu</span><span class="sxs-lookup"><span data-stu-id="cd57d-147">C# 1.0/1.1 [ISO/IEC 23270:2003](https://www.iso.org/standard/36768.html) Information technology -- C# Language Specification : ISO Catalogue</span></span>  
 <span data-ttu-id="cd57d-148">C# 2.0 [ISO/IEC 23270: 2006](https://www.iso.org/standard/42926.html) informačních technologií – specifikace jazyka C#: ISO katalogu</span><span class="sxs-lookup"><span data-stu-id="cd57d-148">C# 2.0 [ISO/IEC 23270:2006](https://www.iso.org/standard/42926.html) Information technology -- C# Language Specification : ISO Catalogue</span></span>  
 <span data-ttu-id="cd57d-149">C# 2.0 [c042926_ISO_IEC_23270_2006 (E) .zip](http://go.microsoft.com/fwlink/?LinkId=144406) ISO/IEC 23270: 2006 ve formátu PDF: volně dostupných standardy ISO</span><span class="sxs-lookup"><span data-stu-id="cd57d-149">C# 2.0 [c042926_ISO_IEC_23270_2006(E).zip](http://go.microsoft.com/fwlink/?LinkId=144406) ISO/IEC 23270:2006 in PDF format : ISO Freely Available Standards</span></span>  
 <span data-ttu-id="cd57d-150">C# 3.0 [CSharp jazyk Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# jazyková specifikace verze 3.0: Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="cd57d-150">C# 3.0 [CSharp Language Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# Language Specification Version 3.0 : Microsoft Corporation</span></span>  
 <span data-ttu-id="cd57d-151">C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) Standard Edition 4. ECMA-334</span><span class="sxs-lookup"><span data-stu-id="cd57d-151">C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) Standard ECMA-334 4th Edition</span></span>    
 <span data-ttu-id="cd57d-152">C# 5.0 [CSharp jazyk Specification.docx](https://www.microsoft.com/download/details.aspx?id=7029) C# jazyková specifikace verze 5.0: Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="cd57d-152">C# 5.0 [CSharp Language Specification.docx](https://www.microsoft.com/download/details.aspx?id=7029) C# Language Specification Version 5.0 : Microsoft Corporation</span></span>  
 <span data-ttu-id="cd57d-153">C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# jazyková specifikace verze 6 - neoficiální konceptu: Foundation rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="cd57d-153">C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# Language Specification Version 6 - Unofficial Draft : .NET Foundation</span></span>  
 <span data-ttu-id="cd57d-154">C# 7.0 (není aktuálně k dispozici)</span><span class="sxs-lookup"><span data-stu-id="cd57d-154">C# 7.0 (not currently available)</span></span>  

<!--- Uncomment and add to the above when they become officially released
 C# 7.1 (spec is not yet finished)  
 C# 7.2 (spec is not yet finished)  
 C# 8.0 (spec is not yet finished)  
-->

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a><span data-ttu-id="cd57d-155">Vyžadovaná pro podporu všech funkcí jazyka kompilátoru minimální verze</span><span class="sxs-lookup"><span data-stu-id="cd57d-155">Minimum compiler version needed to support all language features</span></span>   
<span data-ttu-id="cd57d-156">[↩](#TDefault)<a name="FDefault">výchozí</a>, <a name="FISO1">ISO1</a>: nástroje sady Microsoft Visual Studio nebo sestavení .net 2002 nebo připojené rozhraní .net Framework 1.0 kompilátoru</span><span class="sxs-lookup"><span data-stu-id="cd57d-156">[↩](#TDefault)<a name="FDefault">Default</a>, <a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .Net 2002 or bundled .Net Framework 1.0 compiler</span></span>     
<span data-ttu-id="cd57d-157">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio nebo sestavení nástroje 2005 nebo připojené rozhraní .net Framework 2.0 kompilátoru</span><span class="sxs-lookup"><span data-stu-id="cd57d-157">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 or bundled .Net Framework 2.0 compiler</span></span>    
<span data-ttu-id="cd57d-158">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio nebo sestavení nástroje 2008 nebo připojené rozhraní .net Framework 3.5 kompilátoru</span><span class="sxs-lookup"><span data-stu-id="cd57d-158">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 or bundled .Net Framework 3.5 compiler</span></span>    
<span data-ttu-id="cd57d-159">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio nebo sestavení nástroje 2010 nebo připojené rozhraní .net Framework 4.0 kompilátoru</span><span class="sxs-lookup"><span data-stu-id="cd57d-159">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 or bundled .Net Framework 4.0 compiler</span></span>    
<span data-ttu-id="cd57d-160">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio nebo sestavení nástroje 2012 nebo připojené rozhraní .net Framework 4.5 kompilátoru</span><span class="sxs-lookup"><span data-stu-id="cd57d-160">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 or bundled .Net Framework 4.5 compiler</span></span>    
<span data-ttu-id="cd57d-161">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio nebo sestavení nástroje 2015</span><span class="sxs-lookup"><span data-stu-id="cd57d-161">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015</span></span>    
<span data-ttu-id="cd57d-162">[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">nejnovější</a>: Microsoft Visual Studio nebo sestavení nástroje 2017</span><span class="sxs-lookup"><span data-stu-id="cd57d-162">[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">Latest</a>: Microsoft Visual Studio/Build Tools 2017</span></span>   

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS8)<a name="FCS71">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
