---
title: Platný obsah XElement a XDocument Objects3
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: c179f2e57abf0e2028ec58428e75c8df786b4214
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483267"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="4d70f-102">Platný obsah objektů XElement a XDocument</span><span class="sxs-lookup"><span data-stu-id="4d70f-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="4d70f-103">Toto téma popisuje platné argumenty, které mohou být předány konstruktorů a metod, které použijete k přidání obsahu do prvků a dokumenty.</span><span class="sxs-lookup"><span data-stu-id="4d70f-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="4d70f-104">Platný obsah</span><span class="sxs-lookup"><span data-stu-id="4d70f-104">Valid Content</span></span>  
 <span data-ttu-id="4d70f-105">Dotazy často vyhodnotit <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> nebo <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4d70f-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="4d70f-106">Můžete předat kolekce <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objektů <xref:System.Xml.Linq.XElement> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4d70f-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="4d70f-107">Proto je vhodné pro předání výsledky dotazu jako obsah do metody a konstruktory, které můžete použít k naplnění stromů XML.</span><span class="sxs-lookup"><span data-stu-id="4d70f-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="4d70f-108">Při přidání jednoduchého obsahu, může být předán různé typy v této metodě.</span><span class="sxs-lookup"><span data-stu-id="4d70f-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="4d70f-109">Platné typy zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="4d70f-109">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="4d70f-110">Libovolný typ, který implementuje `Object.ToString`.</span><span class="sxs-lookup"><span data-stu-id="4d70f-110">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="4d70f-111">Libovolný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="4d70f-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="4d70f-112">Při přidávání komplexní obsahu, různé typy lze předat tuto metodu:</span><span class="sxs-lookup"><span data-stu-id="4d70f-112">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="4d70f-113">Libovolný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="4d70f-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="4d70f-114">Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vytvořena kolekce v objektu a jsou přidány všechny položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="4d70f-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="4d70f-115">Pokud kolekce obsahuje <xref:System.Xml.Linq.XNode> nebo <xref:System.Xml.Linq.XAttribute> objekty, každá položka v kolekci se přidá samostatně.</span><span class="sxs-lookup"><span data-stu-id="4d70f-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="4d70f-116">Pokud kolekce obsahuje text (nebo objekty, které jsou převedeny na text), je text v kolekci zřetězit a přidat jako jeden textový uzel.</span><span class="sxs-lookup"><span data-stu-id="4d70f-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="4d70f-117">Pokud je obsah `null`, není nic přidáno.</span><span class="sxs-lookup"><span data-stu-id="4d70f-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="4d70f-118">Při předání kolekce položek v kolekci může být `null`.</span><span class="sxs-lookup"><span data-stu-id="4d70f-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="4d70f-119">A `null` položky v kolekci nemá žádný vliv na stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="4d70f-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="4d70f-120">Přidání atributu musí mít jedinečný název v rámci svého nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="4d70f-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="4d70f-121">Při přidávání <xref:System.Xml.Linq.XNode> nebo <xref:System.Xml.Linq.XAttribute> objektů, pokud se nový obsah nemá žádný nadřazený objekt, pak objekty jednoduše připojeny ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="4d70f-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="4d70f-122">Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, poté klonovat nový obsah a nově naklonovaného obsahu je připojen ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="4d70f-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="4d70f-123">Platný obsah pro dokumenty</span><span class="sxs-lookup"><span data-stu-id="4d70f-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="4d70f-124">Atributy a jednoduchý obsah nelze přidat do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4d70f-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="4d70f-125">Nejsou k dispozici mnoho scénářů, které vyžadují, abyste k vytvoření <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="4d70f-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="4d70f-126">Místo toho je možné vytvářet vaše stromů XML s <xref:System.Xml.Linq.XElement> kořenový uzel.</span><span class="sxs-lookup"><span data-stu-id="4d70f-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="4d70f-127">Pokud nemáte konkrétní požadavek na vytvoření dokumentu (například proto budete muset vytvořit pokyny pro zpracování a komentáře na nejvyšší úrovni, nebo máte pro podporu typů dokumentů), často je vhodné použít <xref:System.Xml.Linq.XElement> jako kořenový uzel.</span><span class="sxs-lookup"><span data-stu-id="4d70f-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="4d70f-128">Platný obsah pro dokument obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="4d70f-128">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="4d70f-129">Nula nebo jedna <xref:System.Xml.Linq.XDocumentType> objekty.</span><span class="sxs-lookup"><span data-stu-id="4d70f-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="4d70f-130">Typy dokumentů musí předcházet elementu.</span><span class="sxs-lookup"><span data-stu-id="4d70f-130">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="4d70f-131">Žádný nebo jeden element.</span><span class="sxs-lookup"><span data-stu-id="4d70f-131">Zero or one element.</span></span>  
  
- <span data-ttu-id="4d70f-132">Nula nebo více komentářů.</span><span class="sxs-lookup"><span data-stu-id="4d70f-132">Zero or more comments.</span></span>  
  
- <span data-ttu-id="4d70f-133">Nula nebo více pokyny pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="4d70f-133">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="4d70f-134">Nula nebo více textové uzly obsahující jenom prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="4d70f-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="4d70f-135">Konstruktory a funkce, které umožňují přidávání obsahu</span><span class="sxs-lookup"><span data-stu-id="4d70f-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="4d70f-136">Následující metody umožňují přidat podřízený obsah do <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="4d70f-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="4d70f-137">Metoda</span><span class="sxs-lookup"><span data-stu-id="4d70f-137">Method</span></span>|<span data-ttu-id="4d70f-138">Popis</span><span class="sxs-lookup"><span data-stu-id="4d70f-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="4d70f-139">Vytvoří <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="4d70f-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="4d70f-140">Vytvoří <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="4d70f-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="4d70f-141">Přidá na konec podřízený obsah <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="4d70f-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="4d70f-142">Přidá obsah po <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="4d70f-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="4d70f-143">Přidá obsah před <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="4d70f-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="4d70f-144">Přidá obsah na začátku podřízený obsah <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="4d70f-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="4d70f-145">Nahradí veškerý obsah (podřízených uzlů a atributy) ze <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="4d70f-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="4d70f-146">Nahradí atributy <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="4d70f-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="4d70f-147">Nahradí nový obsah podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="4d70f-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="4d70f-148">Nahradí uzlu nový obsah.</span><span class="sxs-lookup"><span data-stu-id="4d70f-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d70f-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d70f-149">See also</span></span>

- [<span data-ttu-id="4d70f-150">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4d70f-150">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md)
