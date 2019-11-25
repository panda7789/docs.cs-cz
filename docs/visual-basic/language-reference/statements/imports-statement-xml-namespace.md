---
title: Imports Statement - XML Namespace
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 52864e4d1c8183b6243025e72368d23627049c84
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351052"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="b3950-102">Imports – Příkaz (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="b3950-102">Imports Statement (XML Namespace)</span></span>

<span data-ttu-id="b3950-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span><span class="sxs-lookup"><span data-stu-id="b3950-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="b3950-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3950-104">Syntax</span></span>

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a><span data-ttu-id="b3950-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b3950-105">Parts</span></span>

`xmlNamespacePrefix`  
<span data-ttu-id="b3950-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b3950-106">Optional.</span></span> <span data-ttu-id="b3950-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span><span class="sxs-lookup"><span data-stu-id="b3950-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="b3950-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span><span class="sxs-lookup"><span data-stu-id="b3950-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="b3950-109">Must be a valid XML identifier.</span><span class="sxs-lookup"><span data-stu-id="b3950-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="b3950-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b3950-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>

`xmlNamespaceName`  
<span data-ttu-id="b3950-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b3950-111">Required.</span></span> <span data-ttu-id="b3950-112">The string identifying the XML namespace being imported.</span><span class="sxs-lookup"><span data-stu-id="b3950-112">The string identifying the XML namespace being imported.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3950-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3950-113">Remarks</span></span>

<span data-ttu-id="b3950-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span><span class="sxs-lookup"><span data-stu-id="b3950-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="b3950-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span><span class="sxs-lookup"><span data-stu-id="b3950-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="b3950-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="b3950-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>

<span data-ttu-id="b3950-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span><span class="sxs-lookup"><span data-stu-id="b3950-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="b3950-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span><span class="sxs-lookup"><span data-stu-id="b3950-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="b3950-119">You can use it when you create XML element literals and when you access XML axis properties.</span><span class="sxs-lookup"><span data-stu-id="b3950-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="b3950-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/index.md).</span><span class="sxs-lookup"><span data-stu-id="b3950-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/index.md).</span></span>

<span data-ttu-id="b3950-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span><span class="sxs-lookup"><span data-stu-id="b3950-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="b3950-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span><span class="sxs-lookup"><span data-stu-id="b3950-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="b3950-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span><span class="sxs-lookup"><span data-stu-id="b3950-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="b3950-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span><span class="sxs-lookup"><span data-stu-id="b3950-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>

<span data-ttu-id="b3950-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span><span class="sxs-lookup"><span data-stu-id="b3950-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="b3950-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span><span class="sxs-lookup"><span data-stu-id="b3950-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="b3950-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span><span class="sxs-lookup"><span data-stu-id="b3950-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>

<span data-ttu-id="b3950-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span><span class="sxs-lookup"><span data-stu-id="b3950-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="b3950-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span><span class="sxs-lookup"><span data-stu-id="b3950-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="b3950-130">This includes both code files and project-level imported namespaces.</span><span class="sxs-lookup"><span data-stu-id="b3950-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="b3950-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b3950-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="b3950-132">Each source file can contain any number of `Imports` statements.</span><span class="sxs-lookup"><span data-stu-id="b3950-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="b3950-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span><span class="sxs-lookup"><span data-stu-id="b3950-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>

## <a name="example"></a><span data-ttu-id="b3950-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3950-134">Example</span></span>

<span data-ttu-id="b3950-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span><span class="sxs-lookup"><span data-stu-id="b3950-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="b3950-136">It then creates XML literals that use both namespaces.</span><span class="sxs-lookup"><span data-stu-id="b3950-136">It then creates XML literals that use both namespaces.</span></span>

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

<span data-ttu-id="b3950-137">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="b3950-137">This code displays the following text:</span></span>

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a><span data-ttu-id="b3950-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3950-138">Example</span></span>

<span data-ttu-id="b3950-139">The following example imports the XML namespace prefix `ns`.</span><span class="sxs-lookup"><span data-stu-id="b3950-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="b3950-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span><span class="sxs-lookup"><span data-stu-id="b3950-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="b3950-141">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="b3950-141">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="b3950-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span><span class="sxs-lookup"><span data-stu-id="b3950-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>

## <a name="example"></a><span data-ttu-id="b3950-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3950-143">Example</span></span>

<span data-ttu-id="b3950-144">The following example imports the XML namespace prefix `ns`.</span><span class="sxs-lookup"><span data-stu-id="b3950-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="b3950-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="b3950-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

<span data-ttu-id="b3950-146">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="b3950-146">This code displays the following text:</span></span>

`Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="b3950-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3950-147">See also</span></span>

- [<span data-ttu-id="b3950-148">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="b3950-148">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="b3950-149">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="b3950-149">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="b3950-150">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="b3950-150">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="b3950-151">Operátor GetXmlNamespace</span><span class="sxs-lookup"><span data-stu-id="b3950-151">GetXmlNamespace Operator</span></span>](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
