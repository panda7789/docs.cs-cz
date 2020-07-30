---
title: Platný obsah XElement a XDocument Objects3
description: Přečtěte si o platných argumentech, které lze předat konstruktorům a metodám, které slouží k přidání obsahu do prvků a dokumentů.
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: dfafbe76b078db6c22b475770ebadaff38c75ba8
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302253"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="171e8-103">Platný obsah objektů XElement a XDocument</span><span class="sxs-lookup"><span data-stu-id="171e8-103">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="171e8-104">Toto téma popisuje platné argumenty, které mohou být předány konstruktorům a metodám, které slouží k přidání obsahu do prvků a dokumentů.</span><span class="sxs-lookup"><span data-stu-id="171e8-104">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="171e8-105">Platný obsah</span><span class="sxs-lookup"><span data-stu-id="171e8-105">Valid Content</span></span>  
 <span data-ttu-id="171e8-106">Dotazy jsou často vyhodnoceny jako <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> nebo <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="171e8-106">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="171e8-107">Můžete předat kolekce <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> objektů nebo do <xref:System.Xml.Linq.XElement> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="171e8-107">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="171e8-108">Proto je vhodné předat výsledky dotazu jako obsah do metod a konstruktorů, které slouží k naplnění stromů XML.</span><span class="sxs-lookup"><span data-stu-id="171e8-108">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="171e8-109">Při přidávání jednoduchého obsahu je možné do této metody předat různé typy.</span><span class="sxs-lookup"><span data-stu-id="171e8-109">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="171e8-110">Mezi platné typy patří následující:</span><span class="sxs-lookup"><span data-stu-id="171e8-110">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="171e8-111">Jakýkoli typ, který implementuje `Object.ToString` .</span><span class="sxs-lookup"><span data-stu-id="171e8-111">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="171e8-112">Jakýkoli typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="171e8-112">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="171e8-113">Při přidávání komplexního obsahu je možné do této metody předat různé typy:</span><span class="sxs-lookup"><span data-stu-id="171e8-113">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="171e8-114">Jakýkoli typ, který implementuje<xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="171e8-114">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="171e8-115">Pokud objekt implementuje, je vyhodnocena <xref:System.Collections.Generic.IEnumerable%601> kolekce v objektu a jsou přidány všechny položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="171e8-115">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="171e8-116">Pokud kolekce obsahuje <xref:System.Xml.Linq.XNode> objekty nebo <xref:System.Xml.Linq.XAttribute> , každá položka v kolekci se přidá samostatně.</span><span class="sxs-lookup"><span data-stu-id="171e8-116">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="171e8-117">Pokud kolekce obsahuje text (nebo objekty, které jsou převedeny na text), je text v kolekci zřetězen a přidán jako jediný textový uzel.</span><span class="sxs-lookup"><span data-stu-id="171e8-117">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="171e8-118">Pokud je obsah `null` , nic se nepřidá.</span><span class="sxs-lookup"><span data-stu-id="171e8-118">If content is `null`, nothing is added.</span></span> <span data-ttu-id="171e8-119">Při předávání položek kolekce v kolekci může být `null` .</span><span class="sxs-lookup"><span data-stu-id="171e8-119">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="171e8-120">`null`Položka v kolekci nemá žádný vliv na strom.</span><span class="sxs-lookup"><span data-stu-id="171e8-120">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="171e8-121">Přidaný atribut musí mít jedinečný název v rámci jeho nadřazeného elementu.</span><span class="sxs-lookup"><span data-stu-id="171e8-121">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="171e8-122">Pokud při <xref:System.Xml.Linq.XNode> přidávání <xref:System.Xml.Linq.XAttribute> objektů nebo objektů není k dispozici žádný nadřazený obsah, jsou objekty jednoduše připojeny ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="171e8-122">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="171e8-123">Pokud je nový obsah již nadřazený a je součástí jiného stromu XML, bude nový obsah naklonován a nově Klonovaný obsah bude připojen ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="171e8-123">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="171e8-124">Platný obsah pro dokumenty</span><span class="sxs-lookup"><span data-stu-id="171e8-124">Valid Content for Documents</span></span>  
 <span data-ttu-id="171e8-125">Do dokumentu nelze přidat atributy a jednoduchý obsah.</span><span class="sxs-lookup"><span data-stu-id="171e8-125">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="171e8-126">Neexistuje mnoho scénářů, které vyžadují, abyste vytvořili <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="171e8-126">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="171e8-127">Místo toho můžete obvykle vytvořit stromy XML s <xref:System.Xml.Linq.XElement> kořenovým uzlem.</span><span class="sxs-lookup"><span data-stu-id="171e8-127">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="171e8-128">Pokud nemáte konkrétní požadavek na vytvoření dokumentu (například proto, že potřebujete vytvořit instrukce a komentáře pro zpracování na nejvyšší úrovni nebo potřebujete podporovat typy dokumentů), je často pohodlnější použít <xref:System.Xml.Linq.XElement> jako kořenový uzel.</span><span class="sxs-lookup"><span data-stu-id="171e8-128">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="171e8-129">Platný obsah dokumentu zahrnuje následující:</span><span class="sxs-lookup"><span data-stu-id="171e8-129">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="171e8-130">Nula nebo jeden <xref:System.Xml.Linq.XDocumentType> objekt.</span><span class="sxs-lookup"><span data-stu-id="171e8-130">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="171e8-131">Typy dokumentů musí předcházet elementu.</span><span class="sxs-lookup"><span data-stu-id="171e8-131">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="171e8-132">Nula nebo jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="171e8-132">Zero or one element.</span></span>  
  
- <span data-ttu-id="171e8-133">Nula nebo více komentářů</span><span class="sxs-lookup"><span data-stu-id="171e8-133">Zero or more comments.</span></span>  
  
- <span data-ttu-id="171e8-134">Nula nebo více instrukcí pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="171e8-134">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="171e8-135">Nula nebo více textových uzlů, které obsahují pouze prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="171e8-135">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="171e8-136">Konstruktory a funkce umožňující přidání obsahu</span><span class="sxs-lookup"><span data-stu-id="171e8-136">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="171e8-137">Následující metody umožňují přidat podřízený obsah do <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> :</span><span class="sxs-lookup"><span data-stu-id="171e8-137">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="171e8-138">Metoda</span><span class="sxs-lookup"><span data-stu-id="171e8-138">Method</span></span>|<span data-ttu-id="171e8-139">Popis</span><span class="sxs-lookup"><span data-stu-id="171e8-139">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="171e8-140">Vytvoří <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="171e8-140">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="171e8-141">Vytvoří <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="171e8-141">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="171e8-142">Přidá na konec podřízeného obsahu <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="171e8-142">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="171e8-143">Přidá obsah za <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="171e8-143">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="171e8-144">Přidá obsah před <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="171e8-144">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="171e8-145">Přidá obsah na začátek podřízeného obsahu <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="171e8-145">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="171e8-146">Nahradí veškerý obsah (podřízené uzly a atributy) typu <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="171e8-146">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="171e8-147">Nahradí atributy <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="171e8-147">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="171e8-148">Nahradí podřízené uzly novým obsahem.</span><span class="sxs-lookup"><span data-stu-id="171e8-148">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="171e8-149">Nahradí uzel novým obsahem.</span><span class="sxs-lookup"><span data-stu-id="171e8-149">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="171e8-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="171e8-150">See also</span></span>

- [<span data-ttu-id="171e8-151">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="171e8-151">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
