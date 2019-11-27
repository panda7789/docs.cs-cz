---
title: 'Postupy: Vložení výrazů do literálů XML'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 2e8dd10b334b0271e3c9de11ed155c9d5d7aae48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332930"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="e82c1-102">Postupy: Vložení výrazů do literálů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e82c1-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="e82c1-103">Můžete zkombinovat literály XML s vloženými výrazy a vytvořit dokument XML, fragment nebo prvek, který obsahuje obsah vytvořený v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e82c1-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="e82c1-104">Následující příklady ukazují, jak použít vložené výrazy k naplnění obsahu prvku, atributů a názvů elementů za běhu.</span><span class="sxs-lookup"><span data-stu-id="e82c1-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="e82c1-105">Syntaxe vloženého výrazu je `<%=` `exp` `%>`, což je stejná syntaxe, kterou používá ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e82c1-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses.</span></span> <span data-ttu-id="e82c1-106">Další informace najdete v tématu [vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e82c1-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="e82c1-107">K vytváření objektů [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete použít taky rozhraní [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API.</span><span class="sxs-lookup"><span data-stu-id="e82c1-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="e82c1-108">Další informace najdete v tématu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e82c1-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="e82c1-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="e82c1-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="e82c1-110">Vložení textu jako obsahu elementu</span><span class="sxs-lookup"><span data-stu-id="e82c1-110">To insert text as element content</span></span>  
  
- <span data-ttu-id="e82c1-111">Následující příklad ukazuje, jak vložit text, který je obsažen v proměnné `contactName` mezi prvky pro otevření a zavření názvu.</span><span class="sxs-lookup"><span data-stu-id="e82c1-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="e82c1-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e82c1-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="e82c1-113">Vložení textu jako hodnoty atributu</span><span class="sxs-lookup"><span data-stu-id="e82c1-113">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="e82c1-114">Následující příklad ukazuje, jak vložit text, který je obsažen v proměnné `phoneType` jako hodnota atributu `type`.</span><span class="sxs-lookup"><span data-stu-id="e82c1-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="e82c1-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e82c1-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="e82c1-116">Vložení textu pro název elementu</span><span class="sxs-lookup"><span data-stu-id="e82c1-116">To insert text for an element name</span></span>  
  
- <span data-ttu-id="e82c1-117">Následující příklad ukazuje, jak vložit text, který je obsažen v proměnné `elementName` jako název elementu.</span><span class="sxs-lookup"><span data-stu-id="e82c1-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="e82c1-118">Při vytváření prvků pomocí této techniky je nutné je zavřít pomocí značky \</>.</span><span class="sxs-lookup"><span data-stu-id="e82c1-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="e82c1-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e82c1-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e82c1-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e82c1-120">See also</span></span>

- [<span data-ttu-id="e82c1-121">Postupy: Vytváření literálů XML</span><span class="sxs-lookup"><span data-stu-id="e82c1-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [<span data-ttu-id="e82c1-122">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="e82c1-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="e82c1-123">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e82c1-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="e82c1-124">XML</span><span class="sxs-lookup"><span data-stu-id="e82c1-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
