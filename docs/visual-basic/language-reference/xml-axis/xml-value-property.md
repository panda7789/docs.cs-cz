---
title: Vlastnost hodnoty XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 571d9130ef69df580bbba5d90bc8758b4b627196
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349423"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="d0db4-102">Vlastnost hodnoty XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0db4-102">XML Value Property (Visual Basic)</span></span>

<span data-ttu-id="d0db4-103">Poskytuje přístup k hodnotě prvního prvku kolekce objektů <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d0db4-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0db4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0db4-104">Syntax</span></span>

```vb
object.Value
```

## <a name="parts"></a><span data-ttu-id="d0db4-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d0db4-105">Parts</span></span>

|<span data-ttu-id="d0db4-106">Termín</span><span class="sxs-lookup"><span data-stu-id="d0db4-106">Term</span></span>|<span data-ttu-id="d0db4-107">Definice</span><span class="sxs-lookup"><span data-stu-id="d0db4-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="d0db4-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d0db4-108">Required.</span></span> <span data-ttu-id="d0db4-109">Kolekce objektů <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d0db4-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  

## <a name="return-value"></a><span data-ttu-id="d0db4-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d0db4-110">Return Value</span></span>

 <span data-ttu-id="d0db4-111">`String`, který obsahuje hodnotu prvního prvku kolekce, nebo `Nothing`, pokud je kolekce prázdná.</span><span class="sxs-lookup"><span data-stu-id="d0db4-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0db4-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0db4-112">Remarks</span></span>

 <span data-ttu-id="d0db4-113">Vlastnost <xref:System.Xml.Linq.XElement.Value%2A> usnadňuje přístup k hodnotě prvního prvku v kolekci objektů <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d0db4-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d0db4-114">Tato vlastnost nejprve ověří, zda kolekce obsahuje alespoň jeden objekt.</span><span class="sxs-lookup"><span data-stu-id="d0db4-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="d0db4-115">Pokud je kolekce prázdná, vrátí tato vlastnost `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="d0db4-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="d0db4-116">V opačném případě tato vlastnost vrátí hodnotu vlastnosti <xref:System.Xml.Linq.XElement.Value%2A> prvního prvku v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d0db4-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="d0db4-117">Při přístupu k hodnotě atributu XML pomocí identifikátoru '\@' se hodnota atributu vrátí jako `String` a nemusíte explicitně určovat vlastnost <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="d0db4-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>

 <span data-ttu-id="d0db4-118">Chcete-li získat přístup k dalším prvkům v kolekci, můžete použít vlastnost indexer rozšíření XML.</span><span class="sxs-lookup"><span data-stu-id="d0db4-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="d0db4-119">Další informace najdete v tématu [vlastnost indexeru rozšíření](extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="d0db4-119">For more information, see [Extension Indexer Property](extension-indexer-property.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="d0db4-120">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="d0db4-120">Inheritance</span></span>

 <span data-ttu-id="d0db4-121">Většina uživatelů nebude muset implementovat <xref:System.Collections.Generic.IEnumerable%601>, a proto může tuto část ignorovat.</span><span class="sxs-lookup"><span data-stu-id="d0db4-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>

 <span data-ttu-id="d0db4-122">Vlastnost <xref:System.Xml.Linq.XElement.Value%2A> je vlastnost rozšíření pro typy, které implementují `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="d0db4-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="d0db4-123">Vazba této vlastnosti rozšíření se podobá vazbě rozšiřujících metod: Pokud typ implementuje jedno z rozhraní a definuje vlastnost s názvem "value", má tato vlastnost přednost před vlastností Extension.</span><span class="sxs-lookup"><span data-stu-id="d0db4-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="d0db4-124">Jinými slovy Tato vlastnost <xref:System.Xml.Linq.XElement.Value%2A> možné přepsat definováním nové vlastnosti ve třídě, která implementuje `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="d0db4-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>

## <a name="example"></a><span data-ttu-id="d0db4-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0db4-125">Example</span></span>

 <span data-ttu-id="d0db4-126">Následující příklad ukazuje, jak použít vlastnost <xref:System.Xml.Linq.XElement.Value%2A> pro přístup k prvnímu uzlu v kolekci objektů <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d0db4-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d0db4-127">V příkladu se používá vlastnost podřízené osy k získání kolekce všech podřízených uzlů s názvem `phone`, které jsou v objektu `contact`.</span><span class="sxs-lookup"><span data-stu-id="d0db4-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 <span data-ttu-id="d0db4-128">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="d0db4-128">This code displays the following text:</span></span>

 `Phone number: 206-555-0144`

## <a name="example"></a><span data-ttu-id="d0db4-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0db4-129">Example</span></span>

 <span data-ttu-id="d0db4-130">Následující příklad ukazuje, jak získat hodnotu atributu XML z kolekce objektů <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d0db4-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="d0db4-131">V příkladu se používá vlastnost osa atributu k zobrazení hodnoty atributu `type` pro všechny `phone` prvky.</span><span class="sxs-lookup"><span data-stu-id="d0db4-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 <span data-ttu-id="d0db4-132">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="d0db4-132">This code displays the following text:</span></span>

 ```console
 home
 work
```

## <a name="see-also"></a><span data-ttu-id="d0db4-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0db4-133">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="d0db4-134">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="d0db4-134">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="d0db4-135">Literály XML</span><span class="sxs-lookup"><span data-stu-id="d0db4-135">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="d0db4-136">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0db4-136">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="d0db4-137">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="d0db4-137">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="d0db4-138">Vlastnost indexeru rozšíření</span><span class="sxs-lookup"><span data-stu-id="d0db4-138">Extension Indexer Property</span></span>](extension-indexer-property.md)
- [<span data-ttu-id="d0db4-139">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="d0db4-139">XML Child Axis Property</span></span>](xml-child-axis-property.md)
- [<span data-ttu-id="d0db4-140">Vlastnost osy atributu XML</span><span class="sxs-lookup"><span data-stu-id="d0db4-140">XML Attribute Axis Property</span></span>](xml-attribute-axis-property.md)
