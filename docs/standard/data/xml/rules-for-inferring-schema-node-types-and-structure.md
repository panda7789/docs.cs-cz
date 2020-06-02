---
title: Pravidla pro odvození typů a struktury uzlů schémat
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
ms.openlocfilehash: 381c5fbd3823514de98b38840b8259a417e48fb8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289080"
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a>Pravidla pro odvození typů a struktury uzlů schémat
Toto téma popisuje, jak proces odvození schématu překládá typy uzlů v dokumentu XML do struktury XSD (XML Schema Definition Language).  
  
## <a name="element-inference-rules"></a>Odvozená pravidla elementu  
 Tato část popisuje odvozená pravidla pro deklarace elementů. Existuje osm struktur deklarací elementů, které budou odvozeny:  
  
1. Element jednoduchého typu  
  
2. Prázdný element  
  
3. Prázdný element s atributy  
  
4. Element s atributy a jednoduchým obsahem  
  
5. Element se sekvencí podřízených elementů  
  
6. Element se sekvencí podřízených elementů a atributů  
  
7. Element s posloupností možností podřízených elementů  
  
8. Element s posloupností možností podřízených elementů a atributů  
  
> [!NOTE]
> Všechny `complexType` deklarace jsou odvozeny jako anonymní typy. Jediným globálním prvkem, který je odvozen, je kořenový element; všechny ostatní prvky jsou místní.  
  
 Další informace o procesu odvození schématu naleznete v tématu odvození [schémat z dokumentů XML](inferring-schemas-from-xml-documents.md).  
  
### <a name="simple-typed-element"></a>Element jednoduchého typu  
 Následující tabulka ukazuje vstup XML do <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metody a schéma XML je vygenerováno. Tučný element ukazuje schéma odvozeno pro element jednoduchého typu.  
  
 Další informace o procesu odvození schématu naleznete v tématu odvození [schémat z dokumentů XML](inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a>Prázdný element  
 Následující tabulka ukazuje vstup XML do <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metody a schéma XML je vygenerováno. Tučný element ukazuje schéma odvozeno pro prázdný element.  
  
 Další informace o procesu odvození schématu naleznete v tématu odvození [schémat z dokumentů XML](inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a>Prázdný element s atributy  
 Následující tabulka ukazuje vstup XML do <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metody a schéma XML je vygenerováno. Tučné prvky znázorňují schéma odvozené pro prázdný element s atributy.  
  
 Další informace o procesu odvození schématu naleznete v tématu odvození [schémat z dokumentů XML](inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a>Element s atributy a jednoduchým obsahem  
 Následující tabulka ukazuje vstup XML do <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metody a schéma XML je vygenerováno. Tučné prvky znázorňují schéma odvoditelné pro element s atributy a jednoduchým obsahem.  
  
 Další informace o procesu odvození schématu naleznete v tématu odvození [schémat z dokumentů XML](inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a>Element se sekvencí podřízených elementů  
 Následující tabulka ukazuje vstup XML do <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metody a schéma XML je vygenerováno. Tučné prvky znázorňují schéma odvozené pro element se sekvencí podřízených elementů.  
  
> [!NOTE]
> I v případě, že element má pouze jeden podřízený prvek, je stále považován za sekvenci.  
  
 Další informace o procesu odvození schématu naleznete v tématu odvození [schémat z dokumentů XML](inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a>Element se sekvencí podřízených elementů a atributů  
 Následující tabulka ukazuje vstup XML do <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metody a schéma XML je vygenerováno. Tučné prvky znázorňují schéma odvozené pro element se sekvencí podřízených elementů a atributů.  
  
> [!NOTE]
> I v případě, že element má pouze jeden podřízený prvek, je stále považován za sekvenci.  
  
 Další informace o procesu odvození schématu naleznete v tématu odvození [schémat z dokumentů XML](inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a>Element s sekvencí a volbami podřízených elementů  
 Následující tabulka ukazuje vstup XML do <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metody a schéma XML je vygenerováno. Tučné prvky znázorňují schéma odvozené pro element se sekvencí a volbou podřízených elementů.  
  
> [!NOTE]
> `maxOccurs`Atribut `xs:choice` prvku je nastaven na hodnotu `"unbounded"` v odvozeném schématu.  
  
 Další informace o procesu odvození schématu naleznete v tématu odvození [schémat z dokumentů XML](inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a>Element s sekvencí a volbou podřízených elementů a atributů  
 Následující tabulka ukazuje vstup XML do <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metody a schéma XML je vygenerováno. Tučné prvky znázorňují schéma odvozené pro element se sekvencí a volbou podřízených elementů a atributů.  
  
> [!NOTE]
> `maxOccurs`Atribut `xs:choice` prvku je nastaven na hodnotu `"unbounded"` v odvozeném schématu.  
  
 Další informace o procesu odvození schématu naleznete v tématu odvození [schémat z dokumentů XML](inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a>Zpracování atributů  
 Vždy, když je v rámci uzlu zjištěn nový atribut, je přidán do odvozené definice uzlu s `use="required"` . Při dalším výskytu stejného uzlu v instanci budou procesy odvození porovnávat atributy aktuální instance s těmi, které již byly odvozeny. Pokud v instanci chybí některé z již odvozených těch, `use="optional"` je přidána do definice atributu. Nové atributy jsou přidány do existujících deklarací pomocí `use="optional"` .  
  
### <a name="occurrence-constraints"></a>Omezení výskytu  
 Během procesu odvození schématu `minOccurs` `maxOccurs` jsou generovány atributy a pro odvozené komponenty schématu s hodnotami `"0"` nebo `"1"` a `"1"` nebo `"unbounded"` . Hodnoty `"1"` a `"unbounded"` jsou použity pouze v případě, že hodnoty `"0"` a `"1"` nelze ověřit dokument XML (například pokud `MinOccurs="0"` není přesně popsán prvek, `minOccurs="1"` je použit).  
  
### <a name="mixed-content"></a>Smíšený obsah  
 Pokud element obsahuje smíšený obsah (například text promísený s elementy), `mixed="true"` atribut je vygenerován pro odvozenou definici komplexního typu.  
  
## <a name="other-node-type-inference-rules"></a>Pravidla odvození typu uzlu  
 Následující tabulka popisuje odvozená pravidla pro zpracování instrukcí, komentářů, odkazů na entity, CDATA, typu dokumentu a uzlů oboru názvů.  
  
|Typ uzlu|Překlad|  
|---------------|-----------------|  
|Instrukce pro zpracování|Přeskočen.|  
|Komentář|Přeskočen.|  
|Referenční údaje k entitám|<xref:System.Xml.Schema.XmlSchemaInference>Třída nezpracovává odkazy na entity. Pokud dokument XML obsahuje odkazy na entity, je nutné použít čtecí modul, který rozšiřuje entity. Například můžete předat <xref:System.Xml.XmlTextReader> s <xref:System.Xml.XmlTextReader.EntityHandling%2A> vlastností nastavenou <xref:System.Xml.EntityHandling.ExpandEntities> jako parametr. Pokud jsou nalezeny odkazy na entity a čtenář nerozšiřuje entity, je vyvolána výjimka.|  
|CDATA|Všechny `<![CDATA[ … ]]` oddíly v dokumentu XML budou odvozené jako `xs:string` .|  
|Typ dokumentu|Přeskočen.|  
|Obory názvů|Přeskočen.|  
  
 Další informace o procesu odvození schématu naleznete v tématu odvození [schémat z dokumentů XML](inferring-schemas-from-xml-documents.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Schema.XmlSchemaInference>
- [Model objektu schématu (SOM) XML](xml-schema-object-model-som.md)
- [Odvození schématu XML](inferring-an-xml-schema.md)
- [Odvození schémat z dokumentů XML](inferring-schemas-from-xml-documents.md)
- [Pravidla pro odvození jednoduchých typů](rules-for-inferring-simple-types.md)
