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
ms.openlocfilehash: 54bd18b050ca58c286bfca3972b242348c61fe45
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737608"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="aa940-102">Vlastnost hodnoty XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa940-102">XML Value Property (Visual Basic)</span></span>
<span data-ttu-id="aa940-103">Poskytuje přístup k hodnotě prvního prvku kolekce <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="aa940-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa940-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa940-104">Syntax</span></span>  
  
```  
object.Value  
```  
  
## <a name="parts"></a><span data-ttu-id="aa940-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="aa940-105">Parts</span></span>  
  
|<span data-ttu-id="aa940-106">Termín</span><span class="sxs-lookup"><span data-stu-id="aa940-106">Term</span></span>|<span data-ttu-id="aa940-107">Definice</span><span class="sxs-lookup"><span data-stu-id="aa940-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="aa940-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="aa940-108">Required.</span></span> <span data-ttu-id="aa940-109">Kolekce <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="aa940-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="aa940-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aa940-110">Return Value</span></span>  
 <span data-ttu-id="aa940-111">A `String` , který obsahuje hodnotu elementu první kolekce, nebo `Nothing` Pokud kolekce je prázdná.</span><span class="sxs-lookup"><span data-stu-id="aa940-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa940-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa940-112">Remarks</span></span>  
 <span data-ttu-id="aa940-113"><xref:System.Xml.Linq.XElement.Value%2A> Vlastnost usnadňuje přístup k hodnotě prvního prvku v kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="aa940-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="aa940-114">Tato vlastnost nejprve zkontroluje, zda kolekce obsahuje minimálně jeden objekt.</span><span class="sxs-lookup"><span data-stu-id="aa940-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="aa940-115">Pokud kolekce je prázdná, vrátí tato vlastnost `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="aa940-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="aa940-116">V opačném případě vrátí tato vlastnost hodnotu <xref:System.Xml.Linq.XElement.Value%2A> vlastnost první prvek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="aa940-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa940-117">Když zobrazujete hodnota atributu XML pomocí "\@" identifikátor, jako je vrácena hodnota atributu `String` a není potřeba explicitně zadat <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="aa940-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="aa940-118">Pro přístup k další prvky v kolekci, můžete použít vlastnost indexeru rozšíření XML.</span><span class="sxs-lookup"><span data-stu-id="aa940-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="aa940-119">Další informace najdete v tématu [vlastnost indexeru rozšíření](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="aa940-119">For more information, see [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="aa940-120">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="aa940-120">Inheritance</span></span>  
 <span data-ttu-id="aa940-121">Většina uživatelů nebudete muset implementovat <xref:System.Collections.Generic.IEnumerable%601>a proto můžete ignorovat tento oddíl.</span><span class="sxs-lookup"><span data-stu-id="aa940-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>  
  
 <span data-ttu-id="aa940-122"><xref:System.Xml.Linq.XElement.Value%2A> Vlastností je vlastnost rozšíření pro typy, které implementují `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="aa940-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="aa940-123">Vazba této vlastnosti rozšíření se podobá vazba metod rozšíření: Pokud typ jednoho z rozhraní implementuje a definuje vlastnost s názvem "Value", tato vlastnost má vyšší prioritu než vlastnost extension.</span><span class="sxs-lookup"><span data-stu-id="aa940-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="aa940-124">Jinými slovy to <xref:System.Xml.Linq.XElement.Value%2A> vlastnost může být přepsána definování nové vlastnosti do třídy, která implementuje `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="aa940-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa940-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa940-125">Example</span></span>  
 <span data-ttu-id="aa940-126">Následující příklad ukazuje způsob použití <xref:System.Xml.Linq.XElement.Value%2A> vlastnosti pro přístup k prvním uzlem v kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="aa940-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="aa940-127">Vlastnost osy podřízeného v příkladu se používá k získání kolekce všech podřízených uzlech s názvem `phone` , které jsou `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="aa940-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 <span data-ttu-id="aa940-128">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="aa940-128">This code displays the following text:</span></span>  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="aa940-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa940-129">Example</span></span>  
 <span data-ttu-id="aa940-130">Následující příklad ukazuje, jak má být získána hodnota atributu XML z kolekce <xref:System.Xml.Linq.XAttribute> objekty.</span><span class="sxs-lookup"><span data-stu-id="aa940-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="aa940-131">V příkladu používá vlastnost osy atributu k zobrazení hodnoty `type` atribut pro všechny `phone` elementy.</span><span class="sxs-lookup"><span data-stu-id="aa940-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 <span data-ttu-id="aa940-132">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="aa940-132">This code displays the following text:</span></span>  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a><span data-ttu-id="aa940-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa940-133">See also</span></span>
- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="aa940-134">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="aa940-134">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="aa940-135">Literály XML</span><span class="sxs-lookup"><span data-stu-id="aa940-135">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="aa940-136">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa940-136">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="aa940-137">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="aa940-137">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="aa940-138">Vlastnost indexeru rozšíření</span><span class="sxs-lookup"><span data-stu-id="aa940-138">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [<span data-ttu-id="aa940-139">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="aa940-139">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="aa940-140">Vlastnost osy atributu XML</span><span class="sxs-lookup"><span data-stu-id="aa940-140">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
