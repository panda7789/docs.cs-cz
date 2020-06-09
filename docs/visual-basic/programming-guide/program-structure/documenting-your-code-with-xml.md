---
title: Dokumentace kódu s XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: f391fb909cfe4de8f27afb24d6db389e2c8cdfae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590926"
---
# <a name="document-your-code-with-xml-visual-basic"></a><span data-ttu-id="9c28a-102">Dokumentování kódu pomocí XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c28a-102">Document your code with XML (Visual Basic)</span></span>

<span data-ttu-id="9c28a-103">V Visual Basic můžete svůj kód zdokumentovat pomocí XML.</span><span class="sxs-lookup"><span data-stu-id="9c28a-103">In Visual Basic, you can document your code using XML.</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="9c28a-104">Komentáře dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="9c28a-104">XML documentation comments</span></span>

<span data-ttu-id="9c28a-105">Visual Basic poskytuje snadný způsob, jak automaticky vytvořit dokumentaci XML pro projekty.</span><span class="sxs-lookup"><span data-stu-id="9c28a-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="9c28a-106">Můžete automaticky vygenerovat kostru XML pro vaše typy a členy a pak poskytnout souhrny, popisnou dokumentaci pro každý parametr a další poznámky.</span><span class="sxs-lookup"><span data-stu-id="9c28a-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="9c28a-107">S příslušným nastavením se dokumentace XML automaticky generuje do souboru XML se stejným kořenovým názvem souboru jako váš projekt.</span><span class="sxs-lookup"><span data-stu-id="9c28a-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same root file name as your project.</span></span> <span data-ttu-id="9c28a-108">Další informace najdete v [dokumentu-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="9c28a-108">For more information, see [-doc](../../reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="9c28a-109">Soubor XML lze spotřebovat nebo jinak manipulovat jako XML.</span><span class="sxs-lookup"><span data-stu-id="9c28a-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="9c28a-110">Tento soubor je umístěn ve stejném adresáři jako výstupní soubor. exe nebo. dll vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="9c28a-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="9c28a-111">Dokumentace XML začíná na `'''` .</span><span class="sxs-lookup"><span data-stu-id="9c28a-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="9c28a-112">Zpracování těchto komentářů má určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="9c28a-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="9c28a-113">Dokumentace musí být ve správném formátu XML.</span><span class="sxs-lookup"><span data-stu-id="9c28a-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="9c28a-114">Pokud XML není ve správném formátu, je vygenerováno upozornění a soubor dokumentace obsahuje komentář, který říká, že došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="9c28a-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="9c28a-115">Vývojářům je zdarma vytvořit vlastní sadu značek.</span><span class="sxs-lookup"><span data-stu-id="9c28a-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="9c28a-116">Je doporučena sada značek (viz [značky komentářů XML](../../language-reference/xmldoc/index.md)).</span><span class="sxs-lookup"><span data-stu-id="9c28a-116">There is a recommended set of tags (see [XML Comment Tags](../../language-reference/xmldoc/index.md)).</span></span> <span data-ttu-id="9c28a-117">Některé z doporučených značek mají zvláštní význam:</span><span class="sxs-lookup"><span data-stu-id="9c28a-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="9c28a-118">Tato \<param> značka se používá k popisu parametrů.</span><span class="sxs-lookup"><span data-stu-id="9c28a-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="9c28a-119">Pokud je použit, kompilátor ověří, zda existuje parametr a zda jsou všechny parametry popsány v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="9c28a-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="9c28a-120">Pokud se ověření nepovede, kompilátor vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="9c28a-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="9c28a-121">`cref`Atribut lze připojit k libovolné značce k poskytnutí odkazu na prvek kódu.</span><span class="sxs-lookup"><span data-stu-id="9c28a-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="9c28a-122">Kompilátor ověřuje, zda tento prvek kódu existuje.</span><span class="sxs-lookup"><span data-stu-id="9c28a-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="9c28a-123">Pokud se ověření nepovede, kompilátor vydá upozornění.</span><span class="sxs-lookup"><span data-stu-id="9c28a-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="9c28a-124">Kompilátor také respektuje všechny `Imports` příkazy při hledání typu, který je popsán v `cref` atributu.</span><span class="sxs-lookup"><span data-stu-id="9c28a-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="9c28a-125">\<summary>Značka je používána technologií IntelliSense v aplikaci Visual Studio k zobrazení dalších informací o typu nebo členu.</span><span class="sxs-lookup"><span data-stu-id="9c28a-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="9c28a-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9c28a-126">Related sections</span></span>

<span data-ttu-id="9c28a-127">Podrobné informace o vytvoření souboru XML s dokumentačními komentáři naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="9c28a-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="9c28a-128">-doc</span><span class="sxs-lookup"><span data-stu-id="9c28a-128">-doc</span></span>](../../reference/command-line-compiler/doc.md)

- [<span data-ttu-id="9c28a-129">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="9c28a-129">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)

- [<span data-ttu-id="9c28a-130">Zpracování souboru XML</span><span class="sxs-lookup"><span data-stu-id="9c28a-130">Processing the XML File</span></span>](processing-the-xml-file.md)

- [<span data-ttu-id="9c28a-131">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="9c28a-131">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)

- [<span data-ttu-id="9c28a-132">Nástroje XML v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c28a-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="9c28a-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c28a-133">See also</span></span>

- [<span data-ttu-id="9c28a-134">Vývoj aplikací pomocí jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c28a-134">Developing Applications with Visual Basic</span></span>](../../developing-apps/index.md)
- [<span data-ttu-id="9c28a-135">Příručka k programování v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c28a-135">Visual Basic Programming Guide</span></span>](../index.md)
