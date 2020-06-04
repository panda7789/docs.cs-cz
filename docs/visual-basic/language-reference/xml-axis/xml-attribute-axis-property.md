---
title: Vlastnost osy atributu XML
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
ms.openlocfilehash: 3f60190a949856cb2bbc2eba09d097c09089bea7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408429"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="f581b-102">Vlastnost osy atributu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f581b-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="f581b-103">Poskytuje přístup k hodnotě atributu pro <xref:System.Xml.Linq.XElement> objekt nebo na první prvek kolekce <xref:System.Xml.Linq.XElement> objektů.</span><span class="sxs-lookup"><span data-stu-id="f581b-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f581b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f581b-104">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="f581b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f581b-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="f581b-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="f581b-106">Required.</span></span> <span data-ttu-id="f581b-107"><xref:System.Xml.Linq.XElement>Objekt nebo kolekce <xref:System.Xml.Linq.XElement> objektů.</span><span class="sxs-lookup"><span data-stu-id="f581b-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="f581b-108">.@</span><span class="sxs-lookup"><span data-stu-id="f581b-108">.@</span></span>  
 <span data-ttu-id="f581b-109">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="f581b-109">Required.</span></span> <span data-ttu-id="f581b-110">Označuje začátek Vlastnosti osy atributu.</span><span class="sxs-lookup"><span data-stu-id="f581b-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="f581b-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f581b-111">Optional.</span></span> <span data-ttu-id="f581b-112">Označuje začátek názvu atributu, pokud `attribute` není platným identifikátorem v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f581b-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="f581b-113">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="f581b-113">Required.</span></span> <span data-ttu-id="f581b-114">Název atributu, pro který má být přístup, z formuláře [ `prefix` :] `name` .</span><span class="sxs-lookup"><span data-stu-id="f581b-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="f581b-115">Část</span><span class="sxs-lookup"><span data-stu-id="f581b-115">Part</span></span>|<span data-ttu-id="f581b-116">Description</span><span class="sxs-lookup"><span data-stu-id="f581b-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="f581b-117">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f581b-117">Optional.</span></span> <span data-ttu-id="f581b-118">Předpona oboru názvů XML pro atribut</span><span class="sxs-lookup"><span data-stu-id="f581b-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="f581b-119">Musí být globální obor názvů XML definovaný `Imports` příkazem.</span><span class="sxs-lookup"><span data-stu-id="f581b-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="f581b-120">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="f581b-120">Required.</span></span> <span data-ttu-id="f581b-121">Název místního atributu</span><span class="sxs-lookup"><span data-stu-id="f581b-121">Local attribute name.</span></span> <span data-ttu-id="f581b-122">Viz [Názvy deklarovaných elementů XML a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="f581b-122">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="f581b-123">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f581b-123">Optional.</span></span> <span data-ttu-id="f581b-124">Označuje konec názvu atributu, pokud `attribute` není platným identifikátorem v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f581b-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f581b-125">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f581b-125">Return Value</span></span>  
 <span data-ttu-id="f581b-126">Řetězec, který obsahuje hodnotu `attribute` .</span><span class="sxs-lookup"><span data-stu-id="f581b-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="f581b-127">Pokud název atributu neexistuje, `Nothing` je vrácen.</span><span class="sxs-lookup"><span data-stu-id="f581b-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f581b-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f581b-128">Remarks</span></span>  
 <span data-ttu-id="f581b-129">Můžete použít vlastnost osy atributu XML pro přístup k hodnotě atributu podle názvu z <xref:System.Xml.Linq.XElement> objektu nebo z prvního prvku v kolekci <xref:System.Xml.Linq.XElement> objektů.</span><span class="sxs-lookup"><span data-stu-id="f581b-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="f581b-130">Můžete načíst hodnotu atributu podle názvu nebo přidat nový atribut k elementu zadáním nového názvu předchází identifikátor @.</span><span class="sxs-lookup"><span data-stu-id="f581b-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="f581b-131">Když odkazujete na atribut XML pomocí @ identifikátor, vrátí se hodnota atributu jako řetězec a nemusíte explicitně zadávat <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f581b-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="f581b-132">Pravidla pro pojmenování atributů XML se liší od pravidel pro pojmenování Visual Basicch identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="f581b-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="f581b-133">Chcete-li získat přístup k atributu XML, který má název, který není platným identifikátorem Visual Basic, uveďte název do lomených závorek ( \< and > ).</span><span class="sxs-lookup"><span data-stu-id="f581b-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="f581b-134">XML – obory názvů</span><span class="sxs-lookup"><span data-stu-id="f581b-134">XML Namespaces</span></span>  
 <span data-ttu-id="f581b-135">Název ve vlastnosti osa atributu může používat pouze předpony oboru názvů XML deklarované globálně pomocí `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="f581b-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="f581b-136">Nemůže použít předpony oboru názvů XML deklarované místně v rámci literálů elementů XML.</span><span class="sxs-lookup"><span data-stu-id="f581b-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="f581b-137">Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="f581b-137">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f581b-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="f581b-138">Example</span></span>  
 <span data-ttu-id="f581b-139">Následující příklad ukazuje, jak získat hodnoty atributů XML s názvem `type` z kolekce elementů XML s názvem `phone` .</span><span class="sxs-lookup"><span data-stu-id="f581b-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="f581b-140">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="f581b-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="f581b-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="f581b-141">Example</span></span>  
 <span data-ttu-id="f581b-142">Následující příklad ukazuje, jak vytvořit atributy pro element XML deklarativně, jako součást XML a dynamicky přidáním atributu do instance <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="f581b-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="f581b-143">`type`Atribut je vytvořen deklarativně a `owner` atribut je vytvořen dynamicky.</span><span class="sxs-lookup"><span data-stu-id="f581b-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="f581b-144">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="f581b-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="f581b-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="f581b-145">Example</span></span>  
 <span data-ttu-id="f581b-146">Následující příklad používá syntaxi lomené závorky k získání hodnoty atributu XML s názvem `number-type` , který není platným identifikátorem v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f581b-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="f581b-147">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="f581b-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="f581b-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="f581b-148">Example</span></span>  
 <span data-ttu-id="f581b-149">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="f581b-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="f581b-150">Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu s kvalifikovaným názvem " `ns:name` ".</span><span class="sxs-lookup"><span data-stu-id="f581b-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="f581b-151">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="f581b-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="f581b-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="f581b-152">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="f581b-153">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="f581b-153">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="f581b-154">Literály XML</span><span class="sxs-lookup"><span data-stu-id="f581b-154">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="f581b-155">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f581b-155">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="f581b-156">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="f581b-156">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
