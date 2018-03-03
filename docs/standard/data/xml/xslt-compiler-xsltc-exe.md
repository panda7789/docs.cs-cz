---
title: XSLT Compiler (xsltc.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 36696617d1e28a370f6b15f15fb39bc816973f15
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/02/2018
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="babad-102">XSLT Compiler (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="babad-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="babad-103">Kompilátor XSLT (xsltc.exe) kompiluje XSLT šablony stylů a generuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="babad-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="babad-104">Kompilované šablony stylů mohou být předány pak přímo do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="babad-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="babad-105">Podepsaná sestavení s xsltc.exe nelze vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="babad-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="babad-106">Nástroj xsltc.exe je součástí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="babad-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="babad-107">Další informace najdete v tématu [Visual Studio stáhne](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="babad-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="babad-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="babad-108">Syntax</span></span>  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="babad-109">Argument</span><span class="sxs-lookup"><span data-stu-id="babad-109">Argument</span></span>  
  
|<span data-ttu-id="babad-110">Argument</span><span class="sxs-lookup"><span data-stu-id="babad-110">Argument</span></span>|<span data-ttu-id="babad-111">Popis</span><span class="sxs-lookup"><span data-stu-id="babad-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="babad-112">Určuje název šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="babad-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="babad-113">Šablony stylů musí být místní soubor nebo se nachází na intranetu.</span><span class="sxs-lookup"><span data-stu-id="babad-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="babad-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="babad-114">Options</span></span>  
  
|<span data-ttu-id="babad-115">Možnost</span><span class="sxs-lookup"><span data-stu-id="babad-115">Option</span></span>|<span data-ttu-id="babad-116">Popis</span><span class="sxs-lookup"><span data-stu-id="babad-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="babad-117">`/c[lass]:``name`</span><span class="sxs-lookup"><span data-stu-id="babad-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="babad-118">Určuje název třídy pro následující šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="babad-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="babad-119">Může být plně kvalifikovaný název třídy.</span><span class="sxs-lookup"><span data-stu-id="babad-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="babad-120">Název třídy výchozí název šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="babad-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="babad-121">Například pokud customers.xsl list stylu zkompilován, výchozí název třídy je zákazníků.</span><span class="sxs-lookup"><span data-stu-id="babad-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="babad-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="babad-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="babad-123">Určuje, jestli se má generovat ladicí informace.</span><span class="sxs-lookup"><span data-stu-id="babad-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="babad-124">Určení `+` nebo `/debug`, způsobí, že kompilátor generovat ladicí informace a umístí jej do souboru databáze (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="babad-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="babad-125">Je název vygenerovaný soubor PDB `assemblyName`pdb.</span><span class="sxs-lookup"><span data-stu-id="babad-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="babad-126">Určení `-`, který je v platnosti, pokud nezadáte `/debug`, způsobí, že žádné informace o ladění, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="babad-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="babad-127">Generuje se prodejní sestavení.</span><span class="sxs-lookup"><span data-stu-id="babad-127">A retail assembly is generated.</span></span> <span data-ttu-id="babad-128">**Poznámka:** kompilace v režimu ladění může výrazně ovlivnit výkon XSLT.</span><span class="sxs-lookup"><span data-stu-id="babad-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="babad-129">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="babad-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="babad-130">Potlačí zpráva o autorských právech kompilátoru ze zobrazení.</span><span class="sxs-lookup"><span data-stu-id="babad-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="babad-131">`/platform:``string`</span><span class="sxs-lookup"><span data-stu-id="babad-131">`/platform:` `string`</span></span>|<span data-ttu-id="babad-132">Určuje platformy, které lze spustit sestavení.</span><span class="sxs-lookup"><span data-stu-id="babad-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="babad-133">Následující text popisuje platformy platné hodnoty:</span><span class="sxs-lookup"><span data-stu-id="babad-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="babad-134">`x86` zkompiluje vaše sestavení ke spuštění 32-bit, kompatibilní s x86 common language runtime</span><span class="sxs-lookup"><span data-stu-id="babad-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="babad-135">`x64` zkompiluje vaše sestavení pro modul common language runtime 64-bit spustit na počítači, který podporuje AMD64 nebo EM64T sada instrukcí.</span><span class="sxs-lookup"><span data-stu-id="babad-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] <span data-ttu-id="babad-136">zkompiluje vaše sestavení pro modul common language runtime 64-bit spustit na počítači, který má [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] procesoru.</span><span class="sxs-lookup"><span data-stu-id="babad-136">compiles your assembly to be run by the 64-bit common language runtime on a computer that has an [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] processor.</span></span><br /><br /> <span data-ttu-id="babad-137">`anycpu` Zkompiluje vaše sestavení pro spouštěn na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="babad-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="babad-138">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="babad-138">This is the default.</span></span>|  
|<span data-ttu-id="babad-139">`/out:``assemblyName`</span><span class="sxs-lookup"><span data-stu-id="babad-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="babad-140">Určuje název sestavení, které je výstup.</span><span class="sxs-lookup"><span data-stu-id="babad-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="babad-141">Pokud jsou k dispozici více šablon stylů, výchozí název sestavení název hlavní šablony stylů nebo první šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="babad-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="babad-142">Pokud list stylu obsahuje skripty, skripty se uloží do samostatné sestavení.</span><span class="sxs-lookup"><span data-stu-id="babad-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="babad-143">Z názvu hlavní sestavení se generují názvy sestavení skriptu.</span><span class="sxs-lookup"><span data-stu-id="babad-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="babad-144">Například pokud jste zadali CustOrders.dll pro název sestavení, první sestavení skriptu název CustOrders_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="babad-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="babad-145">`/settings:``document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="babad-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="babad-146">Určuje, jestli se má povolit `document()` funkce, skript XSLT nebo dokumentu zadejte definice (DTD) v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="babad-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="babad-147">Zakáže podporu pro DTD, použije se výchozí chování `document()` funkce a skriptování.</span><span class="sxs-lookup"><span data-stu-id="babad-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="babad-148">`@``file`</span><span class="sxs-lookup"><span data-stu-id="babad-148">`@` `file`</span></span>|<span data-ttu-id="babad-149">Umožňuje zadat soubor, který obsahuje možnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="babad-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="babad-150">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="babad-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="babad-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="babad-151">Remarks</span></span>  
 <span data-ttu-id="babad-152">XSLT řešení se může skládat z více modulů list stylu.</span><span class="sxs-lookup"><span data-stu-id="babad-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="babad-153">Nástroj xsltc.exe generuje sestavení ze šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="babad-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="babad-154">Sestavení může být předána do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="babad-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="babad-155">To může pomoct snížit náklady na výkon v některých scénářích nasazení XSLT.</span><span class="sxs-lookup"><span data-stu-id="babad-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="babad-156">Navíc musí zahrnovat kompilované sestavení jako odkaz v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="babad-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="babad-157">Nástroj xsltc.exe nelze ověřit třídu (`/class:``name`) nebo sestavení (`/out:``assemblyName`) názvy.</span><span class="sxs-lookup"><span data-stu-id="babad-157">The xsltc.exe tool does not validate the class (`/class:``name`) or assembly (`/out:``assemblyName`) names.</span></span> <span data-ttu-id="babad-158">Chyby jsou vyvolané modul common language runtime, pokud se názvy nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="babad-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="babad-159">Příklady</span><span class="sxs-lookup"><span data-stu-id="babad-159">Examples</span></span>  
 <span data-ttu-id="babad-160">Následující příkaz zkompiluje šablony stylů a vytvoří sestavení s názvem booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="babad-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="babad-161">Následující příkaz zkompiluje šablony stylů a vytvoří sestavení a souboru PDB, který je pojmenován booksort.dll a booksort.pdb v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="babad-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="babad-162">Následující příkaz zkompiluje šablony stylů, která obsahuje msxsl:script element a vytvoří dvě sestavení s názvem calc.dll a calc_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="babad-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="babad-163">Následující příkaz umožňuje podporu specifikace DTD zpracování a skript a vytvoří dvě sestavení s názvem myTest.dll a myTest_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="babad-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="babad-164">Následující příkaz zkompiluje dva moduly list stylu a vytvoří jednoho sestavení s názvem booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="babad-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="babad-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="babad-165">See Also</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="babad-166">Postup: Provedení transformace XSLT pomocí sestavení</span><span class="sxs-lookup"><span data-stu-id="babad-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
 [<span data-ttu-id="babad-167">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="babad-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
