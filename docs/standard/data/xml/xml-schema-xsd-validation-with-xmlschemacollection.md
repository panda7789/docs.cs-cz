---
title: "Ověření schématu (XSD) XML s kolekci XmlSchemaCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ad0b5717-3d32-41ad-a4d7-072c3e492b82
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ebe8a55cd5dd80be10553948c7765f81429c0957
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xml-schema-xsd-validation-with-xmlschemacollection"></a>Ověření schématu (XSD) XML s kolekci XmlSchemaCollection
Můžete použít <xref:System.Xml.Schema.XmlSchemaCollection> ověřit dokument XML pomocí schématu XML definition language (XSD) schémat. <xref:System.Xml.Schema.XmlSchemaCollection> Díky ukládání schémata v kolekci, takže nejsou načtena do paměti dojde k ověření jednotlivých časové zvyšuje výkon. Pokud schéma existuje v kolekci schémat `schemaLocation` atribut slouží k vyhledání schématu v kolekci.  
  
> [!IMPORTANT]
>  <xref:System.Xml.Schema.XmlSchemaCollection> Třída je zastaralá a nahradila s <xref:System.Xml.Schema.XmlSchemaSet> třídy. Další informace o <xref:System.Xml.Schema.XmlSchemaSet> najdete třída [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).  
  
 Následující příklad ukazuje kořenový element datového souboru.  
  
```xml  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:bookstore-schema"  
    elementFormDefault="qualified"  
    targetNamespace="urn:bookstore-schema">  
```  
  
 V tomto příkladu hodnotu `targetNamespace` atribut je `urn:bookstore-schema`, což je stejný obor názvů, který se používá při přidávání schéma tak, aby <xref:System.Xml.Schema.XmlSchemaCollection>.  
  
 Následující příklad kódu přidá schéma XML <xref:System.Xml.Schema.XmlSchemaCollection>.  
  
```vb  
Dim xsc As New XmlSchemaCollection()  
' XML Schema.  
xsc.Add("urn:bookstore-schema", schema)   
reader = New XmlTextReader(filename)  
vreader = New XmlValidatingReader(reader)  
vreader.Schemas.Add(xsc)  
```  
  
```csharp  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
// XML Schema.  
xsc.Add("urn:bookstore-schema", schema);  
reader = new XmlTextReader (filename);  
vreader = new XmlValidatingReader (reader);  
vreader.Schemas.Add(xsc);  
```  
  
 `targetNamespace` Atribut se zpravidla používá, když přidáte `namespaceURI` vlastnost v <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaCollection>. Můžete zadat odkaz s hodnotou null před přidáním schéma tak, aby <xref:System.Xml.Schema.XmlSchemaCollection>. Prázdný řetězec ("") se má používat pro schémata bez oboru názvů. <xref:System.Xml.Schema.XmlSchemaCollection> Může mít pouze jedno schéma bez oboru názvů.  
  
 Následující příklad kódu přidá schématu XML HeadCount.xsd, na <xref:System.Xml.Schema.XmlSchemaCollection> a ověří HeadCount.xml.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Schema  
  
Namespace ValidationSample  
  
   Class Sample  
  
      Public Shared Sub Main()  
         Dim tr As New XmlTextReader("HeadCount.xml")  
         Dim vr As New XmlValidatingReader(tr)  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd")  
         vr.ValidationType = ValidationType.Schema  
         AddHandler vr.ValidationEventHandler, AddressOf ValidationHandler  
  
         While vr.Read()  
         End While  
         Console.WriteLine("Validation finished")  
      End Sub  
      ' Main  
  
      Public Shared Sub ValidationHandler(sender As Object, args As ValidationEventArgs)  
         Console.WriteLine("***Validation error")  
         Console.WriteLine("Severity:{0}", args.Severity)  
         Console.WriteLine("Message:{0}", args.Message)  
      End Sub  
      ' ValidationHandler  
   End Class  
   ' Sample  
End Namespace  
' ValidationSample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Schema;  
  
namespace ValidationSample  
{  
   class Sample  
   {  
      public static void Main()  
      {  
         XmlTextReader tr = new XmlTextReader("HeadCount.xml");  
         XmlValidatingReader vr = new XmlValidatingReader(tr);  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd");  
         vr.ValidationType = ValidationType.Schema;  
         vr.ValidationEventHandler += new ValidationEventHandler (ValidationHandler);  
  
         while(vr.Read());  
         Console.WriteLine("Validation finished");  
      }  
  
      public static void ValidationHandler(object sender, ValidationEventArgs args)  
      {  
         Console.WriteLine("***Validation error");  
         Console.WriteLine("\tSeverity:{0}", args.Severity);  
         Console.WriteLine("\tMessage  :{0}", args.Message);  
      }  
   }  
}  
```  
  
 Následující část popisuje obsah souboru vstupního souboru, HeadCount.xml, který má být ověřen.  
  
```xml  
<!--Load HeadCount.xsd in SchemaCollection for Validation-->  
<hc:HeadCount xmlns:hc='xsdHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</hc:HeadCount>  
```  
  
 Následující část popisuje obsah souboru schématu XML, HeadCount.xsd, chcete-li ověřit pomocí.  
  
```xml  
<xs:schema xmlns="xsdHeadCount" targetNamespace="xsdHeadCount" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name='HeadCount' type="HEADCOUNT"/>  
   <xs:complexType name="HEADCOUNT">  
      <xs:sequence>  
         <xs:element name='Name' type='xs:string' maxOccurs='unbounded'/>  
      </xs:sequence>  
      <xs:attribute name='division' type='xs:int' use='optional' default='8'/>  
   </xs:complexType>  
</xs:schema>  
```  
  
 Následující příklad kódu vytvoří <xref:System.Xml.XmlValidatingReader> , která má <xref:System.Xml.XmlTextReader>. Vstupní soubor, sample4.xml, bude ověřeno schématu XML sample4.xsd.  
  
```vb  
Dim tr As New XmlTextReader("sample4.xml")  
Dim vr As New XmlValidatingReader(tr)  
vr.ValidationType = ValidationType.Schema  
vr.Schemas.Add("datatypesTest", "sample4.xsd")  
AddHandler vr.ValidationEventHandler, AddressOf ValidationCallBack  
While vr.Read()  
   Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name)  
End While  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("sample4.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
vr.ValidationType = ValidationType.Schema;  
        vr.Schemas.Add("datatypesTest", "sample4.xsd");  
vr.ValidationEventHandler += new ValidationEventHandler(ValidationCallBack);  
while(vr.Read()) {  
    Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name);  
    }  
```  
  
 Následující část popisuje obsah souboru vstupního souboru, sample4.xml, který má být ověřen.  
  
```xml  
<datatypes xmlns="datatypesTest">  
    <number>  
        <number_1>123</number_1>  
    </number>  
</datatypes>  
```  
  
 Následující část popisuje obsah souboru schématu XML, sample4.xsd, chcete-li ověřit pomocí.  
  
```xml  
<xs:schema   
    xmlns:xs="http://www.w3.org/2001/XMLSchema"   
    xmlns:tns="datatypesTest"   
    targetNamespace="datatypesTest"  
    elementFormDefault="qualified">  
  
<xs:element name = "datatypes">  
  <xs:complexType>  
    <xs:all>  
        <xs:element name="number">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="number_1" type="xs:decimal" maxOccurs="unbounded"/>  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
    </xs:all>  
  </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlParserContext>  
 <xref:System.Xml.XmlValidatingReader.ValidationEventHandler?displayProperty=nameWithType>  
 <xref:System.Xml.XmlValidatingReader.Schemas%2A?displayProperty=nameWithType>  
 [Schéma kolekci XmlSchemaCollection kompilace](../../../../docs/standard/data/xml/xmlschemacollection-schema-compilation.md)
