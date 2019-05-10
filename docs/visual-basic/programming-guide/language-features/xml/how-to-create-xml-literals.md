---
title: 'Postupy: Vytváření literálů XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 991f10b00082bb4eb2b54f10c1b85cdc2c9009d2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598544"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="94c66-102">Postupy: Vytváření literálů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94c66-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="94c66-103">Dokument XML, fragment nebo element můžete vytvořit přímo v kódu pomocí literálů XML.</span><span class="sxs-lookup"><span data-stu-id="94c66-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="94c66-104">Příklady v tomto tématu ukazují, jak vytvořit element XML, který obsahuje tři podřízené prvky a vytvořit dokument XML.</span><span class="sxs-lookup"><span data-stu-id="94c66-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="94c66-105">Můžete také použít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API k vytvoření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty.</span><span class="sxs-lookup"><span data-stu-id="94c66-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="94c66-106">Další informace naleznete v tématu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="94c66-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="94c66-107">Chcete-li vytvořit XML element</span><span class="sxs-lookup"><span data-stu-id="94c66-107">To create an XML element</span></span>  
  
- <span data-ttu-id="94c66-108">Vytvořte vložený kód XML pomocí syntaxe literálu XML, který je stejný jako skutečný syntaxe jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="94c66-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     <span data-ttu-id="94c66-109">Spusťte kód.</span><span class="sxs-lookup"><span data-stu-id="94c66-109">Run the code.</span></span> <span data-ttu-id="94c66-110">Výstup tohoto kódu je následující:</span><span class="sxs-lookup"><span data-stu-id="94c66-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="94c66-111">Chcete-li vytvořit dokument XML</span><span class="sxs-lookup"><span data-stu-id="94c66-111">To create an XML document</span></span>  
  
- <span data-ttu-id="94c66-112">Vytvořte vložený dokument XML.</span><span class="sxs-lookup"><span data-stu-id="94c66-112">Create the XML document inline.</span></span> <span data-ttu-id="94c66-113">Následující kód vytvoří dokument XML, který má literálu syntaxi deklarace XML, instrukce pro zpracování, komentáře a element, který obsahuje jiný prvek.</span><span class="sxs-lookup"><span data-stu-id="94c66-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     <span data-ttu-id="94c66-114">Spusťte kód.</span><span class="sxs-lookup"><span data-stu-id="94c66-114">Run the code.</span></span> <span data-ttu-id="94c66-115">Výstup tohoto kódu je následující:</span><span class="sxs-lookup"><span data-stu-id="94c66-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="94c66-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94c66-116">See also</span></span>

- [<span data-ttu-id="94c66-117">XML</span><span class="sxs-lookup"><span data-stu-id="94c66-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="94c66-118">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="94c66-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="94c66-119">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="94c66-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="94c66-120">Literál dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="94c66-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
