---
title: Vlastnost indexeru rozšíření (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: ab9eacc3fb3796139d8ed8382146a4a6c2b28a97
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736617"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="e65ea-102">Vlastnost indexeru rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e65ea-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="e65ea-103">Poskytuje přístup k jednotlivým prvkům v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e65ea-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e65ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e65ea-104">Syntax</span></span>  
  
```  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="e65ea-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e65ea-105">Parts</span></span>  
  
|<span data-ttu-id="e65ea-106">Termín</span><span class="sxs-lookup"><span data-stu-id="e65ea-106">Term</span></span>|<span data-ttu-id="e65ea-107">Definice</span><span class="sxs-lookup"><span data-stu-id="e65ea-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="e65ea-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e65ea-108">Required.</span></span> <span data-ttu-id="e65ea-109">Dotazovatelná kolekce.</span><span class="sxs-lookup"><span data-stu-id="e65ea-109">A queryable collection.</span></span> <span data-ttu-id="e65ea-110">To znamená, že kolekce, která implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="e65ea-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="e65ea-111">(</span><span class="sxs-lookup"><span data-stu-id="e65ea-111">(</span></span>|<span data-ttu-id="e65ea-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e65ea-112">Required.</span></span> <span data-ttu-id="e65ea-113">Označuje začátek vlastnost indexeru.</span><span class="sxs-lookup"><span data-stu-id="e65ea-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="e65ea-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e65ea-114">Required.</span></span> <span data-ttu-id="e65ea-115">Celočíselný výraz, který určuje pozice s nulovým základem elementu kolekce.</span><span class="sxs-lookup"><span data-stu-id="e65ea-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="e65ea-116">)</span><span class="sxs-lookup"><span data-stu-id="e65ea-116">)</span></span>|<span data-ttu-id="e65ea-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e65ea-117">Required.</span></span> <span data-ttu-id="e65ea-118">Označuje konec vlastnost indexeru.</span><span class="sxs-lookup"><span data-stu-id="e65ea-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="e65ea-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e65ea-119">Return Value</span></span>  
 <span data-ttu-id="e65ea-120">Objekt v zadaném umístění v kolekci, nebo `Nothing` Pokud index je mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="e65ea-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e65ea-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e65ea-121">Remarks</span></span>  
 <span data-ttu-id="e65ea-122">Vlastnost indexeru rozšíření můžete použít pro přístup k jednotlivým prvkům v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e65ea-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="e65ea-123">Tato vlastnost indexeru se obvykle používá ve výstupu vlastnosti osy XML.</span><span class="sxs-lookup"><span data-stu-id="e65ea-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="e65ea-124">Podřízené XML a vlastnosti XML podřízené osy vrací kolekce <xref:System.Xml.Linq.XElement> objekty nebo hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="e65ea-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="e65ea-125">Kompilátor jazyka Visual Basic převede vlastnosti indexeru rozšíření na volání `ElementAtOrDefault` metody.</span><span class="sxs-lookup"><span data-stu-id="e65ea-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="e65ea-126">Na rozdíl od pole indexer `ElementAtOrDefault` vrátí metoda `Nothing` Pokud index je mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="e65ea-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="e65ea-127">Toto chování je užitečné, když nelze snadno určit počet prvků v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e65ea-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="e65ea-128">Tato vlastnost indexer je jako vlastnost rozšíření pro kolekce, které implementují <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>: používá se pouze v případě, kolekce nemá výchozí vlastnost nebo indexer.</span><span class="sxs-lookup"><span data-stu-id="e65ea-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="e65ea-129">Pro přístup k hodnotě prvního prvku v kolekci <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objekty, můžete použít XML `Value` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e65ea-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="e65ea-130">Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="e65ea-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e65ea-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="e65ea-131">Example</span></span>  
 <span data-ttu-id="e65ea-132">Následující příklad ukazuje, jak používat indexovací modul rozšíření pro přístup k druhý podřízený uzel v kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="e65ea-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="e65ea-133">Kolekce lze přistupovat pomocí vlastnost podřízené osy, který získá všechny podřízené prvky s názvem `phone` v `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="e65ea-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 <span data-ttu-id="e65ea-134">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="e65ea-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="e65ea-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="e65ea-135">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="e65ea-136">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="e65ea-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="e65ea-137">Literály XML</span><span class="sxs-lookup"><span data-stu-id="e65ea-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="e65ea-138">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e65ea-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="e65ea-139">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="e65ea-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
