---
title: Vlastnost osy podřízeného souboru XML (Visual Basic)
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
ms.openlocfilehash: 1407a3315d8971895b70893af9d85c8bb428c3be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603857"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="70dc8-102">Vlastnost osy podřízeného souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70dc8-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="70dc8-103">Poskytuje přístup k podřízené objekty daného jednu z následujících: <xref:System.Xml.Linq.XElement> objektu, <xref:System.Xml.Linq.XDocument> objektu, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="70dc8-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70dc8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70dc8-104">Syntax</span></span>  
  
```  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="70dc8-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="70dc8-105">Parts</span></span>  
  
|<span data-ttu-id="70dc8-106">Termín</span><span class="sxs-lookup"><span data-stu-id="70dc8-106">Term</span></span>|<span data-ttu-id="70dc8-107">Definice</span><span class="sxs-lookup"><span data-stu-id="70dc8-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="70dc8-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="70dc8-108">Required.</span></span> <span data-ttu-id="70dc8-109"><xref:System.Xml.Linq.XElement> Objektu, <xref:System.Xml.Linq.XDocument> objektu, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="70dc8-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="70dc8-110">.<</span><span class="sxs-lookup"><span data-stu-id="70dc8-110">.<</span></span>|<span data-ttu-id="70dc8-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="70dc8-111">Required.</span></span> <span data-ttu-id="70dc8-112">Označuje začátek vlastnost osy podřízeného.</span><span class="sxs-lookup"><span data-stu-id="70dc8-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="70dc8-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="70dc8-113">Required.</span></span> <span data-ttu-id="70dc8-114">Název podřízené uzly pro přístup k ve formátu [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="70dc8-114">Name of the child nodes to access, of the form [`prefix``:`]`name`.</span></span><br /><br /> <span data-ttu-id="70dc8-115">-   `Prefix` -Volitelné.</span><span class="sxs-lookup"><span data-stu-id="70dc8-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="70dc8-116">Předpona oboru názvů XML pro podřízený uzel.</span><span class="sxs-lookup"><span data-stu-id="70dc8-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="70dc8-117">Musí být globální obor názvů XML definovány se `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="70dc8-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="70dc8-118">-   `Name` -Vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="70dc8-118">-   `Name` - Required.</span></span> <span data-ttu-id="70dc8-119">Název místní podřízený uzel.</span><span class="sxs-lookup"><span data-stu-id="70dc8-119">Local child node name.</span></span> <span data-ttu-id="70dc8-120">V tématu [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="70dc8-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="70dc8-121">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="70dc8-121">Required.</span></span> <span data-ttu-id="70dc8-122">Označuje konec vlastnost osy podřízeného.</span><span class="sxs-lookup"><span data-stu-id="70dc8-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="70dc8-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="70dc8-123">Return Value</span></span>  
 <span data-ttu-id="70dc8-124">Kolekce <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="70dc8-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70dc8-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70dc8-125">Remarks</span></span>  
 <span data-ttu-id="70dc8-126">Můžete vlastnost osy podřízeného souboru XML pro přístup k podřízené uzly podle názvu z <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt, nebo z kolekce <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="70dc8-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="70dc8-127">Použít soubor XML `Value` vlastnost pro přístup k hodnotě první podřízený uzel v vrácená kolekce.</span><span class="sxs-lookup"><span data-stu-id="70dc8-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="70dc8-128">Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="70dc8-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="70dc8-129">Visual Basic – kompilátor převede vlastnosti osy podřízeného volání <xref:System.Xml.Linq.XContainer.Elements%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="70dc8-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="70dc8-130">Obory názvů XML</span><span class="sxs-lookup"><span data-stu-id="70dc8-130">XML Namespaces</span></span>  
 <span data-ttu-id="70dc8-131">Název v vlastnost osy podřízeného můžete použít pouze XML – předpony oboru názvů globálně deklarovat s `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="70dc8-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="70dc8-132">Nemůže používat lokálně deklarované v rámci elementu XML – literály XML – předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="70dc8-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="70dc8-133">Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="70dc8-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="70dc8-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="70dc8-134">Example</span></span>  
 <span data-ttu-id="70dc8-135">Následující příklad ukazuje, jak získat přístup k podřízené uzly s názvem `phone` z `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="70dc8-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 <span data-ttu-id="70dc8-136">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="70dc8-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="70dc8-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="70dc8-137">Example</span></span>  
 <span data-ttu-id="70dc8-138">Následující příklad ukazuje, jak získat přístup k podřízené uzly s názvem `phone` z kolekce vrácené `contact` vlastnost podřízené osy `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="70dc8-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 <span data-ttu-id="70dc8-139">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="70dc8-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="70dc8-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="70dc8-140">Example</span></span>  
 <span data-ttu-id="70dc8-141">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="70dc8-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="70dc8-142">Poté použije Předpona oboru názvů k vytvoření literál XML a přístup k první podřízený uzel s kvalifikovaný název `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="70dc8-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 <span data-ttu-id="70dc8-143">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="70dc8-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="70dc8-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="70dc8-144">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="70dc8-145">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="70dc8-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="70dc8-146">Literály XML</span><span class="sxs-lookup"><span data-stu-id="70dc8-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="70dc8-147">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70dc8-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="70dc8-148">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="70dc8-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
