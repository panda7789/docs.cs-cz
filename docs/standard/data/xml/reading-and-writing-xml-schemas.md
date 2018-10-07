---
title: Čtení a zápis schémat XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 241ff40448c3dca2846f9e420dc7df41427dc79d
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841200"
---
# <a name="reading-and-writing-xml-schemas"></a>Čtení a zápis schémat XML
Schéma objektu modelu (SOM) rozhraní API lze použít ke čtení a zápis schémata jazyk (XSD) definice schématu XML ze souborů nebo jiných zdrojů a sestavení XML schémata v paměti pomocí tříd v <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů, které mapují na struktury definované v celém světě Wide Web Consortium (W3C) doporučení schématu XML.  
  
## <a name="reading-and-writing-xml-schemas"></a>Čtení a zápis schémat XML  
 <xref:System.Xml.Schema.XmlSchema> Třída poskytuje <xref:System.Xml.Schema.XmlSchema.Read%2A> a <xref:System.Xml.Schema.XmlSchema.Write%2A> metody pro čtení a zápis schémat XML. <xref:System.Xml.Schema.XmlSchema.Read%2A> Vrátí metoda <xref:System.Xml.Schema.XmlSchema> objekt představující schématu XML a přijímá volitelný <xref:System.Xml.Schema.ValidationEventHandler> jako parametr pro zpracování upozornění při ověřování schématu a při čtení schématu XML došlo k chybám.  
  
 <xref:System.Xml.Schema.XmlSchema.Write%2A> Metoda zapíše schémat XML pro <xref:System.IO.Stream>, <xref:System.IO.TextWriter> a <xref:System.Xml.XmlWriter> objektů a můžete provést volitelný <xref:System.Xml.XmlNamespaceManager> objektu jako parametr. <xref:System.Xml.XmlNamespaceManager> Se používá ke zpracování obory názvů v schématu XML. Další informace o <xref:System.Xml.XmlNamespaceManager> najdete v tématu [Správa oborů názvů v dokumentu XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).  
  
 Následující příklad kódu ukazuje čtení a zápis schémat XML z a do souboru. Příklad kódu používá `example.xsd` souboru, načte ji do <xref:System.Xml.Schema.XmlSchema> pomocí `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metoda a pak zapíše do konzoly a nový soubor `new.xsd` souboru. Příklad kódu také poskytuje <xref:System.Xml.Schema.ValidationEventHandler> jako parametr `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metodu ke zpracování všech upozornění při ověřování schématu nebo při čtení schématu XML došlo k chybám. Pokud <xref:System.Xml.Schema.ValidationEventHandler> nezadáte (`null`), žádná upozornění ani chyby jsou hlášeny.  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 V příkladu přebírá `example.xsd` jako vstup.  
  
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
