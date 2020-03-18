---
title: Platný obsah objektů XElement a XDocument3
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: 1ad5b18e3bbc2143a56f9c8e7b34354761b4e42f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590935"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="ba464-102">Platný obsah objektů XElement a XDocument</span><span class="sxs-lookup"><span data-stu-id="ba464-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="ba464-103">Toto téma popisuje platné argumenty, které mohou být předány konstruktorům a metodám, které slouží k přidání obsahu do prvků a dokumentů.</span><span class="sxs-lookup"><span data-stu-id="ba464-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="ba464-104">Platný obsah</span><span class="sxs-lookup"><span data-stu-id="ba464-104">Valid Content</span></span>  
 <span data-ttu-id="ba464-105">Dotazy <xref:System.Collections.Generic.IEnumerable%601> často vyhodnocují do nebo <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ba464-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="ba464-106">Konstruktoru <xref:System.Xml.Linq.XElement> můžete předat <xref:System.Xml.Linq.XAttribute> kolekce <xref:System.Xml.Linq.XElement> nebo objekty.</span><span class="sxs-lookup"><span data-stu-id="ba464-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="ba464-107">Proto je vhodné předat výsledky dotazu jako obsah do metod a konstruktorů, které používáte k naplnění stromů XML.</span><span class="sxs-lookup"><span data-stu-id="ba464-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="ba464-108">Při přidávání jednoduchého obsahu mohou být této metodě předány různé typy.</span><span class="sxs-lookup"><span data-stu-id="ba464-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="ba464-109">Mezi platné typy patří následující:</span><span class="sxs-lookup"><span data-stu-id="ba464-109">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="ba464-110">Libovolný typ, `Object.ToString`který implementuje .</span><span class="sxs-lookup"><span data-stu-id="ba464-110">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="ba464-111">Libovolný typ, <xref:System.Collections.Generic.IEnumerable%601>který implementuje .</span><span class="sxs-lookup"><span data-stu-id="ba464-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="ba464-112">Při přidávání komplexního obsahu mohou být této metodě předány různé typy:</span><span class="sxs-lookup"><span data-stu-id="ba464-112">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="ba464-113">Libovolný typ, který implementuje<xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="ba464-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="ba464-114">Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekce v objektu je výčtu a jsou přidány všechny položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ba464-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="ba464-115">Pokud kolekce <xref:System.Xml.Linq.XNode> obsahuje <xref:System.Xml.Linq.XAttribute> nebo objekty, každá položka v kolekci je přidán samostatně.</span><span class="sxs-lookup"><span data-stu-id="ba464-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="ba464-116">Pokud kolekce obsahuje text (nebo objekty, které jsou převedeny na text), text v kolekci je zřetězena a přidána jako jeden textový uzel.</span><span class="sxs-lookup"><span data-stu-id="ba464-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="ba464-117">Pokud je `null`obsah , nic není přidáno.</span><span class="sxs-lookup"><span data-stu-id="ba464-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="ba464-118">Při předávání položek kolekce v `null`kolekci může být .</span><span class="sxs-lookup"><span data-stu-id="ba464-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="ba464-119">Položka `null` v kolekci nemá žádný vliv na strom.</span><span class="sxs-lookup"><span data-stu-id="ba464-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="ba464-120">Přidaný atribut musí mít jedinečný název v rámci obsahujícího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba464-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="ba464-121">Při <xref:System.Xml.Linq.XNode> přidávání nebo <xref:System.Xml.Linq.XAttribute> objekty, pokud nový obsah nemá nadřazený, pak objekty jsou jednoduše připojeny ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="ba464-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="ba464-122">Pokud je nový obsah již nadřazený a je součástí jiného stromu XML, je nový obsah klonován a nově klonovaný obsah je připojen ke stromu XML.</span><span class="sxs-lookup"><span data-stu-id="ba464-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="ba464-123">Platný obsah pro dokumenty</span><span class="sxs-lookup"><span data-stu-id="ba464-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="ba464-124">Atributy a jednoduchý obsah nelze přidat do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ba464-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="ba464-125">Není mnoho scénářů, které vyžadují <xref:System.Xml.Linq.XDocument>vytvoření .</span><span class="sxs-lookup"><span data-stu-id="ba464-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="ba464-126">Místo toho můžete obvykle vytvořit stromy <xref:System.Xml.Linq.XElement> XML s kořenovým uzlem.</span><span class="sxs-lookup"><span data-stu-id="ba464-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="ba464-127">Pokud nemáte konkrétní požadavek na vytvoření dokumentu (například proto, že musíte vytvořit pokyny pro zpracování a komentáře na nejvyšší úrovni <xref:System.Xml.Linq.XElement> nebo musíte podporovat typy dokumentů), je často vhodnější použít jako kořenový uzel.</span><span class="sxs-lookup"><span data-stu-id="ba464-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="ba464-128">Platný obsah dokumentu zahrnuje následující:</span><span class="sxs-lookup"><span data-stu-id="ba464-128">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="ba464-129">Nula <xref:System.Xml.Linq.XDocumentType> nebo jeden objekt.</span><span class="sxs-lookup"><span data-stu-id="ba464-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="ba464-130">Typy dokumentů musí být před elementem.</span><span class="sxs-lookup"><span data-stu-id="ba464-130">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="ba464-131">Nula nebo jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="ba464-131">Zero or one element.</span></span>  
  
- <span data-ttu-id="ba464-132">Nula nebo více komentářů.</span><span class="sxs-lookup"><span data-stu-id="ba464-132">Zero or more comments.</span></span>  
  
- <span data-ttu-id="ba464-133">Nula nebo více pokynů pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="ba464-133">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="ba464-134">Nula nebo více uzly textu, které obsahují pouze prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="ba464-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="ba464-135">Konstruktory a funkce, které umožňují přidávání obsahu</span><span class="sxs-lookup"><span data-stu-id="ba464-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="ba464-136">Následující metody umožňují přidat podřízený <xref:System.Xml.Linq.XElement> obsah <xref:System.Xml.Linq.XDocument>do aplikace nebo :</span><span class="sxs-lookup"><span data-stu-id="ba464-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="ba464-137">Metoda</span><span class="sxs-lookup"><span data-stu-id="ba464-137">Method</span></span>|<span data-ttu-id="ba464-138">Popis</span><span class="sxs-lookup"><span data-stu-id="ba464-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="ba464-139">Vytvoří <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="ba464-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="ba464-140">Vytvoří <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="ba464-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="ba464-141">Přidá na konec podřízeného <xref:System.Xml.Linq.XElement> obsahu <xref:System.Xml.Linq.XDocument>nebo .</span><span class="sxs-lookup"><span data-stu-id="ba464-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="ba464-142">Přidá obsah <xref:System.Xml.Linq.XNode>za .</span><span class="sxs-lookup"><span data-stu-id="ba464-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="ba464-143">Přidá obsah <xref:System.Xml.Linq.XNode>před .</span><span class="sxs-lookup"><span data-stu-id="ba464-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="ba464-144">Přidá obsah na začátku podřízeného obsahu . <xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="ba464-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="ba464-145">Nahradí veškerý obsah (podřízené uzly <xref:System.Xml.Linq.XElement>a atributy) .</span><span class="sxs-lookup"><span data-stu-id="ba464-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="ba464-146">Nahradí atributy . <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="ba464-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="ba464-147">Nahradí podřízené uzly novým obsahem.</span><span class="sxs-lookup"><span data-stu-id="ba464-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="ba464-148">Nahradí uzel novým obsahem.</span><span class="sxs-lookup"><span data-stu-id="ba464-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba464-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba464-149">See also</span></span>

- [<span data-ttu-id="ba464-150">Vytváření stromů XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ba464-150">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
