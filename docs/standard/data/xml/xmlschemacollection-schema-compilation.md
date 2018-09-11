---
title: Kompilace schématu XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7b6ea782020dde83aa7d59be8ec3058a27075ad
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44267948"
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="c2364-102">Kompilace schématu XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="c2364-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="c2364-103">**Třídou XmlSchemaCollection** mezipaměti nebo knihovny, kde můžete ukládat a ověřit XML-Data Reduced (XDR) a schéma XML definice jazyk (XSD) schémata.</span><span class="sxs-lookup"><span data-stu-id="c2364-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="c2364-104">**Kolekci XmlSchemaCollection** zvyšuje výkon díky ukládání do mezipaměti schémat v paměti namísto se k nim dostanete ze souboru nebo adresy URL.</span><span class="sxs-lookup"><span data-stu-id="c2364-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2364-105">I když **třídou XmlSchemaCollection** třída uchovává XDR schémat a schémat XML, všechny metody a vlastnosti, která přijímá nebo vrátí **XmlSchema** objekt podporuje pouze schémata XML.</span><span class="sxs-lookup"><span data-stu-id="c2364-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c2364-106"><xref:System.Xml.Schema.XmlSchemaCollection> Třída je zastaralá a bylo nahrazeno tématem <xref:System.Xml.Schema.XmlSchemaSet> třídy.</span><span class="sxs-lookup"><span data-stu-id="c2364-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="c2364-107">Další informace o <xref:System.Xml.Schema.XmlSchemaSet> třídy viz [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="c2364-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="c2364-108">Přidání do kolekce schémat</span><span class="sxs-lookup"><span data-stu-id="c2364-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="c2364-109">Schémata jsou načteny do kolekce pomocí **přidat** metoda **třídou XmlSchemaCollection**, po kterém schéma je přidružen k oboru názvů identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="c2364-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="c2364-110">Schémat XML obor názvů URI bude obvykle cílový obor názvů pro schéma.</span><span class="sxs-lookup"><span data-stu-id="c2364-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="c2364-111">Pro schémata XDR identifikátor URI oboru názvů je že obor názvů určený při schématu byl přidán do kolekce.</span><span class="sxs-lookup"><span data-stu-id="c2364-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="c2364-112">Vyhledat schéma v kolekci</span><span class="sxs-lookup"><span data-stu-id="c2364-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="c2364-113">Můžete zkontrolovat, jestli schéma je v kolekci pomocí **obsahuje** metoda.</span><span class="sxs-lookup"><span data-stu-id="c2364-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="c2364-114">**Obsahuje** metoda přebírá buď **XmlSchema** objekt (pouze schémata XML) nebo řetězec představující obor názvů URI přidružený k schématu (pro schémata schémat XML a XDR).</span><span class="sxs-lookup"><span data-stu-id="c2364-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="c2364-115">Načíst schéma z kolekce</span><span class="sxs-lookup"><span data-stu-id="c2364-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="c2364-116">Můžete načíst schéma z kolekce pomocí **položky** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c2364-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="c2364-117">**Položky** vlastnost přebírá řetězec představující obor názvů URI přidružený k schématu, obvykle jeho cílový obor názvů a vrátí **XmlSchema** objektu.</span><span class="sxs-lookup"><span data-stu-id="c2364-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="c2364-118">**Položky** vlastnost se vztahuje pouze na schématech XML.</span><span class="sxs-lookup"><span data-stu-id="c2364-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="c2364-119">Vrácená hodnota je vždy odkaz s hodnotou null pro schémata XDR, protože nemají objekt modelu, který je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c2364-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="c2364-120">Ověření XML dokumenty v kolekci XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="c2364-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="c2364-121">Můžete ověřit v instanci dokumentu XML pomocí **třídou XmlSchemaCollection** tak, že vytvoříte **třídou XmlSchemaCollection** objektu, přidání vašeho schémata do kolekce a nastavení **schémata**  vlastnost **objekt XmlValidatingReader** přiřadit vytvořený **třídou XmlSchemaCollection** k **objekt XmlValidatingReader**.</span><span class="sxs-lookup"><span data-stu-id="c2364-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="c2364-122">Vylepšení výkonu</span><span class="sxs-lookup"><span data-stu-id="c2364-122">Improved Performance</span></span>  
 <span data-ttu-id="c2364-123">Doporučuje, pokud se ověření více než jeden dokument pomocí stejné schéma, že používáte **třídou XmlSchemaCollection** vzhledem k tomu, že poskytuje lepší výkon díky ukládání do mezipaměti schémat v paměti.</span><span class="sxs-lookup"><span data-stu-id="c2364-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="c2364-124">Následující příklad kódu vytvoří **třídou XmlSchemaCollection** objekt, přidá do kolekce schémat a nastaví **schémata** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c2364-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c2364-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2364-125">See also</span></span>

- [<span data-ttu-id="c2364-126">Ověření XDR s třídou XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="c2364-126">XDR Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
- [<span data-ttu-id="c2364-127">Ověření schématu XML (XSD) s třídou XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="c2364-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
