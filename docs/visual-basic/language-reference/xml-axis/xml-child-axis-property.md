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
ms.openlocfilehash: 597a7bef66ac3908345aa5c8b59c838a3e65b2f4
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065879"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="73f78-102">Vlastnost osy podřízeného souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73f78-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="73f78-103">Poskytuje přístup k podřízené objekty daného jednu z následujících: <xref:System.Xml.Linq.XElement> objekt, <xref:System.Xml.Linq.XDocument> object, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="73f78-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73f78-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73f78-104">Syntax</span></span>  
  
```  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="73f78-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="73f78-105">Parts</span></span>  
  
|<span data-ttu-id="73f78-106">Termín</span><span class="sxs-lookup"><span data-stu-id="73f78-106">Term</span></span>|<span data-ttu-id="73f78-107">Definice</span><span class="sxs-lookup"><span data-stu-id="73f78-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="73f78-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="73f78-108">Required.</span></span> <span data-ttu-id="73f78-109"><xref:System.Xml.Linq.XElement> Objekt, <xref:System.Xml.Linq.XDocument> object, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="73f78-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="73f78-110">.<</span><span class="sxs-lookup"><span data-stu-id="73f78-110">.<</span></span>|<span data-ttu-id="73f78-111">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="73f78-111">Required.</span></span> <span data-ttu-id="73f78-112">Označuje začátek vlastnost osy podřízeného.</span><span class="sxs-lookup"><span data-stu-id="73f78-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="73f78-113">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="73f78-113">Required.</span></span> <span data-ttu-id="73f78-114">Název podřízené uzly, které chcete získat přístup, a to ve tvaru [`prefix:]name`.</span><span class="sxs-lookup"><span data-stu-id="73f78-114">Name of the child nodes to access, of the form [`prefix:]name`.</span></span><br /><br /> <span data-ttu-id="73f78-115">-   `Prefix` – Volitelné.</span><span class="sxs-lookup"><span data-stu-id="73f78-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="73f78-116">Předpona oboru názvů XML pro podřízený uzel.</span><span class="sxs-lookup"><span data-stu-id="73f78-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="73f78-117">Musí se definovat globální obor názvů XML `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="73f78-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="73f78-118">-   `Name` -Vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="73f78-118">-   `Name` - Required.</span></span> <span data-ttu-id="73f78-119">Název místní podřízeného uzlu.</span><span class="sxs-lookup"><span data-stu-id="73f78-119">Local child node name.</span></span> <span data-ttu-id="73f78-120">Zobrazit [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="73f78-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="73f78-121">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="73f78-121">Required.</span></span> <span data-ttu-id="73f78-122">Označuje konec vlastnost osy podřízeného.</span><span class="sxs-lookup"><span data-stu-id="73f78-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="73f78-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="73f78-123">Return Value</span></span>  
 <span data-ttu-id="73f78-124">Kolekce <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="73f78-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73f78-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73f78-125">Remarks</span></span>  
 <span data-ttu-id="73f78-126">Vlastnost osy podřízeného souboru XML můžete použít k přístupu k podřízené uzly prostřednictvím jeho názvu <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objektu, nebo z kolekce <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="73f78-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="73f78-127">Použít XML `Value` pro přístup k hodnotě první podřízený uzel v kolekci vrácené vlastností.</span><span class="sxs-lookup"><span data-stu-id="73f78-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="73f78-128">Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="73f78-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="73f78-129">Kompilátor jazyka Visual Basic převede podřízené vlastnosti osy na volání <xref:System.Xml.Linq.XContainer.Elements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="73f78-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="73f78-130">Obory názvů XML</span><span class="sxs-lookup"><span data-stu-id="73f78-130">XML Namespaces</span></span>  
 <span data-ttu-id="73f78-131">Název v vlastnost osy podřízeného lze použít pouze předpon oboru názvů XML globálně deklarované s `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="73f78-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="73f78-132">Místně deklarované v rámci elementu literály XML předpon názvového prostoru XML nemůže používat.</span><span class="sxs-lookup"><span data-stu-id="73f78-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="73f78-133">Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="73f78-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73f78-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="73f78-134">Example</span></span>  
 <span data-ttu-id="73f78-135">Následující příklad ukazuje, jak získat přístup k podřízené uzly s názvem `phone` z `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="73f78-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 <span data-ttu-id="73f78-136">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="73f78-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="73f78-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="73f78-137">Example</span></span>  
 <span data-ttu-id="73f78-138">Následující příklad ukazuje, jak získat přístup k podřízené uzly s názvem `phone` v kolekci vrácené poskytovatelem `contact` vlastnost podřízené osy `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="73f78-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 <span data-ttu-id="73f78-139">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="73f78-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="73f78-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="73f78-140">Example</span></span>  
 <span data-ttu-id="73f78-141">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="73f78-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="73f78-142">Poté použije předponu oboru názvů XML vytvoření literálu a přístup k první podřízený uzel s kvalifikovaným názvem `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="73f78-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 <span data-ttu-id="73f78-143">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="73f78-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="73f78-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73f78-144">See also</span></span>
- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="73f78-145">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="73f78-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="73f78-146">Literály XML</span><span class="sxs-lookup"><span data-stu-id="73f78-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="73f78-147">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="73f78-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="73f78-148">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="73f78-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
