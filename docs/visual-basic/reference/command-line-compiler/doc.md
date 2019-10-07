---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: 3da049b912d791f26814bb4b6cbb70998803726a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005645"
---
# <a name="-doc"></a><span data-ttu-id="e7683-102">-doc</span><span class="sxs-lookup"><span data-stu-id="e7683-102">-doc</span></span>
<span data-ttu-id="e7683-103">Zpracuje komentáře dokumentace do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="e7683-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7683-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7683-104">Syntax</span></span>  
  
```console  
-doc[+ | -]  
```

<span data-ttu-id="e7683-105">or</span><span class="sxs-lookup"><span data-stu-id="e7683-105">or</span></span>  

```console
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="e7683-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="e7683-106">Arguments</span></span>  
  
|<span data-ttu-id="e7683-107">Termín</span><span class="sxs-lookup"><span data-stu-id="e7683-107">Term</span></span>|<span data-ttu-id="e7683-108">Definice</span><span class="sxs-lookup"><span data-stu-id="e7683-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="e7683-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e7683-109">`+` &#124; `-`</span></span>|<span data-ttu-id="e7683-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e7683-110">Optional.</span></span> <span data-ttu-id="e7683-111">Zadáním + nebo pouhým `-doc` způsobí, že kompilátor vygeneruje informace o dokumentaci a umístí je do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="e7683-111">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="e7683-112">Zadání `-` je ekvivalentem neurčení `-doc`, což nezpůsobí vytvoření informací o dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="e7683-112">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="e7683-113">Vyžaduje se, pokud se používá `-doc:`.</span><span class="sxs-lookup"><span data-stu-id="e7683-113">Required if `-doc:` is used.</span></span> <span data-ttu-id="e7683-114">Určuje výstupní soubor XML, který je vyplněn komentáři ze souborů zdrojového kódu kompilace.</span><span class="sxs-lookup"><span data-stu-id="e7683-114">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="e7683-115">Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="e7683-115">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7683-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7683-116">Remarks</span></span>  
 <span data-ttu-id="e7683-117">Možnost `-doc` určuje, zda kompilátor generuje soubor XML obsahující dokumentační komentáře.</span><span class="sxs-lookup"><span data-stu-id="e7683-117">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="e7683-118">Použijete-li syntaxi `-doc:file`, parametr `file` určuje název souboru XML.</span><span class="sxs-lookup"><span data-stu-id="e7683-118">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="e7683-119">Použijete-li `-doc` nebo `-doc+`, kompilátor převezme název souboru XML ze spustitelného souboru nebo knihovny, kterou vytvořil kompilátor.</span><span class="sxs-lookup"><span data-stu-id="e7683-119">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="e7683-120">Použijete-li `-doc-` nebo nezadáte možnost `-doc`, kompilátor nevytvoří soubor XML.</span><span class="sxs-lookup"><span data-stu-id="e7683-120">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="e7683-121">V souborech zdrojového kódu mohou komentáře k dokumentaci předcházet následující definice:</span><span class="sxs-lookup"><span data-stu-id="e7683-121">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
- <span data-ttu-id="e7683-122">Uživatelsky definované typy, jako je [Třída](../../../visual-basic/language-reference/statements/class-statement.md) nebo [rozhraní](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="e7683-122">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
- <span data-ttu-id="e7683-123">Členy, jako je pole, [událost](../../../visual-basic/language-reference/statements/event-statement.md), [vlastnost](../../../visual-basic/language-reference/statements/property-statement.md), [funkce](../../../visual-basic/language-reference/statements/function-statement.md)nebo [subrutina](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e7683-123">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="e7683-124">Chcete-li použít vygenerovaný soubor XML s funkcí Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) , nechte název souboru XML stejný jako sestavení, které chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="e7683-124">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="e7683-125">Ujistěte se, že soubor XML je ve stejném adresáři jako sestavení, takže pokud je na sestavení odkazováno v projektu sady Visual Studio, je nalezen soubor. XML také.</span><span class="sxs-lookup"><span data-stu-id="e7683-125">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="e7683-126">Soubory dokumentace XML nejsou vyžadovány, aby technologie IntelliSense pracovala pro kód v rámci projektu nebo v rámci projektů, na které se odkazuje v projektu.</span><span class="sxs-lookup"><span data-stu-id="e7683-126">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="e7683-127">Pokud nekompilujete s `/target:module`, soubor XML obsahuje značky `<assembly></assembly>`.</span><span class="sxs-lookup"><span data-stu-id="e7683-127">Unless you compile with `/target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="e7683-128">Tyto značky určují název souboru obsahujícího manifest sestavení pro výstupní soubor kompilace.</span><span class="sxs-lookup"><span data-stu-id="e7683-128">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="e7683-129">Způsoby, jak generovat dokumentaci z komentářů v kódu, naleznete v tématu [značky komentářů XML](../../../visual-basic/language-reference/xmldoc/index.md) .</span><span class="sxs-lookup"><span data-stu-id="e7683-129">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="e7683-130">Nastavení-doc v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e7683-130">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="e7683-131">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="e7683-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e7683-132">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="e7683-132">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="e7683-133">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="e7683-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="e7683-134">3. Nastavte hodnotu v poli **Generovat soubor dokumentace XML** .</span><span class="sxs-lookup"><span data-stu-id="e7683-134">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e7683-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7683-135">Example</span></span>  
 <span data-ttu-id="e7683-136">Ukázku naleznete v tématu [dokumentování kódu pomocí XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) .</span><span class="sxs-lookup"><span data-stu-id="e7683-136">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7683-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7683-137">See also</span></span>

- [<span data-ttu-id="e7683-138">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="e7683-138">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e7683-139">Dokumentace kódu s XML</span><span class="sxs-lookup"><span data-stu-id="e7683-139">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
