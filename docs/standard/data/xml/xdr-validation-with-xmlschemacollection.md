---
title: "Ověření XDR s kolekci XmlSchemaCollection"
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
ms.assetid: 00833027-1428-4586-83c1-42f5de3323d1
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f875169d43a2f733050b46c76cea0891b4cfabf7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xdr-validation-with-xmlschemacollection"></a><span data-ttu-id="f409f-102">Ověření XDR s kolekci XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="f409f-102">XDR Validation with XmlSchemaCollection</span></span>
<span data-ttu-id="f409f-103">Pokud je schéma XML-Data Reduced (XDR) jsou ověření proti uložen v **kolekci XmlSchemaCollection**, je přidružen obor názvů zadaný identifikátor URI při schématu byla přidána do kolekce.</span><span class="sxs-lookup"><span data-stu-id="f409f-103">If the XML-Data Reduced (XDR) schema you are validating against is stored in the **XmlSchemaCollection**, it is associated with the namespace URI specified when the schema was added to the collection.</span></span> <span data-ttu-id="f409f-104">**Třídy XmlValidatingReader** identifikátor URI oboru názvů v dokumentu XML se mapuje na schéma, která odpovídá této URI v kolekci.</span><span class="sxs-lookup"><span data-stu-id="f409f-104">**XmlValidatingReader** maps the namespace URI in the XML document to the schema that corresponds to that URI in the collection.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f409f-105"><xref:System.Xml.Schema.XmlSchemaCollection> Třída je zastaralá a nahradila s <xref:System.Xml.Schema.XmlSchemaSet> třídy.</span><span class="sxs-lookup"><span data-stu-id="f409f-105">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="f409f-106">Další informace o <xref:System.Xml.Schema.XmlSchemaSet> najdete třída [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="f409f-106">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
 <span data-ttu-id="f409f-107">Například, pokud je kořenový element dokumentu XML `<bookstore xmlns="urn:newbooks-schema">`, když je schéma přidán do **kolekci XmlSchemaCollection** odkazuje na stejný obor názvů, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f409f-107">For example, if the root element of the XML document is `<bookstore xmlns="urn:newbooks-schema">`, when the schema is added to the **XmlSchemaCollection** it references the same namespace, as follows:</span></span>  
  
```  
xsc.Add("urn:newbooks-schema", "newbooks.xdr")  
```  
  
 <span data-ttu-id="f409f-108">Následující příklad kódu vytvoří **třídy XmlValidatingReader** , která má **XmlTextReader** a přidá do schématu XDR, HeadCount.xdr, **kolekci XmlSchemaCollection**.</span><span class="sxs-lookup"><span data-stu-id="f409f-108">The following code example creates an **XmlValidatingReader** that takes an **XmlTextReader** and adds an XDR schema, HeadCount.xdr, to the **XmlSchemaCollection**.</span></span>  
  
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
  
         vr.Schemas.Add("xdrHeadCount", "HeadCount.xdr")  
         vr.ValidationType = ValidationType.XDR  
         AddHandler vr.ValidationEventHandler, AddressOf ValidationHandler  
  
         While vr.Read()  
            PrintTypeInfo(vr)  
            If vr.NodeType = XmlNodeType.Element Then  
               While vr.MoveToNextAttribute()  
                  PrintTypeInfo(vr)  
               End While  
            End If  
         End While  
         Console.WriteLine("Validation finished")  
      End Sub  
      ' Main  
  
      Public Shared Sub PrintTypeInfo(vr As XmlValidatingReader)  
         If Not (vr.SchemaType Is Nothing) Then  
            If TypeOf vr.SchemaType Is XmlSchemaDatatype Or TypeOf vr.SchemaType Is XmlSchemaSimpleType Then  
               Dim value As Object = vr.ReadTypedValue()  
               Console.WriteLine("{0}({1},{2}):{3}", vr.NodeType, vr.Name, value.GetType().Name, value)  
            End If  
         End If  
      End Sub  
      ' PrintTypeInfo  
  
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
  
         vr.Schemas.Add("xdrHeadCount", "HeadCount.xdr");  
         vr.ValidationType = ValidationType.XDR;  
         vr.ValidationEventHandler += new ValidationEventHandler (ValidationHandler);  
  
         while(vr.Read())  
         {  
            PrintTypeInfo(vr);  
            if(vr.NodeType == XmlNodeType.Element)  
            {  
               while(vr.MoveToNextAttribute())  
                  PrintTypeInfo(vr);  
            }  
         }  
         Console.WriteLine("Validation finished");  
      }  
  
      public static void PrintTypeInfo(XmlValidatingReader vr)  
      {  
         if(vr.SchemaType != null)  
         {  
            if(vr.SchemaType is XmlSchemaDatatype || vr.SchemaType is XmlSchemaSimpleType)  
            {  
               object value = vr.ReadTypedValue();  
               Console.WriteLine("{0}({1},{2}):{3}", vr.NodeType, vr.Name, value.GetType().Name, value);  
            }  
         }  
      }  
  
      public static void ValidationHandler(object sender, ValidationEventArgs args)  
      {  
         Console.WriteLine("***Validation error");  
         Console.WriteLine("\tSeverity:{0}", args.Severity);  
         Console.WriteLine("\tMessage:{0}", args.Message);  
      }  
   }  
}  
```  
  
 <span data-ttu-id="f409f-109">Následující část popisuje obsah souboru vstupního souboru, HeadCount.xml, který má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="f409f-109">The following outlines the contents of the input file, HeadCount.xml, to be validated.</span></span>  
  
```xml  
<!--Load HeadCount.xdr in SchemaCollection for Validation-->  
<HeadCount xmlns='xdrHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</HeadCount>  
```  
  
 <span data-ttu-id="f409f-110">Následující část popisuje obsah souboru schématu XDR, HeadCount.xdr, chcete-li ověřit pomocí.</span><span class="sxs-lookup"><span data-stu-id="f409f-110">The following outlines the contents of the XDR schema file, HeadCount.xdr, to be validated against.</span></span>  
  
```xml  
<Schema xmlns="urn:schemas-microsoft-com:xml-data" xmlns:dt="urn:schemas-microsoft-com:datatypes">  
   <ElementType name="Name" content="textOnly"/>  
   <AttributeType name="Bldg" default="2"/>  
   <ElementType name="HeadCount" content="eltOnly">  
      <element type="Name"/>  
      <attribute type="Bldg"/>  
   </ElementType>  
</Schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f409f-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f409f-111">See Also</span></span>  
 <xref:System.Xml.XmlValidatingReader.ValidationType%2A>  
 <!--zz <xref:System.Xml.XmlValidatingReader.Settings%2A>-->  `System.Xml.XmlValidatingReader.Settings`  
 [<span data-ttu-id="f409f-112">Kompilace schématu XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="f409f-112">XmlSchemaCollection Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemacollection-schema-compilation.md)
