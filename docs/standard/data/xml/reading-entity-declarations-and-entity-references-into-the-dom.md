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
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>Čtení deklarace Entity a odkazy na Entity do modelu DOM
Entita je deklarace, která určuje název, který se má použít v souboru XML místo obsahu nebo značek. Existují dvě části na entity. Nejdřív musíte tie název, který nahrazení obsah s použitím deklarace entity. Deklarace entity je vytvořená pomocí `<!ENTITY name "value">` syntaxe v definici typu dokumentu (DTD) nebo schématu XML. Za druhé název definovaný v deklaraci entity následně použít v souboru XML. Pokud se použije v souboru XML, nazývá odkazu na entitu. Například následující deklarace entity deklaruje entity názvu `publisher` bylo možné přidružit obsah "Společnosti Microsoft Press".  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 Následující příklad ukazuje použití tuto deklaraci entity v kódu XML jako odkaz na entitu.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Některé analyzátory automaticky rozbalit entity, pokud dokument je načten do paměti. Proto když XML je načítán do paměti, deklarace entity jsou zapamatovaných a uložit. Pokud následně analyzátor nalezne `&;` znaky, které identifikovat odkaz obecné entity, analyzátor vyhledá tento název v tabulce deklarace entity. Odkaz na `&publisher;` je nahrazena obsah, který reprezentuje. Pomocí následující kód XML  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 rozbalení odkaz na entitu a nahraďte `&publisher;` s společnosti Microsoft Press obsah poskytuje následující rozšířené XML.  
  
 **Výstup**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Existují různé druhy entity. Následující diagram ukazuje rozpis typy entit a terminologii.  
  
 ![Vývojový diagram hierarchie typů entit](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")  
  
 Výchozí hodnota pro implementaci rozhraní Microsoft .NET Framework z XML modelu DOM (Document Object) je zachování odkazy entity a není rozbalit entity, pokud je načtený kód XML. Z toho vyplývá tohoto objektu je, jak dokument je načten do modelu DOM, **XmlEntityReference** uzlu, který obsahuje odkaz na proměnnou `&publisher;` je vytvořen, s podřízenými uzly představující obsah entity v DTD deklarován.  
  
 Pomocí `<!ENTITY publisher "Microsoft Press">` deklarace entity následující diagram znázorňuje **XmlEntity** a **XmlText** uzlů vytvořené z této deklarace.  
  
 ![uzlů vytvořené z deklarací entity](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 Rozdíly jsou v rozbaleném odkazy na entity, a pokud nejsou je nějaký rozdíl v jaké uzly se generují ve stromové struktuře DOM, v paměti. Rozdíl v uzlech, které jsou generovány, najdete v tématech [odkazy na Entity se zachovají](../../../../docs/standard/data/xml/entity-references-are-preserved.md) a [odkazy na Entity jsou rozšířené a není zachovaná](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Viz také  
 [XML Document Object Model (DOM).](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
