---
title: Vlastnost hodnoty XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 9edf95c7cedced55ab2441baf51b7c2052e4654c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942980"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="56f21-102">Vlastnost hodnoty XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56f21-102">XML Value Property (Visual Basic)</span></span>
<span data-ttu-id="56f21-103">Poskytuje přístup k hodnotě prvního prvku kolekce <xref:System.Xml.Linq.XElement> objektů.</span><span class="sxs-lookup"><span data-stu-id="56f21-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56f21-104">Syntax</span></span>  
  
```  
object.Value  
```  
  
## <a name="parts"></a><span data-ttu-id="56f21-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="56f21-105">Parts</span></span>  
  
|<span data-ttu-id="56f21-106">Termín</span><span class="sxs-lookup"><span data-stu-id="56f21-106">Term</span></span>|<span data-ttu-id="56f21-107">Definice</span><span class="sxs-lookup"><span data-stu-id="56f21-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="56f21-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="56f21-108">Required.</span></span> <span data-ttu-id="56f21-109"><xref:System.Xml.Linq.XElement> Kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="56f21-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="56f21-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="56f21-110">Return Value</span></span>  
 <span data-ttu-id="56f21-111">, Který obsahuje hodnotu prvního prvku kolekce, nebo `Nothing` Pokud je kolekce prázdná. `String`</span><span class="sxs-lookup"><span data-stu-id="56f21-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56f21-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56f21-112">Remarks</span></span>  
 <span data-ttu-id="56f21-113">Vlastnost usnadňuje přístup k hodnotě prvního prvku v <xref:System.Xml.Linq.XElement> kolekci objektů. <xref:System.Xml.Linq.XElement.Value%2A></span><span class="sxs-lookup"><span data-stu-id="56f21-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="56f21-114">Tato vlastnost nejprve ověří, zda kolekce obsahuje alespoň jeden objekt.</span><span class="sxs-lookup"><span data-stu-id="56f21-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="56f21-115">Pokud je kolekce prázdná, vrátí `Nothing`Tato vlastnost.</span><span class="sxs-lookup"><span data-stu-id="56f21-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="56f21-116">V opačném případě tato vlastnost vrátí hodnotu <xref:System.Xml.Linq.XElement.Value%2A> vlastnosti prvního prvku v kolekci.</span><span class="sxs-lookup"><span data-stu-id="56f21-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56f21-117">Při přístupu k hodnotě atributu XML pomocí\@identifikátoru se hodnota atributu vrátí `String` jako a <xref:System.Xml.Linq.XAttribute.Value%2A> nemusíte explicitně zadávat vlastnost.</span><span class="sxs-lookup"><span data-stu-id="56f21-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="56f21-118">Chcete-li získat přístup k dalším prvkům v kolekci, můžete použít vlastnost indexer rozšíření XML.</span><span class="sxs-lookup"><span data-stu-id="56f21-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="56f21-119">Další informace najdete v tématu [vlastnost indexeru rozšíření](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="56f21-119">For more information, see [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="56f21-120">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="56f21-120">Inheritance</span></span>  
 <span data-ttu-id="56f21-121">Většina uživatelů nebude muset implementovat <xref:System.Collections.Generic.IEnumerable%601>, a proto může tuto část ignorovat.</span><span class="sxs-lookup"><span data-stu-id="56f21-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>  
  
 <span data-ttu-id="56f21-122">Vlastnost je vlastnost rozšíření pro typy, které implementují `IEnumerable(Of XElement)`. <xref:System.Xml.Linq.XElement.Value%2A></span><span class="sxs-lookup"><span data-stu-id="56f21-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="56f21-123">Vazba této vlastnosti rozšíření se podobá vazbě rozšiřujících metod: Pokud typ implementuje jedno z rozhraní a definuje vlastnost s názvem "value", má tato vlastnost přednost před vlastností Extension.</span><span class="sxs-lookup"><span data-stu-id="56f21-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="56f21-124">Jinými slovy Tato <xref:System.Xml.Linq.XElement.Value%2A> vlastnost může být přepsána definováním nové vlastnosti ve třídě, která implementuje `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="56f21-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56f21-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="56f21-125">Example</span></span>  
 <span data-ttu-id="56f21-126">Následující příklad ukazuje, jak použít <xref:System.Xml.Linq.XElement.Value%2A> vlastnost pro přístup k prvnímu uzlu v <xref:System.Xml.Linq.XElement> kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="56f21-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="56f21-127">V příkladu se používá vlastnost podřízené osy k získání kolekce všech podřízených uzlů s názvem `phone` , které jsou `contact` v objektu.</span><span class="sxs-lookup"><span data-stu-id="56f21-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 <span data-ttu-id="56f21-128">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="56f21-128">This code displays the following text:</span></span>  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="56f21-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="56f21-129">Example</span></span>  
 <span data-ttu-id="56f21-130">Následující příklad ukazuje, jak získat hodnotu atributu XML z kolekce <xref:System.Xml.Linq.XAttribute> objektů.</span><span class="sxs-lookup"><span data-stu-id="56f21-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="56f21-131">V příkladu se používá vlastnost osa atributu k zobrazení hodnoty `type` atributu pro všechny `phone` elementy.</span><span class="sxs-lookup"><span data-stu-id="56f21-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 <span data-ttu-id="56f21-132">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="56f21-132">This code displays the following text:</span></span>  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a><span data-ttu-id="56f21-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56f21-133">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="56f21-134">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="56f21-134">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="56f21-135">Literály XML</span><span class="sxs-lookup"><span data-stu-id="56f21-135">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="56f21-136">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56f21-136">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="56f21-137">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="56f21-137">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="56f21-138">Vlastnost indexeru rozšíření</span><span class="sxs-lookup"><span data-stu-id="56f21-138">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [<span data-ttu-id="56f21-139">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="56f21-139">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="56f21-140">Vlastnost osy atributu XML</span><span class="sxs-lookup"><span data-stu-id="56f21-140">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
