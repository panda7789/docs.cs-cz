---
title: Čtení ze schémat XML a zápis do nich
description: Čtení a zápis schémat XML Schema Definition Language (XSD) ze souborů nebo jiných zdrojů v rozhraní .NET pomocí rozhraní API SOM (Schema Object Model)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: 874b0bdb0e13d545cfff4c813881f1398a8f9487
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767660"
---
# <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="6c433-103">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="6c433-103">Reading and Writing XML Schemas</span></span>
<span data-ttu-id="6c433-104">Rozhraní API modelu modelu objektu schématu (SOM) lze použít ke čtení a zápisu schémat XML Schema Definition Language (XSD) ze souborů nebo jiných zdrojů a sestavení schémat XML v paměti pomocí tříd v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů, které jsou mapovány na struktury definované v doporučeních schématu xml konsorcium World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="6c433-104">The Schema Object Model (SOM) API can be used to read and write XML Schema definition language (XSD) schemas from files or other sources and build XML schemas in-memory using the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation.</span></span>  
  
## <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="6c433-105">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="6c433-105">Reading and Writing XML Schemas</span></span>  
 <span data-ttu-id="6c433-106"><xref:System.Xml.Schema.XmlSchema>Třída poskytuje <xref:System.Xml.Schema.XmlSchema.Read%2A> <xref:System.Xml.Schema.XmlSchema.Write%2A> metody a pro čtení a zápis schémat XML.</span><span class="sxs-lookup"><span data-stu-id="6c433-106">The <xref:System.Xml.Schema.XmlSchema> class provides the <xref:System.Xml.Schema.XmlSchema.Read%2A> and <xref:System.Xml.Schema.XmlSchema.Write%2A> methods to read and write XML schemas.</span></span> <span data-ttu-id="6c433-107"><xref:System.Xml.Schema.XmlSchema.Read%2A>Metoda vrátí <xref:System.Xml.Schema.XmlSchema> objekt představující schéma XML a převezme volitelné <xref:System.Xml.Schema.ValidationEventHandler> jako parametr pro zpracování upozornění ověřování schématu a chyb zjištěných při čtení schématu XML.</span><span class="sxs-lookup"><span data-stu-id="6c433-107">The <xref:System.Xml.Schema.XmlSchema.Read%2A> method returns an <xref:System.Xml.Schema.XmlSchema> object representing the XML schema and takes an optional <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to handle schema validation warnings and errors encountered while reading an XML schema.</span></span>  
  
 <span data-ttu-id="6c433-108"><xref:System.Xml.Schema.XmlSchema.Write%2A>Metoda zapisuje schémata XML do <xref:System.IO.Stream> <xref:System.IO.TextWriter> objektů a <xref:System.Xml.XmlWriter> objekty a může <xref:System.Xml.XmlNamespaceManager> jako parametr převzít volitelný objekt.</span><span class="sxs-lookup"><span data-stu-id="6c433-108">The <xref:System.Xml.Schema.XmlSchema.Write%2A> method writes XML schemas to <xref:System.IO.Stream>, <xref:System.IO.TextWriter> and <xref:System.Xml.XmlWriter> objects and can take an optional <xref:System.Xml.XmlNamespaceManager> object as a parameter.</span></span> <span data-ttu-id="6c433-109"><xref:System.Xml.XmlNamespaceManager>Slouží ke zpracování oborů názvů, které byly zjištěny ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="6c433-109">An <xref:System.Xml.XmlNamespaceManager> is used to handle namespaces encountered in an XML schema.</span></span> <span data-ttu-id="6c433-110">Další informace o <xref:System.Xml.XmlNamespaceManager> třídě naleznete v tématu [Správa oborů názvů v dokumentu XML](managing-namespaces-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="6c433-110">For more information about the <xref:System.Xml.XmlNamespaceManager> class, see [Managing Namespaces in an XML Document](managing-namespaces-in-an-xml-document.md).</span></span>  
  
 <span data-ttu-id="6c433-111">Následující příklad kódu ukazuje čtení a zápis XML schémat z a do souboru.</span><span class="sxs-lookup"><span data-stu-id="6c433-111">The following code example illustrates reading and writing XML schemas from and to a file.</span></span> <span data-ttu-id="6c433-112">Příklad kódu převezme `example.xsd` soubor, přečte jej do <xref:System.Xml.Schema.XmlSchema> objektu pomocí `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metody a pak zapíše soubor do konzoly a do nového `new.xsd` souboru.</span><span class="sxs-lookup"><span data-stu-id="6c433-112">The code example takes the `example.xsd` file, reads it into an <xref:System.Xml.Schema.XmlSchema> object using the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method, and then writes the file to the console and a new `new.xsd` file.</span></span> <span data-ttu-id="6c433-113">Příklad kódu také poskytuje <xref:System.Xml.Schema.ValidationEventHandler> jako parametr `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metodě pro zpracování jakýchkoli upozornění ověřování schématu nebo chyb, ke kterým došlo při čtení schématu XML.</span><span class="sxs-lookup"><span data-stu-id="6c433-113">The code example also provides a <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method to handle any schema validation warnings or errors encountered while reading the XML schema.</span></span> <span data-ttu-id="6c433-114">Pokud <xref:System.Xml.Schema.ValidationEventHandler> parametr není zadán ( `null` ), nejsou hlášeny žádná upozornění ani chyby.</span><span class="sxs-lookup"><span data-stu-id="6c433-114">If the <xref:System.Xml.Schema.ValidationEventHandler> is not specified (`null`), no warnings or errors are reported.</span></span>  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 <span data-ttu-id="6c433-115">Příklad přebírá `example.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="6c433-115">The example takes the `example.xsd` as input.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6c433-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c433-116">See also</span></span>

- [<span data-ttu-id="6c433-117">Přehled Modelu objektu schématu XML</span><span class="sxs-lookup"><span data-stu-id="6c433-117">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="6c433-118">Sestavování schémat XML</span><span class="sxs-lookup"><span data-stu-id="6c433-118">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="6c433-119">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="6c433-119">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="6c433-120">Úpravy schémat XML</span><span class="sxs-lookup"><span data-stu-id="6c433-120">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="6c433-121">Zahrnutí nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="6c433-121">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="6c433-122">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="6c433-122">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="6c433-123">Informační sada po kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="6c433-123">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
- [<span data-ttu-id="6c433-124">Správa oborů názvů v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="6c433-124">Managing Namespaces in an XML Document</span></span>](managing-namespaces-in-an-xml-document.md)
