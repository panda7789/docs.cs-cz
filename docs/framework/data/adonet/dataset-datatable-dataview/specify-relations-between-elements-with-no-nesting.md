---
title: Určení relací mezi elementy bez vnoření
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: bee427c6cdf76792773ea827c8772b276ff29c31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150815"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="3b83c-102">Určení relací mezi elementy bez vnoření</span><span class="sxs-lookup"><span data-stu-id="3b83c-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="3b83c-103">Pokud prvky nejsou vnořené, jsou vytvořeny žádné implicitní vztahy.</span><span class="sxs-lookup"><span data-stu-id="3b83c-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="3b83c-104">Můžete však explicitně určit vztahy mezi prvky, které nejsou vnořeny pomocí anotace **msdata:Relationship.**</span><span class="sxs-lookup"><span data-stu-id="3b83c-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="3b83c-105">Následující příklad ukazuje schéma XML, ve kterém je zadána poznámka **msdata:Relationship** mezi prvky **Order** a **OrderDetail,** které nejsou vnořeny.</span><span class="sxs-lookup"><span data-stu-id="3b83c-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="3b83c-106">Anotace **msdata:Relationship** je určena jako podřízený prvek elementu **Schéma.**</span><span class="sxs-lookup"><span data-stu-id="3b83c-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="3b83c-107">Proces mapování schématu schématu schématu schématu schématu XML <xref:System.Data.DataSet> (XSD) vytvoří tabulky **S Order** a **OrderDetail** a relaci určenou mezi těmito dvěma tabulkami, jak je znázorněno níže.</span><span class="sxs-lookup"><span data-stu-id="3b83c-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber
ChildTable: OrderDetail  
ChildColumns: OrderNo
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b83c-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b83c-108">See also</span></span>

- [<span data-ttu-id="3b83c-109">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="3b83c-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="3b83c-110">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="3b83c-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="3b83c-111">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3b83c-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
