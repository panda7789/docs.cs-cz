---
title: Vložené výrazy v XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: d4ff9442aa82a3eb46d56500159562174646ea58
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410254"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="2eaa5-102">Vložené výrazy v XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2eaa5-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="2eaa5-103">Vložené výrazy umožňují vytvořit literály XML, které obsahují výrazy, které jsou vyhodnocovány v době běhu.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="2eaa5-104">Syntaxe vloženého výrazu je `<%=` `expression` `%>` , která je stejná jako syntaxe použitá v ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in ASP.NET.</span></span>  
  
 <span data-ttu-id="2eaa5-105">Můžete například vytvořit literál elementu XML a zkombinovat vložené výrazy s textovým obsahem literálu.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 <span data-ttu-id="2eaa5-106">Pokud `isbnNumber` obsahuje celé číslo 12345 a `modifiedDate` obsahuje datum 3/5/2006, když se tento kód spustí, hodnota `book` je:</span><span class="sxs-lookup"><span data-stu-id="2eaa5-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="2eaa5-107">Umístění a ověřování vloženého výrazu</span><span class="sxs-lookup"><span data-stu-id="2eaa5-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="2eaa5-108">Vložené výrazy mohou být zobrazeny pouze v určitých umístěních ve výrazech literálů XML.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="2eaa5-109">Umístění výrazu určuje, které typy výrazů mohou vracet a jak `Nothing` je zpracována.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="2eaa5-110">Následující tabulka popisuje povolená umístění a typy vložených výrazů.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="2eaa5-111">Umístění v literálu</span><span class="sxs-lookup"><span data-stu-id="2eaa5-111">Location in literal</span></span>|<span data-ttu-id="2eaa5-112">Typ výrazu</span><span class="sxs-lookup"><span data-stu-id="2eaa5-112">Type of expression</span></span>|<span data-ttu-id="2eaa5-113">Manipulace s`Nothing`</span><span class="sxs-lookup"><span data-stu-id="2eaa5-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="2eaa5-114">Název elementu XML</span><span class="sxs-lookup"><span data-stu-id="2eaa5-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="2eaa5-115">Chyba</span><span class="sxs-lookup"><span data-stu-id="2eaa5-115">Error</span></span>|  
|<span data-ttu-id="2eaa5-116">Obsah elementu XML</span><span class="sxs-lookup"><span data-stu-id="2eaa5-116">XML element content</span></span>|<span data-ttu-id="2eaa5-117">`Object`nebo pole`Object`</span><span class="sxs-lookup"><span data-stu-id="2eaa5-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="2eaa5-118">Ignorováno</span><span class="sxs-lookup"><span data-stu-id="2eaa5-118">Ignored</span></span>|  
|<span data-ttu-id="2eaa5-119">Název atributu elementu XML</span><span class="sxs-lookup"><span data-stu-id="2eaa5-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="2eaa5-120">Chyba, pokud není hodnota atributu také`Nothing`</span><span class="sxs-lookup"><span data-stu-id="2eaa5-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="2eaa5-121">Hodnota atributu elementu XML</span><span class="sxs-lookup"><span data-stu-id="2eaa5-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="2eaa5-122">Deklarace atributu se ignorovala.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="2eaa5-123">Atribut elementu XML</span><span class="sxs-lookup"><span data-stu-id="2eaa5-123">XML element attribute</span></span>|<span data-ttu-id="2eaa5-124"><xref:System.Xml.Linq.XAttribute>nebo kolekce<xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="2eaa5-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="2eaa5-125">Ignorováno</span><span class="sxs-lookup"><span data-stu-id="2eaa5-125">Ignored</span></span>|  
|<span data-ttu-id="2eaa5-126">Kořenový element dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="2eaa5-126">XML document root element</span></span>|<span data-ttu-id="2eaa5-127"><xref:System.Xml.Linq.XElement>nebo kolekce jednoho <xref:System.Xml.Linq.XElement> objektu a libovolného počtu <xref:System.Xml.Linq.XProcessingInstruction> objektů a. <xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="2eaa5-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="2eaa5-128">Ignorováno</span><span class="sxs-lookup"><span data-stu-id="2eaa5-128">Ignored</span></span>|  
  
- <span data-ttu-id="2eaa5-129">Příklad vloženého výrazu v názvu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="2eaa5-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- <span data-ttu-id="2eaa5-130">Příklad vloženého výrazu v obsahu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="2eaa5-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- <span data-ttu-id="2eaa5-131">Příklad vloženého výrazu v názvu atributu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="2eaa5-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- <span data-ttu-id="2eaa5-132">Příklad vloženého výrazu v hodnotě atributu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="2eaa5-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- <span data-ttu-id="2eaa5-133">Příklad vloženého výrazu v atributu elementu XML:</span><span class="sxs-lookup"><span data-stu-id="2eaa5-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- <span data-ttu-id="2eaa5-134">Příklad vloženého výrazu v kořenovém elementu dokumentu XML:</span><span class="sxs-lookup"><span data-stu-id="2eaa5-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 <span data-ttu-id="2eaa5-135">Pokud povolíte `Option Strict` , kompilátor zkontroluje, že se typ každého vloženého výrazu rozšíří na požadovaný typ.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="2eaa5-136">Jediná výjimka je určena pro kořenový prvek dokumentu XML, který je ověřen při spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="2eaa5-137">Pokud kompilujete bez `Option Strict` , můžete vkládat výrazy typu `Object` a jejich typ je ověřován za běhu.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="2eaa5-138">V místech, kde je obsah nepovinný, vložené výrazy, které obsahují, `Nothing` se ignorují.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="2eaa5-139">To znamená, že nemusíte kontrolovat obsah elementu, hodnoty atributů a prvky pole, `Nothing` než použijete LITERÁL XML.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="2eaa5-140">Požadované hodnoty, jako jsou názvy elementů a atributů, nemůžou být `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="2eaa5-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="2eaa5-141">Další informace o použití vloženého výrazu v konkrétním typu literálu naleznete v tématu [literál dokumentu XML](../../../language-reference/xml-literals/xml-document-literal.md), [literál elementu XML](../../../language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="2eaa5-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="2eaa5-142">Pravidla oboru</span><span class="sxs-lookup"><span data-stu-id="2eaa5-142">Scoping Rules</span></span>  
 <span data-ttu-id="2eaa5-143">Kompilátor převede každý literál XML na volání konstruktoru pro příslušný typ literálu.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="2eaa5-144">Obsah literálu a vložené výrazy v literálu XML jsou předány jako argumenty konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="2eaa5-145">To znamená, že všechny programové prvky Visual Basic dostupné pro literál XML jsou také k dispozici pro vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-145">This means that all Visual Basic programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="2eaa5-146">V rámci literálu XML máte přístup k předponám oboru názvů XML deklarovaným pomocí `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="2eaa5-147">Můžete deklarovat novou předponu oboru názvů XML nebo vytvořit stín předpony oboru názvů XML v elementu pomocí `xmlns` atributu.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="2eaa5-148">Nový obor názvů je k dispozici podřízeným uzlům daného prvku, ale nikoli k literálům XML ve vložených výrazech.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2eaa5-149">Pokud deklarujete předponu oboru názvů XML pomocí `xmlns` atributu namespace, hodnota atributu musí být konstantní řetězec.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="2eaa5-150">V tomto ohledu použití `xmlns` atributu je například použití `Imports` příkazu k deklaraci oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="2eaa5-151">Vložený výraz nelze použít k určení hodnoty oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="2eaa5-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eaa5-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="2eaa5-152">See also</span></span>

- [<span data-ttu-id="2eaa5-153">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2eaa5-153">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="2eaa5-154">Literál dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="2eaa5-154">XML Document Literal</span></span>](../../../language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="2eaa5-155">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="2eaa5-155">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="2eaa5-156">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="2eaa5-156">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="2eaa5-157">Imports – příkaz (obor názvů a typ rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="2eaa5-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="2eaa5-158">Přehled literálů XML</span><span class="sxs-lookup"><span data-stu-id="2eaa5-158">XML Literals Overview</span></span>](xml-literals-overview.md)
