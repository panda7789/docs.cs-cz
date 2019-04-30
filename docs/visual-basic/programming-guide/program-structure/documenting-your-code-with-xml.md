---
title: Dokumentace kódu s XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 6b9fe9994b7bdf2259dcdb1ecef906e0f9955c8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785499"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="98ff5-102">Dokumentace kódu s XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98ff5-102">Documenting Your Code with XML (Visual Basic)</span></span>

<span data-ttu-id="98ff5-103">V jazyce Visual Basic můžete dokumentaci kódu pomocí XML</span><span class="sxs-lookup"><span data-stu-id="98ff5-103">In Visual Basic, you can document your code using XML</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="98ff5-104">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="98ff5-104">XML Documentation Comments</span></span>

<span data-ttu-id="98ff5-105">Visual Basic poskytuje snadný způsob, jak automaticky vytvořit dokumentaci XML pro projekty.</span><span class="sxs-lookup"><span data-stu-id="98ff5-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="98ff5-106">Můžete automaticky generovat skeleton XML pro typy a členy a pak zadejte souhrny, popisný dokumentace pro každého parametru a další poznámky.</span><span class="sxs-lookup"><span data-stu-id="98ff5-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="98ff5-107">S odpovídající instalační program je automaticky vygenerován dokumentace XML do souboru XML se stejným názvem jako váš projekt a příponu .xml.</span><span class="sxs-lookup"><span data-stu-id="98ff5-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="98ff5-108">Další informace najdete v tématu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="98ff5-108">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="98ff5-109">Soubor XML můžete využívat nebo jinak zpracovávají jako XML.</span><span class="sxs-lookup"><span data-stu-id="98ff5-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="98ff5-110">Tento soubor je umístěn ve stejném adresáři jako soubor .exe nebo .dll výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="98ff5-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="98ff5-111">Dokumentace XML začíná `'''`.</span><span class="sxs-lookup"><span data-stu-id="98ff5-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="98ff5-112">Zpracování tyto poznámky platí některá omezení:</span><span class="sxs-lookup"><span data-stu-id="98ff5-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="98ff5-113">V dokumentaci k musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="98ff5-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="98ff5-114">Pokud není správně vytvořený kód XML, je vygenerováno upozornění a soubor dokumentace obsahuje komentář informacemi o tom, že došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="98ff5-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="98ff5-115">Vývojáři jsou zdarma vytvořit vlastní sadu značek.</span><span class="sxs-lookup"><span data-stu-id="98ff5-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="98ff5-116">Je doporučená sada značky (viz "Související oddíly" v tomto tématu).</span><span class="sxs-lookup"><span data-stu-id="98ff5-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="98ff5-117">Některé doporučené značky mají zvláštní význam:</span><span class="sxs-lookup"><span data-stu-id="98ff5-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="98ff5-118">\<Param > Značka se používá k popisu parametrů.</span><span class="sxs-lookup"><span data-stu-id="98ff5-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="98ff5-119">Pokud použijete, kompilátor ověří, že parametr existuje a že všechny parametry jsou popsané v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="98ff5-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="98ff5-120">Pokud se ověření nezdaří, kompilátor vyvolá upozornění.</span><span class="sxs-lookup"><span data-stu-id="98ff5-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="98ff5-121">`cref` Atribut lze připojit ke každé značce poskytnout odkaz na prvek kódu.</span><span class="sxs-lookup"><span data-stu-id="98ff5-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="98ff5-122">Kompilátor ověří, zda tento prvek kódu existuje.</span><span class="sxs-lookup"><span data-stu-id="98ff5-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="98ff5-123">Pokud se ověření nezdaří, kompilátor vyvolá upozornění.</span><span class="sxs-lookup"><span data-stu-id="98ff5-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="98ff5-124">Kompilátor respektuje také některé `Imports` příkazy při hledání typu je popsáno v `cref` atribut.</span><span class="sxs-lookup"><span data-stu-id="98ff5-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="98ff5-125">\<Summary > Značka se používá technologie IntelliSense v sadě Visual Studio zobrazíte další informace o typu nebo členu.</span><span class="sxs-lookup"><span data-stu-id="98ff5-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="98ff5-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="98ff5-126">Related Sections</span></span>

<span data-ttu-id="98ff5-127">Podrobné informace o vytváření souboru XML s komentáře k dokumentaci naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="98ff5-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="98ff5-128">/doc</span><span class="sxs-lookup"><span data-stu-id="98ff5-128">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)

- [<span data-ttu-id="98ff5-129">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="98ff5-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

- [<span data-ttu-id="98ff5-130">Zpracování souboru XML</span><span class="sxs-lookup"><span data-stu-id="98ff5-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [<span data-ttu-id="98ff5-131">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="98ff5-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [<span data-ttu-id="98ff5-132">Nástroje XML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="98ff5-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="98ff5-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98ff5-133">See also</span></span>

- [<span data-ttu-id="98ff5-134">Vývoj aplikací v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="98ff5-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)
- [<span data-ttu-id="98ff5-135">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="98ff5-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
