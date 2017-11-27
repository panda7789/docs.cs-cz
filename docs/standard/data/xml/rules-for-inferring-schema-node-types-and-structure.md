---
title: "Pravidla pro odvození typů uzlů schéma a struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c28c0f21b03fe7db014f118251363230a6ffc591
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a>Pravidla pro odvození typů uzlů schéma a struktura
Toto téma popisuje, jak proces odvození schématu překládá typy uzlů v dokumentu XML na strukturu schématu XML definition language (XSD).  
  
## <a name="element-inference-rules"></a>Element odvozená pravidla  
 Tato část popisuje odvozená pravidla pro deklarace na element. Existují osm struktury element deklarace, které bude odvodit:  
  
1.  Element jednoduchý typ.  
  
2.  Prázdný element  
  
3.  Prázdný element s atributy  
  
4.  Element s atributy a jednoduchý obsah  
  
5.  Element s pořadí podřízených elementů  
  
6.  Element s posloupností podřízené elementy a atributy  
  
7.  Element s posloupností volby podřízených elementů  
  
8.  Element s posloupností volby podřízených elementů a atributů  
  
> [!NOTE]
>  Všechny `complexType` deklarace jsou odvodit jako anonymní typy. Element jenom globální odvodit není kořenovým elementem; všechny další elementy jsou místní.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémata z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
### <a name="simple-typed-element"></a>Jednoduché typem elementu  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Element uveden tučně znázorňuje schéma odvodit jednoduchý typ elementu.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémata z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a>Prázdný Element  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Element uveden tučně znázorňuje schéma odvodit pro prázdný element.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémata z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a>Prázdný Element s atributy  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Elementy uveden tučně zobrazit schéma odvodit pro prázdný element s atributy.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémata z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a>Element s atributy a jednoduchý obsah  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Elementy uveden tučně zobrazit schéma odvodit pro element s atributy a jednoduchý obsah.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémata z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a>Element s pořadí podřízených elementů  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Elementy uveden tučně zobrazit schéma odvodit pro element s posloupností podřízené elementy.  
  
> [!NOTE]
>  I v případě, že element má pouze jeden podřízený element, se stále zpracovává jako sekvenci.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémata z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a>Element s posloupností podřízené elementy a atributy  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Elementy uveden tučně zobrazit schéma odvodit pro element s posloupností podřízené elementy a atributy.  
  
> [!NOTE]
>  I v případě, že element má pouze jeden podřízený element, se stále zpracovává jako sekvenci.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémata z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a>Element s sekvenci a možnosti podřízených elementů  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Elementy uveden tučně zobrazit schéma odvodit pro element s pořadí a výběr podřízených elementů.  
  
> [!NOTE]
>  `maxOccurs` Atribut `xs:choice` element je nastaven na hodnotu `"unbounded"` ve odvozené schématu.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémata z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a>Element s pořadí a volba podřízené elementy a atributy  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Elementy uveden tučně zobrazit schéma odvodit pro element s pořadí a výběr podřízených elementů a atributů.  
  
> [!NOTE]
>  `maxOccurs` Atribut `xs:choice` element je nastaven na hodnotu `"unbounded"` ve odvozené schématu.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémata z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a>Zpracování atributu  
 Vždy, když je nový atribut došlo v rámci uzlu, přidá se do odvozené definice uzlu se `use="required"`. Při příštím stejného uzlu se nachází v instanci procesu odvození se porovná atributy aktuální instance těmi, které jsou již odvodit. Pokud již odvozené ty, které chybí některé v instanci `use="optional"` je přidán do definice atributu. Nové atributy jsou přidány do existujících deklarace s `use="optional"`.  
  
### <a name="occurrence-constraints"></a>Omezení výskytu  
 Během procesu odvození schématu `minOccurs` a `maxOccurs` atributy jsou generovány pro odvozené komponenty schématu s hodnotami `"0"` nebo `"1"` a `"1"` nebo `"unbounded"`. Hodnoty `"1"` a `"unbounded"` se používají pouze tehdy, když hodnoty `"0"` a `"1"` nelze ověřit v dokumentu XML (například pokud `MinOccurs="0"` přesně nepopisuje elementu, `minOccurs="1"` se používá).  
  
### <a name="mixed-content"></a>Smíšený obsah  
 Pokud element obsahuje smíšený obsah (například. text spolu s prvky), `mixed="true"` atribut se generuje pro definici odvozené komplexního typu.  
  
## <a name="other-node-type-inference-rules"></a>Další uzel typu odvozená pravidla  
 Následující tabulka popisuje odvozená pravidla pro zpracování instrukcí, komentáře, odkaz na entitu, CDATA, typ dokumentu a uzly oboru názvů.  
  
|Typ uzlu|Překlad|  
|---------------|-----------------|  
|Zpracování instrukcí|Ignorovat.|  
|Komentář|Ignorovat.|  
|Odkaz na entitu|<xref:System.Xml.Schema.XmlSchemaInference> Třída nezpracovává odkazy na entity. Pokud dokument XML obsahuje odkazy na entity, budete muset použít čtečka čipových karet, které zasahuje entity. Například můžete předat <xref:System.Xml.XmlTextReader> s <xref:System.Xml.XmlTextReader.EntityHandling%2A> vlastnost nastavena na hodnotu <xref:System.Xml.EntityHandling.ExpandEntities> jako parametr. Pokud došlo k odkazy na entity a čtečky nerozšiřuje entity, je výjimku throw.|  
|CDATA|Všechny `<![CDATA[ … ]]` oddíly v dokumentu XML se odvodit jako `xs:string`.|  
|Typ dokumentu|Ignorovat.|  
|Obory názvů|Ignorovat.|  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémata z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Schema.XmlSchemaInference>  
 [Objektový Model schématu XML (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [Odvození schématu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 [Odvození schémata z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)  
 [Pravidla pro jednoduché typy odvození](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
