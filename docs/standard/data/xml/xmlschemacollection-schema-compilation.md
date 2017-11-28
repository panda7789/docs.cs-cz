---
title: "Schéma kolekci XmlSchemaCollection kompilace"
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
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 901c3fdc8fdc80cc7c3bf13170646de857a5e009
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="9fa20-102">Schéma kolekci XmlSchemaCollection kompilace</span><span class="sxs-lookup"><span data-stu-id="9fa20-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="9fa20-103">**Kolekci XmlSchemaCollection** je do mezipaměti nebo knihovny, kam můžete ukládat a ověřit XML-Data Reduced (XDR) a schématu XML schémata definition language (XSD).</span><span class="sxs-lookup"><span data-stu-id="9fa20-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="9fa20-104">**Kolekci XmlSchemaCollection** zlepšuje výkon díky ukládání do mezipaměti schémata v paměti místo k nim přistupovat ze souboru nebo adresa URL.</span><span class="sxs-lookup"><span data-stu-id="9fa20-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fa20-105">I když **kolekci XmlSchemaCollection** třída ukládá XDR schémata a schémat XML, všechny metody a vlastnosti, která přebírá nebo vrátí **XmlSchema** objekt podporuje pouze schémat XML.</span><span class="sxs-lookup"><span data-stu-id="9fa20-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9fa20-106"><xref:System.Xml.Schema.XmlSchemaCollection> Třída je zastaralá a nahradila s <xref:System.Xml.Schema.XmlSchemaSet> třídy.</span><span class="sxs-lookup"><span data-stu-id="9fa20-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="9fa20-107">Další informace o <xref:System.Xml.Schema.XmlSchemaSet> najdete třída [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="9fa20-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="9fa20-108">Přidat do kolekce schémat.</span><span class="sxs-lookup"><span data-stu-id="9fa20-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="9fa20-109">Schémata jsou načteny do kolekce pomocí **přidat** metodu **kolekci XmlSchemaCollection**, po kterých je přidružen identifikátor URI oboru názvů schématu.</span><span class="sxs-lookup"><span data-stu-id="9fa20-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="9fa20-110">Schémat XML identifikátor URI oboru názvů bude obvykle cílový obor názvů pro schéma.</span><span class="sxs-lookup"><span data-stu-id="9fa20-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="9fa20-111">U XDR schémat identifikátor URI oboru názvů je že obor názvů zadán, pokud bylo schéma přidat do kolekce.</span><span class="sxs-lookup"><span data-stu-id="9fa20-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="9fa20-112">Zkontrolujte schéma v kolekci</span><span class="sxs-lookup"><span data-stu-id="9fa20-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="9fa20-113">Můžete zkontrolovat, zda schéma je v kolekci pomocí **obsahuje** metoda.</span><span class="sxs-lookup"><span data-stu-id="9fa20-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="9fa20-114">**Obsahuje** metoda přebírá buď **XmlSchema** objektu (pro jenom schémata XML) nebo řetězec představující identifikátor URI oboru názvů přidružené schéma (pro schémat XML a XDR schémat).</span><span class="sxs-lookup"><span data-stu-id="9fa20-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="9fa20-115">Načíst schéma z kolekce</span><span class="sxs-lookup"><span data-stu-id="9fa20-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="9fa20-116">Můžete načíst schéma z kolekce pomocí **položky** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9fa20-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="9fa20-117">**Položky** vlastnost přebírá řetězec představující obor názvů URI přidružený schématu, obvykle jeho cílový obor názvů a vrátí **XmlSchema** objektu.</span><span class="sxs-lookup"><span data-stu-id="9fa20-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="9fa20-118">**Položky** vlastnost se vztahuje pouze na schémata XML.</span><span class="sxs-lookup"><span data-stu-id="9fa20-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="9fa20-119">Vrácená hodnota je vždy odkaz s hodnotou null pro schémata XDR, protože nemají objektový model, který je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9fa20-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="9fa20-120">Ověření pomocí kolekci XmlSchemaCollection dokumentů XML</span><span class="sxs-lookup"><span data-stu-id="9fa20-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="9fa20-121">Můžete ověřit instance dokumentu XML pomocí **kolekci XmlSchemaCollection** vytvořením **kolekci XmlSchemaCollection** objekt, přidávání vaší schémata do kolekce a nastavení **schémat.**  vlastnost **třídy XmlValidatingReader** přiřadit vytvořený **kolekci XmlSchemaCollection** k **třídy XmlValidatingReader**.</span><span class="sxs-lookup"><span data-stu-id="9fa20-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="9fa20-122">Lepší výkon</span><span class="sxs-lookup"><span data-stu-id="9fa20-122">Improved Performance</span></span>  
 <span data-ttu-id="9fa20-123">Se doporučuje, pokud ověřujete více než jeden dokument pro stejné schéma, že používáte **kolekci XmlSchemaCollection** protože poskytuje lepší výkon pomocí ukládání do mezipaměti schémata v paměti.</span><span class="sxs-lookup"><span data-stu-id="9fa20-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="9fa20-124">Následující příklad kódu vytvoří **kolekci XmlSchemaCollection** objekt, přidá do kolekce schémat a nastaví **schémata** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9fa20-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fa20-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9fa20-125">See Also</span></span>  
 [<span data-ttu-id="9fa20-126">Ověření XDR s kolekci XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="9fa20-126">XDR Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [<span data-ttu-id="9fa20-127">Ověření schématu (XSD) XML s kolekci XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="9fa20-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
