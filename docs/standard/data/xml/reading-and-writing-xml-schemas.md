---
title: Čtení a zápis XML schémata
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b652adb27c3bb075fe86c09d7c9ab33511371279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="reading-and-writing-xml-schemas"></a>Čtení a zápis XML schémata
Schéma objektu modelu (SOM) rozhraní API lze použít ke čtení a zápisu definice schématu XML schémata jazyk (XSD) ze souborů nebo jiných zdrojů a XML schémata v paměti pomocí třídy v sestavení <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů, který mapování struktury definované v celém světě Doporučení schématu XML Wide Web Consortium (W3C).  
  
## <a name="reading-and-writing-xml-schemas"></a>Čtení a zápis XML schémata  
 <xref:System.Xml.Schema.XmlSchema> Třída poskytuje <xref:System.Xml.Schema.XmlSchema.Read%2A> a <xref:System.Xml.Schema.XmlSchema.Write%2A> metody pro čtení a zápis schémat XML. <xref:System.Xml.Schema.XmlSchema.Read%2A> Metoda vrátí <xref:System.Xml.Schema.XmlSchema> objekt reprezentující schématu XML a přijímá volitelný <xref:System.Xml.Schema.ValidationEventHandler> jako parametr pro zpracování schématu ověření upozornění a chyb zjištěných při načítání schématu XML.  
  
 <xref:System.Xml.Schema.XmlSchema.Write%2A> Metoda zapíše schémat XML do <xref:System.IO.Stream>, <xref:System.IO.TextWriter> a <xref:System.Xml.XmlWriter> objektů což může trvat volitelný <xref:System.Xml.XmlNamespaceManager> objekt jako parametr. <xref:System.Xml.XmlNamespaceManager> Slouží ke zpracování obory názvů v schématu XML. Další informace o <xref:System.Xml.XmlNamespaceManager> třídy najdete v tématu [Správa obory názvů v dokumentu XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).  
  
 Následující příklad kódu ukazuje čtení a zápis schémat XML z a do souboru. Příklad kódu trvá `example.xsd` souboru, přečte ji do <xref:System.Xml.Schema.XmlSchema> pomocí `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metoda a pak zapisuje do konzoly a nový soubor `new.xsd` souboru. Také poskytuje příklad kódu <xref:System.Xml.Schema.ValidationEventHandler> jako parametr, který se `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metodu ke zpracování všechna schématu ověření upozornění a chyb zjištěných při načítání schématu XML. Pokud <xref:System.Xml.Schema.ValidationEventHandler> není zadán (`null`), jsou hlášeny žádná varování nebo chyby.  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 V příkladu trvá `example.xsd` jako vstup.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Přehled Modelu objektu schématu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [Sestavování schémat XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [Procházení schémat XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [Úpravy schémat XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [Zahrnutí nebo import schémat XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Informační sada po kompilaci schématu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)  
 [Správa oborů názvů v dokumentu XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)
