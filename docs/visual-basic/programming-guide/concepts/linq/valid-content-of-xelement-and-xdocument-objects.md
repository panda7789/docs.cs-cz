---
title: Platný obsah XElement a XDocument Objects2
ms.date: 07/20/2015
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
ms.openlocfilehash: 4b1d588f0ebbfec6d5cf7a58b63f92005db75acc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649380"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="5a405-102">Platný obsah XElement a XDocument objektů</span><span class="sxs-lookup"><span data-stu-id="5a405-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="5a405-103">Toto téma popisuje platné argumenty, které lze předat konstruktorů a metod, které můžete použít k přidání obsahu do elementů a dokumenty.</span><span class="sxs-lookup"><span data-stu-id="5a405-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="5a405-104">Platný obsah</span><span class="sxs-lookup"><span data-stu-id="5a405-104">Valid Content</span></span>  
 <span data-ttu-id="5a405-105">Dotazy často vyhodnocení <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> nebo <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5a405-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="5a405-106">Můžete předat kolekce <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objekty ke <xref:System.Xml.Linq.XElement> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="5a405-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="5a405-107">Proto je vhodné k předání výsledků dotazu jako obsah do metod a konstruktory, které můžete použít k naplnění stromy XML.</span><span class="sxs-lookup"><span data-stu-id="5a405-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="5a405-108">Při přidávání jednoduchým obsahem, může být různých typů předané této metodě.</span><span class="sxs-lookup"><span data-stu-id="5a405-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="5a405-109">Platné typy jsou následující:</span><span class="sxs-lookup"><span data-stu-id="5a405-109">Valid types include the following:</span></span>  
  
-   <xref:System.String>  
  
-   <xref:System.Double>  
  
-   <xref:System.Single>  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Boolean>  
  
-   <xref:System.DateTime>  
  
-   <xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset>  
  
-   <span data-ttu-id="5a405-110">Žádný typ, který implementuje `Object.ToString`.</span><span class="sxs-lookup"><span data-stu-id="5a405-110">Any type that implements `Object.ToString`.</span></span>  
  
-   <span data-ttu-id="5a405-111">Žádný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="5a405-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="5a405-112">Při přidávání složitým obsahem, může být různých typů předaná této metodě:</span><span class="sxs-lookup"><span data-stu-id="5a405-112">When adding complex content, various types can be passed to this method:</span></span>  
  
-   <xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   <span data-ttu-id="5a405-113">Žádný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5a405-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="5a405-114">Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vytvořena kolekce v objektu, a jsou přidány všechny položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="5a405-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="5a405-115">Pokud kolekce obsahuje <xref:System.Xml.Linq.XNode> nebo <xref:System.Xml.Linq.XAttribute> objekty, každá položka v kolekci se přidá samostatně.</span><span class="sxs-lookup"><span data-stu-id="5a405-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="5a405-116">Pokud kolekce obsahuje text (nebo objekty, které jsou převedeny na text), je text v kolekci zřetězených a přidat jako uzel jednoho textu.</span><span class="sxs-lookup"><span data-stu-id="5a405-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="5a405-117">Pokud je obsah `null`, není nic přidáno.</span><span class="sxs-lookup"><span data-stu-id="5a405-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="5a405-118">Při předávání kolekce položek v kolekci může být `null`.</span><span class="sxs-lookup"><span data-stu-id="5a405-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="5a405-119">A `null` položky v kolekci nemá žádný vliv na stromu.</span><span class="sxs-lookup"><span data-stu-id="5a405-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="5a405-120">Přidání atributu musí mít jedinečný název v rámci svého nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="5a405-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="5a405-121">Při přidávání <xref:System.Xml.Linq.XNode> nebo <xref:System.Xml.Linq.XAttribute> objekty, pokud nemá žádný nadřazený uzel s nový obsah, pak objekty jednoduše přiřazeny ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="5a405-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="5a405-122">Pokud nový obsah už je nadřazena a je součástí jiného stromu XML, pak je nový obsah klonovat a nově naklonovaný obsah je připojen k stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="5a405-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="5a405-123">Platný obsah pro dokumenty</span><span class="sxs-lookup"><span data-stu-id="5a405-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="5a405-124">Atributy a jednoduchý obsah nelze přidat do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5a405-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="5a405-125">Nejsou k dispozici mnoho scénářů, které vyžadují, abyste vytvořili <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="5a405-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="5a405-126">Místo toho je možné vytvářet vaše stromy XML s <xref:System.Xml.Linq.XElement> kořenový uzel.</span><span class="sxs-lookup"><span data-stu-id="5a405-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="5a405-127">Pokud máte specifické požadavky pro vytvoření dokumentu (například proto je nutné vytvořit pokyny pro zpracování a komentáře na nejvyšší úrovni, nebo nemáte k podpoře typů dokumentů), je často vhodnější použít <xref:System.Xml.Linq.XElement> jako kořenový uzel.</span><span class="sxs-lookup"><span data-stu-id="5a405-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="5a405-128">Platný obsah pro dokument obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="5a405-128">Valid content for a document includes the following:</span></span>  
  
-   <span data-ttu-id="5a405-129">Nula nebo jedna <xref:System.Xml.Linq.XDocumentType> objekty.</span><span class="sxs-lookup"><span data-stu-id="5a405-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="5a405-130">Element musí předcházet typů dokumentů.</span><span class="sxs-lookup"><span data-stu-id="5a405-130">The document types must come before the element.</span></span>  
  
-   <span data-ttu-id="5a405-131">Nula nebo jeden element.</span><span class="sxs-lookup"><span data-stu-id="5a405-131">Zero or one element.</span></span>  
  
-   <span data-ttu-id="5a405-132">Komentáře v počtu nula či více.</span><span class="sxs-lookup"><span data-stu-id="5a405-132">Zero or more comments.</span></span>  
  
-   <span data-ttu-id="5a405-133">Pokyny pro zpracování nula nebo více.</span><span class="sxs-lookup"><span data-stu-id="5a405-133">Zero or more processing instructions.</span></span>  
  
-   <span data-ttu-id="5a405-134">Nula nebo více textové uzly, které obsahují jenom prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="5a405-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="5a405-135">Konstruktory a funkce, které umožňují přidávání obsahu</span><span class="sxs-lookup"><span data-stu-id="5a405-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="5a405-136">Následující metody umožňují přidat podřízené obsah tak, aby <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="5a405-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="5a405-137">Metoda</span><span class="sxs-lookup"><span data-stu-id="5a405-137">Method</span></span>|<span data-ttu-id="5a405-138">Popis</span><span class="sxs-lookup"><span data-stu-id="5a405-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="5a405-139">Vytvoří <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5a405-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="5a405-140">Vytvoří <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="5a405-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="5a405-141">Přidá na konec obsahu z podřízené <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="5a405-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="5a405-142">Přidá obsah po <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="5a405-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="5a405-143">Přidá obsahu před <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="5a405-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="5a405-144">Přidá obsah na začátku podřízené obsah <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="5a405-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="5a405-145">Nahradí všechny obsah (podřízené uzly a atributy) <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5a405-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="5a405-146">Nahradí atributy <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5a405-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="5a405-147">Podřízené uzly nahradí nový obsah.</span><span class="sxs-lookup"><span data-stu-id="5a405-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="5a405-148">Nahradí uzlu nový obsah.</span><span class="sxs-lookup"><span data-stu-id="5a405-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a405-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a405-149">See Also</span></span>  
 [<span data-ttu-id="5a405-150">Vytváření stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a405-150">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
