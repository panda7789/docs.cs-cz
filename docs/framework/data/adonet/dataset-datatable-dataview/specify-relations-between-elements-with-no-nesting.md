---
title: "Určit vztahy mezi elementy s bez vnoření"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 51d2248094ecf66eedbf8cd187cf6c8270ca5116
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="33c7b-102">Určit vztahy mezi elementy s bez vnoření</span><span class="sxs-lookup"><span data-stu-id="33c7b-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="33c7b-103">Když nejsou vnořené prvky, jsou vytvořeny žádné implicitní vztahy.</span><span class="sxs-lookup"><span data-stu-id="33c7b-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="33c7b-104">Můžete však explicitně určit vztahy mezi elementy, které nejsou vnořené pomocí **msdata:Relationship** poznámky.</span><span class="sxs-lookup"><span data-stu-id="33c7b-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="33c7b-105">Následující příklad ukazuje schéma XML, ve kterém **msdata:Relationship** poznámky je zadaný v rozmezí **pořadí** a **OrderDetail** elementy, které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="33c7b-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="33c7b-106">**Msdata:Relationship** poznámky je zadán jako podřízený element **schématu** elementu.</span><span class="sxs-lookup"><span data-stu-id="33c7b-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="33c7b-107">Vytvoří mapování proces schématu XML definition language (XSD) schématu <xref:System.Data.DataSet> s **pořadí** a **OrderDetail** tabulky a relace zadaný mezi těmito dvěma tabulkami, jako vidíte níže.</span><span class="sxs-lookup"><span data-stu-id="33c7b-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="33c7b-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="33c7b-108">See Also</span></span>  
 [<span data-ttu-id="33c7b-109">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="33c7b-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="33c7b-110">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="33c7b-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="33c7b-111">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="33c7b-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
