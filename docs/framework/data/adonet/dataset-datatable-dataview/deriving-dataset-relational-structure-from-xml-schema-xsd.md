---
title: Odvozování relační struktury datové sady ze schématu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 98c43b6af2913b9737085d2d983b37c6da4c1724
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934469"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="274c2-102">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="274c2-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="274c2-103">Tato část poskytuje přehled o tom, jak je relační schéma a `DataSet` sestaveno z dokumentu schématu XSD (XML Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="274c2-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="274c2-104">Obecně platí, že pro `complexType` každý podřízený element elementu schématu je tabulka generována `DataSet`v.</span><span class="sxs-lookup"><span data-stu-id="274c2-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="274c2-105">Struktura tabulky je určena definicí komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="274c2-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="274c2-106">Tabulky jsou vytvořeny v `DataSet` prvku pro prvky nejvyšší úrovně ve schématu.</span><span class="sxs-lookup"><span data-stu-id="274c2-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="274c2-107">Tabulka je však vytvořena pouze pro element `complexType` nejvyšší úrovně, je- `complexType` li element vnořen uvnitř jiného `complexType` prvku, v `DataTable` takovém případě je `DataSet`vnořený `complexType` prvek mapován na v rámci.</span><span class="sxs-lookup"><span data-stu-id="274c2-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="274c2-108">Další informace o XSD najdete v části schéma XML pro konsorcium World Wide Web (W3C [) – část 0: Doporučení](https://www.w3.org/TR/xmlschema-0/) pro[Úvod, část schématu XML 1: Doporučení](https://www.w3.org/TR/xmlschema-1/) ke[strukturám a část schématu XML 2: Doporučení](https://www.w3.org/TR/xmlschema-2/)pro DataTypes.</span><span class="sxs-lookup"><span data-stu-id="274c2-108">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="274c2-109">Následující příklad ukazuje schéma XML, kde `customers` je podřízený element `MyDataSet` elementu, který je element **DataSet** .</span><span class="sxs-lookup"><span data-stu-id="274c2-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
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
  
 <span data-ttu-id="274c2-110">V předchozím příkladu je element `customers` prvkem komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="274c2-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="274c2-111">Proto se definice komplexního typu analyzuje a proces mapování vytvoří následující tabulku.</span><span class="sxs-lookup"><span data-stu-id="274c2-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 <span data-ttu-id="274c2-112">Datový typ každého sloupce v tabulce je odvozen od typu schématu XML odpovídajícího elementu nebo atributu.</span><span class="sxs-lookup"><span data-stu-id="274c2-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="274c2-113">Pokud je prvek `customers` jednoduchého datového typu schématu XML, jako je například **celé číslo**, není vygenerována žádná tabulka.</span><span class="sxs-lookup"><span data-stu-id="274c2-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="274c2-114">Tabulky jsou vytvořeny pouze pro prvky nejvyšší úrovně, které jsou komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="274c2-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="274c2-115">V následujícím schématu XML má element **Schema** dva podřízené `InStateCustomers` prvky elementu a. `OutOfStateCustomers`</span><span class="sxs-lookup"><span data-stu-id="274c2-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
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
  
 <span data-ttu-id="274c2-116">I podřízené prvky jsou elementy komplexního typu (`customerType`). `OutOfStateCustomers` `InStateCustomers`</span><span class="sxs-lookup"><span data-stu-id="274c2-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="274c2-117">Proto proces mapování generuje následující dvě identické tabulky v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="274c2-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="274c2-118">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="274c2-118">In This Section</span></span>  
 [<span data-ttu-id="274c2-119">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="274c2-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="274c2-120">Popisuje prvky schématu XML, které se používají k vytvoření jedinečnosti a omezení cizího klíče v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="274c2-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="274c2-121">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="274c2-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="274c2-122">Popisuje prvky schématu XML, které slouží k vytvoření vztahů mezi sloupci tabulky v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="274c2-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="274c2-123">Omezení schématu XML a relací</span><span class="sxs-lookup"><span data-stu-id="274c2-123">XML Schema Constraints and Relationships</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="274c2-124">Popisuje `DataSet`, jak jsou relace vytvořeny implicitně při použití elementů schématu XML k vytvoření omezení v.</span><span class="sxs-lookup"><span data-stu-id="274c2-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="274c2-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="274c2-125">Related Sections</span></span>  
 [<span data-ttu-id="274c2-126">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="274c2-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="274c2-127">Popisuje, jak načíst a zachovat relační strukturu a data ve `DataSet` formě dat XML.</span><span class="sxs-lookup"><span data-stu-id="274c2-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="274c2-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="274c2-128">See also</span></span>

- [<span data-ttu-id="274c2-129">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="274c2-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
