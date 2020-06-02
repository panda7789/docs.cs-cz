---
title: Kompilátor XSLT (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
ms.openlocfilehash: 18f351546699487316858198b705e970de4856c1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282607"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="b06be-102">Kompilátor XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="b06be-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="b06be-103">Kompilátor XSLT (xsltc. exe) kompiluje šablony stylů XSLT a generuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="b06be-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="b06be-104">Kompilovaná šablona stylů může být předána přímo do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b06be-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b06be-105">Nelze generovat podepsaná sestavení pomocí xsltc. exe.</span><span class="sxs-lookup"><span data-stu-id="b06be-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="b06be-106">Nástroj xsltc. exe je součástí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b06be-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="b06be-107">Další informace najdete v tématu [soubory ke stažení pro Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="b06be-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b06be-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b06be-108">Syntax</span></span>  
  
```console  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="b06be-109">Argument</span><span class="sxs-lookup"><span data-stu-id="b06be-109">Argument</span></span>  
  
|<span data-ttu-id="b06be-110">Argument</span><span class="sxs-lookup"><span data-stu-id="b06be-110">Argument</span></span>|<span data-ttu-id="b06be-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b06be-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="b06be-112">Určuje název předlohy se styly.</span><span class="sxs-lookup"><span data-stu-id="b06be-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="b06be-113">Šablona stylů musí být místní soubor nebo se nachází na intranetu.</span><span class="sxs-lookup"><span data-stu-id="b06be-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="b06be-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="b06be-114">Options</span></span>  
  
|<span data-ttu-id="b06be-115">Možnost</span><span class="sxs-lookup"><span data-stu-id="b06be-115">Option</span></span>|<span data-ttu-id="b06be-116">Popis</span><span class="sxs-lookup"><span data-stu-id="b06be-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b06be-117">`/c[lass]:` `name`</span><span class="sxs-lookup"><span data-stu-id="b06be-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="b06be-118">Určuje název třídy pro následující šablonu stylů.</span><span class="sxs-lookup"><span data-stu-id="b06be-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="b06be-119">Název třídy může být plně kvalifikovaný.</span><span class="sxs-lookup"><span data-stu-id="b06be-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="b06be-120">Název třídy je ve výchozím nastavení název předlohy se styly.</span><span class="sxs-lookup"><span data-stu-id="b06be-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="b06be-121">Například pokud je tabulka stylů Customers. XSL je kompilována, výchozí název třídy je Customers.</span><span class="sxs-lookup"><span data-stu-id="b06be-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="b06be-122">`/debug[`+&#124; –`]`</span><span class="sxs-lookup"><span data-stu-id="b06be-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="b06be-123">Určuje, zda se mají generovat ladicí informace.</span><span class="sxs-lookup"><span data-stu-id="b06be-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="b06be-124">Při zadání `+` nebo `/debug` způsobí, že kompilátor vygeneruje ladicí informace a umístí je do souboru programu databáze (PDB).</span><span class="sxs-lookup"><span data-stu-id="b06be-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="b06be-125">Název generovaného souboru PDB je `assemblyName` . pdb.</span><span class="sxs-lookup"><span data-stu-id="b06be-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="b06be-126">Určení `-` , které platí v případě, že neurčíte `/debug` , nezpůsobí vytváření ladicích informací.</span><span class="sxs-lookup"><span data-stu-id="b06be-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="b06be-127">Vygeneruje se maloobchodní sestavení.</span><span class="sxs-lookup"><span data-stu-id="b06be-127">A retail assembly is generated.</span></span> <span data-ttu-id="b06be-128">**Poznámka:**  Kompilace v režimu ladění může významně ovlivnit výkon XSLT.</span><span class="sxs-lookup"><span data-stu-id="b06be-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="b06be-129">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="b06be-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="b06be-130">Potlačí zobrazení zprávy o autorských právech kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b06be-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="b06be-131">`/platform:` `string`</span><span class="sxs-lookup"><span data-stu-id="b06be-131">`/platform:` `string`</span></span>|<span data-ttu-id="b06be-132">Určuje platformy, na kterých lze spustit sestavení.</span><span class="sxs-lookup"><span data-stu-id="b06be-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="b06be-133">Následující popis obsahuje platné hodnoty platformy:</span><span class="sxs-lookup"><span data-stu-id="b06be-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="b06be-134">`x86`zkompiluje sestavení tak, aby běželo 32 modul CLR (Common Language Runtime) kompatibilním s platformou x86.</span><span class="sxs-lookup"><span data-stu-id="b06be-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="b06be-135">`x64`zkompiluje sestavení tak, aby běželo pomocí 64 modulu CLR (Common Language Runtime) v počítači, který podporuje instrukční sady AMD64 nebo EM64T.</span><span class="sxs-lookup"><span data-stu-id="b06be-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> <span data-ttu-id="b06be-136">Procesory Itanium zkompiluje vaše sestavení tak, aby bylo spuštěno pomocí 64 modulu CLR (Common Language Runtime) v počítači, který má procesor s procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="b06be-136">Itanium compiles your assembly to be run by the 64-bit common language runtime on a computer that has an Itanium processor.</span></span><br /><br /> <span data-ttu-id="b06be-137">`anycpu`zkompiluje sestavení pro spuštění na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="b06be-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="b06be-138">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="b06be-138">This is the default.</span></span>|  
|<span data-ttu-id="b06be-139">`/out:` `assemblyName`</span><span class="sxs-lookup"><span data-stu-id="b06be-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="b06be-140">Určuje název sestavení, které je výstupem.</span><span class="sxs-lookup"><span data-stu-id="b06be-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="b06be-141">Název sestavení je výchozím názvem pro hlavní šablonu stylů nebo první šablonu stylů, pokud je k dispozici více šablon stylů.</span><span class="sxs-lookup"><span data-stu-id="b06be-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="b06be-142">Pokud šablona stylů obsahuje skripty, skripty jsou uloženy do samostatného sestavení.</span><span class="sxs-lookup"><span data-stu-id="b06be-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="b06be-143">Názvy sestavení skriptu jsou generovány z hlavního názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="b06be-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="b06be-144">Například pokud jste pro název sestavení zadali CustOrders. dll, první sestavení skriptu má název CustOrders_Script1. dll.</span><span class="sxs-lookup"><span data-stu-id="b06be-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="b06be-145">`/settings:` `document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="b06be-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="b06be-146">Určuje, zda mají být `document()` v šabloně stylů povoleny funkce, skripty XSLT nebo definice typu dokumentu (DTD).</span><span class="sxs-lookup"><span data-stu-id="b06be-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="b06be-147">Výchozí chování zakáže podporu DTD, `document()` funkce a skriptování.</span><span class="sxs-lookup"><span data-stu-id="b06be-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="b06be-148">`@` `file`</span><span class="sxs-lookup"><span data-stu-id="b06be-148">`@` `file`</span></span>|<span data-ttu-id="b06be-149">Umožňuje zadat soubor, který obsahuje možnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b06be-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="b06be-150">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="b06be-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b06be-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b06be-151">Remarks</span></span>  
 <span data-ttu-id="b06be-152">Řešení XSLT se mohou skládat z několika modulů šablon stylů.</span><span class="sxs-lookup"><span data-stu-id="b06be-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="b06be-153">Nástroj xsltc. exe generuje sestavení ze šablon stylů.</span><span class="sxs-lookup"><span data-stu-id="b06be-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="b06be-154">Sestavení lze následně předat do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b06be-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b06be-155">To může přispět ke snížení nákladů na výkon v některých scénářích nasazení XSLT.</span><span class="sxs-lookup"><span data-stu-id="b06be-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b06be-156">Také je nutné zahrnout zkompilované sestavení jako odkaz do aplikace.</span><span class="sxs-lookup"><span data-stu-id="b06be-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="b06be-157">Nástroj xsltc. exe neověřuje názvy tříd ( `/class:` *Name*) nebo Assembly ( `/out:` *AssemblyName*).</span><span class="sxs-lookup"><span data-stu-id="b06be-157">The xsltc.exe tool does not validate the class (`/class:`*name*) or assembly (`/out:`*assemblyName*) names.</span></span> <span data-ttu-id="b06be-158">Pokud názvy nejsou platné, jsou chyby vyvolány modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b06be-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b06be-159">Příklady</span><span class="sxs-lookup"><span data-stu-id="b06be-159">Examples</span></span>  
 <span data-ttu-id="b06be-160">Následující příkaz zkompiluje šablonu stylů a vytvoří sestavení s názvem booksort. dll.</span><span class="sxs-lookup"><span data-stu-id="b06be-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="b06be-161">Následující příkaz zkompiluje šablonu stylů a vytvoří sestavení a soubor PDB s názvem booksort. dll a booksort. pdb v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b06be-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```console  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="b06be-162">Následující příkaz zkompiluje šablonu stylů obsahující element msxsl: Script a vytvoří dvě sestavení s názvem Calc. dll a calc_Script1. dll.</span><span class="sxs-lookup"><span data-stu-id="b06be-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```console  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="b06be-163">Následující příkaz umožňuje zpracování a podporu skriptu DTD a vytváří dvě sestavení s názvem myTest. dll a myTest_Script1. dll.</span><span class="sxs-lookup"><span data-stu-id="b06be-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```console  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="b06be-164">Následující příkaz zkompiluje dva moduly šablon stylů a vytvoří jedno sestavení s názvem booksort. dll.</span><span class="sxs-lookup"><span data-stu-id="b06be-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="b06be-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="b06be-165">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="b06be-166">Postupy: Provedení transformace XSLT pomocí sestavení</span><span class="sxs-lookup"><span data-stu-id="b06be-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [<span data-ttu-id="b06be-167">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="b06be-167">XSLT Transformations</span></span>](xslt-transformations.md)
