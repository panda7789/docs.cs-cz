---
title: "Mapování vztahy zadané pro vnořené prvky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 221e204c9eef5a861fbd6b85c1e23a0674c6aa4c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="2776b-102">Mapování vztahy zadané pro vnořené prvky</span><span class="sxs-lookup"><span data-stu-id="2776b-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="2776b-103">Schéma může zahrnovat **msdata:Relationship** poznámky k explicitnímu zadání mapování mezi dvěma prvky ve schématu.</span><span class="sxs-lookup"><span data-stu-id="2776b-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="2776b-104">Dva prvky určené ve **msdata:Relationship** mohou být použity ve schématu, ale nemusí být.</span><span class="sxs-lookup"><span data-stu-id="2776b-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="2776b-105">Proces mapování používá **msdata:Relationship** ve schématu vygenerovat primární klíč, cizí klíče relaci mezi dvěma sloupci.</span><span class="sxs-lookup"><span data-stu-id="2776b-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="2776b-106">Následující příklad ukazuje schéma XML, ve kterém **OrderDetail** element je podřízený prvek **pořadí**.</span><span class="sxs-lookup"><span data-stu-id="2776b-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="2776b-107">**Msdata:Relationship** identifikuje tuto relaci nadřazený podřízený a určuje, že **OrderNumber** sloupec výsledná **pořadí** tabulky souvisí se **OrderNo** sloupec výsledná **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="2776b-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="2776b-108">Proces mapování schématu XML vytvoří následující <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="2776b-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="2776b-109">**Pořadí** a **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="2776b-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   <span data-ttu-id="2776b-110">Vztah mezi **pořadí** a **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="2776b-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="2776b-111">**Vnořené** pro tento vztah je nastavena na **True** protože **pořadí** a **OrderDetail** vnořené prvky ve schématu .</span><span class="sxs-lookup"><span data-stu-id="2776b-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="2776b-112">Proces mapování nevytvoří žádné omezení.</span><span class="sxs-lookup"><span data-stu-id="2776b-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2776b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="2776b-113">See Also</span></span>  
 [<span data-ttu-id="2776b-114">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="2776b-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="2776b-115">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="2776b-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="2776b-116">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="2776b-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
