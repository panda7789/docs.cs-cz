---
title: Vlastnost osy podřízeného souboru XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 968154908bc6cb62bb221d42a1f71b329aa7096f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349453"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="f118e-102">Vlastnost osy podřízeného souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f118e-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="f118e-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span><span class="sxs-lookup"><span data-stu-id="f118e-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f118e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f118e-104">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="f118e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f118e-105">Parts</span></span>  
  
|<span data-ttu-id="f118e-106">Termín</span><span class="sxs-lookup"><span data-stu-id="f118e-106">Term</span></span>|<span data-ttu-id="f118e-107">Definice</span><span class="sxs-lookup"><span data-stu-id="f118e-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="f118e-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f118e-108">Required.</span></span> <span data-ttu-id="f118e-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span><span class="sxs-lookup"><span data-stu-id="f118e-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="f118e-110">.<</span><span class="sxs-lookup"><span data-stu-id="f118e-110">.<</span></span>|<span data-ttu-id="f118e-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f118e-111">Required.</span></span> <span data-ttu-id="f118e-112">Denotes the start of a child axis property.</span><span class="sxs-lookup"><span data-stu-id="f118e-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="f118e-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f118e-113">Required.</span></span> <span data-ttu-id="f118e-114">Name of the child nodes to access, of the form [`prefix:]name`.</span><span class="sxs-lookup"><span data-stu-id="f118e-114">Name of the child nodes to access, of the form [`prefix:]name`.</span></span><br /><br /> <span data-ttu-id="f118e-115">-   `Prefix` - Optional.</span><span class="sxs-lookup"><span data-stu-id="f118e-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="f118e-116">XML namespace prefix for the child node.</span><span class="sxs-lookup"><span data-stu-id="f118e-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="f118e-117">Must be a global XML namespace defined with an `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="f118e-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="f118e-118">-   `Name` - Required.</span><span class="sxs-lookup"><span data-stu-id="f118e-118">-   `Name` - Required.</span></span> <span data-ttu-id="f118e-119">Local child node name.</span><span class="sxs-lookup"><span data-stu-id="f118e-119">Local child node name.</span></span> <span data-ttu-id="f118e-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="f118e-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="f118e-121">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f118e-121">Required.</span></span> <span data-ttu-id="f118e-122">Denotes the end of a child axis property.</span><span class="sxs-lookup"><span data-stu-id="f118e-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="f118e-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f118e-123">Return Value</span></span>  
 <span data-ttu-id="f118e-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="f118e-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f118e-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f118e-125">Remarks</span></span>  
 <span data-ttu-id="f118e-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span><span class="sxs-lookup"><span data-stu-id="f118e-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="f118e-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span><span class="sxs-lookup"><span data-stu-id="f118e-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="f118e-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="f118e-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="f118e-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span><span class="sxs-lookup"><span data-stu-id="f118e-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="f118e-130">XML Namespaces</span><span class="sxs-lookup"><span data-stu-id="f118e-130">XML Namespaces</span></span>  
 <span data-ttu-id="f118e-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="f118e-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="f118e-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span><span class="sxs-lookup"><span data-stu-id="f118e-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="f118e-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="f118e-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f118e-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="f118e-134">Example</span></span>  
 <span data-ttu-id="f118e-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span><span class="sxs-lookup"><span data-stu-id="f118e-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="f118e-136">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="f118e-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="f118e-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="f118e-137">Example</span></span>  
 <span data-ttu-id="f118e-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span><span class="sxs-lookup"><span data-stu-id="f118e-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="f118e-139">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="f118e-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="f118e-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="f118e-140">Example</span></span>  
 <span data-ttu-id="f118e-141">The following example declares `ns` as an XML namespace prefix.</span><span class="sxs-lookup"><span data-stu-id="f118e-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="f118e-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="f118e-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="f118e-143">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="f118e-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="f118e-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f118e-144">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="f118e-145">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="f118e-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="f118e-146">Literály XML</span><span class="sxs-lookup"><span data-stu-id="f118e-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="f118e-147">Creating XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f118e-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="f118e-148">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="f118e-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
