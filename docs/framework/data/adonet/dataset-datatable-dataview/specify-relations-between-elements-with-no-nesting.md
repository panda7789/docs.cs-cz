---
title: Určení relací mezi elementy bez vnoření
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 83dce7173c016a7d7d2d626bb7a3606de29d54ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204465"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="9273a-102">Určení relací mezi elementy bez vnoření</span><span class="sxs-lookup"><span data-stu-id="9273a-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="9273a-103">Nejsou-li prvky vnořené, nejsou vytvořeny žádné implicitní vztahy.</span><span class="sxs-lookup"><span data-stu-id="9273a-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="9273a-104">Můžete však explicitně zadat vztahy mezi prvky, které nejsou vnořeny pomocí anotace **msdata: Relationship** .</span><span class="sxs-lookup"><span data-stu-id="9273a-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="9273a-105">Následující příklad ukazuje schéma XML, ve kterém je zadána anotace **msdata: Relationship** mezi prvky **Order** a **OrderDetail** , které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="9273a-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="9273a-106">Poznámka **msdata: Relationship** je zadána jako podřízený element elementu **Schema** .</span><span class="sxs-lookup"><span data-stu-id="9273a-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
             xmlns:xs="http://www.w3.org/2001/XMLSchema"   
             xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:string" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNumber" type="xs:string" />  
           <xs:element name="EmpNumber" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  </xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrderDetailRelation"  
                            msdata:parent="Order"   
                            msdata:child="OrderDetail"   
                            msdata:parentkey="OrderNumber"   
                            msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
</xs:schema>  
```  
  
 <span data-ttu-id="9273a-107">Proces mapování schématu XSD (XML Schema Definition Language) vytvoří <xref:System.Data.DataSet> s tabulkami **Order** a **OrderDetail** a vztah zadaný mezi těmito dvěma tabulkami, jak je znázorněno níže.</span><span class="sxs-lookup"><span data-stu-id="9273a-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="9273a-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9273a-108">See also</span></span>

- [<span data-ttu-id="9273a-109">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="9273a-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="9273a-110">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="9273a-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="9273a-111">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="9273a-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
