---
title: Vytvoření XML v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: d847f589bc47f8ab3d6691666bbd879e795db0c6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813038"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="217e6-102">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="217e6-102">Creating XML in Visual Basic</span></span>
<span data-ttu-id="217e6-103">Visual Basic umožňuje používat *literály XML* přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="217e6-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="217e6-104">Syntaxe XML literál představuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty a to se podobá syntaxi XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="217e6-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="217e6-105">To usnadňuje vytvořit prvky, dokumenty a fragmenty XML prostřednictvím kódu programu, protože váš kód má stejnou strukturu jako poslední XML.</span><span class="sxs-lookup"><span data-stu-id="217e6-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="217e6-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="217e6-106">In This Section</span></span>  
  
|<span data-ttu-id="217e6-107">Termín</span><span class="sxs-lookup"><span data-stu-id="217e6-107">Term</span></span>|<span data-ttu-id="217e6-108">Definice</span><span class="sxs-lookup"><span data-stu-id="217e6-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="217e6-109">Přehled literálů XML</span><span class="sxs-lookup"><span data-stu-id="217e6-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="217e6-110">Seznámení s literály XML a jak souvisejí s nabídkou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="217e6-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="217e6-111">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="217e6-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="217e6-112">Popisuje, jak používat vložené výrazy v literálech XML.</span><span class="sxs-lookup"><span data-stu-id="217e6-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="217e6-113">Postupy: Vytváření literálů XML</span><span class="sxs-lookup"><span data-stu-id="217e6-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="217e6-114">Popisuje, jak vytvořit prvek XML v kódu pomocí literálů XML.</span><span class="sxs-lookup"><span data-stu-id="217e6-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="217e6-115">Prázdné znaky v literálech XML</span><span class="sxs-lookup"><span data-stu-id="217e6-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="217e6-116">Popisuje, jak Visual Basic zpracovává prázdné znaky v literálech XML.</span><span class="sxs-lookup"><span data-stu-id="217e6-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="217e6-117">Literály XML a specifikace XML 1.0</span><span class="sxs-lookup"><span data-stu-id="217e6-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="217e6-118">Popisuje, jak je literál syntaxe jazyka XML v jazyce Visual Basic má vztah k specifikace XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="217e6-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="217e6-119">Postupy: Vložení výrazů do literálů XML</span><span class="sxs-lookup"><span data-stu-id="217e6-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="217e6-120">Popisuje, jak používat vložené výrazy v literálech XML k vytváření obsahu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="217e6-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="217e6-121">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="217e6-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="217e6-122">Popisuje pravidla pro vytváření názvů XML elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="217e6-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="217e6-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="217e6-123">See also</span></span>

- [<span data-ttu-id="217e6-124">XML</span><span class="sxs-lookup"><span data-stu-id="217e6-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
