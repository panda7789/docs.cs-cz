---
title: "Dokumentace kódu s XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ddb1f366002c4f0c675c591d83aab1b31ef8f602
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="6efc3-102">Dokumentace kódu s XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6efc3-102">Documenting Your Code with XML (Visual Basic)</span></span>
<span data-ttu-id="6efc3-103">V [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], můžete dokumentu kódu pomocí XML</span><span class="sxs-lookup"><span data-stu-id="6efc3-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], you can document your code using XML</span></span>  
  
## <a name="xml-documentation-comments"></a><span data-ttu-id="6efc3-104">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="6efc3-104">XML Documentation Comments</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="6efc3-105">poskytuje snadný způsob, jak automaticky vytvoření dokumentace XML pro projekty.</span><span class="sxs-lookup"><span data-stu-id="6efc3-105"> provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="6efc3-106">Můžete automaticky generovat kostru XML pro typy a členy a pak zadejte souhrny, popisný dokumentace pro jednotlivé parametry a další poznámky.</span><span class="sxs-lookup"><span data-stu-id="6efc3-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="6efc3-107">V instalaci příslušné je automaticky vygenerované dokumentace XML do souboru XML se stejným názvem jako váš projekt a příponu .xml.</span><span class="sxs-lookup"><span data-stu-id="6efc3-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="6efc3-108">Další informace najdete v tématu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="6efc3-108">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
 <span data-ttu-id="6efc3-109">Soubor XML můžete využívat nebo jinak s nimi manipulovat jako XML.</span><span class="sxs-lookup"><span data-stu-id="6efc3-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="6efc3-110">Tento soubor nachází ve stejném adresáři jako výstupní soubor .exe nebo .dll projektu.</span><span class="sxs-lookup"><span data-stu-id="6efc3-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>  
  
 <span data-ttu-id="6efc3-111">Dokumentace XML začíná `'''`.</span><span class="sxs-lookup"><span data-stu-id="6efc3-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="6efc3-112">Zpracování tyto komentáře má určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="6efc3-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="6efc3-113">V dokumentaci musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="6efc3-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="6efc3-114">Pokud není ve správném formátu XML, se generuje upozornění a soubor dokumentace obsahuje komentář s informacemi o tom, že došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="6efc3-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>  
  
-   <span data-ttu-id="6efc3-115">Vývojáři mohou vytvořit vlastní sadu značky.</span><span class="sxs-lookup"><span data-stu-id="6efc3-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="6efc3-116">Existuje sada doporučené značky (viz "Související oddíly" v tomto tématu).</span><span class="sxs-lookup"><span data-stu-id="6efc3-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="6efc3-117">Některé z doporučené značky mají zvláštní význam:</span><span class="sxs-lookup"><span data-stu-id="6efc3-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="6efc3-118">\<Param > Značka se používá k popisu parametry.</span><span class="sxs-lookup"><span data-stu-id="6efc3-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="6efc3-119">Pokud se používá, kompilátor ověří, zda parametr existuje a že všechny parametry jsou popsané v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="6efc3-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="6efc3-120">Pokud ověření selže, vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="6efc3-120">If the verification fails, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="6efc3-121">`cref` Atributu může být připojen k žádné značky, které poskytují odkaz na element kódu.</span><span class="sxs-lookup"><span data-stu-id="6efc3-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="6efc3-122">Kompilátor ověří, zda tento element kódu existuje.</span><span class="sxs-lookup"><span data-stu-id="6efc3-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="6efc3-123">Pokud ověření selže, vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="6efc3-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="6efc3-124">Kompilátor také respektuje žádné `Imports` příkazy při vyhledávání pro typ popsané v `cref` atribut.</span><span class="sxs-lookup"><span data-stu-id="6efc3-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="6efc3-125">\<Souhrnné > Značka je používán IntelliSense v [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] zobrazíte další informace o typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="6efc3-125">The \<summary> tag is used by IntelliSense in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] to display additional information about a type or member.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6efc3-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6efc3-126">Related Sections</span></span>  
 <span data-ttu-id="6efc3-127">Podrobné informace o vytváření souboru XML s dokumentační komentáře najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="6efc3-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>  
  
-   [<span data-ttu-id="6efc3-128">/ DOC</span><span class="sxs-lookup"><span data-stu-id="6efc3-128">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [<span data-ttu-id="6efc3-129">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="6efc3-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="6efc3-130">Zpracování souboru XML</span><span class="sxs-lookup"><span data-stu-id="6efc3-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="6efc3-131">Postupy: vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="6efc3-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [<span data-ttu-id="6efc3-132">Nástroje XML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6efc3-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a><span data-ttu-id="6efc3-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="6efc3-133">See Also</span></span>  
 [<span data-ttu-id="6efc3-134">Vývoj aplikací v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6efc3-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)  
 [<span data-ttu-id="6efc3-135">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6efc3-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
