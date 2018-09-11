---
title: Čtení deklarací entit a odkazy na Entity do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e30b52b8cdfb4d185687d58c80f4475730031c86
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264269"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="44844-102">Čtení deklarací entit a odkazy na Entity do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="44844-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="44844-103">Entita je deklarace, která uvádí název, který se má použít v souboru XML místo obsahu nebo značky.</span><span class="sxs-lookup"><span data-stu-id="44844-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="44844-104">Existují dvě části k entitám.</span><span class="sxs-lookup"><span data-stu-id="44844-104">There are two parts to entities.</span></span> <span data-ttu-id="44844-105">Nejprve musíte tie název pro nahrazení obsahu pomocí deklarace entity.</span><span class="sxs-lookup"><span data-stu-id="44844-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="44844-106">Vytvoří pomocí deklarace entity `<!ENTITY name "value">` syntaxe v definici typu dokumentu (DTD) nebo schématu XML.</span><span class="sxs-lookup"><span data-stu-id="44844-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="44844-107">Za druhé název definovaný v deklaraci entity se následně používá v souboru XML.</span><span class="sxs-lookup"><span data-stu-id="44844-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="44844-108">Při použití v souboru XML, je volána odkazu na entitu.</span><span class="sxs-lookup"><span data-stu-id="44844-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="44844-109">Například následující deklaraci entita deklaruje entity názvu `publisher` jsou spojeny s obsahem "Microsoft Press".</span><span class="sxs-lookup"><span data-stu-id="44844-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="44844-110">Následující příklad ukazuje použití této deklarace entity v XML jako odkaz na entitu.</span><span class="sxs-lookup"><span data-stu-id="44844-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="44844-111">Některé analyzátorů automaticky rozšíří entity dokumentu je načtena do paměti.</span><span class="sxs-lookup"><span data-stu-id="44844-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="44844-112">Proto když XML je načítána do paměti, entity prohlášení jsou zapamatovaných a uložit.</span><span class="sxs-lookup"><span data-stu-id="44844-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="44844-113">Pokud následně analyzátor nalezne `&;` znaků, které identifikovat odkaz na obecnou entitu, analyzátor vyhledá tímto názvem v tabulce entity prohlášení.</span><span class="sxs-lookup"><span data-stu-id="44844-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="44844-114">Odkaz na `&publisher;` nahrazuje obsah, který představuje.</span><span class="sxs-lookup"><span data-stu-id="44844-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="44844-115">Pomocí následující kód XML</span><span class="sxs-lookup"><span data-stu-id="44844-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="44844-116">rozbalení odkaz na entitu a nahrazování `&publisher;` díky Microsoft Press obsah poskytuje následující rozšířené kód XML.</span><span class="sxs-lookup"><span data-stu-id="44844-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="44844-117">**Output**</span><span class="sxs-lookup"><span data-stu-id="44844-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="44844-118">Existují různé druhy entit.</span><span class="sxs-lookup"><span data-stu-id="44844-118">There are many kinds of entities.</span></span> <span data-ttu-id="44844-119">Následující diagram znázorňuje rozdělení typy entit a terminologie.</span><span class="sxs-lookup"><span data-stu-id="44844-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="44844-120">![Vývojový diagram hierarchie typů entit](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="44844-120">![flow chart of entity type hierarchy](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="44844-121">Ve výchozím nastavení pro implementaci rozhraní Microsoft .NET Framework z XML Document Object Model (DOM) je zachování odkazy na entity a ne rozbalit entity při načtení XML.</span><span class="sxs-lookup"><span data-stu-id="44844-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="44844-122">Důsledkem tohoto je, že jako dokument se načte do modelu DOM, **XmlEntityReference** uzlu, který obsahuje odkaz na proměnnou `&publisher;` je vytvořen, s podřízenými uzly představující obsah entity deklarované v DTD.</span><span class="sxs-lookup"><span data-stu-id="44844-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="44844-123">Použití `<!ENTITY publisher "Microsoft Press">` entity prohlášení, následující diagram ukazuje **XmlEntity** a **XmlText** uzlů vytvořené z této deklarace.</span><span class="sxs-lookup"><span data-stu-id="44844-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="44844-124">![uzlů vytvořené z entity prohlášení](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="44844-124">![nodes created from entity declaration](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="44844-125">Rozdíly při odkazy na entity rozbaleny, a pokud nejsou různá v jakých uzlů se generují ve stromové struktuře modelu DOM, v paměti.</span><span class="sxs-lookup"><span data-stu-id="44844-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="44844-126">Rozdíl v uzlech, které jsou generovány je vysvětleno v tématech [odkazy na Entity jsou zachovány](../../../../docs/standard/data/xml/entity-references-are-preserved.md) a [odkazy na Entity jsou rozšířené a Nezachované](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="44844-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](../../../../docs/standard/data/xml/entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44844-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44844-127">See also</span></span>

- [<span data-ttu-id="44844-128">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="44844-128">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
