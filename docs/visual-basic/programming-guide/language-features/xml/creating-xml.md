---
title: Vytváření XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: 0777b428d651c09d4bfb9789ab7b2ac8e74cc32e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410280"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="6a0ae-102">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a0ae-102">Creating XML in Visual Basic</span></span>
<span data-ttu-id="6a0ae-103">Visual Basic umožňuje používat *literály XML* přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="6a0ae-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="6a0ae-104">Syntaxe literálu XML reprezentuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty a je podobná SYNTAXI XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="6a0ae-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="6a0ae-105">To usnadňuje vytváření elementů XML, dokumentů a fragmentů programově, protože váš kód má stejnou strukturu jako finální XML.</span><span class="sxs-lookup"><span data-stu-id="6a0ae-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6a0ae-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6a0ae-106">In This Section</span></span>  
  
|<span data-ttu-id="6a0ae-107">Pojem</span><span class="sxs-lookup"><span data-stu-id="6a0ae-107">Term</span></span>|<span data-ttu-id="6a0ae-108">Definice</span><span class="sxs-lookup"><span data-stu-id="6a0ae-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="6a0ae-109">Přehled literálů XML</span><span class="sxs-lookup"><span data-stu-id="6a0ae-109">XML Literals Overview</span></span>](xml-literals-overview.md)|<span data-ttu-id="6a0ae-110">Seznámení s literály XML a jejich vztah k [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6a0ae-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="6a0ae-111">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="6a0ae-111">Embedded Expressions in XML</span></span>](embedded-expressions-in-xml.md)|<span data-ttu-id="6a0ae-112">Popisuje, jak použít vložené výrazy v literálech XML.</span><span class="sxs-lookup"><span data-stu-id="6a0ae-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="6a0ae-113">Postupy: Vytváření literálů XML</span><span class="sxs-lookup"><span data-stu-id="6a0ae-113">How to: Create XML Literals</span></span>](how-to-create-xml-literals.md)|<span data-ttu-id="6a0ae-114">Popisuje, jak vytvořit element XML v kódu pomocí literálu XML.</span><span class="sxs-lookup"><span data-stu-id="6a0ae-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="6a0ae-115">Prázdné znaky v literálech XML</span><span class="sxs-lookup"><span data-stu-id="6a0ae-115">White Space in XML Literals</span></span>](white-space-in-xml-literals.md)|<span data-ttu-id="6a0ae-116">Popisuje, jak Visual Basic zachází s prázdným znakem v literálech XML.</span><span class="sxs-lookup"><span data-stu-id="6a0ae-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="6a0ae-117">Literály XML a specifikace XML 1.0</span><span class="sxs-lookup"><span data-stu-id="6a0ae-117">XML Literals and the XML 1.0 Specification</span></span>](xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="6a0ae-118">Popisuje, jak syntaxe literálu XML v Visual Basic souvisí se specifikací XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="6a0ae-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="6a0ae-119">Postupy: Vložení výrazů do literálů XML</span><span class="sxs-lookup"><span data-stu-id="6a0ae-119">How to: Embed Expressions in XML Literals</span></span>](how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="6a0ae-120">Popisuje, jak použít vložené výrazy v literálech XML k vytvoření obsahu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6a0ae-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="6a0ae-121">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="6a0ae-121">Names of Declared XML Elements and Attributes</span></span>](names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="6a0ae-122">Popisuje pokyny pro pojmenovávání elementů a atributů XML.</span><span class="sxs-lookup"><span data-stu-id="6a0ae-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a0ae-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a0ae-123">See also</span></span>

- [<span data-ttu-id="6a0ae-124">XML</span><span class="sxs-lookup"><span data-stu-id="6a0ae-124">XML</span></span>](index.md)
