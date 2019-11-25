---
title: 'Postupy: Vytváření literálů XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: e3af5185d2c2106e6a696a6569ef59897d0f1fe1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333005"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="5c6db-102">Postupy: Vytváření literálů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c6db-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="5c6db-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span><span class="sxs-lookup"><span data-stu-id="5c6db-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="5c6db-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span><span class="sxs-lookup"><span data-stu-id="5c6db-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="5c6db-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span><span class="sxs-lookup"><span data-stu-id="5c6db-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="5c6db-106">Další informace najdete v tématu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5c6db-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="5c6db-107">To create an XML element</span><span class="sxs-lookup"><span data-stu-id="5c6db-107">To create an XML element</span></span>  
  
- <span data-ttu-id="5c6db-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span><span class="sxs-lookup"><span data-stu-id="5c6db-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     <span data-ttu-id="5c6db-109">Run the code.</span><span class="sxs-lookup"><span data-stu-id="5c6db-109">Run the code.</span></span> <span data-ttu-id="5c6db-110">The output of this code is:</span><span class="sxs-lookup"><span data-stu-id="5c6db-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="5c6db-111">To create an XML document</span><span class="sxs-lookup"><span data-stu-id="5c6db-111">To create an XML document</span></span>  
  
- <span data-ttu-id="5c6db-112">Create the XML document inline.</span><span class="sxs-lookup"><span data-stu-id="5c6db-112">Create the XML document inline.</span></span> <span data-ttu-id="5c6db-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span><span class="sxs-lookup"><span data-stu-id="5c6db-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     <span data-ttu-id="5c6db-114">Run the code.</span><span class="sxs-lookup"><span data-stu-id="5c6db-114">Run the code.</span></span> <span data-ttu-id="5c6db-115">The output of this code is:</span><span class="sxs-lookup"><span data-stu-id="5c6db-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="5c6db-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c6db-116">See also</span></span>

- [<span data-ttu-id="5c6db-117">XML</span><span class="sxs-lookup"><span data-stu-id="5c6db-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="5c6db-118">Creating XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5c6db-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="5c6db-119">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="5c6db-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="5c6db-120">Literál dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="5c6db-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
