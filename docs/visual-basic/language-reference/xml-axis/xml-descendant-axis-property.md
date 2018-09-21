---
title: Vlastnost osy nástupce XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 6040401ce3e98c835677be3c4cc7698013348f37
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46472143"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="b850c-102">Vlastnost osy nástupce XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b850c-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="b850c-103">Poskytuje přístup k následníky z následujících akcí: <xref:System.Xml.Linq.XElement> objektu, <xref:System.Xml.Linq.XDocument> object, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="b850c-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b850c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b850c-104">Syntax</span></span>  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="b850c-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b850c-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="b850c-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b850c-106">Required.</span></span> <span data-ttu-id="b850c-107"><xref:System.Xml.Linq.XElement> Objekt, <xref:System.Xml.Linq.XDocument> object, kolekce <xref:System.Xml.Linq.XElement> objekty nebo kolekci <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="b850c-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="b850c-108">...<</span><span class="sxs-lookup"><span data-stu-id="b850c-108">...<</span></span>  
 <span data-ttu-id="b850c-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b850c-109">Required.</span></span> <span data-ttu-id="b850c-110">Označuje začátek vlastnost Následnické osy.</span><span class="sxs-lookup"><span data-stu-id="b850c-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="b850c-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b850c-111">Required.</span></span> <span data-ttu-id="b850c-112">Název podřízených uzlů pro přístup k ve tvaru [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="b850c-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="b850c-113">Část</span><span class="sxs-lookup"><span data-stu-id="b850c-113">Part</span></span>|<span data-ttu-id="b850c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b850c-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="b850c-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b850c-115">Optional.</span></span> <span data-ttu-id="b850c-116">Předpona oboru názvů XML pro uzel potomka.</span><span class="sxs-lookup"><span data-stu-id="b850c-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="b850c-117">Musí být globální obor názvů XML, který je definován s použitím `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="b850c-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="b850c-118">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b850c-118">Required.</span></span> <span data-ttu-id="b850c-119">Místní název uzel potomka.</span><span class="sxs-lookup"><span data-stu-id="b850c-119">Local name of the descendant node.</span></span> <span data-ttu-id="b850c-120">Zobrazit [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b850c-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="b850c-121">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b850c-121">Required.</span></span> <span data-ttu-id="b850c-122">Označuje konec vlastnost Následnické osy.</span><span class="sxs-lookup"><span data-stu-id="b850c-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b850c-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b850c-123">Return Value</span></span>  
 <span data-ttu-id="b850c-124">Kolekce <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="b850c-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b850c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b850c-125">Remarks</span></span>  
 <span data-ttu-id="b850c-126">Můžete použít vlastnost osy nástupce XML pro přístup k následnickým uzlů podle názvu ze <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objektu, nebo z kolekce <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekty.</span><span class="sxs-lookup"><span data-stu-id="b850c-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="b850c-127">Použít XML `Value` pro přístup k hodnotě první uzel potomka v kolekci vrácené vlastností.</span><span class="sxs-lookup"><span data-stu-id="b850c-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="b850c-128">Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="b850c-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="b850c-129">Kompilátor jazyka Visual Basic převede vlastnosti osy nástupce na volání <xref:System.Xml.Linq.XContainer.Descendants%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b850c-129">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="b850c-130">Obory názvů XML</span><span class="sxs-lookup"><span data-stu-id="b850c-130">XML Namespaces</span></span>  
 <span data-ttu-id="b850c-131">Název v vlastnost Následnické osy můžete použít pouze obory názvů XML globálně deklarované s `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="b850c-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="b850c-132">Místně deklarované v rámci elementu literály XML obory názvů XML nemůže používat.</span><span class="sxs-lookup"><span data-stu-id="b850c-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="b850c-133">Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b850c-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b850c-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="b850c-134">Example</span></span>  
 <span data-ttu-id="b850c-135">Následující příklad ukazuje, jak přistupovat k hodnotě prvního následníky uzel s názvem `name` a hodnoty všech podřízených uzlů s názvem `phone` z `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="b850c-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 <span data-ttu-id="b850c-136">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="b850c-136">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="b850c-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="b850c-137">Example</span></span>  
 <span data-ttu-id="b850c-138">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="b850c-138">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="b850c-139">Poté použije předponu oboru názvů k vytvoření literálu XML a přistupovat k hodnotě první podřízený uzel s kvalifikovaným názvem `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="b850c-139">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 <span data-ttu-id="b850c-140">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="b850c-140">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="b850c-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="b850c-141">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="b850c-142">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="b850c-142">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="b850c-143">Literály XML</span><span class="sxs-lookup"><span data-stu-id="b850c-143">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="b850c-144">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b850c-144">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="b850c-145">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="b850c-145">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
