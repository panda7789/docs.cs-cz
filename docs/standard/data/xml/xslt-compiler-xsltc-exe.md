---
title: "Kompilátoru XSLT (xsltc.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2b4ede7bdb8dad65e9cd959dfaa2f8956a877762
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="ef16e-102">Kompilátoru XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="ef16e-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="ef16e-103">Kompilátor XSLT (xsltc.exe) kompiluje XSLT šablony stylů a generuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef16e-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="ef16e-104">Kompilované šablony stylů mohou být předány pak přímo do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="ef16e-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ef16e-105">Podepsaná sestavení s xsltc.exe nelze vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="ef16e-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="ef16e-106">Nástroj xsltc.exe je součástí sady Visual Studio 2008.</span><span class="sxs-lookup"><span data-stu-id="ef16e-106">The xsltc.exe tool is included with Visual Studio 2008.</span></span> <span data-ttu-id="ef16e-107">Další informace najdete v tématu [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=89463).</span><span class="sxs-lookup"><span data-stu-id="ef16e-107">For more information, see the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=89463).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef16e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef16e-108">Syntax</span></span>  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="ef16e-109">Argument</span><span class="sxs-lookup"><span data-stu-id="ef16e-109">Argument</span></span>  
  
|<span data-ttu-id="ef16e-110">Argument</span><span class="sxs-lookup"><span data-stu-id="ef16e-110">Argument</span></span>|<span data-ttu-id="ef16e-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ef16e-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="ef16e-112">Určuje název šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="ef16e-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="ef16e-113">Šablony stylů musí být místní soubor nebo se nachází na intranetu.</span><span class="sxs-lookup"><span data-stu-id="ef16e-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="ef16e-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ef16e-114">Options</span></span>  
  
|<span data-ttu-id="ef16e-115">Možnost</span><span class="sxs-lookup"><span data-stu-id="ef16e-115">Option</span></span>|<span data-ttu-id="ef16e-116">Popis</span><span class="sxs-lookup"><span data-stu-id="ef16e-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ef16e-117">`/c[lass]:``name`</span><span class="sxs-lookup"><span data-stu-id="ef16e-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="ef16e-118">Určuje název třídy pro následující šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="ef16e-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="ef16e-119">Může být plně kvalifikovaný název třídy.</span><span class="sxs-lookup"><span data-stu-id="ef16e-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="ef16e-120">Název třídy výchozí název šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="ef16e-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="ef16e-121">Například pokud customers.xsl list stylu zkompilován, výchozí název třídy je zákazníků.</span><span class="sxs-lookup"><span data-stu-id="ef16e-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="ef16e-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="ef16e-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="ef16e-123">Určuje, jestli se má generovat ladicí informace.</span><span class="sxs-lookup"><span data-stu-id="ef16e-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="ef16e-124">Určení `+` nebo `/debug`, způsobí, že kompilátor generovat ladicí informace a umístí jej do souboru databáze (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="ef16e-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="ef16e-125">Je název vygenerovaný soubor PDB `assemblyName`pdb.</span><span class="sxs-lookup"><span data-stu-id="ef16e-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="ef16e-126">Určení `-`, který je v platnosti, pokud nezadáte `/debug`, způsobí, že žádné informace o ladění, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="ef16e-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="ef16e-127">Generuje se prodejní sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef16e-127">A retail assembly is generated.</span></span> <span data-ttu-id="ef16e-128">**Poznámka:** kompilace v režimu ladění může výrazně ovlivnit výkon XSLT.</span><span class="sxs-lookup"><span data-stu-id="ef16e-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="ef16e-129">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="ef16e-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="ef16e-130">Potlačí zpráva o autorských právech kompilátoru ze zobrazení.</span><span class="sxs-lookup"><span data-stu-id="ef16e-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="ef16e-131">`/platform:``string`</span><span class="sxs-lookup"><span data-stu-id="ef16e-131">`/platform:` `string`</span></span>|<span data-ttu-id="ef16e-132">Určuje platformy, které lze spustit sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef16e-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="ef16e-133">Následující text popisuje platformy platné hodnoty:</span><span class="sxs-lookup"><span data-stu-id="ef16e-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="ef16e-134">`x86`zkompiluje vaše sestavení ke spuštění 32-bit, kompatibilní s x86 common language runtime</span><span class="sxs-lookup"><span data-stu-id="ef16e-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="ef16e-135">`x64`zkompiluje vaše sestavení pro modul common language runtime 64-bit spustit na počítači, který podporuje AMD64 nebo EM64T sada instrukcí.</span><span class="sxs-lookup"><span data-stu-id="ef16e-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)]<span data-ttu-id="ef16e-136">zkompiluje vaše sestavení pro modul common language runtime 64-bit spustit na počítači, který má [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] procesoru.</span><span class="sxs-lookup"><span data-stu-id="ef16e-136"> compiles your assembly to be run by the 64-bit common language runtime on a computer that has an [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] processor.</span></span><br /><br /> <span data-ttu-id="ef16e-137">`anycpu`zkompiluje vaše sestavení pro spouštěn na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="ef16e-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="ef16e-138">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="ef16e-138">This is the default.</span></span>|  
|<span data-ttu-id="ef16e-139">`/out:``assemblyName`</span><span class="sxs-lookup"><span data-stu-id="ef16e-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="ef16e-140">Určuje název sestavení, které je výstup.</span><span class="sxs-lookup"><span data-stu-id="ef16e-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="ef16e-141">Pokud jsou k dispozici více šablon stylů, výchozí název sestavení název hlavní šablony stylů nebo první šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="ef16e-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="ef16e-142">Pokud list stylu obsahuje skripty, skripty se uloží do samostatné sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef16e-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="ef16e-143">Z názvu hlavní sestavení se generují názvy sestavení skriptu.</span><span class="sxs-lookup"><span data-stu-id="ef16e-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="ef16e-144">Například pokud jste zadali CustOrders.dll pro název sestavení, první sestavení skriptu název CustOrders_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="ef16e-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="ef16e-145">`/settings:``document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="ef16e-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="ef16e-146">Určuje, jestli se má povolit `document()` funkce, skript XSLT nebo dokumentu zadejte definice (DTD) v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="ef16e-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="ef16e-147">Zakáže podporu pro DTD, použije se výchozí chování `document()` funkce a skriptování.</span><span class="sxs-lookup"><span data-stu-id="ef16e-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="ef16e-148">`@``file`</span><span class="sxs-lookup"><span data-stu-id="ef16e-148">`@` `file`</span></span>|<span data-ttu-id="ef16e-149">Umožňuje zadat soubor, který obsahuje možnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ef16e-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="ef16e-150">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="ef16e-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef16e-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef16e-151">Remarks</span></span>  
 <span data-ttu-id="ef16e-152">XSLT řešení se může skládat z více modulů list stylu.</span><span class="sxs-lookup"><span data-stu-id="ef16e-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="ef16e-153">Nástroj xsltc.exe generuje sestavení ze šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="ef16e-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="ef16e-154">Sestavení může být předána do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="ef16e-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ef16e-155">To může pomoct snížit náklady na výkon v některých scénářích nasazení XSLT.</span><span class="sxs-lookup"><span data-stu-id="ef16e-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef16e-156">Navíc musí zahrnovat kompilované sestavení jako odkaz v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ef16e-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="ef16e-157">Nástroj xsltc.exe nelze ověřit třídu (`/class:``name`) nebo sestavení (`/out:``assemblyName`) názvy.</span><span class="sxs-lookup"><span data-stu-id="ef16e-157">The xsltc.exe tool does not validate the class (`/class:``name`) or assembly (`/out:``assemblyName`) names.</span></span> <span data-ttu-id="ef16e-158">Chyby jsou vyvolané modul common language runtime, pokud se názvy nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="ef16e-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ef16e-159">Příklady</span><span class="sxs-lookup"><span data-stu-id="ef16e-159">Examples</span></span>  
 <span data-ttu-id="ef16e-160">Následující příkaz zkompiluje šablony stylů a vytvoří sestavení s názvem booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="ef16e-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="ef16e-161">Následující příkaz zkompiluje šablony stylů a vytvoří sestavení a souboru PDB, který je pojmenován booksort.dll a booksort.pdb v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ef16e-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="ef16e-162">Následující příkaz zkompiluje šablony stylů, která obsahuje msxsl:script element a vytvoří dvě sestavení s názvem calc.dll a calc_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="ef16e-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="ef16e-163">Následující příkaz umožňuje podporu specifikace DTD zpracování a skript a vytvoří dvě sestavení s názvem myTest.dll a myTest_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="ef16e-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="ef16e-164">Následující příkaz zkompiluje dva moduly list stylu a vytvoří jednoho sestavení s názvem booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="ef16e-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef16e-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef16e-165">See Also</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="ef16e-166">Postup: provedení transformace XSLT pomocí sestavení</span><span class="sxs-lookup"><span data-stu-id="ef16e-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
 [<span data-ttu-id="ef16e-167">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="ef16e-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
