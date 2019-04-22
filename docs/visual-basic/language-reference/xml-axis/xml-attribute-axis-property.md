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
ms.openlocfilehash: a7a93608d14bcbec316228b59467b23e9247e043
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828798"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="0b258-102">Vlastnost osy atributu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b258-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="0b258-103">Poskytuje přístup k hodnotě atributu pro <xref:System.Xml.Linq.XElement> objekt nebo na první prvek v kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="0b258-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b258-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b258-104">Syntax</span></span>  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="0b258-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="0b258-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="0b258-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0b258-106">Required.</span></span> <span data-ttu-id="0b258-107"><xref:System.Xml.Linq.XElement> Objektu nebo kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="0b258-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="0b258-108">.@</span><span class="sxs-lookup"><span data-stu-id="0b258-108">.@</span></span>  
 <span data-ttu-id="0b258-109">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0b258-109">Required.</span></span> <span data-ttu-id="0b258-110">Označuje začátek vlastnost osy atributu.</span><span class="sxs-lookup"><span data-stu-id="0b258-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="0b258-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0b258-111">Optional.</span></span> <span data-ttu-id="0b258-112">Označuje začátek název atributu při `attribute` není platný identifikátor v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0b258-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="0b258-113">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0b258-113">Required.</span></span> <span data-ttu-id="0b258-114">Název atributu pro přístup k ve tvaru [`prefix`:]`name`.</span><span class="sxs-lookup"><span data-stu-id="0b258-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="0b258-115">Část</span><span class="sxs-lookup"><span data-stu-id="0b258-115">Part</span></span>|<span data-ttu-id="0b258-116">Popis</span><span class="sxs-lookup"><span data-stu-id="0b258-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="0b258-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0b258-117">Optional.</span></span> <span data-ttu-id="0b258-118">Předpona oboru názvů XML pro atribut.</span><span class="sxs-lookup"><span data-stu-id="0b258-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="0b258-119">Musí se definovat globální obor názvů XML `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="0b258-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="0b258-120">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0b258-120">Required.</span></span> <span data-ttu-id="0b258-121">Local – atribut názvu.</span><span class="sxs-lookup"><span data-stu-id="0b258-121">Local attribute name.</span></span> <span data-ttu-id="0b258-122">Zobrazit [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0b258-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="0b258-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0b258-123">Optional.</span></span> <span data-ttu-id="0b258-124">Označuje konec názvu atributu při `attribute` není platný identifikátor v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0b258-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b258-125">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0b258-125">Return Value</span></span>  
 <span data-ttu-id="0b258-126">Řetězec, který obsahuje hodnotu `attribute`.</span><span class="sxs-lookup"><span data-stu-id="0b258-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="0b258-127">Pokud název neexistuje, `Nothing` je vrácena.</span><span class="sxs-lookup"><span data-stu-id="0b258-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b258-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b258-128">Remarks</span></span>  
 <span data-ttu-id="0b258-129">Můžete použít vlastnost osy atributu XML pro přístup k hodnotě atributu prostřednictvím jeho názvu <xref:System.Xml.Linq.XElement> objektu nebo z první prvek v kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="0b258-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="0b258-130">Hodnotu atributu načíst podle názvu nebo přidat nový atribut na prvek tak, že zadáte nový název, před kterými @ identifikátor.</span><span class="sxs-lookup"><span data-stu-id="0b258-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="0b258-131">Když budete odkazovat na atribut XML s použitím @ identifikátor, vrátí se hodnota atributu jako řetězec a není potřeba explicitně zadat <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0b258-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="0b258-132">Pravidla pojmenování atributů XML se liší od pravidla pojmenování identifikátorů jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0b258-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="0b258-133">Pro přístup k atributu XML, který má název, který není platným identifikátorem jazyka Visual Basic, uzavřete název v ostrých závorek (\< a >).</span><span class="sxs-lookup"><span data-stu-id="0b258-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="0b258-134">Obory názvů XML</span><span class="sxs-lookup"><span data-stu-id="0b258-134">XML Namespaces</span></span>  
 <span data-ttu-id="0b258-135">Název ve vlastnosti osy atribut lze použít pouze předpon oboru názvů XML globálně deklarovaná příkazem using `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="0b258-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="0b258-136">Místně deklarované v rámci elementu literály XML předpon názvového prostoru XML nemůže používat.</span><span class="sxs-lookup"><span data-stu-id="0b258-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="0b258-137">Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="0b258-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b258-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b258-138">Example</span></span>  
 <span data-ttu-id="0b258-139">Následující příklad ukazuje, jak získat hodnoty atributů XML s názvem `type` z kolekce elementů XML, které jsou pojmenovány `phone`.</span><span class="sxs-lookup"><span data-stu-id="0b258-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="0b258-140">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="0b258-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="0b258-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b258-141">Example</span></span>  
 <span data-ttu-id="0b258-142">Následující příklad ukazuje, jak vytvořit atributy pro element XML i deklarativně, jako součást XML a dynamicky tak, že přidáte atribut k instanci <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="0b258-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="0b258-143">`type` Atributu je vytvořen pomocí deklarace a `owner` atribut se vytváří dynamicky.</span><span class="sxs-lookup"><span data-stu-id="0b258-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="0b258-144">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="0b258-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="0b258-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b258-145">Example</span></span>  
 <span data-ttu-id="0b258-146">Následující příklad používá syntaxi ostré závorky k získání hodnoty atributu XML s názvem `number-type`, což není platný identifikátor v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0b258-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="0b258-147">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="0b258-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="0b258-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b258-148">Example</span></span>  
 <span data-ttu-id="0b258-149">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="0b258-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="0b258-150">Poté použije předponu oboru názvů XML vytvoření literálu a přístup k první podřízený uzel s kvalifikovaným názvem "`ns:name`".</span><span class="sxs-lookup"><span data-stu-id="0b258-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="0b258-151">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="0b258-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="0b258-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b258-152">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="0b258-153">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="0b258-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="0b258-154">Literály XML</span><span class="sxs-lookup"><span data-stu-id="0b258-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="0b258-155">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0b258-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="0b258-156">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="0b258-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
