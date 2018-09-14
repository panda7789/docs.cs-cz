---
title: Kompilátor XSLT (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 470dd0eb37d8081d388ef69b204293f568096a5e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516983"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="7dc6d-102">Kompilátor XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="7dc6d-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="7dc6d-103">Kompilátor XSLT (xsltc.exe) zkompiluje šablon stylů XSLT a generuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="7dc6d-104">Zkompilované šablony stylů je pak možné předat přímo do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7dc6d-105">Podepsaná sestavení s xsltc.exe nelze generovat.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="7dc6d-106">Nástroj xsltc.exe je součástí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="7dc6d-107">Další informace najdete v tématu [stahování sady Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="7dc6d-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dc6d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7dc6d-108">Syntax</span></span>  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="7dc6d-109">Argument</span><span class="sxs-lookup"><span data-stu-id="7dc6d-109">Argument</span></span>  
  
|<span data-ttu-id="7dc6d-110">Argument</span><span class="sxs-lookup"><span data-stu-id="7dc6d-110">Argument</span></span>|<span data-ttu-id="7dc6d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="7dc6d-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="7dc6d-112">Určuje název šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="7dc6d-113">Šablona stylů musí být místní soubor nebo umístěného v intranetu.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="7dc6d-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="7dc6d-114">Options</span></span>  
  
|<span data-ttu-id="7dc6d-115">Možnost</span><span class="sxs-lookup"><span data-stu-id="7dc6d-115">Option</span></span>|<span data-ttu-id="7dc6d-116">Popis</span><span class="sxs-lookup"><span data-stu-id="7dc6d-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7dc6d-117">`/c[lass]:``name`</span><span class="sxs-lookup"><span data-stu-id="7dc6d-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="7dc6d-118">Určuje název třídy pro následující šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="7dc6d-119">Může být plně kvalifikovaný název třídy.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="7dc6d-120">Výchozí název třídy na název šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="7dc6d-121">Například pokud je kompilován customers.xsl list stylu, výchozí název třídy je zákazníkům.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="7dc6d-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="7dc6d-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="7dc6d-123">Určuje, jestli se má generovat ladicí informace.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="7dc6d-124">Určení `+` nebo `/debug`, způsobí, že kompilátor generovat ladicí informace a vložit ho do souboru databáze (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="7dc6d-125">Název generovaného souboru PDB je `assemblyName`.pdb.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="7dc6d-126">Určení `-`, který je v platnosti, pokud nezadáte `/debug`, způsobí, že žádné informace o ladění, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="7dc6d-127">Maloobchodní sestavení je generováno.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-127">A retail assembly is generated.</span></span> <span data-ttu-id="7dc6d-128">**Poznámka:** kompilace v režimu ladění může významně ovlivnit výkon XSLT.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="7dc6d-129">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="7dc6d-130">Potlačí zprávu o autorských právech kompilátoru ze zobrazení.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="7dc6d-131">`/platform:``string`</span><span class="sxs-lookup"><span data-stu-id="7dc6d-131">`/platform:` `string`</span></span>|<span data-ttu-id="7dc6d-132">Určuje sestavení můžete spustit na platformách.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="7dc6d-133">Následující část popisuje hodnoty platné platformy:</span><span class="sxs-lookup"><span data-stu-id="7dc6d-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="7dc6d-134">`x86` kompiluje sestavení ke spuštění v 32bitové, které je kompatibilní x86 common language runtime</span><span class="sxs-lookup"><span data-stu-id="7dc6d-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="7dc6d-135">`x64` kompiluje sestavení ke spuštění modulem common language runtime 64-bit na počítači, který podporuje AMD64 nebo EM64T instrukční sadu.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)]<span data-ttu-id="7dc6d-136"> kompiluje sestavení ke spuštění modulem common language runtime 64-bit na počítači, který má [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] procesoru.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-136"> compiles your assembly to be run by the 64-bit common language runtime on a computer that has an [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] processor.</span></span><br /><br /> <span data-ttu-id="7dc6d-137">`anycpu` Kompiluje sestavení pro spouštěn na libovolné platformě.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="7dc6d-138">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-138">This is the default.</span></span>|  
|<span data-ttu-id="7dc6d-139">`/out:``assemblyName`</span><span class="sxs-lookup"><span data-stu-id="7dc6d-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="7dc6d-140">Určuje název sestavení, které je výstup.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="7dc6d-141">Název sestavení použije výchozí název hlavní šablony stylů nebo první šablony stylů, pokud jsou k dispozici více šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="7dc6d-142">Pokud šablona stylů obsahuje skripty, skripty se uloží do samostatného sestavení.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="7dc6d-143">Názvy sestavení skriptu se generují z názvu hlavní sestavení.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="7dc6d-144">Například pokud jste zadali pro název vašeho sestavení CustOrders.dll, první skript sestavení je pojmenováno CustOrders_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="7dc6d-145">`/settings:``document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="7dc6d-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="7dc6d-146">Určuje, jestli se má povolit `document()` funkce XSLT skriptu nebo dokumentu typ definice (DTD) v šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="7dc6d-147">Výchozí chování zakáže podporu pro DTD, `document()` funkce a skriptování.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="7dc6d-148">`@``file`</span><span class="sxs-lookup"><span data-stu-id="7dc6d-148">`@` `file`</span></span>|<span data-ttu-id="7dc6d-149">Umožňuje určit soubor obsahující možnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="7dc6d-150">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dc6d-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7dc6d-151">Remarks</span></span>  
 <span data-ttu-id="7dc6d-152">Řešení XSLT se může skládat z více modulů list stylu.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="7dc6d-153">Nástroj xsltc.exe generuje sestavení ze šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="7dc6d-154">Sestavení je pak možné předat do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7dc6d-155">To může pomoct snížit náklady na výkon v některých scénářích nasazení XSLT.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7dc6d-156">Je také nutné uvést zkompilovaného sestavení jako odkaz ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="7dc6d-157">Nástroj xsltc.exe nelze ověřit třídu (`/class:``name`) nebo sestavení (`/out:``assemblyName`) názvy.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-157">The xsltc.exe tool does not validate the class (`/class:``name`) or assembly (`/out:``assemblyName`) names.</span></span> <span data-ttu-id="7dc6d-158">Chyby jsou vyvolány pomocí modul common language runtime, pokud názvy nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7dc6d-159">Příklady</span><span class="sxs-lookup"><span data-stu-id="7dc6d-159">Examples</span></span>  
 <span data-ttu-id="7dc6d-160">Následující příkaz zkompiluje šablony stylů a vytvoří sestavení s názvem booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="7dc6d-161">Následující příkaz zkompiluje šablony stylů a vytvoří sestavení a soubor PDB, které jsou pojmenovány booksort.dll a booksort.pdb v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="7dc6d-162">Následující příkaz zkompiluje šablony stylů, která obsahuje element msxsl: Script a vytvoří dvě sestavení s názvem calc.dll a calc_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="7dc6d-163">Následující příkaz povolí zpracování a skript podporu specifikace DTD a vytvoří dvě sestavení s názvem myTest.dll a myTest_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="7dc6d-164">Následující příkaz pro kompilaci dvou modulů list stylu a vytvoří jednoho sestavení s názvem booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="7dc6d-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="7dc6d-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7dc6d-165">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>  
- [<span data-ttu-id="7dc6d-166">Postup: Provedení transformace XSLT pomocí sestavení</span><span class="sxs-lookup"><span data-stu-id="7dc6d-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
- [<span data-ttu-id="7dc6d-167">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="7dc6d-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
