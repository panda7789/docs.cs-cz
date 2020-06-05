---
title: 'Postupy: Vytváření literálů XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 61b138c0851c747ed30eedc10cb882cc3b03c4d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392607"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="9ed94-102">Postupy: Vytváření literálů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ed94-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="9ed94-103">Můžete vytvořit dokument XML, fragment nebo element přímo v kódu pomocí literálu XML.</span><span class="sxs-lookup"><span data-stu-id="9ed94-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="9ed94-104">Příklady v tomto tématu ukazují, jak vytvořit element XML, který má tři podřízené prvky a jak vytvořit dokument XML.</span><span class="sxs-lookup"><span data-stu-id="9ed94-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="9ed94-105">Můžete také použít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API k vytvoření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektů.</span><span class="sxs-lookup"><span data-stu-id="9ed94-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="9ed94-106">Další informace naleznete v tématu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="9ed94-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="9ed94-107">Vytvoření elementu XML</span><span class="sxs-lookup"><span data-stu-id="9ed94-107">To create an XML element</span></span>  
  
- <span data-ttu-id="9ed94-108">Vytvořte XML inline pomocí syntaxe literálu XML, která je stejná jako skutečná syntaxe XML.</span><span class="sxs-lookup"><span data-stu-id="9ed94-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     <span data-ttu-id="9ed94-109">Spusťte kód.</span><span class="sxs-lookup"><span data-stu-id="9ed94-109">Run the code.</span></span> <span data-ttu-id="9ed94-110">Výstup tohoto kódu je:</span><span class="sxs-lookup"><span data-stu-id="9ed94-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="9ed94-111">Vytvoření dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="9ed94-111">To create an XML document</span></span>  
  
- <span data-ttu-id="9ed94-112">Vytvořte vložený dokument XML.</span><span class="sxs-lookup"><span data-stu-id="9ed94-112">Create the XML document inline.</span></span> <span data-ttu-id="9ed94-113">Následující kód vytvoří dokument XML, který má syntaxi literálu, deklaraci XML, instrukci zpracování, komentář a prvek, který obsahuje jiný element.</span><span class="sxs-lookup"><span data-stu-id="9ed94-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     <span data-ttu-id="9ed94-114">Spusťte kód.</span><span class="sxs-lookup"><span data-stu-id="9ed94-114">Run the code.</span></span> <span data-ttu-id="9ed94-115">Výstup tohoto kódu je:</span><span class="sxs-lookup"><span data-stu-id="9ed94-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="9ed94-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ed94-116">See also</span></span>

- [<span data-ttu-id="9ed94-117">XML</span><span class="sxs-lookup"><span data-stu-id="9ed94-117">XML</span></span>](index.md)
- [<span data-ttu-id="9ed94-118">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ed94-118">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="9ed94-119">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="9ed94-119">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="9ed94-120">Literál dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="9ed94-120">XML Document Literal</span></span>](../../../language-reference/xml-literals/xml-document-literal.md)
