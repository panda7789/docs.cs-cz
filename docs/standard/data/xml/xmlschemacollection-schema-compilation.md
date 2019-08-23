---
title: XmlSchemaCollection Schema Compilation
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40d7ef11dde882d99c21fe541c2689c52a634edf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915941"
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="db8e3-102">XmlSchemaCollection Schema Compilation</span><span class="sxs-lookup"><span data-stu-id="db8e3-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="db8e3-103">**XmlSchemaCollection** je mezipaměť nebo knihovna, kde mohou být uloženy a ověřeny schémata XML-data redukovaná (XDR) a XML Schema Definition Language (XSD).</span><span class="sxs-lookup"><span data-stu-id="db8e3-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="db8e3-104">**XmlSchemaCollection** vylepšuje výkon ukládáním schémat do paměti místo přístupu ze souboru nebo adresy URL.</span><span class="sxs-lookup"><span data-stu-id="db8e3-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db8e3-105">I když třída XmlSchemaCollection ukládá schémata XDR i schémata XML, jakákoliv metoda a vlastnost, která přijímá nebo vrací objekt **XmlSchema** , podporuje pouze schémata XML.</span><span class="sxs-lookup"><span data-stu-id="db8e3-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="db8e3-106">Třída je nyní zastaralá a byla nahrazena <xref:System.Xml.Schema.XmlSchemaSet> třídou. <xref:System.Xml.Schema.XmlSchemaCollection></span><span class="sxs-lookup"><span data-stu-id="db8e3-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="db8e3-107">Další informace o <xref:System.Xml.Schema.XmlSchemaSet> třídě naleznete v tématu Třída [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="db8e3-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="db8e3-108">Přidání schémat do kolekce</span><span class="sxs-lookup"><span data-stu-id="db8e3-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="db8e3-109">Schémata jsou načtena do kolekce pomocí metody **Add** kolekce **XmlSchemaCollection**, v níž je schéma přidruženo k identifikátoru URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="db8e3-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="db8e3-110">V případě schémat XML bude identifikátor URI oboru názvů obvykle cílovým oborem názvů schématu.</span><span class="sxs-lookup"><span data-stu-id="db8e3-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="db8e3-111">V případě schémat XDR je identifikátor URI oboru názvů zadaný při přidání schématu do kolekce.</span><span class="sxs-lookup"><span data-stu-id="db8e3-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="db8e3-112">Vyhledat schéma v kolekci</span><span class="sxs-lookup"><span data-stu-id="db8e3-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="db8e3-113">Můžete zjistit, zda je schéma v kolekci, pomocí metody **Contains** .</span><span class="sxs-lookup"><span data-stu-id="db8e3-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="db8e3-114">Metoda **Contains** přebírá buď objekt **XmlSchema** (pouze schémata XML), nebo řetězec představující identifikátor URI oboru názvů přidruženého ke schématu (pro schémata XML schémat a XDR).</span><span class="sxs-lookup"><span data-stu-id="db8e3-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="db8e3-115">Načtení schématu z kolekce</span><span class="sxs-lookup"><span data-stu-id="db8e3-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="db8e3-116">Schéma můžete z kolekce načíst pomocí vlastnosti **Item** .</span><span class="sxs-lookup"><span data-stu-id="db8e3-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="db8e3-117">Vlastnost **Item** přebírá řetězec představující identifikátor URI oboru názvů přidružený ke schématu, obvykle jeho cílový obor názvů a vrací objekt **XmlSchema** .</span><span class="sxs-lookup"><span data-stu-id="db8e3-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="db8e3-118">Vlastnost **Item** se vztahuje pouze na schémata XML.</span><span class="sxs-lookup"><span data-stu-id="db8e3-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="db8e3-119">Návratová hodnota je vždy nulový odkaz pro schémata XDR, protože nemají k dispozici objektový model.</span><span class="sxs-lookup"><span data-stu-id="db8e3-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="db8e3-120">Ověřování dokumentů XML pomocí XmlSchemacollection</span><span class="sxs-lookup"><span data-stu-id="db8e3-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="db8e3-121">Dokument instance XML můžete ověřit pomocí kolekce XmlSchemaCollection vytvořením objektu XmlSchemaCollection , přidáním schémat do kolekce a nastavením vlastnosti schemas v **XmlValidatingReader** na hodnotu Přiřaďte vytvořenou **kolekci XmlSchemaCollection** k **XmlValidatingReader**.</span><span class="sxs-lookup"><span data-stu-id="db8e3-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="db8e3-122">Vylepšený výkon</span><span class="sxs-lookup"><span data-stu-id="db8e3-122">Improved Performance</span></span>  
 <span data-ttu-id="db8e3-123">Doporučuje se, pokud ověřujete více než jeden dokument proti stejnému schématu, že použijete sadu XmlSchemaCollection , protože poskytuje lepší výkon ukládáním schémat do mezipaměti v paměti.</span><span class="sxs-lookup"><span data-stu-id="db8e3-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="db8e3-124">Následující příklad kódu vytvoří objekt **XmlSchemaCollection** , přidá schémata do kolekce a nastaví vlastnost **schemas** .</span><span class="sxs-lookup"><span data-stu-id="db8e3-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db8e3-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db8e3-125">See also</span></span>

- [<span data-ttu-id="db8e3-126">Ověření XDR s třídou XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="db8e3-126">XDR Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)
- [<span data-ttu-id="db8e3-127">Ověření schématu XML (XSD) s třídou XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="db8e3-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
