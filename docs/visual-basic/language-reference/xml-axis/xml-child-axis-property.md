---
title: Vlastnost osy podřízeného XML
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
ms.openlocfilehash: 90dc22d12be5566fa1ee40f6b0e48eff8088e67b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400263"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="26d83-102">Vlastnost osy podřízeného souboru XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26d83-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="26d83-103">Poskytuje přístup k podřízeným položkám jednoho z následujících objektů: <xref:System.Xml.Linq.XElement> objekt, <xref:System.Xml.Linq.XDocument> objekt, kolekce <xref:System.Xml.Linq.XElement> objektů nebo kolekce <xref:System.Xml.Linq.XDocument> objektů.</span><span class="sxs-lookup"><span data-stu-id="26d83-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26d83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26d83-104">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="26d83-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="26d83-105">Parts</span></span>  
  
|<span data-ttu-id="26d83-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="26d83-106">Term</span></span>|<span data-ttu-id="26d83-107">Definice</span><span class="sxs-lookup"><span data-stu-id="26d83-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="26d83-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="26d83-108">Required.</span></span> <span data-ttu-id="26d83-109"><xref:System.Xml.Linq.XElement>Objekt, <xref:System.Xml.Linq.XDocument> objekt, kolekce <xref:System.Xml.Linq.XElement> objektů nebo kolekce <xref:System.Xml.Linq.XDocument> objektů.</span><span class="sxs-lookup"><span data-stu-id="26d83-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="26d83-110">. <</span><span class="sxs-lookup"><span data-stu-id="26d83-110">.<</span></span>|<span data-ttu-id="26d83-111">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="26d83-111">Required.</span></span> <span data-ttu-id="26d83-112">Označuje začátek podřízené vlastnosti osy.</span><span class="sxs-lookup"><span data-stu-id="26d83-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="26d83-113">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="26d83-113">Required.</span></span> <span data-ttu-id="26d83-114">Název podřízených uzlů, pro které má být přístup, ve formuláři `[prefix:]name` .</span><span class="sxs-lookup"><span data-stu-id="26d83-114">Name of the child nodes to access, of the form `[prefix:]name`.</span></span><br /><br /> <span data-ttu-id="26d83-115">-   `Prefix`Volitelné.</span><span class="sxs-lookup"><span data-stu-id="26d83-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="26d83-116">Předpona oboru názvů XML pro podřízený uzel.</span><span class="sxs-lookup"><span data-stu-id="26d83-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="26d83-117">Musí být globální obor názvů XML definovaný `Imports` příkazem.</span><span class="sxs-lookup"><span data-stu-id="26d83-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="26d83-118">-   `Name`Požadovanou.</span><span class="sxs-lookup"><span data-stu-id="26d83-118">-   `Name` - Required.</span></span> <span data-ttu-id="26d83-119">Název místního podřízeného uzlu.</span><span class="sxs-lookup"><span data-stu-id="26d83-119">Local child node name.</span></span> <span data-ttu-id="26d83-120">Viz [Názvy deklarovaných elementů XML a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="26d83-120">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="26d83-121">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="26d83-121">Required.</span></span> <span data-ttu-id="26d83-122">Označuje konec podřízené vlastnosti osy.</span><span class="sxs-lookup"><span data-stu-id="26d83-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="26d83-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="26d83-123">Return Value</span></span>  
 <span data-ttu-id="26d83-124">Kolekce objektů <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="26d83-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26d83-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26d83-125">Remarks</span></span>  
 <span data-ttu-id="26d83-126">Můžete použít vlastnost podřízené osy XML pro přístup k podřízeným uzlům podle názvu z <xref:System.Xml.Linq.XElement> objektu nebo nebo <xref:System.Xml.Linq.XDocument> z kolekce <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objektů nebo.</span><span class="sxs-lookup"><span data-stu-id="26d83-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="26d83-127">Použijte vlastnost XML `Value` pro přístup k hodnotě prvního podřízeného uzlu ve vrácené kolekci.</span><span class="sxs-lookup"><span data-stu-id="26d83-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="26d83-128">Další informace najdete v tématu [vlastnost hodnoty XML](xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="26d83-128">For more information, see [XML Value Property](xml-value-property.md).</span></span>  
  
 <span data-ttu-id="26d83-129">Kompilátor Visual Basic převede vlastnosti podřízené osy na volání <xref:System.Xml.Linq.XContainer.Elements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="26d83-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="26d83-130">XML – obory názvů</span><span class="sxs-lookup"><span data-stu-id="26d83-130">XML Namespaces</span></span>  
 <span data-ttu-id="26d83-131">Název v podřízené vlastnosti osy může používat pouze předpony oboru názvů XML deklarované globálně s `Imports` příkazem.</span><span class="sxs-lookup"><span data-stu-id="26d83-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="26d83-132">Nemůže použít předpony oboru názvů XML deklarované místně v rámci literálů elementů XML.</span><span class="sxs-lookup"><span data-stu-id="26d83-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="26d83-133">Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="26d83-133">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="26d83-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="26d83-134">Example</span></span>  
 <span data-ttu-id="26d83-135">Následující příklad ukazuje, jak přistupovat k podřízeným uzlům s názvem `phone` z `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="26d83-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="26d83-136">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="26d83-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="26d83-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="26d83-137">Example</span></span>  
 <span data-ttu-id="26d83-138">Následující příklad ukazuje, jak přistupovat k podřízeným uzlům, které jsou pojmenovány `phone` z kolekce vrácené `contact` vlastností podřízené osy `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="26d83-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="26d83-139">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="26d83-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="26d83-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="26d83-140">Example</span></span>  
 <span data-ttu-id="26d83-141">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="26d83-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="26d83-142">Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu s kvalifikovaným názvem `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="26d83-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="26d83-143">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="26d83-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="26d83-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="26d83-144">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="26d83-145">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="26d83-145">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="26d83-146">Literály XML</span><span class="sxs-lookup"><span data-stu-id="26d83-146">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="26d83-147">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26d83-147">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="26d83-148">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="26d83-148">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
