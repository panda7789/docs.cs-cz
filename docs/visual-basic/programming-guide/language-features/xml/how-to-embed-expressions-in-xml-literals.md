---
title: "Postupy: Vložení výrazů do literálů XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bef4662d69ca7ceddeb2641cbe265d93712c5d16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="61615-102">Postupy: Vložení výrazů do literálů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61615-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="61615-103">XML – literály můžete kombinovat s vložené výrazy vytvořit dokument XML, fragment nebo elementu, který obsahuje obsah vytvořený v době běhu.</span><span class="sxs-lookup"><span data-stu-id="61615-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="61615-104">Následující příklady ukazují, jak používat vložené výrazy k naplnění obsahu elementu, atributy a názvy elementu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="61615-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="61615-105">Syntaxe pro embedded výrazu je `<%=` `exp` `%>`, který se stejnou syntaxí, [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] používá.</span><span class="sxs-lookup"><span data-stu-id="61615-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uses.</span></span> <span data-ttu-id="61615-106">Další informace najdete v tématu [vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="61615-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="61615-107">Můžete také [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API pro vytvoření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty.</span><span class="sxs-lookup"><span data-stu-id="61615-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="61615-108">Další informace naleznete v tématu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="61615-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="61615-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="61615-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="61615-110">Chcete-li vložit textového obsahu elementu</span><span class="sxs-lookup"><span data-stu-id="61615-110">To insert text as element content</span></span>  
  
-   <span data-ttu-id="61615-111">Následující příklad ukazuje, jak vložit text, který je součástí `contactName` mezi otevřením a uzavření elementy, název proměnné.</span><span class="sxs-lookup"><span data-stu-id="61615-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     <span data-ttu-id="61615-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61615-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="61615-113">Chcete-li vložit text hodnota atributu</span><span class="sxs-lookup"><span data-stu-id="61615-113">To insert text as an attribute value</span></span>  
  
-   <span data-ttu-id="61615-114">Následující příklad ukazuje, jak vložit text, který je součástí `phoneType` jako hodnotu proměnné `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="61615-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     <span data-ttu-id="61615-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61615-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="61615-116">Chcete-li vložit text pro název elementu</span><span class="sxs-lookup"><span data-stu-id="61615-116">To insert text for an element name</span></span>  
  
-   <span data-ttu-id="61615-117">Následující příklad ukazuje, jak vložit text, který je součástí `elementName` proměnné jako název elementu.</span><span class="sxs-lookup"><span data-stu-id="61615-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="61615-118">Při vytváření elementů pomocí Tato technika, je třeba nejprve zavřít je \</ > značky.</span><span class="sxs-lookup"><span data-stu-id="61615-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     <span data-ttu-id="61615-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61615-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="61615-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="61615-120">See Also</span></span>  
 [<span data-ttu-id="61615-121">Postupy: vytváření literálů XML</span><span class="sxs-lookup"><span data-stu-id="61615-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)  
 [<span data-ttu-id="61615-122">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="61615-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [<span data-ttu-id="61615-123">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="61615-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="61615-124">XML</span><span class="sxs-lookup"><span data-stu-id="61615-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
