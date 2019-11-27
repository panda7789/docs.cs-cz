---
title: Vlastnost indexeru rozšíření
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 5f91dc8a6b1a0d82daa4891cf826c16e2716839f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352700"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="62afa-102">Vlastnost indexeru rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62afa-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="62afa-103">Poskytuje přístup k jednotlivým prvkům v kolekci.</span><span class="sxs-lookup"><span data-stu-id="62afa-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62afa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62afa-104">Syntax</span></span>  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="62afa-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="62afa-105">Parts</span></span>  
  
|<span data-ttu-id="62afa-106">Termín</span><span class="sxs-lookup"><span data-stu-id="62afa-106">Term</span></span>|<span data-ttu-id="62afa-107">Definice</span><span class="sxs-lookup"><span data-stu-id="62afa-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="62afa-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="62afa-108">Required.</span></span> <span data-ttu-id="62afa-109">Kolekce Queryable.</span><span class="sxs-lookup"><span data-stu-id="62afa-109">A queryable collection.</span></span> <span data-ttu-id="62afa-110">To znamená, že kolekce, která implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="62afa-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="62afa-111">(</span><span class="sxs-lookup"><span data-stu-id="62afa-111">(</span></span>|<span data-ttu-id="62afa-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="62afa-112">Required.</span></span> <span data-ttu-id="62afa-113">Označuje začátek vlastnosti indexeru.</span><span class="sxs-lookup"><span data-stu-id="62afa-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="62afa-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="62afa-114">Required.</span></span> <span data-ttu-id="62afa-115">Celočíselný výraz, který určuje pozici prvku kolekce na základě nuly.</span><span class="sxs-lookup"><span data-stu-id="62afa-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="62afa-116">)</span><span class="sxs-lookup"><span data-stu-id="62afa-116">)</span></span>|<span data-ttu-id="62afa-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="62afa-117">Required.</span></span> <span data-ttu-id="62afa-118">Označuje konec vlastnosti indexeru.</span><span class="sxs-lookup"><span data-stu-id="62afa-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="62afa-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="62afa-119">Return Value</span></span>  
 <span data-ttu-id="62afa-120">Objekt ze zadaného umístění v kolekci, nebo `Nothing`, pokud je index mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="62afa-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62afa-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62afa-121">Remarks</span></span>  
 <span data-ttu-id="62afa-122">Vlastnost indexeru rozšíření můžete použít pro přístup k jednotlivým prvkům v kolekci.</span><span class="sxs-lookup"><span data-stu-id="62afa-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="62afa-123">Tato vlastnost indexeru se obvykle používá ve výstupu vlastností osy XML.</span><span class="sxs-lookup"><span data-stu-id="62afa-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="62afa-124">Vlastnosti podřízenosti a podřízené osy XML vrací kolekce objektů <xref:System.Xml.Linq.XElement> nebo hodnoty atributu.</span><span class="sxs-lookup"><span data-stu-id="62afa-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="62afa-125">Kompilátor Visual Basic převádí vlastnosti indexeru rozšíření na volání metody `ElementAtOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="62afa-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="62afa-126">Na rozdíl od indexeru pole vrací metoda `ElementAtOrDefault` `Nothing`, pokud je index mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="62afa-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="62afa-127">Toto chování je užitečné, pokud nemůžete snadno určit počet prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="62afa-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="62afa-128">Tato vlastnost indexeru je stejná jako vlastnost rozšíření pro kolekce, které implementují <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>: používá se pouze v případě, že kolekce nemá indexer nebo výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="62afa-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="62afa-129">Pro přístup k hodnotě prvního prvku v kolekci objektů <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> můžete použít vlastnost `Value` XML.</span><span class="sxs-lookup"><span data-stu-id="62afa-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="62afa-130">Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="62afa-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62afa-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="62afa-131">Example</span></span>  
 <span data-ttu-id="62afa-132">Následující příklad ukazuje, jak použít indexer rozšíření pro přístup k druhému podřízenému uzlu v kolekci objektů <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="62afa-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="62afa-133">Ke kolekci je přistupovaná pomocí vlastnosti podřízené osy, která získá všechny podřízené prvky s názvem `phone` v objektu `contact`.</span><span class="sxs-lookup"><span data-stu-id="62afa-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="62afa-134">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="62afa-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="62afa-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62afa-135">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="62afa-136">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="62afa-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="62afa-137">Literály XML</span><span class="sxs-lookup"><span data-stu-id="62afa-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="62afa-138">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="62afa-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="62afa-139">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="62afa-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
