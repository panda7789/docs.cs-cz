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
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>Načtení deklarací entit a odkazů na entity do modelu DOM
Entita je deklarace, která uvádí název, který se má použít v XML místo obsahu nebo kódu. Existují dvě části pro entity. Nejprve je třeba spojit název nahrazujícího obsahu pomocí deklarace entity. Deklarace entity je vytvořena pomocí `<!ENTITY name "value">` syntaxe v dokumentu definice typu dokumentu (DTD) nebo schématu XML. V druhém případě je název definovaný v deklaraci entity následně použit v souboru XML. Při použití v kódu XML se nazývá odkaz na entitu. Například následující deklarace entity deklaruje entitu názvu, `publisher` která je přidružena k obsahu "Microsoft Press".  
  
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
  
 Rozbalením odkazu na entitu a nahrazením `&publisher;` pomocí obsahu Microsoft Press získáte následující rozšířené XML.  
  
 **Výstup**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Existuje mnoho druhů entit. Následující diagram znázorňuje rozdělení typů entit a terminologie.  
  
 ![Vývojový diagram hierarchie typů entit](media/entity-hierarchy.gif "Entity_hierarchy")  
  
 Výchozí hodnota pro implementaci model DOM (Document Object Model) XML (DOM) pro Microsoft .NET Framework je zachovat odkazy na entity a nerozšiřovat entity, když je XML načteno. Důvodem je, že když je dokument načten v modelu DOM, je vytvořen uzel **XmlEntityReference** obsahující referenční proměnnou `&publisher;` s podřízenými uzly, které představují obsah v entitě deklarované v souboru DTD.  
  
 Pomocí `<!ENTITY publisher "Microsoft Press">` deklarace entity následující diagram znázorňuje uzly **XmlEntity** a **XmlText** vytvořené z této deklarace.  
  
 ![uzly vytvořené z deklarace entity](media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 Rozdíly při rozbalení odkazů na entity a v případě, že nejsou v nich rozdíl v tom, jaké uzly jsou generovány ve stromové struktuře modelu DOM, v paměti. Rozdíl v uzlech, které jsou generovány, je vysvětlen v tématech [odkazy na entity jsou zachovány](entity-references-are-preserved.md) a [odkazy na entity jsou rozšířeny a nejsou zachovány](entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
