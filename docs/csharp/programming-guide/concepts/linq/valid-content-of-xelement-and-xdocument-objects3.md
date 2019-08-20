---
title: Platný obsah XElement a XDocument Objects3
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: 1ad5b18e3bbc2143a56f9c8e7b34354761b4e42f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590935"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="d2fbd-102">Platný obsah objektů XElement a XDocument</span><span class="sxs-lookup"><span data-stu-id="d2fbd-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="d2fbd-103">Toto téma popisuje platné argumenty, které mohou být předány konstruktorům a metodám, které slouží k přidání obsahu do prvků a dokumentů.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="d2fbd-104">Platný obsah</span><span class="sxs-lookup"><span data-stu-id="d2fbd-104">Valid Content</span></span>  
 <span data-ttu-id="d2fbd-105">Dotazy <xref:System.Collections.Generic.IEnumerable%601> jsou <xref:System.Xml.Linq.XElement> často vyhodnoceny <xref:System.Collections.Generic.IEnumerable%601> jako <xref:System.Xml.Linq.XAttribute>nebo z.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="d2fbd-106">Můžete předat kolekce <xref:System.Xml.Linq.XElement> objektů nebo <xref:System.Xml.Linq.XAttribute> do <xref:System.Xml.Linq.XElement> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="d2fbd-107">Proto je vhodné předat výsledky dotazu jako obsah do metod a konstruktorů, které slouží k naplnění stromů XML.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="d2fbd-108">Při přidávání jednoduchého obsahu je možné do této metody předat různé typy.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="d2fbd-109">Mezi platné typy patří následující:</span><span class="sxs-lookup"><span data-stu-id="d2fbd-109">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="d2fbd-110">Jakýkoli typ, který `Object.ToString`implementuje.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-110">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="d2fbd-111">Jakýkoli typ, který <xref:System.Collections.Generic.IEnumerable%601>implementuje.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="d2fbd-112">Při přidávání komplexního obsahu je možné do této metody předat různé typy:</span><span class="sxs-lookup"><span data-stu-id="d2fbd-112">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="d2fbd-113">Jakýkoli typ, který implementuje<xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="d2fbd-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="d2fbd-114">Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, je vyhodnocena kolekce v objektu a jsou přidány všechny položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="d2fbd-115">Pokud kolekce obsahuje <xref:System.Xml.Linq.XNode> objekty nebo <xref:System.Xml.Linq.XAttribute> , každá položka v kolekci se přidá samostatně.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="d2fbd-116">Pokud kolekce obsahuje text (nebo objekty, které jsou převedeny na text), je text v kolekci zřetězen a přidán jako jediný textový uzel.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="d2fbd-117">Pokud je `null`obsah, nic se nepřidá.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="d2fbd-118">Při předávání položek kolekce v kolekci může být `null`.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="d2fbd-119">`null` Položka v kolekci nemá žádný vliv na strom.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="d2fbd-120">Přidaný atribut musí mít jedinečný název v rámci jeho nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="d2fbd-121">Pokud při <xref:System.Xml.Linq.XNode> přidávání <xref:System.Xml.Linq.XAttribute> objektů nebo objektů není k dispozici žádný nadřazený obsah, jsou objekty jednoduše připojeny ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="d2fbd-122">Pokud je nový obsah již nadřazený a je součástí jiného stromu XML, bude nový obsah naklonován a nově Klonovaný obsah bude připojen ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="d2fbd-123">Platný obsah pro dokumenty</span><span class="sxs-lookup"><span data-stu-id="d2fbd-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="d2fbd-124">Do dokumentu nelze přidat atributy a jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="d2fbd-125">Neexistuje mnoho scénářů, které vyžadují, abyste vytvořili <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="d2fbd-126">Místo toho můžete obvykle vytvořit stromy XML s <xref:System.Xml.Linq.XElement> kořenovým uzlem.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="d2fbd-127">Pokud nemáte konkrétní požadavek na vytvoření dokumentu (například proto, že potřebujete vytvořit instrukce a komentáře pro zpracování na nejvyšší úrovni nebo potřebujete podporovat typy dokumentů), je často pohodlnější použít <xref:System.Xml.Linq.XElement> jako kořenový uzel.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="d2fbd-128">Platný obsah dokumentu zahrnuje následující:</span><span class="sxs-lookup"><span data-stu-id="d2fbd-128">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="d2fbd-129">Nula nebo jeden <xref:System.Xml.Linq.XDocumentType> objekt.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="d2fbd-130">Typy dokumentů musí předcházet elementu.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-130">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="d2fbd-131">Nula nebo jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-131">Zero or one element.</span></span>  
  
- <span data-ttu-id="d2fbd-132">Nula nebo více komentářů</span><span class="sxs-lookup"><span data-stu-id="d2fbd-132">Zero or more comments.</span></span>  
  
- <span data-ttu-id="d2fbd-133">Nula nebo více instrukcí pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-133">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="d2fbd-134">Nula nebo více textových uzlů, které obsahují pouze prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="d2fbd-135">Konstruktory a funkce umožňující přidání obsahu</span><span class="sxs-lookup"><span data-stu-id="d2fbd-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="d2fbd-136">Následující metody umožňují přidat podřízený obsah do <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>nebo:</span><span class="sxs-lookup"><span data-stu-id="d2fbd-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="d2fbd-137">Metoda</span><span class="sxs-lookup"><span data-stu-id="d2fbd-137">Method</span></span>|<span data-ttu-id="d2fbd-138">Popis</span><span class="sxs-lookup"><span data-stu-id="d2fbd-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="d2fbd-139"><xref:System.Xml.Linq.XElement>Vytvoří.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="d2fbd-140"><xref:System.Xml.Linq.XDocument>Vytvoří.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="d2fbd-141">Přidá na konec podřízeného obsahu <xref:System.Xml.Linq.XElement> nebo. <xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="d2fbd-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="d2fbd-142">Přidá obsah za <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="d2fbd-143">Přidá obsah před <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="d2fbd-144">Přidá obsah na začátek podřízeného obsahu <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="d2fbd-145">Nahradí veškerý obsah (podřízené uzly a atributy) <xref:System.Xml.Linq.XElement>typu.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="d2fbd-146">Nahradí atributy <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="d2fbd-147">Nahradí podřízené uzly novým obsahem.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="d2fbd-148">Nahradí uzel novým obsahem.</span><span class="sxs-lookup"><span data-stu-id="d2fbd-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2fbd-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2fbd-149">See also</span></span>

- [<span data-ttu-id="d2fbd-150">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d2fbd-150">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
