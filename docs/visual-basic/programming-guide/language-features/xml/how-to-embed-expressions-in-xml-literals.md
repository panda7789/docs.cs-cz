---
title: 'Postupy: Vložení výrazů do literálů XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 9d0fd1e3713dc5b81cfca0ce54b571b38e648f87
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879102"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="e4057-102">Postupy: Vložení výrazů do literálů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4057-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="e4057-103">Literály XML lze kombinovat s vložené výrazy pro vytvoření dokumentu XML, fragment nebo element, který obsahuje obsah vytvořený v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e4057-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="e4057-104">Následující příklady ukazují, jak používat vložené výrazy k naplnění obsah elementu, atributy a názvy elementů v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e4057-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="e4057-105">Syntaxe pro vložený výraz je `<%=` `exp` `%>`, což je stejné syntaxe, která používá ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e4057-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses.</span></span> <span data-ttu-id="e4057-106">Další informace najdete v tématu [vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e4057-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="e4057-107">Můžete také použít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API k vytvoření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty.</span><span class="sxs-lookup"><span data-stu-id="e4057-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="e4057-108">Další informace naleznete v tématu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e4057-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="e4057-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="e4057-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="e4057-110">Chcete-li vložit textového obsahu elementu</span><span class="sxs-lookup"><span data-stu-id="e4057-110">To insert text as element content</span></span>  
  
- <span data-ttu-id="e4057-111">Následující příklad ukazuje, jak vložit text, který je součástí `contactName` mezi prvky a na konci názvu proměnné.</span><span class="sxs-lookup"><span data-stu-id="e4057-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="e4057-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e4057-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="e4057-113">Chcete-li vložit text hodnotu atributu</span><span class="sxs-lookup"><span data-stu-id="e4057-113">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="e4057-114">Následující příklad ukazuje, jak vložit text, který je součástí `phoneType` jako hodnotu proměnné `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="e4057-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="e4057-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e4057-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="e4057-116">Chcete-li vložit text pro název elementu</span><span class="sxs-lookup"><span data-stu-id="e4057-116">To insert text for an element name</span></span>  
  
- <span data-ttu-id="e4057-117">Následující příklad ukazuje, jak vložit text, který je součástí `elementName` proměnné jako název elementu.</span><span class="sxs-lookup"><span data-stu-id="e4057-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="e4057-118">Při vytváření elementů tímto způsobem, je nutné zavřít jim \</ > značky.</span><span class="sxs-lookup"><span data-stu-id="e4057-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="e4057-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e4057-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e4057-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4057-120">See also</span></span>

- [<span data-ttu-id="e4057-121">Postupy: Vytváření literálů XML</span><span class="sxs-lookup"><span data-stu-id="e4057-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [<span data-ttu-id="e4057-122">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="e4057-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="e4057-123">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e4057-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="e4057-124">XML</span><span class="sxs-lookup"><span data-stu-id="e4057-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
