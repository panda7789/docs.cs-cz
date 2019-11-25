---
title: Literál XML elementu
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6d900ca6868cfffe6b0e5b349321a79c5716c46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347031"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="b5682-102">Literál XML elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5682-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="b5682-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span><span class="sxs-lookup"><span data-stu-id="b5682-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5682-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5682-104">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="b5682-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b5682-105">Parts</span></span>

- `<`

  <span data-ttu-id="b5682-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b5682-106">Required.</span></span> <span data-ttu-id="b5682-107">Opens the starting element tag.</span><span class="sxs-lookup"><span data-stu-id="b5682-107">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="b5682-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b5682-108">Required.</span></span> <span data-ttu-id="b5682-109">Name of the element.</span><span class="sxs-lookup"><span data-stu-id="b5682-109">Name of the element.</span></span> <span data-ttu-id="b5682-110">The format is one of the following:</span><span class="sxs-lookup"><span data-stu-id="b5682-110">The format is one of the following:</span></span>

  - <span data-ttu-id="b5682-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span><span class="sxs-lookup"><span data-stu-id="b5682-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="b5682-112">Part</span><span class="sxs-lookup"><span data-stu-id="b5682-112">Part</span></span>|<span data-ttu-id="b5682-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b5682-113">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="b5682-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b5682-114">Optional.</span></span> <span data-ttu-id="b5682-115">XML namespace prefix for the element.</span><span class="sxs-lookup"><span data-stu-id="b5682-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="b5682-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span><span class="sxs-lookup"><span data-stu-id="b5682-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="b5682-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b5682-117">Required.</span></span> <span data-ttu-id="b5682-118">Name of the element.</span><span class="sxs-lookup"><span data-stu-id="b5682-118">Name of the element.</span></span> <span data-ttu-id="b5682-119">The format is one of the following:</span><span class="sxs-lookup"><span data-stu-id="b5682-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="b5682-120">- Literal text.</span><span class="sxs-lookup"><span data-stu-id="b5682-120">- Literal text.</span></span> <span data-ttu-id="b5682-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b5682-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="b5682-122">- Embedded expression of the form `<%= eNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="b5682-122">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="b5682-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="b5682-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="b5682-124">Embedded expression of the form `<%= nameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="b5682-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="b5682-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="b5682-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="b5682-126">An embedded expression is not allowed in a closing tag of an element.</span><span class="sxs-lookup"><span data-stu-id="b5682-126">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="b5682-127">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b5682-127">Optional.</span></span> <span data-ttu-id="b5682-128">List of attributes declared in the literal.</span><span class="sxs-lookup"><span data-stu-id="b5682-128">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="b5682-129">Each `attribute` has one of the following syntaxes:</span><span class="sxs-lookup"><span data-stu-id="b5682-129">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="b5682-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span><span class="sxs-lookup"><span data-stu-id="b5682-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="b5682-131">Part</span><span class="sxs-lookup"><span data-stu-id="b5682-131">Part</span></span>|<span data-ttu-id="b5682-132">Popis</span><span class="sxs-lookup"><span data-stu-id="b5682-132">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="b5682-133">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b5682-133">Optional.</span></span> <span data-ttu-id="b5682-134">XML namespace prefix for the attribute.</span><span class="sxs-lookup"><span data-stu-id="b5682-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="b5682-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span><span class="sxs-lookup"><span data-stu-id="b5682-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="b5682-136">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b5682-136">Required.</span></span> <span data-ttu-id="b5682-137">Name of the attribute.</span><span class="sxs-lookup"><span data-stu-id="b5682-137">Name of the attribute.</span></span> <span data-ttu-id="b5682-138">The format is one of the following:</span><span class="sxs-lookup"><span data-stu-id="b5682-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="b5682-139">- Literal text.</span><span class="sxs-lookup"><span data-stu-id="b5682-139">- Literal text.</span></span> <span data-ttu-id="b5682-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b5682-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="b5682-141">- Embedded expression of the form `<%= aNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="b5682-141">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="b5682-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="b5682-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="b5682-143">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b5682-143">Optional.</span></span> <span data-ttu-id="b5682-144">Value of the attribute.</span><span class="sxs-lookup"><span data-stu-id="b5682-144">Value of the attribute.</span></span> <span data-ttu-id="b5682-145">The format is one of the following:</span><span class="sxs-lookup"><span data-stu-id="b5682-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="b5682-146">- Literal text, enclosed in quotation marks.</span><span class="sxs-lookup"><span data-stu-id="b5682-146">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="b5682-147">- Embedded expression of the form `<%= aValueExp %>`.</span><span class="sxs-lookup"><span data-stu-id="b5682-147">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="b5682-148">Any type is allowed.</span><span class="sxs-lookup"><span data-stu-id="b5682-148">Any type is allowed.</span></span>|

  - <span data-ttu-id="b5682-149">Embedded expression of the form `<%= aExp %>`.</span><span class="sxs-lookup"><span data-stu-id="b5682-149">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="b5682-150">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b5682-150">Optional.</span></span> <span data-ttu-id="b5682-151">Indicates that the element is an empty element, without content.</span><span class="sxs-lookup"><span data-stu-id="b5682-151">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="b5682-152">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b5682-152">Required.</span></span> <span data-ttu-id="b5682-153">Ends the beginning or empty element tag.</span><span class="sxs-lookup"><span data-stu-id="b5682-153">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="b5682-154">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b5682-154">Optional.</span></span> <span data-ttu-id="b5682-155">Content of the element.</span><span class="sxs-lookup"><span data-stu-id="b5682-155">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="b5682-156">Each `content` can be one of the following:</span><span class="sxs-lookup"><span data-stu-id="b5682-156">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="b5682-157">Literal text.</span><span class="sxs-lookup"><span data-stu-id="b5682-157">Literal text.</span></span> <span data-ttu-id="b5682-158">All the white space in `elementContents` becomes significant if there is any literal text.</span><span class="sxs-lookup"><span data-stu-id="b5682-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="b5682-159">Embedded expression of the form `<%= contentExp %>`.</span><span class="sxs-lookup"><span data-stu-id="b5682-159">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="b5682-160">XML element literal.</span><span class="sxs-lookup"><span data-stu-id="b5682-160">XML element literal.</span></span>

  - <span data-ttu-id="b5682-161">XML comment literal.</span><span class="sxs-lookup"><span data-stu-id="b5682-161">XML comment literal.</span></span> <span data-ttu-id="b5682-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="b5682-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>

  - <span data-ttu-id="b5682-163">XML processing instruction literal.</span><span class="sxs-lookup"><span data-stu-id="b5682-163">XML processing instruction literal.</span></span> <span data-ttu-id="b5682-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="b5682-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="b5682-165">XML CDATA literal.</span><span class="sxs-lookup"><span data-stu-id="b5682-165">XML CDATA literal.</span></span> <span data-ttu-id="b5682-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="b5682-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="b5682-167">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b5682-167">Optional.</span></span> <span data-ttu-id="b5682-168">Represents the closing tag for the element.</span><span class="sxs-lookup"><span data-stu-id="b5682-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="b5682-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span><span class="sxs-lookup"><span data-stu-id="b5682-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="b5682-170">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b5682-170">Return Value</span></span>

<span data-ttu-id="b5682-171">An <xref:System.Xml.Linq.XElement> object.</span><span class="sxs-lookup"><span data-stu-id="b5682-171">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5682-172">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5682-172">Remarks</span></span>

<span data-ttu-id="b5682-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span><span class="sxs-lookup"><span data-stu-id="b5682-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="b5682-174">An XML literal can span multiple lines without using line continuation characters.</span><span class="sxs-lookup"><span data-stu-id="b5682-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="b5682-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span><span class="sxs-lookup"><span data-stu-id="b5682-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="b5682-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span><span class="sxs-lookup"><span data-stu-id="b5682-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="b5682-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b5682-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="b5682-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span><span class="sxs-lookup"><span data-stu-id="b5682-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="b5682-179">XML Namespaces</span><span class="sxs-lookup"><span data-stu-id="b5682-179">XML Namespaces</span></span>

<span data-ttu-id="b5682-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span><span class="sxs-lookup"><span data-stu-id="b5682-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="b5682-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span><span class="sxs-lookup"><span data-stu-id="b5682-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="b5682-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b5682-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="b5682-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span><span class="sxs-lookup"><span data-stu-id="b5682-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="b5682-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span><span class="sxs-lookup"><span data-stu-id="b5682-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="b5682-185">The embedded expression can access only the global XML namespace.</span><span class="sxs-lookup"><span data-stu-id="b5682-185">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="b5682-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span><span class="sxs-lookup"><span data-stu-id="b5682-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="b5682-187">Global XML namespaces that are not used do not appear in the generated code.</span><span class="sxs-lookup"><span data-stu-id="b5682-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="b5682-188">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5682-188">Example</span></span>

<span data-ttu-id="b5682-189">The following example shows how to create a simple XML element that has two nested empty elements.</span><span class="sxs-lookup"><span data-stu-id="b5682-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="b5682-190">The example displays the following text.</span><span class="sxs-lookup"><span data-stu-id="b5682-190">The example displays the following text.</span></span> <span data-ttu-id="b5682-191">Notice that the literal preserves the structure of the empty elements.</span><span class="sxs-lookup"><span data-stu-id="b5682-191">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="b5682-192">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5682-192">Example</span></span>

<span data-ttu-id="b5682-193">The following example shows how to use embedded expressions to name an element and create attributes.</span><span class="sxs-lookup"><span data-stu-id="b5682-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="b5682-194">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="b5682-194">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="b5682-195">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5682-195">Example</span></span>

<span data-ttu-id="b5682-196">The following example declares `ns` as an XML namespace prefix.</span><span class="sxs-lookup"><span data-stu-id="b5682-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="b5682-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span><span class="sxs-lookup"><span data-stu-id="b5682-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="b5682-198">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="b5682-198">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="b5682-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span><span class="sxs-lookup"><span data-stu-id="b5682-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="b5682-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span><span class="sxs-lookup"><span data-stu-id="b5682-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="b5682-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="b5682-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5682-202">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5682-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="b5682-203">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="b5682-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="b5682-204">Literál komentáře XML</span><span class="sxs-lookup"><span data-stu-id="b5682-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="b5682-205">Literál XML CDATA</span><span class="sxs-lookup"><span data-stu-id="b5682-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [<span data-ttu-id="b5682-206">Literály XML</span><span class="sxs-lookup"><span data-stu-id="b5682-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="b5682-207">Creating XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5682-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="b5682-208">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="b5682-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="b5682-209">Příkaz Imports (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="b5682-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
