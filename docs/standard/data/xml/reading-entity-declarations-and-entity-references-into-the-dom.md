---
title: "Čtení deklarace Entity a odkazy na Entity do modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6370db06cbe7ff8d46258b0315059f5c37587fea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="60782-102">Čtení deklarace Entity a odkazy na Entity do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="60782-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="60782-103">Entita je deklarace, která určuje název, který se má použít v souboru XML místo obsahu nebo značek.</span><span class="sxs-lookup"><span data-stu-id="60782-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="60782-104">Existují dvě části na entity.</span><span class="sxs-lookup"><span data-stu-id="60782-104">There are two parts to entities.</span></span> <span data-ttu-id="60782-105">Nejdřív musíte tie název, který nahrazení obsah s použitím deklarace entity.</span><span class="sxs-lookup"><span data-stu-id="60782-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="60782-106">Deklarace entity je vytvořená pomocí `<!ENTITY name "value">` syntaxe v definici typu dokumentu (DTD) nebo schématu XML.</span><span class="sxs-lookup"><span data-stu-id="60782-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="60782-107">Za druhé název definovaný v deklaraci entity následně použít v souboru XML.</span><span class="sxs-lookup"><span data-stu-id="60782-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="60782-108">Pokud se použije v souboru XML, nazývá odkazu na entitu.</span><span class="sxs-lookup"><span data-stu-id="60782-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="60782-109">Například následující deklarace entity deklaruje entity názvu `publisher` bylo možné přidružit obsah "Společnosti Microsoft Press".</span><span class="sxs-lookup"><span data-stu-id="60782-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="60782-110">Následující příklad ukazuje použití tuto deklaraci entity v kódu XML jako odkaz na entitu.</span><span class="sxs-lookup"><span data-stu-id="60782-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="60782-111">Některé analyzátory automaticky rozbalit entity, pokud dokument je načten do paměti.</span><span class="sxs-lookup"><span data-stu-id="60782-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="60782-112">Proto když XML je načítán do paměti, deklarace entity jsou zapamatovaných a uložit.</span><span class="sxs-lookup"><span data-stu-id="60782-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="60782-113">Pokud následně analyzátor nalezne `&;` znaky, které identifikovat odkaz obecné entity, analyzátor vyhledá tento název v tabulce deklarace entity.</span><span class="sxs-lookup"><span data-stu-id="60782-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="60782-114">Odkaz na `&publisher;` je nahrazena obsah, který reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="60782-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="60782-115">Pomocí následující kód XML</span><span class="sxs-lookup"><span data-stu-id="60782-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="60782-116">rozbalení odkaz na entitu a nahraďte `&publisher;` s společnosti Microsoft Press obsah poskytuje následující rozšířené XML.</span><span class="sxs-lookup"><span data-stu-id="60782-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="60782-117">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="60782-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="60782-118">Existují různé druhy entity.</span><span class="sxs-lookup"><span data-stu-id="60782-118">There are many kinds of entities.</span></span> <span data-ttu-id="60782-119">Následující diagram ukazuje rozpis typy entit a terminologii.</span><span class="sxs-lookup"><span data-stu-id="60782-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="60782-120">![Vývojový diagram hierarchie typů entit](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="60782-120">![flow chart of entity type hierarchy](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="60782-121">Výchozí hodnota pro implementaci rozhraní Microsoft .NET Framework z XML modelu DOM (Document Object) je zachování odkazy entity a není rozbalit entity, pokud je načtený kód XML.</span><span class="sxs-lookup"><span data-stu-id="60782-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="60782-122">Z toho vyplývá tohoto objektu je, jak dokument je načten do modelu DOM, **XmlEntityReference** uzlu, který obsahuje odkaz na proměnnou `&publisher;` je vytvořen, s podřízenými uzly představující obsah entity v DTD deklarován.</span><span class="sxs-lookup"><span data-stu-id="60782-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="60782-123">Pomocí `<!ENTITY publisher "Microsoft Press">` deklarace entity následující diagram znázorňuje **XmlEntity** a **XmlText** uzlů vytvořené z této deklarace.</span><span class="sxs-lookup"><span data-stu-id="60782-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="60782-124">![uzlů vytvořené z deklarací entity](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="60782-124">![nodes created from entity declaration](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="60782-125">Rozdíly jsou v rozbaleném odkazy na entity, a pokud nejsou je nějaký rozdíl v jaké uzly se generují ve stromové struktuře DOM, v paměti.</span><span class="sxs-lookup"><span data-stu-id="60782-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="60782-126">Rozdíl v uzlech, které jsou generovány, najdete v tématech [odkazy na Entity se zachovají](../../../../docs/standard/data/xml/entity-references-are-preserved.md) a [odkazy na Entity jsou rozšířené a není zachovaná](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="60782-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](../../../../docs/standard/data/xml/entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60782-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="60782-127">See Also</span></span>  
 [<span data-ttu-id="60782-128">XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="60782-128">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
