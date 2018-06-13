---
title: 'Postupy: Vložení výrazů do literálů XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 41dc6ef8d2ec2ffd6cd1cf793911f2e09f1a1e77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652266"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="17dbe-102">Postupy: Vložení výrazů do literálů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17dbe-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="17dbe-103">XML – literály můžete kombinovat s vložené výrazy vytvořit dokument XML, fragment nebo elementu, který obsahuje obsah vytvořený v době běhu.</span><span class="sxs-lookup"><span data-stu-id="17dbe-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="17dbe-104">Následující příklady ukazují, jak používat vložené výrazy k naplnění obsahu elementu, atributy a názvy elementu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="17dbe-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="17dbe-105">Syntaxe pro embedded výrazu je `<%=` `exp` `%>`, který se stejnou syntaxí, [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] používá.</span><span class="sxs-lookup"><span data-stu-id="17dbe-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uses.</span></span> <span data-ttu-id="17dbe-106">Další informace najdete v tématu [vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="17dbe-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="17dbe-107">Můžete také [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API pro vytvoření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty.</span><span class="sxs-lookup"><span data-stu-id="17dbe-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="17dbe-108">Další informace naleznete v tématu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="17dbe-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="17dbe-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="17dbe-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="17dbe-110">Chcete-li vložit textového obsahu elementu</span><span class="sxs-lookup"><span data-stu-id="17dbe-110">To insert text as element content</span></span>  
  
-   <span data-ttu-id="17dbe-111">Následující příklad ukazuje, jak vložit text, který je součástí `contactName` mezi otevřením a uzavření elementy, název proměnné.</span><span class="sxs-lookup"><span data-stu-id="17dbe-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     <span data-ttu-id="17dbe-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="17dbe-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="17dbe-113">Chcete-li vložit text hodnota atributu</span><span class="sxs-lookup"><span data-stu-id="17dbe-113">To insert text as an attribute value</span></span>  
  
-   <span data-ttu-id="17dbe-114">Následující příklad ukazuje, jak vložit text, který je součástí `phoneType` jako hodnotu proměnné `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="17dbe-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     <span data-ttu-id="17dbe-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="17dbe-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="17dbe-116">Chcete-li vložit text pro název elementu</span><span class="sxs-lookup"><span data-stu-id="17dbe-116">To insert text for an element name</span></span>  
  
-   <span data-ttu-id="17dbe-117">Následující příklad ukazuje, jak vložit text, který je součástí `elementName` proměnné jako název elementu.</span><span class="sxs-lookup"><span data-stu-id="17dbe-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="17dbe-118">Při vytváření elementů pomocí Tato technika, je třeba nejprve zavřít je \</ > značky.</span><span class="sxs-lookup"><span data-stu-id="17dbe-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     <span data-ttu-id="17dbe-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="17dbe-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="17dbe-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="17dbe-120">See Also</span></span>  
 [<span data-ttu-id="17dbe-121">Postupy: Vytváření literálů XML</span><span class="sxs-lookup"><span data-stu-id="17dbe-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)  
 [<span data-ttu-id="17dbe-122">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="17dbe-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [<span data-ttu-id="17dbe-123">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17dbe-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="17dbe-124">XML</span><span class="sxs-lookup"><span data-stu-id="17dbe-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
