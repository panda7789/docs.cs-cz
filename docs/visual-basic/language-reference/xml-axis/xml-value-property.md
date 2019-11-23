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
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="9b822-102">Vlastnost hodnoty XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b822-102">XML Value Property (Visual Basic)</span></span>

<span data-ttu-id="9b822-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="9b822-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="9b822-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b822-104">Syntax</span></span>

```vb
object.Value
```

## <a name="parts"></a><span data-ttu-id="9b822-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="9b822-105">Parts</span></span>

|<span data-ttu-id="9b822-106">Termín</span><span class="sxs-lookup"><span data-stu-id="9b822-106">Term</span></span>|<span data-ttu-id="9b822-107">Definice</span><span class="sxs-lookup"><span data-stu-id="9b822-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="9b822-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9b822-108">Required.</span></span> <span data-ttu-id="9b822-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="9b822-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  

## <a name="return-value"></a><span data-ttu-id="9b822-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9b822-110">Return Value</span></span>

 <span data-ttu-id="9b822-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span><span class="sxs-lookup"><span data-stu-id="9b822-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b822-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b822-112">Remarks</span></span>

 <span data-ttu-id="9b822-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="9b822-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="9b822-114">This property first checks whether the collection contains at least one object.</span><span class="sxs-lookup"><span data-stu-id="9b822-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="9b822-115">If the collection is empty, this property returns `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9b822-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="9b822-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span><span class="sxs-lookup"><span data-stu-id="9b822-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="9b822-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span><span class="sxs-lookup"><span data-stu-id="9b822-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>

 <span data-ttu-id="9b822-118">To access other elements in a collection, you can use the XML extension indexer property.</span><span class="sxs-lookup"><span data-stu-id="9b822-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="9b822-119">For more information, see [Extension Indexer Property](extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="9b822-119">For more information, see [Extension Indexer Property](extension-indexer-property.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="9b822-120">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="9b822-120">Inheritance</span></span>

 <span data-ttu-id="9b822-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span><span class="sxs-lookup"><span data-stu-id="9b822-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>

 <span data-ttu-id="9b822-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="9b822-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="9b822-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span><span class="sxs-lookup"><span data-stu-id="9b822-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="9b822-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="9b822-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>

## <a name="example"></a><span data-ttu-id="9b822-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b822-125">Example</span></span>

 <span data-ttu-id="9b822-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="9b822-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="9b822-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span><span class="sxs-lookup"><span data-stu-id="9b822-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 <span data-ttu-id="9b822-128">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="9b822-128">This code displays the following text:</span></span>

 `Phone number: 206-555-0144`

## <a name="example"></a><span data-ttu-id="9b822-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b822-129">Example</span></span>

 <span data-ttu-id="9b822-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span><span class="sxs-lookup"><span data-stu-id="9b822-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="9b822-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span><span class="sxs-lookup"><span data-stu-id="9b822-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 <span data-ttu-id="9b822-132">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="9b822-132">This code displays the following text:</span></span>

 ```console
 home
 work
```

## <a name="see-also"></a><span data-ttu-id="9b822-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b822-133">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="9b822-134">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="9b822-134">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="9b822-135">Literály XML</span><span class="sxs-lookup"><span data-stu-id="9b822-135">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="9b822-136">Creating XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b822-136">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="9b822-137">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="9b822-137">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="9b822-138">Vlastnost indexeru rozšíření</span><span class="sxs-lookup"><span data-stu-id="9b822-138">Extension Indexer Property</span></span>](extension-indexer-property.md)
- [<span data-ttu-id="9b822-139">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="9b822-139">XML Child Axis Property</span></span>](xml-child-axis-property.md)
- [<span data-ttu-id="9b822-140">Vlastnost osy atributu XML</span><span class="sxs-lookup"><span data-stu-id="9b822-140">XML Attribute Axis Property</span></span>](xml-attribute-axis-property.md)
