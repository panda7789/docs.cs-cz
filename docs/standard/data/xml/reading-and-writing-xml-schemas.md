---
title: Čtení ze schémat XML a zápis do nich
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: 889c5f85a2ea3fc08dadefda5509de0fcfab76ec
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710411"
---
# <a name="reading-and-writing-xml-schemas"></a>Čtení ze schémat XML a zápis do nich
Rozhraní API modelu modelu objektu schématu (SOM) je možné použít ke čtení a zápisu schémat XML Schema Definition Language (XSD) ze souborů nebo jiných zdrojů a sestavení schémat XML v paměti pomocí tříd v oboru názvů <xref:System.Xml.Schema?displayProperty=nameWithType>, který se mapuje na struktury definované v doporučeních schématu XML konsorcium World Wide Web (W3C).  
  
## <a name="reading-and-writing-xml-schemas"></a>Čtení ze schémat XML a zápis do nich  
 Třída <xref:System.Xml.Schema.XmlSchema> poskytuje metody <xref:System.Xml.Schema.XmlSchema.Read%2A> a <xref:System.Xml.Schema.XmlSchema.Write%2A> pro čtení a zápis schémat XML. Metoda <xref:System.Xml.Schema.XmlSchema.Read%2A> vrátí objekt <xref:System.Xml.Schema.XmlSchema> reprezentující schéma XML a převezme volitelné <xref:System.Xml.Schema.ValidationEventHandler> jako parametr pro zpracování upozornění ověřování schématu a chyby zjištěné při čtení schématu XML.  
  
 Metoda <xref:System.Xml.Schema.XmlSchema.Write%2A> zapisuje schémata XML do <xref:System.IO.Stream>, <xref:System.IO.TextWriter> a <xref:System.Xml.XmlWriter> objektů a může převzít volitelný objekt <xref:System.Xml.XmlNamespaceManager> jako parametr. <xref:System.Xml.XmlNamespaceManager> se používá ke zpracování oborů názvů zjištěných ve schématu XML. Další informace o třídě <xref:System.Xml.XmlNamespaceManager> naleznete v tématu [Správa oborů názvů v dokumentu XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).  
  
 Následující příklad kódu ukazuje čtení a zápis XML schémat z a do souboru. Příklad kódu přebírá soubor `example.xsd`, čte ho do objektu <xref:System.Xml.Schema.XmlSchema> pomocí metody `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> a pak zapíše soubor do konzoly a do nového souboru `new.xsd`. Příklad kódu také poskytuje <xref:System.Xml.Schema.ValidationEventHandler> jako parametr pro metodu `static`<xref:System.Xml.Schema.XmlSchema.Read%2A>, která zpracovává všechna upozornění ověřování schématu nebo chyby zjištěné při čtení schématu XML. Pokud není zadán <xref:System.Xml.Schema.ValidationEventHandler> (`null`), nejsou hlášeny žádná upozornění ani chyby.  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 Příklad přebírá `example.xsd` jako vstup.  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled Modelu objektu schématu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Procházení schémat XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Úpravy schémat XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [Zahrnutí nebo import schémat XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Informační sada po kompilaci schématu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
- [Správa oborů názvů v dokumentu XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)
