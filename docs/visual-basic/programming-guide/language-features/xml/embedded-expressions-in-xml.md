---
title: "Vložené výrazy v XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b1cdba0a39a932f143ac98c2514240e1696a8fe0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="dfe6c-102">Vložené výrazy v XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfe6c-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="dfe6c-103">Vložené výrazy umožňují vytváření literálů XML, které obsahují výrazy, které jsou vyhodnocovány v době běhu.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="dfe6c-104">Syntaxe pro embedded výrazu je `<%=` `expression` `%>`, což je stejný jako syntaxe použít v [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dfe6c-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="dfe6c-105">Například můžete vytvoříte XML element literálu, kombinace vložené výrazy s literálu textového obsahu.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 <span data-ttu-id="dfe6c-106">Pokud `isbnNumber` obsahuje 12345 celé číslo a `modifiedDate` obsahuje datum 3/5/2006, když tento kód provede, hodnota `book` je:</span><span class="sxs-lookup"><span data-stu-id="dfe6c-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="dfe6c-107">Umístění vložených výraz a ověřování</span><span class="sxs-lookup"><span data-stu-id="dfe6c-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="dfe6c-108">Vložené výrazy se může vyskytovat pouze v určitých umístění ve výrazech literál XML.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="dfe6c-109">Ovládací prvky výraz umístění, které typy výraz se můžete vrátit a jak `Nothing` se zpracovává.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="dfe6c-110">Následující tabulka popisuje povolených umístění a typy vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="dfe6c-111">Umístění v literál</span><span class="sxs-lookup"><span data-stu-id="dfe6c-111">Location in literal</span></span>|<span data-ttu-id="dfe6c-112">Typ výrazu</span><span class="sxs-lookup"><span data-stu-id="dfe6c-112">Type of expression</span></span>|<span data-ttu-id="dfe6c-113">Zpracování`Nothing`</span><span class="sxs-lookup"><span data-stu-id="dfe6c-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="dfe6c-114">Název elementu XML</span><span class="sxs-lookup"><span data-stu-id="dfe6c-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="dfe6c-115">Chyba</span><span class="sxs-lookup"><span data-stu-id="dfe6c-115">Error</span></span>|  
|<span data-ttu-id="dfe6c-116">Obsah elementu XML</span><span class="sxs-lookup"><span data-stu-id="dfe6c-116">XML element content</span></span>|<span data-ttu-id="dfe6c-117">`Object`nebo pole`Object`</span><span class="sxs-lookup"><span data-stu-id="dfe6c-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="dfe6c-118">Ignorováno</span><span class="sxs-lookup"><span data-stu-id="dfe6c-118">Ignored</span></span>|  
|<span data-ttu-id="dfe6c-119">Atribut název elementu XML</span><span class="sxs-lookup"><span data-stu-id="dfe6c-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="dfe6c-120">Chyba, pokud hodnota atributu je také`Nothing`</span><span class="sxs-lookup"><span data-stu-id="dfe6c-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="dfe6c-121">Hodnota atributu XML element</span><span class="sxs-lookup"><span data-stu-id="dfe6c-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="dfe6c-122">Atribut deklarace ignorovat</span><span class="sxs-lookup"><span data-stu-id="dfe6c-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="dfe6c-123">Atribut XML element</span><span class="sxs-lookup"><span data-stu-id="dfe6c-123">XML element attribute</span></span>|<span data-ttu-id="dfe6c-124"><xref:System.Xml.Linq.XAttribute>nebo kolekci<xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="dfe6c-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="dfe6c-125">Ignorováno</span><span class="sxs-lookup"><span data-stu-id="dfe6c-125">Ignored</span></span>|  
|<span data-ttu-id="dfe6c-126">Kořenový element dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="dfe6c-126">XML document root element</span></span>|<span data-ttu-id="dfe6c-127"><xref:System.Xml.Linq.XElement>nebo kolekce jednoho <xref:System.Xml.Linq.XElement> objekt a libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> a <xref:System.Xml.Linq.XComment> objekty</span><span class="sxs-lookup"><span data-stu-id="dfe6c-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="dfe6c-128">Ignorováno</span><span class="sxs-lookup"><span data-stu-id="dfe6c-128">Ignored</span></span>|  
  
-   <span data-ttu-id="dfe6c-129">Příklad embedded výrazu v název elementu XML:</span><span class="sxs-lookup"><span data-stu-id="dfe6c-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   <span data-ttu-id="dfe6c-130">Příklad výrazu vložený obsah elementu XML:</span><span class="sxs-lookup"><span data-stu-id="dfe6c-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   <span data-ttu-id="dfe6c-131">Příklad embedded výrazu v atributu název elementu XML:</span><span class="sxs-lookup"><span data-stu-id="dfe6c-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   <span data-ttu-id="dfe6c-132">Příklad embedded výrazu v hodnotě atributu – element XML:</span><span class="sxs-lookup"><span data-stu-id="dfe6c-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   <span data-ttu-id="dfe6c-133">Příklad embedded výrazu v atributu – element XML:</span><span class="sxs-lookup"><span data-stu-id="dfe6c-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   <span data-ttu-id="dfe6c-134">Příklad embedded výrazu v kořenový element dokumentu XML:</span><span class="sxs-lookup"><span data-stu-id="dfe6c-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 <span data-ttu-id="dfe6c-135">Pokud povolíte `Option Strict`, kompilátor ověří, že typ každý embedded výraz rozšiřuje na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="dfe6c-136">Jedinou výjimkou je pro kořenový element dokumentu XML, který bude ověřen při spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="dfe6c-137">Pokud je kompilovat bez `Option Strict`, můžete vložit výrazy typu `Object` a jejich typů bude ověřen v době běhu.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="dfe6c-138">V umístění, kde je volitelné, obsah vložené výrazy, které obsahují `Nothing` jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="dfe6c-139">To znamená, nemáte ke kontrole obsahu elementu hodnoty atributu, a elementy pole nejsou `Nothing` dříve, než použijete literál XML.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="dfe6c-140">Požadované hodnoty, například názvy elementu a atributu nelze `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="dfe6c-141">Další informace o použití vložených výrazu v konkrétní typ literál najdete v tématu [literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="dfe6c-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="dfe6c-142">Pravidla rozsahu</span><span class="sxs-lookup"><span data-stu-id="dfe6c-142">Scoping Rules</span></span>  
 <span data-ttu-id="dfe6c-143">Kompilátor převede každý literál XML volání konstruktoru pro příslušný typ literálu.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="dfe6c-144">Literál obsah a vložené výrazy v literál XML jsou předány jako argumenty pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="dfe6c-145">To znamená, že všechny [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programovací elementy, které jsou k dispozici literál XML je také možné jeho vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-145">This means that all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="dfe6c-146">V rámci literál XML, můžete přístup k oboru názvů XML, který je předpony deklarovat s `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="dfe6c-147">Můžete deklarovat nový obor názvů XML nebo stínové předponu existující obor názvů XML elementu s použitím `xmlns` atribut.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="dfe6c-148">Nový obor názvů je k dispozici na podřízených uzlů tohoto elementu, ale ne na XML – literály v vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfe6c-149">Pokud deklarace předponu oboru názvů XML pomocí `xmlns` atribut namespace hodnota atributu musí být konstantní řetězec.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="dfe6c-150">V tomto ohledu pomocí `xmlns` atribut je třeba pomocí `Imports` příkaz k deklaraci oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="dfe6c-151">Vložené výrazu nelze použít k určení hodnoty obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="dfe6c-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfe6c-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="dfe6c-152">See Also</span></span>  
 [<span data-ttu-id="dfe6c-153">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dfe6c-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="dfe6c-154">Literál dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="dfe6c-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [<span data-ttu-id="dfe6c-155">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="dfe6c-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="dfe6c-156">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="dfe6c-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="dfe6c-157">Imports – příkaz (Namespace .NET a typ)</span><span class="sxs-lookup"><span data-stu-id="dfe6c-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="dfe6c-158">Přehled literálů XML</span><span class="sxs-lookup"><span data-stu-id="dfe6c-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
