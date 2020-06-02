---
title: Ověření schématu XML (XSD) s třídou XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ad0b5717-3d32-41ad-a4d7-072c3e492b82
ms.openlocfilehash: 2ff8a8b85c3bfa594bd958a9a3688380885e0426
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290302"
---
# <a name="xml-schema-xsd-validation-with-xmlschemacollection"></a>Ověření schématu XML (XSD) s třídou XmlSchemaCollection
Můžete použít <xref:System.Xml.Schema.XmlSchemaCollection> k ověření dokumentu XML proti schématům XML Schema Definition Language (XSD). <xref:System.Xml.Schema.XmlSchemaCollection>Zlepšuje výkon tím, že ukládá schémata do kolekce, takže nejsou načteny do paměti pokaždé, když dojde k ověření. Pokud schéma existuje v kolekci schémat, `schemaLocation` je použit atribut k vyhledání schématu v kolekci.  
  
> [!IMPORTANT]
> <xref:System.Xml.Schema.XmlSchemaCollection>Třída je nyní zastaralá a byla nahrazena <xref:System.Xml.Schema.XmlSchemaSet> třídou. Další informace o <xref:System.Xml.Schema.XmlSchemaSet> třídě naleznete v tématu Třída [XmlSchemaSet pro kompilaci schématu](xmlschemaset-for-schema-compilation.md).  
  
 Následující příklad ukazuje kořenový prvek datového souboru.  
  
```xml  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:bookstore-schema"  
    elementFormDefault="qualified"  
    targetNamespace="urn:bookstore-schema">  
```  
  
 V tomto příkladu je hodnota `targetNamespace` atributu `urn:bookstore-schema` , což je stejný obor názvů, který se používá při přidávání schématu do <xref:System.Xml.Schema.XmlSchemaCollection> .  
  
 Následující příklad kódu přidá schéma XML do <xref:System.Xml.Schema.XmlSchemaCollection> .  
  
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
  
 `targetNamespace`Atribut je obecně používán při přidání `namespaceURI` vlastnosti do <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metody pro <xref:System.Xml.Schema.XmlSchemaCollection> . Před přidáním schématu do nástroje lze zadat odkaz s hodnotou null <xref:System.Xml.Schema.XmlSchemaCollection> . Pro schémata bez oboru názvů by měl být použit prázdný řetězec (""). <xref:System.Xml.Schema.XmlSchemaCollection>Může obsahovat pouze jedno schéma bez oboru názvů.  
  
 Následující příklad kódu přidá schéma XML, #. xsd, do <xref:System.Xml.Schema.XmlSchemaCollection> a ověří soubor. XML.  
  
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
  
 Následující text objednává obsah vstupního souboru... XML, který se má ověřit.  
  
```xml  
<!--Load HeadCount.xsd in SchemaCollection for Validation-->  
<hc:HeadCount xmlns:hc='xsdHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</hc:HeadCount>  
```  
  
 Následující text popisuje obsah souboru schématu XML, soubor. xsd, který má být ověřen proti.  
  
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
  
 Následující příklad kódu vytvoří objekt <xref:System.Xml.XmlValidatingReader> , který převezme <xref:System.Xml.XmlTextReader> . Vstupní soubor sample4. XML je ověřen proti schématu XML sample4. xsd.  
  
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
  
 Následující text objednává obsah vstupního souboru sample4. XML, který má být ověřen.  
  
```xml  
<datatypes xmlns="datatypesTest">  
    <number>  
        <number_1>123</number_1>  
    </number>  
</datatypes>  
```  
  
 Následující text popisuje obsah souboru schématu XML sample4. xsd, který má být ověřen proti.  
  
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

- <xref:System.Xml.XmlParserContext>
- <xref:System.Xml.XmlValidatingReader.ValidationEventHandler?displayProperty=nameWithType>
- <xref:System.Xml.XmlValidatingReader.Schemas%2A?displayProperty=nameWithType>
- [Kompilace schématu XmlSchemaCollection](xmlschemacollection-schema-compilation.md)
