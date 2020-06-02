---
title: Načtení deklarací entit a odkazů na entity do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
ms.openlocfilehash: 41d88de9ee988a29c54c6e2c6c437963b9f79cf8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289873"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="dce3d-102">Načtení deklarací entit a odkazů na entity do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="dce3d-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="dce3d-103">Entita je deklarace, která uvádí název, který se má použít v XML místo obsahu nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="dce3d-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="dce3d-104">Existují dvě části pro entity.</span><span class="sxs-lookup"><span data-stu-id="dce3d-104">There are two parts to entities.</span></span> <span data-ttu-id="dce3d-105">Nejprve je třeba spojit název nahrazujícího obsahu pomocí deklarace entity.</span><span class="sxs-lookup"><span data-stu-id="dce3d-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="dce3d-106">Deklarace entity je vytvořena pomocí `<!ENTITY name "value">` syntaxe v dokumentu definice typu dokumentu (DTD) nebo schématu XML.</span><span class="sxs-lookup"><span data-stu-id="dce3d-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="dce3d-107">V druhém případě je název definovaný v deklaraci entity následně použit v souboru XML.</span><span class="sxs-lookup"><span data-stu-id="dce3d-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="dce3d-108">Při použití v kódu XML se nazývá odkaz na entitu.</span><span class="sxs-lookup"><span data-stu-id="dce3d-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="dce3d-109">Například následující deklarace entity deklaruje entitu názvu, `publisher` která je přidružena k obsahu "Microsoft Press".</span><span class="sxs-lookup"><span data-stu-id="dce3d-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="dce3d-110">Následující příklad ukazuje použití této deklarace entity v XML jako odkaz na entitu.</span><span class="sxs-lookup"><span data-stu-id="dce3d-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="dce3d-111">Některé analyzátory automaticky rozbalí entity, když je dokument načten do paměti.</span><span class="sxs-lookup"><span data-stu-id="dce3d-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="dce3d-112">Proto když je soubor XML čten do paměti, deklarace entit jsou zachovány a uloženy.</span><span class="sxs-lookup"><span data-stu-id="dce3d-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="dce3d-113">Když analyzátor následně nalezne `&;` znaky, které identifikují obecný odkaz na entitu, analyzátor vyhledá tento název v tabulce deklarací entit.</span><span class="sxs-lookup"><span data-stu-id="dce3d-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="dce3d-114">Odkaz `&publisher;` je nahrazen obsahem, který představuje.</span><span class="sxs-lookup"><span data-stu-id="dce3d-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="dce3d-115">Pomocí následujícího kódu XML</span><span class="sxs-lookup"><span data-stu-id="dce3d-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="dce3d-116">Rozbalením odkazu na entitu a nahrazením `&publisher;` pomocí obsahu Microsoft Press získáte následující rozšířené XML.</span><span class="sxs-lookup"><span data-stu-id="dce3d-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="dce3d-117">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="dce3d-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="dce3d-118">Existuje mnoho druhů entit.</span><span class="sxs-lookup"><span data-stu-id="dce3d-118">There are many kinds of entities.</span></span> <span data-ttu-id="dce3d-119">Následující diagram znázorňuje rozdělení typů entit a terminologie.</span><span class="sxs-lookup"><span data-stu-id="dce3d-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="dce3d-120">![Vývojový diagram hierarchie typů entit](media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="dce3d-120">![flow chart of entity type hierarchy](media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="dce3d-121">Výchozí hodnota pro implementaci model DOM (Document Object Model) XML (DOM) pro Microsoft .NET Framework je zachovat odkazy na entity a nerozšiřovat entity, když je XML načteno.</span><span class="sxs-lookup"><span data-stu-id="dce3d-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="dce3d-122">Důvodem je, že když je dokument načten v modelu DOM, je vytvořen uzel **XmlEntityReference** obsahující referenční proměnnou `&publisher;` s podřízenými uzly, které představují obsah v entitě deklarované v souboru DTD.</span><span class="sxs-lookup"><span data-stu-id="dce3d-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="dce3d-123">Pomocí `<!ENTITY publisher "Microsoft Press">` deklarace entity následující diagram znázorňuje uzly **XmlEntity** a **XmlText** vytvořené z této deklarace.</span><span class="sxs-lookup"><span data-stu-id="dce3d-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="dce3d-124">![uzly vytvořené z deklarace entity](media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="dce3d-124">![nodes created from entity declaration](media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="dce3d-125">Rozdíly při rozbalení odkazů na entity a v případě, že nejsou v nich rozdíl v tom, jaké uzly jsou generovány ve stromové struktuře modelu DOM, v paměti.</span><span class="sxs-lookup"><span data-stu-id="dce3d-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="dce3d-126">Rozdíl v uzlech, které jsou generovány, je vysvětlen v tématech [odkazy na entity jsou zachovány](entity-references-are-preserved.md) a [odkazy na entity jsou rozšířeny a nejsou zachovány](entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="dce3d-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce3d-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="dce3d-127">See also</span></span>

- [<span data-ttu-id="dce3d-128">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="dce3d-128">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
