---
title: -doc
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0948b9ef0675541ca595bb297e01e62c9d79a181
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-doc"></a><span data-ttu-id="05bfe-102">-doc</span><span class="sxs-lookup"><span data-stu-id="05bfe-102">-doc</span></span>
<span data-ttu-id="05bfe-103">Zpracuje dokumentační komentáře do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="05bfe-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05bfe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05bfe-104">Syntax</span></span>  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="05bfe-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="05bfe-105">Arguments</span></span>  
  
|<span data-ttu-id="05bfe-106">Termín</span><span class="sxs-lookup"><span data-stu-id="05bfe-106">Term</span></span>|<span data-ttu-id="05bfe-107">Definice</span><span class="sxs-lookup"><span data-stu-id="05bfe-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="05bfe-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="05bfe-108">`+` &#124; `-`</span></span>|<span data-ttu-id="05bfe-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="05bfe-109">Optional.</span></span> <span data-ttu-id="05bfe-110">Určení +, nebo jenom `-doc`, způsobí, že kompilátor generovat informace o dokumentaci a umístěte jej do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="05bfe-110">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="05bfe-111">Určení `-` je ekvivalentem není zadávání `-doc`, způsobuje žádné informace dokumentaci, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="05bfe-111">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="05bfe-112">Požadováno pokud `-doc:` se používá.</span><span class="sxs-lookup"><span data-stu-id="05bfe-112">Required if `-doc:` is used.</span></span> <span data-ttu-id="05bfe-113">Určuje výstupního souboru XML, který se zobrazí v komentářů ze souborů zdrojového kódu kompilace.</span><span class="sxs-lookup"><span data-stu-id="05bfe-113">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="05bfe-114">Pokud název souboru obsahuje mezery, uzavřete název uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="05bfe-114">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05bfe-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05bfe-115">Remarks</span></span>  
 <span data-ttu-id="05bfe-116">`-doc` Možnost ovládací prvky, zda kompilátor vygeneruje soubor XML obsahující dokumentační komentáře.</span><span class="sxs-lookup"><span data-stu-id="05bfe-116">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="05bfe-117">Pokud použijete `-doc:file` syntaxi, která `file` parametr určuje název souboru XML.</span><span class="sxs-lookup"><span data-stu-id="05bfe-117">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="05bfe-118">Pokud používáte `-doc` nebo `-doc+`, kompilátor použije název souboru XML z spustitelný soubor nebo knihovny, který vytváří kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="05bfe-118">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="05bfe-119">Pokud používáte `-doc-` nebo nezadávejte `-doc` možnost kompilátor nevytváří soubor XML.</span><span class="sxs-lookup"><span data-stu-id="05bfe-119">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="05bfe-120">V souborech zdrojového kódu lze předcházet dokumentační komentáře následující definice:</span><span class="sxs-lookup"><span data-stu-id="05bfe-120">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
-   <span data-ttu-id="05bfe-121">Uživatelem definované typy, jako například [třída](../../../visual-basic/language-reference/statements/class-statement.md) nebo [rozhraní](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="05bfe-121">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
-   <span data-ttu-id="05bfe-122">Členové, jako je například pole, [událostí](../../../visual-basic/language-reference/statements/event-statement.md), [vlastnost](../../../visual-basic/language-reference/statements/property-statement.md), [funkce](../../../visual-basic/language-reference/statements/function-statement.md), nebo [podprogramu](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="05bfe-122">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="05bfe-123">Použít generovaný soubor XML s [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense) funkci, ponechte název souboru XML být stejný jako sestavení, které chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="05bfe-123">To use the generated XML file with the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="05bfe-124">Zkontrolujte, zda je soubor XML ve stejném adresáři jako sestavení tak, aby při sestavení odkazuje [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] projektu soubor .xml nalezen také.</span><span class="sxs-lookup"><span data-stu-id="05bfe-124">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] project, the .xml file is found as well.</span></span> <span data-ttu-id="05bfe-125">Soubory dokumentace XML nejsou potřeba pro technologii IntelliSense, která pracují pro kódu v rámci projektu nebo projekty odkazuje na projekt.</span><span class="sxs-lookup"><span data-stu-id="05bfe-125">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="05bfe-126">Pokud je kompilovat s `/target:module`, soubor XML obsahuje značek `<assembly></assembly>`.</span><span class="sxs-lookup"><span data-stu-id="05bfe-126">Unless you compile with `/target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="05bfe-127">Tyto značky zadejte název souboru, který obsahuje manifest sestavení pro výstupní soubor kompilace.</span><span class="sxs-lookup"><span data-stu-id="05bfe-127">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="05bfe-128">V tématu [značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) pro způsoby, jak generovat dokumentaci z komentářů v kódu.</span><span class="sxs-lookup"><span data-stu-id="05bfe-128">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="05bfe-129">Chcete-li nastavit - dokumentů v sadě Visual Studio integrované vývojové prostředí</span><span class="sxs-lookup"><span data-stu-id="05bfe-129">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="05bfe-130">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="05bfe-130">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="05bfe-131">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="05bfe-131">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="05bfe-132">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="05bfe-132">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="05bfe-133">3.  Nastavte hodnotu v **souborů dokumentace XML vygenerovat** pole.</span><span class="sxs-lookup"><span data-stu-id="05bfe-133">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="05bfe-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="05bfe-134">Example</span></span>  
 <span data-ttu-id="05bfe-135">V tématu [dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) pro ukázku.</span><span class="sxs-lookup"><span data-stu-id="05bfe-135">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05bfe-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="05bfe-136">See Also</span></span>  
 [<span data-ttu-id="05bfe-137">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="05bfe-137">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="05bfe-138">Dokumentace kódu s XML</span><span class="sxs-lookup"><span data-stu-id="05bfe-138">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
