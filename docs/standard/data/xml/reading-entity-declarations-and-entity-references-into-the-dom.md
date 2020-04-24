---
title: Načtení deklarací entit a odkazů na entity do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
ms.openlocfilehash: fa650e75d7661eeafea74146f5cbb61878978575
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710398"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>Načtení deklarací entit a odkazů na entity do modelu DOM
Entita je deklarace, která uvádí název, který se má použít v XML místo obsahu nebo kódu. Existují dvě části pro entity. Nejprve je třeba spojit název nahrazujícího obsahu pomocí deklarace entity. Deklarace entity je vytvořena pomocí `<!ENTITY name "value">` syntaxe v dokumentu definice typu dokumentu (DTD) nebo schématu XML. V druhém případě je název definovaný v deklaraci entity následně použit v souboru XML. Při použití v kódu XML se nazývá odkaz na entitu. Například následující deklarace entity deklaruje entitu názvu `publisher` , která je přidružena k obsahu "Microsoft Press".  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 Následující příklad ukazuje použití této deklarace entity v XML jako odkaz na entitu.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Některé analyzátory automaticky rozbalí entity, když je dokument načten do paměti. Proto když je soubor XML čten do paměti, deklarace entit jsou zachovány a uloženy. Když analyzátor následně nalezne `&;` znaky, které identifikují obecný odkaz na entitu, analyzátor vyhledá tento název v tabulce deklarací entit. Odkaz `&publisher;` je nahrazen obsahem, který představuje. Pomocí následujícího kódu XML  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Rozbalením odkazu na entitu `&publisher;` a nahrazením pomocí obsahu Microsoft Press získáte následující rozšířené XML.  
  
 **Výstup**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Existuje mnoho druhů entit. Následující diagram znázorňuje rozdělení typů entit a terminologie.  
  
 ![Vývojový diagram hierarchie typů entit](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")  
  
 Výchozí hodnota pro implementaci model DOM (Document Object Model) XML (DOM) pro Microsoft .NET Framework je zachovat odkazy na entity a nerozšiřovat entity, když je XML načteno. Důvodem je, že když je dokument načten v modelu DOM, je vytvořen uzel **XmlEntityReference** obsahující referenční proměnnou `&publisher;` s podřízenými uzly, které představují obsah v entitě deklarované v souboru DTD.  
  
 Pomocí deklarace `<!ENTITY publisher "Microsoft Press">` entity následující diagram znázorňuje uzly **XmlEntity** a **XmlText** vytvořené z této deklarace.  
  
 ![uzly vytvořené z deklarace entity](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 Rozdíly při rozbalení odkazů na entity a v případě, že nejsou v nich rozdíl v tom, jaké uzly jsou generovány ve stromové struktuře modelu DOM, v paměti. Rozdíl v uzlech, které jsou generovány, je vysvětlen v tématech [odkazy na entity jsou zachovány](../../../../docs/standard/data/xml/entity-references-are-preserved.md) a [odkazy na entity jsou rozšířeny a nejsou zachovány](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
