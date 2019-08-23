---
title: Vložené výrazy v XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 525fa04db86a299d88e1612aac76d014f35124eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922619"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="2f66b-102">Vložené výrazy v XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f66b-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="2f66b-103">Vložené výrazy umožňují vytvořit literály XML, které obsahují výrazy, které jsou vyhodnocovány v době běhu.</span><span class="sxs-lookup"><span data-stu-id="2f66b-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="2f66b-104">Syntaxe vloženého výrazu je `<%=` `expression` `%>`, která je stejná jako syntaxe použitá v ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2f66b-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in ASP.NET.</span></span>  
  
 <span data-ttu-id="2f66b-105">Můžete například vytvořit literál elementu XML a zkombinovat vložené výrazy s textovým obsahem literálu.</span><span class="sxs-lookup"><span data-stu-id="2f66b-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 <span data-ttu-id="2f66b-106">Pokud `isbnNumber` obsahuje celé číslo 12345 a `modifiedDate` obsahuje datum 3/5/2006, když se tento kód `book` spustí, hodnota je:</span><span class="sxs-lookup"><span data-stu-id="2f66b-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="2f66b-107">Umístění a ověřování vloženého výrazu</span><span class="sxs-lookup"><span data-stu-id="2f66b-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="2f66b-108">Vložené výrazy mohou být zobrazeny pouze v určitých umístěních ve výrazech literálů XML.</span><span class="sxs-lookup"><span data-stu-id="2f66b-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="2f66b-109">Umístění výrazu určuje, které typy výrazů mohou vracet a jak `Nothing` je zpracována.</span><span class="sxs-lookup"><span data-stu-id="2f66b-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="2f66b-110">Následující tabulka popisuje povolená umístění a typy vložených výrazů.</span><span class="sxs-lookup"><span data-stu-id="2f66b-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="2f66b-111">Umístění v literálu</span><span class="sxs-lookup"><span data-stu-id="2f66b-111">Location in literal</span></span>|<span data-ttu-id="2f66b-112">Typ výrazu</span><span class="sxs-lookup"><span data-stu-id="2f66b-112">Type of expression</span></span>|<span data-ttu-id="2f66b-113">Manipulace s`Nothing`</span><span class="sxs-lookup"><span data-stu-id="2f66b-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="2f66b-114">Název elementu XML</span><span class="sxs-lookup"><span data-stu-id="2f66b-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="2f66b-115">Chyba</span><span class="sxs-lookup"><span data-stu-id="2f66b-115">Error</span></span>|  
|<span data-ttu-id="2f66b-116">Obsah elementu XML</span><span class="sxs-lookup"><span data-stu-id="2f66b-116">XML element content</span></span>|<span data-ttu-id="2f66b-117">`Object`nebo pole`Object`</span><span class="sxs-lookup"><span data-stu-id="2f66b-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="2f66b-118">Ignorováno</span><span class="sxs-lookup"><span data-stu-id="2f66b-118">Ignored</span></span>|  
|<span data-ttu-id="2f66b-119">Název atributu elementu XML</span><span class="sxs-lookup"><span data-stu-id="2f66b-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="2f66b-120">Chyba, pokud není hodnota atributu také`Nothing`</span><span class="sxs-lookup"><span data-stu-id="2f66b-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="2f66b-121">Hodnota atributu elementu XML</span><span class="sxs-lookup"><span data-stu-id="2f66b-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="2f66b-122">Deklarace atributu se ignorovala.</span><span class="sxs-lookup"><span data-stu-id="2f66b-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="2f66b-123">Atribut elementu XML</span><span class="sxs-lookup"><span data-stu-id="2f66b-123">XML element attribute</span></span>|<span data-ttu-id="2f66b-124"><xref:System.Xml.Linq.XAttribute>nebo kolekce<xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="2f66b-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="2f66b-125">Ignorováno</span><span class="sxs-lookup"><span data-stu-id="2f66b-125">Ignored</span></span>|  
|<span data-ttu-id="2f66b-126">Kořenový element dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="2f66b-126">XML document root element</span></span>|<span data-ttu-id="2f66b-127"><xref:System.Xml.Linq.XElement>nebo kolekce jednoho <xref:System.Xml.Linq.XElement> objektu a libovolného <xref:System.Xml.Linq.XProcessingInstruction> počtu objektů a <xref:System.Xml.Linq.XComment> .</span><span class="sxs-lookup"><span data-stu-id="2f66b-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="2f66b-128">Ignorováno</span><span class="sxs-lookup"><span data-stu-id="2f66b-128">Ignored</span></span>|  
  
- <span data-ttu-id="2f66b-129">Příklad vloženého výrazu v názvu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="2f66b-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- <span data-ttu-id="2f66b-130">Příklad vloženého výrazu v obsahu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="2f66b-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- <span data-ttu-id="2f66b-131">Příklad vloženého výrazu v názvu atributu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="2f66b-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- <span data-ttu-id="2f66b-132">Příklad vloženého výrazu v hodnotě atributu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="2f66b-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- <span data-ttu-id="2f66b-133">Příklad vloženého výrazu v atributu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="2f66b-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- <span data-ttu-id="2f66b-134">Příklad vloženého výrazu v kořenovém elementu dokumentu XML:</span><span class="sxs-lookup"><span data-stu-id="2f66b-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 <span data-ttu-id="2f66b-135">Pokud povolíte `Option Strict`, kompilátor zkontroluje, že se typ každého vloženého výrazu rozšíří na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="2f66b-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="2f66b-136">Jediná výjimka je určena pro kořenový prvek dokumentu XML, který je ověřen při spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="2f66b-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="2f66b-137">Pokud kompilujete bez `Option Strict`, můžete vkládat výrazy typu `Object` a jejich typ je ověřován za běhu.</span><span class="sxs-lookup"><span data-stu-id="2f66b-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="2f66b-138">V místech, kde je obsah nepovinný, vložené `Nothing` výrazy, které obsahují, se ignorují.</span><span class="sxs-lookup"><span data-stu-id="2f66b-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="2f66b-139">To znamená, že nemusíte kontrolovat obsah elementu, hodnoty atributů a prvky `Nothing` pole, než použijete literál XML.</span><span class="sxs-lookup"><span data-stu-id="2f66b-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="2f66b-140">Požadované hodnoty, jako jsou názvy elementů a atributů, nemůžou být `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="2f66b-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="2f66b-141">Další informace o použití vloženého výrazu v konkrétním typu literálu naleznete v tématu [literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [literál elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="2f66b-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="2f66b-142">Pravidla oboru</span><span class="sxs-lookup"><span data-stu-id="2f66b-142">Scoping Rules</span></span>  
 <span data-ttu-id="2f66b-143">Kompilátor převede každý literál XML na volání konstruktoru pro příslušný typ literálu.</span><span class="sxs-lookup"><span data-stu-id="2f66b-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="2f66b-144">Obsah literálu a vložené výrazy v literálu XML jsou předány jako argumenty konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="2f66b-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="2f66b-145">To znamená, že všechny programové prvky Visual Basic dostupné pro literál XML jsou také k dispozici pro vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="2f66b-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="2f66b-146">V rámci literálu XML máte přístup k předponám oboru názvů XML deklarovaným pomocí `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="2f66b-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="2f66b-147">Můžete deklarovat novou předponu oboru názvů XML nebo vytvořit stín předpony oboru názvů XML v elementu pomocí `xmlns` atributu.</span><span class="sxs-lookup"><span data-stu-id="2f66b-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="2f66b-148">Nový obor názvů je k dispozici podřízeným uzlům daného prvku, ale nikoli k literálům XML ve vložených výrazech.</span><span class="sxs-lookup"><span data-stu-id="2f66b-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f66b-149">Pokud deklarujete předponu oboru názvů XML pomocí `xmlns` atributu namespace, hodnota atributu musí být konstantní řetězec.</span><span class="sxs-lookup"><span data-stu-id="2f66b-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="2f66b-150">V tomto ohledu použití `xmlns` atributu je například `Imports` použití příkazu k deklaraci oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="2f66b-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="2f66b-151">Vložený výraz nelze použít k určení hodnoty oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="2f66b-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f66b-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f66b-152">See also</span></span>

- [<span data-ttu-id="2f66b-153">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f66b-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="2f66b-154">Literál dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="2f66b-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="2f66b-155">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="2f66b-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="2f66b-156">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="2f66b-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="2f66b-157">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="2f66b-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="2f66b-158">Přehled literálů XML</span><span class="sxs-lookup"><span data-stu-id="2f66b-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
