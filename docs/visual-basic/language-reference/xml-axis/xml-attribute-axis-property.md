---
title: Vlastnost osy atributu XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 896081c3dc7ca9e50b4dc4bd87675e957c34b649
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582167"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="e8223-102">Vlastnost osy atributu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8223-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="e8223-103">Poskytuje přístup k hodnotě atributu pro objekt <xref:System.Xml.Linq.XElement> nebo k prvnímu prvku kolekce objektů <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e8223-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8223-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8223-104">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="e8223-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e8223-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="e8223-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e8223-106">Required.</span></span> <span data-ttu-id="e8223-107">Objekt <xref:System.Xml.Linq.XElement> nebo kolekce objektů <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e8223-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="e8223-108">. @</span><span class="sxs-lookup"><span data-stu-id="e8223-108">.@</span></span>  
 <span data-ttu-id="e8223-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e8223-109">Required.</span></span> <span data-ttu-id="e8223-110">Označuje začátek Vlastnosti osy atributu.</span><span class="sxs-lookup"><span data-stu-id="e8223-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="e8223-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e8223-111">Optional.</span></span> <span data-ttu-id="e8223-112">Označuje začátek názvu atributu, pokud `attribute` není platným identifikátorem v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e8223-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="e8223-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e8223-113">Required.</span></span> <span data-ttu-id="e8223-114">Název atributu, pro který má být přístup, z formuláře [`prefix`:] `name`.</span><span class="sxs-lookup"><span data-stu-id="e8223-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="e8223-115">Částí</span><span class="sxs-lookup"><span data-stu-id="e8223-115">Part</span></span>|<span data-ttu-id="e8223-116">Popis</span><span class="sxs-lookup"><span data-stu-id="e8223-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="e8223-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e8223-117">Optional.</span></span> <span data-ttu-id="e8223-118">Předpona oboru názvů XML pro atribut</span><span class="sxs-lookup"><span data-stu-id="e8223-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="e8223-119">Musí být globální obor názvů XML definovaný pomocí příkazu `Imports`.</span><span class="sxs-lookup"><span data-stu-id="e8223-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="e8223-120">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e8223-120">Required.</span></span> <span data-ttu-id="e8223-121">Název místního atributu</span><span class="sxs-lookup"><span data-stu-id="e8223-121">Local attribute name.</span></span> <span data-ttu-id="e8223-122">Viz [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="e8223-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="e8223-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e8223-123">Optional.</span></span> <span data-ttu-id="e8223-124">Označuje konec názvu atributu, pokud `attribute` není platným identifikátorem v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e8223-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8223-125">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e8223-125">Return Value</span></span>  
 <span data-ttu-id="e8223-126">Řetězec, který obsahuje hodnotu `attribute`.</span><span class="sxs-lookup"><span data-stu-id="e8223-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="e8223-127">Pokud název atributu neexistuje, `Nothing` se vrátí.</span><span class="sxs-lookup"><span data-stu-id="e8223-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8223-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8223-128">Remarks</span></span>  
 <span data-ttu-id="e8223-129">Můžete použít vlastnost osy atributu XML pro přístup k hodnotě atributu podle názvu z objektu <xref:System.Xml.Linq.XElement> nebo z prvního prvku kolekce objektů <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e8223-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="e8223-130">Můžete načíst hodnotu atributu podle názvu nebo přidat nový atribut k elementu zadáním nového názvu předchází identifikátor @.</span><span class="sxs-lookup"><span data-stu-id="e8223-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="e8223-131">Když odkazujete na atribut XML pomocí @ identifikátor, vrátí se hodnota atributu jako řetězec a nemusíte explicitně určovat vlastnost <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="e8223-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="e8223-132">Pravidla pro pojmenování atributů XML se liší od pravidel pro pojmenování Visual Basicch identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="e8223-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="e8223-133">Chcete-li získat přístup k atributu XML, který má název, který není platným identifikátorem Visual Basic, zadejte název do lomených závorek (\< a >).</span><span class="sxs-lookup"><span data-stu-id="e8223-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="e8223-134">XML – obory názvů</span><span class="sxs-lookup"><span data-stu-id="e8223-134">XML Namespaces</span></span>  
 <span data-ttu-id="e8223-135">Název ve vlastnosti osy atributu může používat pouze předpony oboru názvů XML deklarované globálně pomocí příkazu `Imports`.</span><span class="sxs-lookup"><span data-stu-id="e8223-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="e8223-136">Nemůže použít předpony oboru názvů XML deklarované místně v rámci literálů elementů XML.</span><span class="sxs-lookup"><span data-stu-id="e8223-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="e8223-137">Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="e8223-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8223-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8223-138">Example</span></span>  
 <span data-ttu-id="e8223-139">Následující příklad ukazuje, jak získat hodnoty atributů XML s názvem `type` z kolekce prvků XML s názvem `phone`.</span><span class="sxs-lookup"><span data-stu-id="e8223-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="e8223-140">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="e8223-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="e8223-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8223-141">Example</span></span>  
 <span data-ttu-id="e8223-142">Následující příklad ukazuje, jak vytvořit atributy pro element XML deklarativně, jako součást XML a dynamicky přidáním atributu do instance objektu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e8223-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="e8223-143">Atribut `type` se vytvoří deklarativně a dynamicky se vytvoří atribut `owner`.</span><span class="sxs-lookup"><span data-stu-id="e8223-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="e8223-144">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="e8223-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="e8223-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8223-145">Example</span></span>  
 <span data-ttu-id="e8223-146">Následující příklad používá syntaxi lomené závorky k získání hodnoty atributu XML s názvem `number-type`, což není platný identifikátor v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e8223-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="e8223-147">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="e8223-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="e8223-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8223-148">Example</span></span>  
 <span data-ttu-id="e8223-149">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="e8223-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="e8223-150">Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu s kvalifikovaným názvem "`ns:name`".</span><span class="sxs-lookup"><span data-stu-id="e8223-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="e8223-151">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="e8223-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="e8223-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8223-152">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="e8223-153">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="e8223-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="e8223-154">Literály XML</span><span class="sxs-lookup"><span data-stu-id="e8223-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="e8223-155">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e8223-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="e8223-156">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="e8223-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
