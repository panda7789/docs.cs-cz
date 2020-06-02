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
# <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="faaac-102">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="faaac-102">Reading and Writing XML Schemas</span></span>
<span data-ttu-id="faaac-103">Rozhraní API modelu modelu objektu schématu (SOM) lze použít ke čtení a zápisu schémat XML Schema Definition Language (XSD) ze souborů nebo jiných zdrojů a sestavení schémat XML v paměti pomocí tříd v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů, které jsou mapovány na struktury definované v doporučeních schématu xml konsorcium World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="faaac-103">The Schema Object Model (SOM) API can be used to read and write XML Schema definition language (XSD) schemas from files or other sources and build XML schemas in-memory using the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation.</span></span>  
  
## <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="faaac-104">Čtení ze schémat XML a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="faaac-104">Reading and Writing XML Schemas</span></span>  
 <span data-ttu-id="faaac-105"><xref:System.Xml.Schema.XmlSchema>Třída poskytuje <xref:System.Xml.Schema.XmlSchema.Read%2A> <xref:System.Xml.Schema.XmlSchema.Write%2A> metody a pro čtení a zápis schémat XML.</span><span class="sxs-lookup"><span data-stu-id="faaac-105">The <xref:System.Xml.Schema.XmlSchema> class provides the <xref:System.Xml.Schema.XmlSchema.Read%2A> and <xref:System.Xml.Schema.XmlSchema.Write%2A> methods to read and write XML schemas.</span></span> <span data-ttu-id="faaac-106"><xref:System.Xml.Schema.XmlSchema.Read%2A>Metoda vrátí <xref:System.Xml.Schema.XmlSchema> objekt představující schéma XML a převezme volitelné <xref:System.Xml.Schema.ValidationEventHandler> jako parametr pro zpracování upozornění ověřování schématu a chyb zjištěných při čtení schématu XML.</span><span class="sxs-lookup"><span data-stu-id="faaac-106">The <xref:System.Xml.Schema.XmlSchema.Read%2A> method returns an <xref:System.Xml.Schema.XmlSchema> object representing the XML schema and takes an optional <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to handle schema validation warnings and errors encountered while reading an XML schema.</span></span>  
  
 <span data-ttu-id="faaac-107"><xref:System.Xml.Schema.XmlSchema.Write%2A>Metoda zapisuje schémata XML do <xref:System.IO.Stream> <xref:System.IO.TextWriter> objektů a <xref:System.Xml.XmlWriter> objekty a může <xref:System.Xml.XmlNamespaceManager> jako parametr převzít volitelný objekt.</span><span class="sxs-lookup"><span data-stu-id="faaac-107">The <xref:System.Xml.Schema.XmlSchema.Write%2A> method writes XML schemas to <xref:System.IO.Stream>, <xref:System.IO.TextWriter> and <xref:System.Xml.XmlWriter> objects and can take an optional <xref:System.Xml.XmlNamespaceManager> object as a parameter.</span></span> <span data-ttu-id="faaac-108"><xref:System.Xml.XmlNamespaceManager>Slouží ke zpracování oborů názvů, které byly zjištěny ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="faaac-108">An <xref:System.Xml.XmlNamespaceManager> is used to handle namespaces encountered in an XML schema.</span></span> <span data-ttu-id="faaac-109">Další informace o <xref:System.Xml.XmlNamespaceManager> třídě naleznete v tématu [Správa oborů názvů v dokumentu XML](managing-namespaces-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="faaac-109">For more information about the <xref:System.Xml.XmlNamespaceManager> class, see [Managing Namespaces in an XML Document](managing-namespaces-in-an-xml-document.md).</span></span>  
  
 <span data-ttu-id="faaac-110">Následující příklad kódu ukazuje čtení a zápis XML schémat z a do souboru.</span><span class="sxs-lookup"><span data-stu-id="faaac-110">The following code example illustrates reading and writing XML schemas from and to a file.</span></span> <span data-ttu-id="faaac-111">Příklad kódu převezme `example.xsd` soubor, přečte jej do <xref:System.Xml.Schema.XmlSchema> objektu pomocí `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metody a pak zapíše soubor do konzoly a do nového `new.xsd` souboru.</span><span class="sxs-lookup"><span data-stu-id="faaac-111">The code example takes the `example.xsd` file, reads it into an <xref:System.Xml.Schema.XmlSchema> object using the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method, and then writes the file to the console and a new `new.xsd` file.</span></span> <span data-ttu-id="faaac-112">Příklad kódu také poskytuje <xref:System.Xml.Schema.ValidationEventHandler> jako parametr `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metodě pro zpracování jakýchkoli upozornění ověřování schématu nebo chyb, ke kterým došlo při čtení schématu XML.</span><span class="sxs-lookup"><span data-stu-id="faaac-112">The code example also provides a <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method to handle any schema validation warnings or errors encountered while reading the XML schema.</span></span> <span data-ttu-id="faaac-113">Pokud <xref:System.Xml.Schema.ValidationEventHandler> parametr není zadán ( `null` ), nejsou hlášeny žádná upozornění ani chyby.</span><span class="sxs-lookup"><span data-stu-id="faaac-113">If the <xref:System.Xml.Schema.ValidationEventHandler> is not specified (`null`), no warnings or errors are reported.</span></span>  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 <span data-ttu-id="faaac-114">Příklad přebírá `example.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="faaac-114">The example takes the `example.xsd` as input.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="faaac-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="faaac-115">See also</span></span>

- [<span data-ttu-id="faaac-116">Přehled Modelu objektu schématu XML</span><span class="sxs-lookup"><span data-stu-id="faaac-116">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="faaac-117">Sestavování schémat XML</span><span class="sxs-lookup"><span data-stu-id="faaac-117">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="faaac-118">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="faaac-118">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="faaac-119">Úpravy schémat XML</span><span class="sxs-lookup"><span data-stu-id="faaac-119">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="faaac-120">Zahrnutí nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="faaac-120">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="faaac-121">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="faaac-121">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="faaac-122">Informační sada po kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="faaac-122">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
- [<span data-ttu-id="faaac-123">Správa oborů názvů v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="faaac-123">Managing Namespaces in an XML Document</span></span>](managing-namespaces-in-an-xml-document.md)
