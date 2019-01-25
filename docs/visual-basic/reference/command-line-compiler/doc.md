---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: eccd68d77eb9afabdc3bd4301f6258b80b7d7e7f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736650"
---
# <a name="-doc"></a><span data-ttu-id="cdb2d-102">-doc</span><span class="sxs-lookup"><span data-stu-id="cdb2d-102">-doc</span></span>
<span data-ttu-id="cdb2d-103">Zpracuje komentáře dokumentace do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdb2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdb2d-104">Syntax</span></span>  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="cdb2d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="cdb2d-105">Arguments</span></span>  
  
|<span data-ttu-id="cdb2d-106">Termín</span><span class="sxs-lookup"><span data-stu-id="cdb2d-106">Term</span></span>|<span data-ttu-id="cdb2d-107">Definice</span><span class="sxs-lookup"><span data-stu-id="cdb2d-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="cdb2d-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="cdb2d-108">`+` &#124; `-`</span></span>|<span data-ttu-id="cdb2d-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-109">Optional.</span></span> <span data-ttu-id="cdb2d-110">Určení +, nebo jen `-doc`, způsobí, že kompilátor generovat informace o dokumentaci a umístěte ho do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-110">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="cdb2d-111">Určení `-` je ekvivalentem bez zadání `-doc`, způsobí žádné informace o dokumentaci má být vytvořen.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-111">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="cdb2d-112">Požadováno pokud `-doc:` se používá.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-112">Required if `-doc:` is used.</span></span> <span data-ttu-id="cdb2d-113">Určuje výstupní soubor XML, který je naplněn komentáře v souborech zdrojového kódu kompilace.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-113">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="cdb2d-114">Pokud název souboru obsahuje mezery, uzavřete název uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="cdb2d-114">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdb2d-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cdb2d-115">Remarks</span></span>  
 <span data-ttu-id="cdb2d-116">`-doc` Možnost řídí, zda kompilátor generuje soubor XML obsahující komentáře k dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-116">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="cdb2d-117">Pokud používáte `-doc:file` syntaxe, `file` parametr určuje název souboru XML.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-117">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="cdb2d-118">Pokud používáte `-doc` nebo `-doc+`, kompilátor přijímá název souboru XML ze spustitelného souboru nebo knihovny, který vytváří kompilátor.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-118">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="cdb2d-119">Pokud používáte `-doc-` nebo nezadávejte `-doc` možnost, kompilátor nevytváří soubor XML.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-119">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="cdb2d-120">V souborech zdrojového kódu může dokumentační komentáře předcházet následující definice:</span><span class="sxs-lookup"><span data-stu-id="cdb2d-120">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
-   <span data-ttu-id="cdb2d-121">Uživatelem definované typy, jako [třídy](../../../visual-basic/language-reference/statements/class-statement.md) nebo [rozhraní](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="cdb2d-121">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
-   <span data-ttu-id="cdb2d-122">Členy, jako je například pole, [události](../../../visual-basic/language-reference/statements/event-statement.md), [vlastnost](../../../visual-basic/language-reference/statements/property-statement.md), [funkce](../../../visual-basic/language-reference/statements/function-statement.md), nebo [podprogram](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cdb2d-122">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="cdb2d-123">Pomocí sady Visual Studio vygenerovaný soubor XML [IntelliSense](/visualstudio/ide/using-intellisense) funkcí, ponechte název souboru XML být stejný jako sestavení, které chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-123">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="cdb2d-124">Ujistěte se, že soubor XML ve stejném adresáři jako sestavení tak, aby při sestavení se odkazuje v projektu sady Visual Studio, je také najít soubor .xml.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-124">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="cdb2d-125">Soubory dokumentace XML nejsou nutné pro technologii IntelliSense pro kód v rámci projektu nebo v rámci projektů odkazuje projekt.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-125">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="cdb2d-126">Pokud kompilujete s `/target:module`, soubor XML obsahuje značky `<assembly></assembly>`.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-126">Unless you compile with `/target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="cdb2d-127">Tyto značky zadejte název souboru obsahujícího manifest sestavení pro výstupní soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-127">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="cdb2d-128">Zobrazit [značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md) způsoby, jak generovat dokumentaci z komentáře v kódu.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-128">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="cdb2d-129">Chcete-li nastavit - doc v sadě Visual Studio integrované vývojové prostředí</span><span class="sxs-lookup"><span data-stu-id="cdb2d-129">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="cdb2d-130">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-130">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="cdb2d-131">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-131">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="cdb2d-132">2.  Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-132">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="cdb2d-133">3.  Nastavte hodnotu **soubor dokumentace XML vygenerovat** pole.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-133">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cdb2d-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="cdb2d-134">Example</span></span>  
 <span data-ttu-id="cdb2d-135">Zobrazit [dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) ukázku.</span><span class="sxs-lookup"><span data-stu-id="cdb2d-135">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb2d-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdb2d-136">See also</span></span>
- [<span data-ttu-id="cdb2d-137">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="cdb2d-137">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="cdb2d-138">Dokumentace kódu s XML</span><span class="sxs-lookup"><span data-stu-id="cdb2d-138">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
