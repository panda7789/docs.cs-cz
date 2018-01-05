---
title: "Mapa implicitní vztahy mezi elementy vnořené schématu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0ad26637ec8cd3e9ea555a20810805cf6eb1444e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="43cdc-102">Mapa implicitní vztahy mezi elementy vnořené schématu</span><span class="sxs-lookup"><span data-stu-id="43cdc-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="43cdc-103">Schématu schématu XML definition language (XSD) může mít komplexní typy vnořit do sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="43cdc-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="43cdc-104">V takovém případě proces mapování použije výchozí mapování a vytvoří následující <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="43cdc-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="43cdc-105">Jedna tabulka pro každou komplexních typů (nadřazené a podřízené).</span><span class="sxs-lookup"><span data-stu-id="43cdc-105">One table for each of the complex types (parent and child).</span></span>  
  
-   <span data-ttu-id="43cdc-106">Pokud na nadřazené neexistuje žádné jedinečné omezení, jeden další sloupec primárního klíče na definici tabulky s názvem *TableName*_Id kde *TableName* je název nadřazené tabulce.</span><span class="sxs-lookup"><span data-stu-id="43cdc-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
-   <span data-ttu-id="43cdc-107">Omezení primárního klíče v nadřazené tabulce identifikace další sloupec jako primární klíč (nastavením **IsPrimaryKey** vlastnost **True**).</span><span class="sxs-lookup"><span data-stu-id="43cdc-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="43cdc-108">Omezení jmenuje omezení *#*  kde  *#*  je 1, 2, 3 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="43cdc-108">The constraint is named Constraint*#* where *#* is 1, 2, 3, and so on.</span></span> <span data-ttu-id="43cdc-109">Například výchozí název pro první omezení je Constraint1.</span><span class="sxs-lookup"><span data-stu-id="43cdc-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
-   <span data-ttu-id="43cdc-110">Omezení cizího klíče na podřízenou tabulku identifikace další sloupec jako cizí klíč odkazující na primární klíč v nadřazené tabulce.</span><span class="sxs-lookup"><span data-stu-id="43cdc-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="43cdc-111">Název omezení *ParentTable_ChildTable* kde *ParentTable* je název nadřazené tabulky a *tabulka* je název podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="43cdc-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
-   <span data-ttu-id="43cdc-112">Data vztah mezi nadřazenou a podřízenou tabulkou.</span><span class="sxs-lookup"><span data-stu-id="43cdc-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="43cdc-113">Následující příklad ukazuje schéma kde **OrderDetail** je podřízený prvek **pořadí**.</span><span class="sxs-lookup"><span data-stu-id="43cdc-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="43cdc-114">Proces mapování schématu XML vytvoří následující **datovou sadu**:</span><span class="sxs-lookup"><span data-stu-id="43cdc-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
-   <span data-ttu-id="43cdc-115">**Pořadí** a **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="43cdc-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   <span data-ttu-id="43cdc-116">Jedinečná omezení **pořadí** tabulky.</span><span class="sxs-lookup"><span data-stu-id="43cdc-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="43cdc-117">Všimněte si, že **IsPrimaryKey** je nastavena na **True**.</span><span class="sxs-lookup"><span data-stu-id="43cdc-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   <span data-ttu-id="43cdc-118">Omezení cizího klíče na **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="43cdc-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   <span data-ttu-id="43cdc-119">Vztah mezi **pořadí** a **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="43cdc-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="43cdc-120">**Vnořené** pro tento vztah je nastavena na **True** protože **pořadí** a **OrderDetail** vnořené prvky ve schématu .</span><span class="sxs-lookup"><span data-stu-id="43cdc-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: Order_Id   
    ChildTable: OrderDetail  
    ChildColumns: Order_Id   
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="43cdc-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="43cdc-121">See Also</span></span>  
 [<span data-ttu-id="43cdc-122">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="43cdc-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="43cdc-123">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="43cdc-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="43cdc-124">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="43cdc-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
