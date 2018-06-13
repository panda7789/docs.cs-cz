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
ms.locfileid: "33570443"
---
# <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="f2c48-102">Čtení a zápis XML schémata</span><span class="sxs-lookup"><span data-stu-id="f2c48-102">Reading and Writing XML Schemas</span></span>
<span data-ttu-id="f2c48-103">Schéma objektu modelu (SOM) rozhraní API lze použít ke čtení a zápisu definice schématu XML schémata jazyk (XSD) ze souborů nebo jiných zdrojů a XML schémata v paměti pomocí třídy v sestavení <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů, který mapování struktury definované v celém světě Doporučení schématu XML Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="f2c48-103">The Schema Object Model (SOM) API can be used to read and write XML Schema definition language (XSD) schemas from files or other sources and build XML schemas in-memory using the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation.</span></span>  
  
## <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="f2c48-104">Čtení a zápis XML schémata</span><span class="sxs-lookup"><span data-stu-id="f2c48-104">Reading and Writing XML Schemas</span></span>  
 <span data-ttu-id="f2c48-105"><xref:System.Xml.Schema.XmlSchema> Třída poskytuje <xref:System.Xml.Schema.XmlSchema.Read%2A> a <xref:System.Xml.Schema.XmlSchema.Write%2A> metody pro čtení a zápis schémat XML.</span><span class="sxs-lookup"><span data-stu-id="f2c48-105">The <xref:System.Xml.Schema.XmlSchema> class provides the <xref:System.Xml.Schema.XmlSchema.Read%2A> and <xref:System.Xml.Schema.XmlSchema.Write%2A> methods to read and write XML schemas.</span></span> <span data-ttu-id="f2c48-106"><xref:System.Xml.Schema.XmlSchema.Read%2A> Metoda vrátí <xref:System.Xml.Schema.XmlSchema> objekt reprezentující schématu XML a přijímá volitelný <xref:System.Xml.Schema.ValidationEventHandler> jako parametr pro zpracování schématu ověření upozornění a chyb zjištěných při načítání schématu XML.</span><span class="sxs-lookup"><span data-stu-id="f2c48-106">The <xref:System.Xml.Schema.XmlSchema.Read%2A> method returns an <xref:System.Xml.Schema.XmlSchema> object representing the XML schema and takes an optional <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to handle schema validation warnings and errors encountered while reading an XML schema.</span></span>  
  
 <span data-ttu-id="f2c48-107"><xref:System.Xml.Schema.XmlSchema.Write%2A> Metoda zapíše schémat XML do <xref:System.IO.Stream>, <xref:System.IO.TextWriter> a <xref:System.Xml.XmlWriter> objektů což může trvat volitelný <xref:System.Xml.XmlNamespaceManager> objekt jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f2c48-107">The <xref:System.Xml.Schema.XmlSchema.Write%2A> method writes XML schemas to <xref:System.IO.Stream>, <xref:System.IO.TextWriter> and <xref:System.Xml.XmlWriter> objects and can take an optional <xref:System.Xml.XmlNamespaceManager> object as a parameter.</span></span> <span data-ttu-id="f2c48-108"><xref:System.Xml.XmlNamespaceManager> Slouží ke zpracování obory názvů v schématu XML.</span><span class="sxs-lookup"><span data-stu-id="f2c48-108">An <xref:System.Xml.XmlNamespaceManager> is used to handle namespaces encountered in an XML schema.</span></span> <span data-ttu-id="f2c48-109">Další informace o <xref:System.Xml.XmlNamespaceManager> třídy najdete v tématu [Správa obory názvů v dokumentu XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="f2c48-109">For more information about the <xref:System.Xml.XmlNamespaceManager> class, see [Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).</span></span>  
  
 <span data-ttu-id="f2c48-110">Následující příklad kódu ukazuje čtení a zápis schémat XML z a do souboru.</span><span class="sxs-lookup"><span data-stu-id="f2c48-110">The following code example illustrates reading and writing XML schemas from and to a file.</span></span> <span data-ttu-id="f2c48-111">Příklad kódu trvá `example.xsd` souboru, přečte ji do <xref:System.Xml.Schema.XmlSchema> pomocí `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metoda a pak zapisuje do konzoly a nový soubor `new.xsd` souboru.</span><span class="sxs-lookup"><span data-stu-id="f2c48-111">The code example takes the `example.xsd` file, reads it into an <xref:System.Xml.Schema.XmlSchema> object using the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method, and then writes the file to the console and a new `new.xsd` file.</span></span> <span data-ttu-id="f2c48-112">Také poskytuje příklad kódu <xref:System.Xml.Schema.ValidationEventHandler> jako parametr, který se `static` <xref:System.Xml.Schema.XmlSchema.Read%2A> metodu ke zpracování všechna schématu ověření upozornění a chyb zjištěných při načítání schématu XML.</span><span class="sxs-lookup"><span data-stu-id="f2c48-112">The code example also provides a <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method to handle any schema validation warnings or errors encountered while reading the XML schema.</span></span> <span data-ttu-id="f2c48-113">Pokud <xref:System.Xml.Schema.ValidationEventHandler> není zadán (`null`), jsou hlášeny žádná varování nebo chyby.</span><span class="sxs-lookup"><span data-stu-id="f2c48-113">If the <xref:System.Xml.Schema.ValidationEventHandler> is not specified (`null`), no warnings or errors are reported.</span></span>  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 <span data-ttu-id="f2c48-114">V příkladu trvá `example.xsd` jako vstup.</span><span class="sxs-lookup"><span data-stu-id="f2c48-114">The example takes the `example.xsd` as input.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2c48-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2c48-115">See Also</span></span>  
 [<span data-ttu-id="f2c48-116">Přehled Modelu objektu schématu XML</span><span class="sxs-lookup"><span data-stu-id="f2c48-116">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [<span data-ttu-id="f2c48-117">Sestavování schémat XML</span><span class="sxs-lookup"><span data-stu-id="f2c48-117">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [<span data-ttu-id="f2c48-118">Procházení schémat XML</span><span class="sxs-lookup"><span data-stu-id="f2c48-118">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="f2c48-119">Úpravy schémat XML</span><span class="sxs-lookup"><span data-stu-id="f2c48-119">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [<span data-ttu-id="f2c48-120">Zahrnutí nebo import schémat XML</span><span class="sxs-lookup"><span data-stu-id="f2c48-120">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [<span data-ttu-id="f2c48-121">XmlSchemaSet pro kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="f2c48-121">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="f2c48-122">Informační sada po kompilaci schématu</span><span class="sxs-lookup"><span data-stu-id="f2c48-122">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)  
 [<span data-ttu-id="f2c48-123">Správa oborů názvů v dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="f2c48-123">Managing Namespaces in an XML Document</span></span>](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)
