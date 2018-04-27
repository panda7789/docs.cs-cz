---
title: Vlastnost osy atributu XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9968e5de0f8cb45fb896ba43c80d9c9a3ab8ef08
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="a3e2d-102">Vlastnost osy atributu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3e2d-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="a3e2d-103">Poskytuje přístup k hodnotě atributu pro <xref:System.Xml.Linq.XElement> objektu nebo na prvním elementem v kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3e2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3e2d-104">Syntax</span></span>  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="a3e2d-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a3e2d-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="a3e2d-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-106">Required.</span></span> <span data-ttu-id="a3e2d-107"><xref:System.Xml.Linq.XElement> Objektu nebo kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="a3e2d-108">.@</span><span class="sxs-lookup"><span data-stu-id="a3e2d-108">.@</span></span>  
 <span data-ttu-id="a3e2d-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-109">Required.</span></span> <span data-ttu-id="a3e2d-110">Označuje začátek vlastnost osy atributu.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="a3e2d-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-111">Optional.</span></span> <span data-ttu-id="a3e2d-112">Označuje začátek název atributu, když `attribute` není platný identifikátor v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="a3e2d-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-113">Required.</span></span> <span data-ttu-id="a3e2d-114">Název atributu pro přístup k ve formátu [`prefix`:]`name`.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="a3e2d-115">Část</span><span class="sxs-lookup"><span data-stu-id="a3e2d-115">Part</span></span>|<span data-ttu-id="a3e2d-116">Popis</span><span class="sxs-lookup"><span data-stu-id="a3e2d-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="a3e2d-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-117">Optional.</span></span> <span data-ttu-id="a3e2d-118">Předpona oboru názvů XML pro atribut.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="a3e2d-119">Musí být globální obor názvů XML definovány se `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="a3e2d-120">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-120">Required.</span></span> <span data-ttu-id="a3e2d-121">Local – atribut názvu.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-121">Local attribute name.</span></span> <span data-ttu-id="a3e2d-122">V tématu [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a3e2d-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="a3e2d-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-123">Optional.</span></span> <span data-ttu-id="a3e2d-124">Označuje konec název atributu, když `attribute` není platný identifikátor v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3e2d-125">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a3e2d-125">Return Value</span></span>  
 <span data-ttu-id="a3e2d-126">Řetězec, který obsahuje hodnotu `attribute`.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="a3e2d-127">Pokud název neexistuje, `Nothing` je vrácen.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3e2d-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3e2d-128">Remarks</span></span>  
 <span data-ttu-id="a3e2d-129">Můžete použít vlastnost osy atributu XML pro přístup k hodnotě atributu podle názvu z <xref:System.Xml.Linq.XElement> objekt nebo z první prvek v kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="a3e2d-130">Můžete načíst hodnotu atributu podle názvu nebo přidat nový atribut pro element tak, že zadáte nový název předchází @ identifikátor.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="a3e2d-131">Když odkazujete na atribut XML pomocí @ identifikátoru, je vrácena hodnota atributu jako řetězec a není nutné explicitně zadat <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="a3e2d-132">Pravidla pojmenování pro atributy XML se liší od pravidla pojmenování pro identifikátory jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="a3e2d-133">Pro přístup k atribut XML, který má název, který není platný identifikátor jazyka Visual Basic, uzavřete název v lomených závorkách (\< a >).</span><span class="sxs-lookup"><span data-stu-id="a3e2d-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="a3e2d-134">Obory názvů XML</span><span class="sxs-lookup"><span data-stu-id="a3e2d-134">XML Namespaces</span></span>  
 <span data-ttu-id="a3e2d-135">Název v vlastnost osy atributu můžete použít pouze XML – předpony oboru názvů deklarovat globálně pomocí `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="a3e2d-136">Nemůže používat lokálně deklarované v rámci elementu XML – literály XML – předpony oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="a3e2d-137">Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="a3e2d-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3e2d-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3e2d-138">Example</span></span>  
 <span data-ttu-id="a3e2d-139">Následující příklad ukazuje, jak získat hodnoty atributů XML s názvem `type` z kolekce elementů XML, které jsou s názvem `phone`.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 <span data-ttu-id="a3e2d-140">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="a3e2d-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="a3e2d-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3e2d-141">Example</span></span>  
 <span data-ttu-id="a3e2d-142">Následující příklad ukazuje, jak vytvořte atributy pro element XML i deklarativně, v rámci kódu XML a dynamicky přidáním atribut na instanci <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="a3e2d-143">`type` Atribut je vytvořen deklarativně a `owner` atribut se vytváří dynamicky.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 <span data-ttu-id="a3e2d-144">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="a3e2d-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="a3e2d-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3e2d-145">Example</span></span>  
 <span data-ttu-id="a3e2d-146">Následující příklad používá syntaxi lomená závorka k získání hodnoty atributu XML s názvem `number-type`, což není platný identifikátor v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 <span data-ttu-id="a3e2d-147">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="a3e2d-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="a3e2d-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3e2d-148">Example</span></span>  
 <span data-ttu-id="a3e2d-149">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="a3e2d-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="a3e2d-150">Poté použije Předpona oboru názvů k vytvoření literál XML a přístup k první podřízený uzel s kvalifikovaný název "`ns:name`".</span><span class="sxs-lookup"><span data-stu-id="a3e2d-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 <span data-ttu-id="a3e2d-151">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="a3e2d-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="a3e2d-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3e2d-152">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="a3e2d-153">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="a3e2d-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="a3e2d-154">Literály XML</span><span class="sxs-lookup"><span data-stu-id="a3e2d-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="a3e2d-155">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a3e2d-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="a3e2d-156">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="a3e2d-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
