---
title: "Vlastnost indexeru rozšíření (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99d14b6e54a59ffc904a9e786c22498d23ee8ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="aa366-102">Vlastnost indexeru rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa366-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="aa366-103">Poskytuje přístup k jednotlivé elementy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="aa366-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa366-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa366-104">Syntax</span></span>  
  
```  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="aa366-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="aa366-105">Parts</span></span>  
  
|<span data-ttu-id="aa366-106">Termín</span><span class="sxs-lookup"><span data-stu-id="aa366-106">Term</span></span>|<span data-ttu-id="aa366-107">Definice</span><span class="sxs-lookup"><span data-stu-id="aa366-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="aa366-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="aa366-108">Required.</span></span> <span data-ttu-id="aa366-109">Dotazovatelná kolekce.</span><span class="sxs-lookup"><span data-stu-id="aa366-109">A queryable collection.</span></span> <span data-ttu-id="aa366-110">To znamená, kolekce, která implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="aa366-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="aa366-111">(</span><span class="sxs-lookup"><span data-stu-id="aa366-111">(</span></span>|<span data-ttu-id="aa366-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="aa366-112">Required.</span></span> <span data-ttu-id="aa366-113">Označuje začátek vlastnost indexeru.</span><span class="sxs-lookup"><span data-stu-id="aa366-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="aa366-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="aa366-114">Required.</span></span> <span data-ttu-id="aa366-115">Celé číslo výraz, který určuje pozice s nulovým základem elementu kolekce.</span><span class="sxs-lookup"><span data-stu-id="aa366-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="aa366-116">)</span><span class="sxs-lookup"><span data-stu-id="aa366-116">)</span></span>|<span data-ttu-id="aa366-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="aa366-117">Required.</span></span> <span data-ttu-id="aa366-118">Označuje konec vlastnost indexeru.</span><span class="sxs-lookup"><span data-stu-id="aa366-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="aa366-119">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aa366-119">Return Value</span></span>  
 <span data-ttu-id="aa366-120">Objekt v zadaném umístění v kolekci, nebo `Nothing` Pokud index je mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="aa366-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa366-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa366-121">Remarks</span></span>  
 <span data-ttu-id="aa366-122">Vlastnost indexeru rozšíření slouží pro přístup k jednotlivé elementy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="aa366-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="aa366-123">Tato vlastnost indexer se obvykle používá na výstup vlastnosti osy XML.</span><span class="sxs-lookup"><span data-stu-id="aa366-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="aa366-124">Podřízené XML a vlastnosti podřízené osy XML vrátí kolekce <xref:System.Xml.Linq.XElement> objekty nebo hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="aa366-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="aa366-125">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru převede vlastnosti indexeru rozšíření na volání `ElementAtOrDefault` metoda.</span><span class="sxs-lookup"><span data-stu-id="aa366-125">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="aa366-126">Na rozdíl od indexer pole `ElementAtOrDefault` metoda vrátí `Nothing` Pokud index je mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="aa366-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="aa366-127">Toto chování je užitečné, když nelze snadno určit počet elementů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="aa366-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="aa366-128">Tato vlastnost indexeru je jako vlastnost rozšíření pro kolekce, které implementují <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>: používá se pouze v případě, že kolekce nemá indexer nebo výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="aa366-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="aa366-129">Pro přístup k hodnotě prvním elementem v kolekci <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objekty, můžete použít soubor XML `Value` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="aa366-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="aa366-130">Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="aa366-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa366-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa366-131">Example</span></span>  
 <span data-ttu-id="aa366-132">Následující příklad ukazuje, jak používat indexovací modul rozšíření pro přístup k druhý podřízený uzel v kolekci <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="aa366-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="aa366-133">Kolekce přistupuje pomocí vlastnost osy podřízeného, který získá všech podřízených elementů s názvem `phone` v `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="aa366-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 <span data-ttu-id="aa366-134">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="aa366-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="aa366-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa366-135">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="aa366-136">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="aa366-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="aa366-137">XML – literály</span><span class="sxs-lookup"><span data-stu-id="aa366-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="aa366-138">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa366-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="aa366-139">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="aa366-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
