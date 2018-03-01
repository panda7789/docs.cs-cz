---
title: "Postupy: Vytváření literálů XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce1bf763529b436158c2d74811c4938182166f92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="bfd7c-102">Postupy: Vytváření literálů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfd7c-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="bfd7c-103">Můžete vytvořit dokument XML, fragment nebo element přímo v kódu pomocí literál XML.</span><span class="sxs-lookup"><span data-stu-id="bfd7c-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="bfd7c-104">V příkladech v tomto tématu ukazují, jak vytvořit element XML, který má tři podřízené elementy a jak vytvořit dokument XML.</span><span class="sxs-lookup"><span data-stu-id="bfd7c-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="bfd7c-105">Můžete také [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API pro vytvoření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty.</span><span class="sxs-lookup"><span data-stu-id="bfd7c-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="bfd7c-106">Další informace naleznete v tématu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="bfd7c-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="bfd7c-107">Chcete-li vytvořit XML element</span><span class="sxs-lookup"><span data-stu-id="bfd7c-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="bfd7c-108">Vytvořte vložený XML pomocí syntaxe literál XML, který je stejný jako skutečný syntaxe jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="bfd7c-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     <span data-ttu-id="bfd7c-109">Spusťte kód.</span><span class="sxs-lookup"><span data-stu-id="bfd7c-109">Run the code.</span></span> <span data-ttu-id="bfd7c-110">Výstup tohoto kódu je:</span><span class="sxs-lookup"><span data-stu-id="bfd7c-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="bfd7c-111">Chcete-li vytvořit dokument XML</span><span class="sxs-lookup"><span data-stu-id="bfd7c-111">To create an XML document</span></span>  
  
-   <span data-ttu-id="bfd7c-112">Vytvořte vložený dokument XML.</span><span class="sxs-lookup"><span data-stu-id="bfd7c-112">Create the XML document inline.</span></span> <span data-ttu-id="bfd7c-113">Následující kód vytvoří dokument XML, který má literálu syntaxe, deklarace XML, pokyny pro zpracování, komentáře a elementu, který obsahuje jiný element.</span><span class="sxs-lookup"><span data-stu-id="bfd7c-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     <span data-ttu-id="bfd7c-114">Spusťte kód.</span><span class="sxs-lookup"><span data-stu-id="bfd7c-114">Run the code.</span></span> <span data-ttu-id="bfd7c-115">Výstup tohoto kódu je:</span><span class="sxs-lookup"><span data-stu-id="bfd7c-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="bfd7c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfd7c-116">See Also</span></span>  
 [<span data-ttu-id="bfd7c-117">XML</span><span class="sxs-lookup"><span data-stu-id="bfd7c-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="bfd7c-118">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bfd7c-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="bfd7c-119">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="bfd7c-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="bfd7c-120">Literál dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="bfd7c-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
