---
title: Pravidla pro odvození typů a struktury uzlů schémat
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c2f28490203bcc4853bc6736ce7089f308bc275
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338706"
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a>Pravidla pro odvození typů a struktury uzlů schémat
Toto téma popisuje, jak procesu odvození schématu přeloží typy uzlů v dokumentu XML pro strukturu schématu XML definice jazyk (XSD).  
  
## <a name="element-inference-rules"></a>Element odvozených pravidel  
 Tato část popisuje odvozená pravidla pro deklarace prvků. Osm struktury deklarace prvků, které bude možné odvodit jsou:  
  
1. Element jednoduchý typ.  
  
2. Prázdný element  
  
3. Prázdný element s atributy  
  
4. Element s atributy a jednoduchý obsah  
  
5. Element s pořadím podřízených elementů  
  
6. Element s posloupnost podřízené prvky a atributy  
  
7. Element s pořadím voleb podřízených elementů  
  
8. Element s pořadím voleb podřízených elementů a atributů  
  
> [!NOTE]
>  Všechny `complexType` deklarace jsou odvozeny jako anonymní typy. Pouze globální element odvodit je kořenový element. všechny ostatní prvky jsou místní.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
### <a name="simple-typed-element"></a>Jednoduché typy – Element  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Prvek tučné zobrazuje schéma odvodit prvku jednoduchého typu.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a>Prázdný Element  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Prvek tučné zobrazuje pro prázdný element odvodit schéma.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a>Prázdný Element s atributy  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Tučně formátovaný prvky zobrazit schéma odvodit pro prázdný element s atributy.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a>Element s atributy a jednoduchý obsah  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Tučně formátovaný prvky zobrazit schéma odvodit pro element s atributy a jednoduchý obsah.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a>Element s pořadím podřízených elementů  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Tučně formátovaný prvky zobrazit schéma odvodit pro element s pořadím podřízených elementů.  
  
> [!NOTE]
>  I v případě, že element má pouze jeden podřízený element, je stále považovány za sekvenci.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a>Element s posloupnost podřízené prvky a atributy  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Tučně formátovaný prvky zobrazit schéma odvodit pro element s pořadím podřízených elementů a atributů.  
  
> [!NOTE]
>  I v případě, že element má pouze jeden podřízený element, je stále považovány za sekvenci.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a>Element s sekvenci a možnosti podřízených elementů  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Tučně formátovaný prvky zobrazit schéma odvodit pro element s sequence a choice podřízených elementů.  
  
> [!NOTE]
>  `maxOccurs` Atribut `xs:choice` prvek je nastaven na `"unbounded"` ve odvozené schématu.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a>Element s Sequence a Choice podřízených elementů a atributů  
 V následující tabulce jsou uvedeny vstup XML <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> metoda a schématu XML vygenerovat. Tučně formátovaný prvky zobrazit schéma odvodit pro element s sequence a choice podřízených elementů a atributů.  
  
> [!NOTE]
>  `maxOccurs` Atribut `xs:choice` prvek je nastaven na `"unbounded"` ve odvozené schématu.  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
|XML|Schéma|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a>Zpracování atributu  
 Pokaždé, když se nový atribut dochází v rámci uzlu, přidá se na definici odvozené uzlu s `use="required"`. Při příštím stejný uzel se nachází v instanci procesu odvození porovná atributy aktuální instance na základě těch již odvodit. Pokud již odvozené struktur chybí některé instance, `use="optional"` je přidán do definice atributu. Nové atributy jsou přidány do existující deklarace s `use="optional"`.  
  
### <a name="occurrence-constraints"></a>Omezení výskytu  
 Během procesu odvození schématu `minOccurs` a `maxOccurs` atributy jsou generovány pro odvozený komponenty schématu s hodnotami `"0"` nebo `"1"` a `"1"` nebo `"unbounded"`. Hodnoty `"1"` a `"unbounded"` se používají pouze tehdy, když hodnoty `"0"` a `"1"` nelze ověřit dokument XML (například pokud `MinOccurs="0"` přesně nepopisuje elementu, `minOccurs="1"` se používá).  
  
### <a name="mixed-content"></a>Smíšený obsah  
 Pokud element obsahuje smíšený obsah (například. text spolu s prvky), `mixed="true"` atribut je generována odvozené komplexní typ definice.  
  
## <a name="other-node-type-inference-rules"></a>Ostatní pravidla odvození typu uzlu  
 Následující tabulka popisuje odvozená pravidla pro zpracování instrukce, komentáře, odkaz na entitu, CDATA, typ dokumentu a uzly oboru názvů.  
  
|Typ uzlu|Překlad|  
|---------------|-----------------|  
|Instrukce pro zpracování|Ignorovat.|  
|Komentář|Ignorovat.|  
|Odkaz na entitu|<xref:System.Xml.Schema.XmlSchemaInference> Třídy nezpracovává odkazy na entity. Pokud dokument XML obsahuje odkazy na entity, budete muset použít čtečku, která rozšiřuje entity. Můžete například předat <xref:System.Xml.XmlTextReader> s <xref:System.Xml.XmlTextReader.EntityHandling%2A> nastavenou na <xref:System.Xml.EntityHandling.ExpandEntities> jako parametr. Pokud nedojde k odkazy na entity a čtečky Nerozbaluje entity, výjimka je vyvolání výjimky.|  
|CDATA|Žádné `<![CDATA[ … ]]` oddíly v dokumentu XML se odvodit jako `xs:string`.|  
|Typ dokumentu|Ignorovat.|  
|Jmenné prostory|Ignorovat.|  
  
 Další informace o procesu odvození schématu najdete v tématu [odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Schema.XmlSchemaInference>
- [Model objektu schématu (SOM) XML](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [Odvození schématu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)
- [Odvození schémat z dokumentů XML](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)
- [Pravidla pro odvození jednoduchých typů](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
