---
title: Mapování relací zadaných pro vnořené elementy
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: 138fbbc3ccaa90096a15fa87544e5c29f66beb08
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040060"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="799dc-102">Mapování relací zadaných pro vnořené elementy</span><span class="sxs-lookup"><span data-stu-id="799dc-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="799dc-103">Schéma může zahrnovat anotaci **msdata: Relationship** pro explicitní určení mapování mezi dvěma prvky ve schématu.</span><span class="sxs-lookup"><span data-stu-id="799dc-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="799dc-104">Dva prvky určené v **msdata: vztah** může být vnořen ve schématu, ale nemusí být.</span><span class="sxs-lookup"><span data-stu-id="799dc-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="799dc-105">Proces mapování používá **msdata: Relationship** ve schématu k vygenerování vztahu primárního klíče/cizího klíče mezi dvěma sloupci.</span><span class="sxs-lookup"><span data-stu-id="799dc-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="799dc-106">Následující příklad ukazuje schéma XML, ve kterém je element **OrderDetail** podřízeným prvkem **Order**.</span><span class="sxs-lookup"><span data-stu-id="799dc-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="799dc-107">**Msdata: Relationship** identifikuje tuto relaci typu nadřazený-podřízený a určí, že sloupec **OrderNumber** výsledné tabulky **objednávky** souvisí se sloupcem **OrderNo** výsledné tabulky **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="799dc-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="799dc-108">Proces mapování schématu XML vytvoří v <xref:System.Data.DataSet>následující:</span><span class="sxs-lookup"><span data-stu-id="799dc-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="799dc-109">**Objednávka** a tabulka **OrderDetail**</span><span class="sxs-lookup"><span data-stu-id="799dc-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="799dc-110">Vztah mezi tabulkami **Order** a **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="799dc-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="799dc-111">**Vnořená** vlastnost pro tento vztah je nastavena na **hodnotu true** , protože prvky **Order** a **OrderDetail** jsou vnořené ve schématu.</span><span class="sxs-lookup"><span data-stu-id="799dc-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="799dc-112">Proces mapování nevytváří žádná omezení.</span><span class="sxs-lookup"><span data-stu-id="799dc-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="799dc-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="799dc-113">See also</span></span>

- [<span data-ttu-id="799dc-114">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="799dc-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="799dc-115">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="799dc-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="799dc-116">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="799dc-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
