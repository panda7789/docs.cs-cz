---
title: Odvozování relační struktury datové sady ze schématu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 549579fca0179994191987097c12b6085ee91756
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119688"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="b17fb-102">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="b17fb-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="b17fb-103">Tato část obsahuje přehled toho, jak relační schéma `DataSet` je sestaven z dokument schématu XML definice jazyk (XSD) schématu.</span><span class="sxs-lookup"><span data-stu-id="b17fb-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="b17fb-104">Obecně platí, pro každou `complexType` podřízený prvek element schématu tabulky se vygeneruje v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b17fb-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="b17fb-105">Struktura tabulky se určuje podle definice komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="b17fb-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="b17fb-106">Tabulky vytvářejí `DataSet` pro nejvyšší úrovně elementy ve schématu.</span><span class="sxs-lookup"><span data-stu-id="b17fb-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="b17fb-107">Ale tabulku je vytvořen pouze pro nejvyšší úroveň `complexType` element při `complexType` element je vnořit do jiného `complexType` element, ve kterém malá a velká ve vnořeném `complexType` element je namapována na `DataTable` v rámci `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b17fb-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="b17fb-108">Další informace o XSD, najdete v článku World Wide Web Consortium (W3C) [XML schématu část 0: Úvod do doporučení](https://www.w3.org/TR/xmlschema-0/), [XML schématu část 1: Struktury doporučení](https://www.w3.org/TR/xmlschema-1/)a [XML schématu část 2: Datové typy doporučení](https://www.w3.org/TR/xmlschema-2/).</span><span class="sxs-lookup"><span data-stu-id="b17fb-108">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="b17fb-109">Následující příklad ukazuje schématu XML kde `customers` je podřízený prvek `MyDataSet` element, který je **datovou sadu** elementu.</span><span class="sxs-lookup"><span data-stu-id="b17fb-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="b17fb-110">V předchozím příkladu prvek `customers` je komplexní typ elementu.</span><span class="sxs-lookup"><span data-stu-id="b17fb-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="b17fb-111">Proto je analyzován definice komplexní typ a proces mapování vytvoří v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b17fb-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 <span data-ttu-id="b17fb-112">Typ dat každého sloupce v tabulce je odvozen od typu schématu XML odpovídající element nebo atribut.</span><span class="sxs-lookup"><span data-stu-id="b17fb-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b17fb-113">Pokud element `customers` je jednoduchý datový typ schématu XML jako **celé číslo**, je vygenerována žádná tabulka.</span><span class="sxs-lookup"><span data-stu-id="b17fb-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="b17fb-114">Tabulky vytvářejí pouze prvky nejvyšší úrovně, které jsou komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="b17fb-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="b17fb-115">V následujícím schématu XML **schématu** element má dva podřízené elementy, `InStateCustomers` a `OutOfStateCustomers`.</span><span class="sxs-lookup"><span data-stu-id="b17fb-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="b17fb-116">Jak `InStateCustomers` a `OutOfStateCustomers` komplexního typu prvků jsou podřízené prvky (`customerType`).</span><span class="sxs-lookup"><span data-stu-id="b17fb-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="b17fb-117">Proto vygeneruje proces mapování následujících dvou tabulkách identické v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b17fb-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="b17fb-118">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b17fb-118">In This Section</span></span>  
 [<span data-ttu-id="b17fb-119">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="b17fb-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="b17fb-120">Popisuje prvky schématu XML použitý k vytvoření jedinečné a cizího klíče omezení `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b17fb-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="b17fb-121">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="b17fb-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="b17fb-122">Popisuje prvky schématu XML použitý k vytvoření relace mezi sloupci tabulky v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b17fb-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="b17fb-123">Omezení schématu XML a relací</span><span class="sxs-lookup"><span data-stu-id="b17fb-123">XML Schema Constraints and Relationships</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="b17fb-124">Popisuje, jak vztahy se vytvářejí implicitně, při použití prvky schématu XML k vytvoření omezení `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b17fb-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b17fb-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b17fb-125">Related Sections</span></span>  
 [<span data-ttu-id="b17fb-126">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="b17fb-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="b17fb-127">Popisuje, jak načíst a zachováte data v a relační struktury `DataSet` jako XML data.</span><span class="sxs-lookup"><span data-stu-id="b17fb-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b17fb-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b17fb-128">See also</span></span>

- [<span data-ttu-id="b17fb-129">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="b17fb-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
