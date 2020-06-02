---
title: Čtení ze schémat XML a zápis do nich
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: bf1078d52f5e9056da6b28acc8dd2fc257eb3636
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291250"
---
# <a name="reading-and-writing-xml-schemas"></a>Čtení ze schémat XML a zápis do nich
Rozhraní API modelu modelu objektu schématu (SOM) lze použít ke čtení a zápisu schémat XML Schema Definition Language (XSD) ze souborů nebo jiných zdrojů a sestavení schémat XML v paměti pomocí tříd v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů, které jsou mapovány na struktury definované v doporučeních schématu xml konsorcium World Wide Web (W3C).  
  
## <a name="reading-and-writing-xml-schemas"></a>Čtení ze schémat XML a zápis do nich  
 <xref:System.Xml.Schema.XmlSchema>Třída poskytuje <xref:System.Xml.Schema.XmlSchema.Read%2A> <xref:System.Xml.Schema.XmlSchema.Write%2A> metody a pro čtení a zápis schémat XML. <xref:System.Xml.Schema.XmlSchema.Read%2A>Metoda vrátí <xref:System.Xml.Schema.XmlSchema> objekt představující schéma XML a převezme volitelné <xref:System.Xml.Schema.ValidationEventHandler> jako parametr pro zpracování upozornění ověřování schématu a chyb zjištěných při čtení schématu XML.  
  
 <xref:System.Xml.Schema.XmlSchema.Write%2A>Metoda zapisuje schémata XML do <xref:System.IO.Stream> <xref:System.IO.TextWriter> objektů a <xref:System.Xml.XmlWriter> objekty a může <xref:System.Xml.XmlNamespaceManager> jako parametr převzít volitelný objekt. <xref:System.Xml.XmlNamespaceManager>Slouží ke zpracování oborů názvů, které byly zjištěny ve schématu XML. Další informace o <xref:System.Xml.XmlNamespaceManager> třídě naleznete v tématu [Správa oborů názvů v dokumentu XML](managing-namespaces-in-an-xml-document.md).  
  
 Následující příklad kódu ukazuje čtení a zápis XML schémat z a do souboru. Příklad kódu převezme `example.xsd` soubor, přečte jej do <xref:System.Xml.Schema.XmlSchema> objektu pomocí `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metody a pak zapíše soubor do konzoly a do nového `new.xsd` souboru. Příklad kódu také poskytuje <xref:System.Xml.Schema.ValidationEventHandler> jako parametr `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metodě pro zpracování jakýchkoli upozornění ověřování schématu nebo chyb, ke kterým došlo při čtení schématu XML. Pokud <xref:System.Xml.Schema.ValidationEventHandler> parametr není zadán ( `null` ), nejsou hlášeny žádná upozornění ani chyby.  
  
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
  
## <a name="see-also"></a>Viz také

- [Přehled Modelu objektu schématu XML](xml-schema-object-model-overview.md)
- [Sestavování schémat XML](building-xml-schemas.md)
- [Procházení schémat XML](traversing-xml-schemas.md)
- [Úpravy schémat XML](editing-xml-schemas.md)
- [Zahrnutí nebo import schémat XML](including-or-importing-xml-schemas.md)
- [XmlSchemaSet pro kompilaci schématu](xmlschemaset-for-schema-compilation.md)
- [Informační sada po kompilaci schématu](post-schema-compilation-infoset.md)
- [Správa oborů názvů v dokumentu XML](managing-namespaces-in-an-xml-document.md)
