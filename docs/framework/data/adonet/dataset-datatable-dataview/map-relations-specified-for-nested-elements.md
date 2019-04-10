---
title: Mapování relací zadaných pro vnořené elementy
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: 9772f077991c758be65bbb44b9474f1ad341371f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203142"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="fccd4-102">Mapování relací zadaných pro vnořené elementy</span><span class="sxs-lookup"><span data-stu-id="fccd4-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="fccd4-103">Schéma může obsahovat **msdata:Relationship** poznámky k explicitnímu zadání mapování mezi dva prvky ve schématu.</span><span class="sxs-lookup"><span data-stu-id="fccd4-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="fccd4-104">Dva prvky určené ve **msdata:Relationship** může být vnořena ve schématu, ale nemusí být.</span><span class="sxs-lookup"><span data-stu-id="fccd4-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="fccd4-105">Proces mapování využívá **msdata:Relationship** ve schématu pro generování primární klíč nebo relace cizího klíče mezi dvěma sloupci.</span><span class="sxs-lookup"><span data-stu-id="fccd4-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="fccd4-106">Následující příklad ukazuje schématu XML, ve kterém **OrderDetail** prvek je podřízený prvek **pořadí**.</span><span class="sxs-lookup"><span data-stu-id="fccd4-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="fccd4-107">**Msdata:Relationship** identifikuje tento vztah nadřízenosti a podřízenosti a určuje, že **OrderNumber** sloupec výsledné **pořadí** tabulka má vztah k **OrderNo** sloupec výsledné **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="fccd4-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
 <xs:complexType>  
  <xs:choice maxOccurs="unbounded">  
   <xs:element name="Order">  
    <xs:complexType>  
     <xs:sequence>  
       <xs:element name="OrderNumber" type="xs:string" />  
       <xs:element name="EmpNumber" type="xs:string" />  
       <xs:element name="OrderDetail">  
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"   
                                msdata:parent="Order"   
                                msdata:child="OrderDetail"   
                                msdata:parentkey="OrderNumber"   
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
          <xs:complexType>  
            <xs:sequence>  
             <xs:element name="OrderNo" type="xs:string" />  
             <xs:element name="ItemNo" type="xs:string" />  
            </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:sequence>  
    </xs:complexType>  
   </xs:element>  
  </xs:choice>  
 </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="fccd4-108">Proces mapování schématu XML vytvoří následující <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="fccd4-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="fccd4-109">**Pořadí** a **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="fccd4-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   <span data-ttu-id="fccd4-110">Vztah mezi **pořadí** a **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="fccd4-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="fccd4-111">**Vnořené** pro tento vztah je nastavena na **True** vzhledem k tomu, **pořadí** a **OrderDetail** elementů je vnořeno ve schématu .</span><span class="sxs-lookup"><span data-stu-id="fccd4-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="fccd4-112">Proces mapování nevytvoří žádná omezení.</span><span class="sxs-lookup"><span data-stu-id="fccd4-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fccd4-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fccd4-113">See also</span></span>

- [<span data-ttu-id="fccd4-114">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="fccd4-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="fccd4-115">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="fccd4-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="fccd4-116">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="fccd4-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
