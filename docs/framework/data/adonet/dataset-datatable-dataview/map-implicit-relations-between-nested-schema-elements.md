---
title: Mapování implicitních relací mezi elementy ve vnořeném schématu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: dc5b81fd06f2860283c8c5fa028af4b945e2b1e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150960"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="9cfe9-102">Mapování implicitních relací mezi elementy ve vnořeném schématu</span><span class="sxs-lookup"><span data-stu-id="9cfe9-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="9cfe9-103">Schéma definice schématu XML (XSD) může mít složité typy vnořené uvnitř sebe.</span><span class="sxs-lookup"><span data-stu-id="9cfe9-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="9cfe9-104">V tomto případě proces mapování použije výchozí mapování a <xref:System.Data.DataSet>vytvoří následující v :</span><span class="sxs-lookup"><span data-stu-id="9cfe9-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="9cfe9-105">Jedna tabulka pro každý z komplexních typů (nadřazený a podřízený).</span><span class="sxs-lookup"><span data-stu-id="9cfe9-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="9cfe9-106">Pokud v nadřazeném objektu neexistuje žádné jedinečné omezení, jeden další sloupec primárního klíče pro definici tabulky s názvem *Název_tabulky*_Id kde *název tablename* je název nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="9cfe9-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="9cfe9-107">Omezení primárního klíče v nadřazené tabulce identifikující další sloupec jako primární klíč (nastavením vlastnosti **IsPrimaryKey** na **hodnotu True).**</span><span class="sxs-lookup"><span data-stu-id="9cfe9-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="9cfe9-108">Omezení se nazývá\# \# Omezení, kde je 1, 2, 3 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="9cfe9-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="9cfe9-109">Například výchozí název pro první omezení je Constraint1.</span><span class="sxs-lookup"><span data-stu-id="9cfe9-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="9cfe9-110">Omezení cizího klíče v podřízené tabulce identifikující další sloupec jako cizí klíč odkazující na primární klíč nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="9cfe9-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="9cfe9-111">Omezení je pojmenováno *ParentTable_ChildTable* kde *ParentTable* je název nadřazené tabulky a *ChildTable* je název podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="9cfe9-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="9cfe9-112">Datový vztah mezi nadřazenou a podřízenou tabulkou.</span><span class="sxs-lookup"><span data-stu-id="9cfe9-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="9cfe9-113">Následující příklad ukazuje schéma, kde **OrderDetail** je podřízený prvek **Order**.</span><span class="sxs-lookup"><span data-stu-id="9cfe9-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="9cfe9-114">Proces mapování schématu XML vytvoří v **datové sadě**následující:</span><span class="sxs-lookup"><span data-stu-id="9cfe9-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="9cfe9-115">**Objednávka** a **orderdetail** tabulka.</span><span class="sxs-lookup"><span data-stu-id="9cfe9-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="9cfe9-116">Jedinečné omezení v tabulce **Objednávka.**</span><span class="sxs-lookup"><span data-stu-id="9cfe9-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="9cfe9-117">Všimněte si, že **IsPrimaryKey** vlastnost je nastavena na **True**.</span><span class="sxs-lookup"><span data-stu-id="9cfe9-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="9cfe9-118">Omezení cizího klíče v tabulce **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="9cfe9-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- <span data-ttu-id="9cfe9-119">Vztah mezi tabulkami **Order** a **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="9cfe9-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="9cfe9-120">**Vnořené vlastnosti** pro tento vztah je nastavena na **True,** protože **Order** a **OrderDetail** prvky jsou vnořeny do schématu.</span><span class="sxs-lookup"><span data-stu-id="9cfe9-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: Order_Id
    ChildTable: OrderDetail  
    ChildColumns: Order_Id
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9cfe9-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cfe9-121">See also</span></span>

- [<span data-ttu-id="9cfe9-122">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="9cfe9-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="9cfe9-123">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="9cfe9-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="9cfe9-124">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9cfe9-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
