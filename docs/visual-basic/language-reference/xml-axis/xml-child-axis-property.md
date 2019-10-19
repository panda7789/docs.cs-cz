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
ms.openlocfilehash: 88d0b1f315bc1bb9dc474604d222a8ebcc1e40aa
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582244"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="6c0f3-102">Vlastnost osy podřízeného souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c0f3-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="6c0f3-103">Poskytuje přístup k podřízeným položkám jedné z následujících: objekt <xref:System.Xml.Linq.XElement>, objekt <xref:System.Xml.Linq.XDocument>, kolekci objektů <xref:System.Xml.Linq.XElement> nebo kolekce objektů <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c0f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c0f3-104">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="6c0f3-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="6c0f3-105">Parts</span></span>  
  
|<span data-ttu-id="6c0f3-106">Termín</span><span class="sxs-lookup"><span data-stu-id="6c0f3-106">Term</span></span>|<span data-ttu-id="6c0f3-107">Definice</span><span class="sxs-lookup"><span data-stu-id="6c0f3-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="6c0f3-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-108">Required.</span></span> <span data-ttu-id="6c0f3-109">Objekt <xref:System.Xml.Linq.XElement>, objekt <xref:System.Xml.Linq.XDocument>, kolekce objektů <xref:System.Xml.Linq.XElement> nebo kolekce objektů <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="6c0f3-110">. <</span><span class="sxs-lookup"><span data-stu-id="6c0f3-110">.<</span></span>|<span data-ttu-id="6c0f3-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-111">Required.</span></span> <span data-ttu-id="6c0f3-112">Označuje začátek podřízené vlastnosti osy.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="6c0f3-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-113">Required.</span></span> <span data-ttu-id="6c0f3-114">Název podřízených uzlů, pro které má být přístup, z formuláře [`prefix:]name`.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-114">Name of the child nodes to access, of the form [`prefix:]name`.</span></span><br /><br /> <span data-ttu-id="6c0f3-115">-    `Prefix` – volitelné.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="6c0f3-116">Předpona oboru názvů XML pro podřízený uzel.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="6c0f3-117">Musí být globální obor názvů XML definovaný pomocí příkazu `Imports`.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="6c0f3-118">`Name` -    – povinné.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-118">-   `Name` - Required.</span></span> <span data-ttu-id="6c0f3-119">Název místního podřízeného uzlu.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-119">Local child node name.</span></span> <span data-ttu-id="6c0f3-120">Viz [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="6c0f3-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="6c0f3-121">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-121">Required.</span></span> <span data-ttu-id="6c0f3-122">Označuje konec podřízené vlastnosti osy.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="6c0f3-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6c0f3-123">Return Value</span></span>  
 <span data-ttu-id="6c0f3-124">Kolekce objektů <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c0f3-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c0f3-125">Remarks</span></span>  
 <span data-ttu-id="6c0f3-126">Vlastnost podřízené osy XML můžete použít pro přístup k podřízeným uzlům podle názvu z objektu <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> nebo z kolekce objektů <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="6c0f3-127">Pro přístup k hodnotě prvního podřízeného uzlu ve vrácené kolekci použijte vlastnost `Value` XML.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="6c0f3-128">Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="6c0f3-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="6c0f3-129">Kompilátor Visual Basic převede vlastnosti podřízené osy na volání metody <xref:System.Xml.Linq.XContainer.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="6c0f3-130">XML – obory názvů</span><span class="sxs-lookup"><span data-stu-id="6c0f3-130">XML Namespaces</span></span>  
 <span data-ttu-id="6c0f3-131">Název v podřízené vlastnosti osy může používat pouze předpony oboru názvů XML deklarované globálně s příkazem `Imports`.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="6c0f3-132">Nemůže použít předpony oboru názvů XML deklarované místně v rámci literálů elementů XML.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="6c0f3-133">Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="6c0f3-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c0f3-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c0f3-134">Example</span></span>  
 <span data-ttu-id="6c0f3-135">Následující příklad ukazuje, jak přistupovat k podřízeným uzlům s názvem `phone` z objektu `contact`.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="6c0f3-136">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="6c0f3-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="6c0f3-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c0f3-137">Example</span></span>  
 <span data-ttu-id="6c0f3-138">Následující příklad ukazuje, jak získat přístup k podřízeným uzlům s názvem `phone` z kolekce vrácené vlastností `contact` podřízená osa objektu `contacts`.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="6c0f3-139">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="6c0f3-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="6c0f3-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c0f3-140">Example</span></span>  
 <span data-ttu-id="6c0f3-141">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="6c0f3-142">Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu s kvalifikovaným názvem `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="6c0f3-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="6c0f3-143">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="6c0f3-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="6c0f3-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c0f3-144">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="6c0f3-145">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="6c0f3-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="6c0f3-146">Literály XML</span><span class="sxs-lookup"><span data-stu-id="6c0f3-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="6c0f3-147">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6c0f3-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="6c0f3-148">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="6c0f3-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
