---
title: Čtení deklarací entit a odkazy na Entity do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e30b52b8cdfb4d185687d58c80f4475730031c86
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44031750"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>Čtení deklarací entit a odkazy na Entity do modelu DOM
Entita je deklarace, která uvádí název, který se má použít v souboru XML místo obsahu nebo značky. Existují dvě části k entitám. Nejprve musíte tie název pro nahrazení obsahu pomocí deklarace entity. Vytvoří pomocí deklarace entity `<!ENTITY name "value">` syntaxe v definici typu dokumentu (DTD) nebo schématu XML. Za druhé název definovaný v deklaraci entity se následně používá v souboru XML. Při použití v souboru XML, je volána odkazu na entitu. Například následující deklaraci entita deklaruje entity názvu `publisher` jsou spojeny s obsahem "Microsoft Press".  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 Následující příklad ukazuje použití této deklarace entity v XML jako odkaz na entitu.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Některé analyzátorů automaticky rozšíří entity dokumentu je načtena do paměti. Proto když XML je načítána do paměti, entity prohlášení jsou zapamatovaných a uložit. Pokud následně analyzátor nalezne `&;` znaků, které identifikovat odkaz na obecnou entitu, analyzátor vyhledá tímto názvem v tabulce entity prohlášení. Odkaz na `&publisher;` nahrazuje obsah, který představuje. Pomocí následující kód XML  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 rozbalení odkaz na entitu a nahrazování `&publisher;` díky Microsoft Press obsah poskytuje následující rozšířené kód XML.  
  
 **Output**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Existují různé druhy entit. Následující diagram znázorňuje rozdělení typy entit a terminologie.  
  
 ![Vývojový diagram hierarchie typů entit](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")  
  
 Ve výchozím nastavení pro implementaci rozhraní Microsoft .NET Framework z XML Document Object Model (DOM) je zachování odkazy na entity a ne rozbalit entity při načtení XML. Důsledkem tohoto je, že jako dokument se načte do modelu DOM, **XmlEntityReference** uzlu, který obsahuje odkaz na proměnnou `&publisher;` je vytvořen, s podřízenými uzly představující obsah entity deklarované v DTD.  
  
 Použití `<!ENTITY publisher "Microsoft Press">` entity prohlášení, následující diagram ukazuje **XmlEntity** a **XmlText** uzlů vytvořené z této deklarace.  
  
 ![uzlů vytvořené z entity prohlášení](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 Rozdíly při odkazy na entity rozbaleny, a pokud nejsou různá v jakých uzlů se generují ve stromové struktuře modelu DOM, v paměti. Rozdíl v uzlech, které jsou generovány je vysvětleno v tématech [odkazy na Entity jsou zachovány](../../../../docs/standard/data/xml/entity-references-are-preserved.md) a [odkazy na Entity jsou rozšířené a Nezachované](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
