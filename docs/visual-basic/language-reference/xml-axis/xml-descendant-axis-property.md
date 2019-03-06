---
title: Vlastnost osy nástupce XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: bc1dff6dc3b580079087f370212b7d3acd30e4fb
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353020"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="1ccd2-102">Vlastnost osy nástupce XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ccd2-102">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="1ccd2-103">Poskytuje přístup k následníky z následujících akcí: <xref:System.Xml.Linq.XElement> objektu, <xref:System.Xml.Linq.XDocument> object, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ccd2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ccd2-104">Syntax</span></span>

```
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="1ccd2-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1ccd2-105">Parts</span></span>

<span data-ttu-id="1ccd2-106">`object` Povinné.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-106">`object` Required.</span></span> <span data-ttu-id="1ccd2-107"><xref:System.Xml.Linq.XElement> Objekt, <xref:System.Xml.Linq.XDocument> object, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="1ccd2-108">`...<` Povinné.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-108">`...<` Required.</span></span> <span data-ttu-id="1ccd2-109">Označuje začátek vlastnost Následnické osy.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-109">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="1ccd2-110">`descendant` Povinné.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-110">`descendant` Required.</span></span> <span data-ttu-id="1ccd2-111">Název podřízených uzlů pro přístup k ve tvaru [`prefix:]name`.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-111">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="1ccd2-112">Část</span><span class="sxs-lookup"><span data-stu-id="1ccd2-112">Part</span></span>|<span data-ttu-id="1ccd2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1ccd2-113">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="1ccd2-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-114">Optional.</span></span> <span data-ttu-id="1ccd2-115">Předpona oboru názvů XML pro uzel potomka.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-115">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="1ccd2-116">Musí být globální obor názvů XML, který je definován s použitím `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-116">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="1ccd2-117">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-117">Required.</span></span> <span data-ttu-id="1ccd2-118">Místní název uzel potomka.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-118">Local name of the descendant node.</span></span> <span data-ttu-id="1ccd2-119">Zobrazit [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="1ccd2-119">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="1ccd2-120">`>` Povinné.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-120">`>` Required.</span></span> <span data-ttu-id="1ccd2-121">Označuje konec vlastnost Následnické osy.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-121">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="1ccd2-122">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1ccd2-122">Return Value</span></span>

<span data-ttu-id="1ccd2-123">Kolekce <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-123">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ccd2-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ccd2-124">Remarks</span></span>

<span data-ttu-id="1ccd2-125">Můžete použít vlastnost osy nástupce XML pro přístup k následnickým uzlů podle názvu ze <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objektu, nebo z kolekce <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-125">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="1ccd2-126">Použít XML `Value` pro přístup k hodnotě první uzel potomka v kolekci vrácené vlastností.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-126">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="1ccd2-127">Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="1ccd2-127">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>

<span data-ttu-id="1ccd2-128">Kompilátor jazyka Visual Basic převede vlastnosti osy nástupce na volání <xref:System.Xml.Linq.XContainer.Descendants%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-128">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="1ccd2-129">Obory názvů XML</span><span class="sxs-lookup"><span data-stu-id="1ccd2-129">XML Namespaces</span></span>

<span data-ttu-id="1ccd2-130">Název v vlastnost Následnické osy můžete použít pouze obory názvů XML globálně deklarované s `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-130">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="1ccd2-131">Místně deklarované v rámci elementu literály XML obory názvů XML nemůže používat.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-131">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="1ccd2-132">Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="1ccd2-132">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="1ccd2-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ccd2-133">Example</span></span>

<span data-ttu-id="1ccd2-134">Následující příklad ukazuje, jak přistupovat k hodnotě prvního následníky uzel s názvem `name` a hodnoty všech podřízených uzlů s názvem `phone` z `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-134">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="1ccd2-135">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="1ccd2-135">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="1ccd2-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ccd2-136">Example</span></span>

<span data-ttu-id="1ccd2-137">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-137">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="1ccd2-138">Poté použije předponu oboru názvů k vytvoření literálu XML a přistupovat k hodnotě první podřízený uzel s kvalifikovaným názvem `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="1ccd2-138">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="1ccd2-139">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="1ccd2-139">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="1ccd2-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ccd2-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="1ccd2-141">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="1ccd2-141">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="1ccd2-142">Literály XML</span><span class="sxs-lookup"><span data-stu-id="1ccd2-142">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="1ccd2-143">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ccd2-143">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="1ccd2-144">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="1ccd2-144">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
