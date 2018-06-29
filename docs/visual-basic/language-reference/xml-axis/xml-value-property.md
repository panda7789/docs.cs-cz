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
ms.openlocfilehash: 927158f940d9b96cd06873c7d3e710be91b887e9
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071615"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="1ef7a-102">Vlastnost hodnoty XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ef7a-102">XML Value Property (Visual Basic)</span></span>
<span data-ttu-id="1ef7a-103">Poskytuje přístup k hodnotě první prvek kolekce <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ef7a-104">Syntax</span></span>  
  
```  
object.Value  
```  
  
## <a name="parts"></a><span data-ttu-id="1ef7a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1ef7a-105">Parts</span></span>  
  
|<span data-ttu-id="1ef7a-106">Termín</span><span class="sxs-lookup"><span data-stu-id="1ef7a-106">Term</span></span>|<span data-ttu-id="1ef7a-107">Definice</span><span class="sxs-lookup"><span data-stu-id="1ef7a-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="1ef7a-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-108">Required.</span></span> <span data-ttu-id="1ef7a-109">Kolekce <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="1ef7a-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1ef7a-110">Return Value</span></span>  
 <span data-ttu-id="1ef7a-111">A `String` obsahující hodnotu první prvek kolekce, nebo `Nothing` Pokud kolekce je prázdná.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ef7a-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ef7a-112">Remarks</span></span>  
 <span data-ttu-id="1ef7a-113"><xref:System.Xml.Linq.XElement.Value%2A> Vlastnost usnadňuje přístup k hodnotě prvním elementem v kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="1ef7a-114">Tato vlastnost nejprve ověří, zda kolekce obsahuje minimálně jeden objekt.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="1ef7a-115">Pokud je kolekce prázdná, vrátí tato vlastnost `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="1ef7a-116">Jinak, vrátí tato vlastnost hodnotu <xref:System.Xml.Linq.XElement.Value%2A> vlastnost první prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ef7a-117">Když k hodnotě atributu XML pomocí '\@' identifikátor, jako je vrácena hodnota atributu `String` a není nutné explicitně zadat <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="1ef7a-118">Pro přístup k další elementy v kolekci, můžete použít vlastnost indexeru rozšíření XML.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="1ef7a-119">Další informace najdete v tématu [vlastnost indexeru rozšíření](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="1ef7a-119">For more information, see [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="1ef7a-120">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="1ef7a-120">Inheritance</span></span>  
 <span data-ttu-id="1ef7a-121">Většina uživatelé nebudou mít k implementaci <xref:System.Collections.Generic.IEnumerable%601>a proto můžete ignorovat v této části.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>  
  
 <span data-ttu-id="1ef7a-122"><xref:System.Xml.Linq.XElement.Value%2A> Vlastnost je vlastnost rozšíření pro typy, které implementují `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="1ef7a-123">Vazba této vlastnosti rozšíření je třeba vazby metod rozšíření: Pokud typu implementuje jednomu z rozhraní a definuje vlastnost, která má název "Value", tato vlastnost má vyšší prioritu než vlastnost rozšíření.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="1ef7a-124">Jinými slovy to <xref:System.Xml.Linq.XElement.Value%2A> mohou být přepsány vlastnosti definovat nové vlastnosti ve třídě, která implementuje `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ef7a-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ef7a-125">Example</span></span>  
 <span data-ttu-id="1ef7a-126">Následující příklad ukazuje, jak používat <xref:System.Xml.Linq.XElement.Value%2A> vlastnost, která má přístup k první uzel v kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="1ef7a-127">Příklad používá vlastnost osy podřízeného k získání kolekce všechny podřízené uzly s názvem `phone` , které jsou v `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 <span data-ttu-id="1ef7a-128">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="1ef7a-128">This code displays the following text:</span></span>  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="1ef7a-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ef7a-129">Example</span></span>  
 <span data-ttu-id="1ef7a-130">Následující příklad ukazuje, jak získat hodnotu atributu XML z kolekce <xref:System.Xml.Linq.XAttribute> objekty.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="1ef7a-131">Příklad používá vlastnost osy atributu k zobrazit hodnotu `type` atribut pro všechny `phone` elementy.</span><span class="sxs-lookup"><span data-stu-id="1ef7a-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 <span data-ttu-id="1ef7a-132">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="1ef7a-132">This code displays the following text:</span></span>  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a><span data-ttu-id="1ef7a-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ef7a-133">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="1ef7a-134">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="1ef7a-134">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="1ef7a-135">Literály XML</span><span class="sxs-lookup"><span data-stu-id="1ef7a-135">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="1ef7a-136">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ef7a-136">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="1ef7a-137">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="1ef7a-137">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [<span data-ttu-id="1ef7a-138">Vlastnost indexeru rozšíření</span><span class="sxs-lookup"><span data-stu-id="1ef7a-138">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [<span data-ttu-id="1ef7a-139">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="1ef7a-139">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [<span data-ttu-id="1ef7a-140">Vlastnost osy atributu XML</span><span class="sxs-lookup"><span data-stu-id="1ef7a-140">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
