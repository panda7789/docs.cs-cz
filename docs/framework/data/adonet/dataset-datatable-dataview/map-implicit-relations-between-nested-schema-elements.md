---
title: Mapování implicitních relací mezi elementy ve vnořeném schématu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 25fc2c427727273038f7b4267376d6ba6446b811
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040387"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="3d450-102">Mapování implicitních relací mezi elementy ve vnořeném schématu</span><span class="sxs-lookup"><span data-stu-id="3d450-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="3d450-103">Schéma jazyka XML Schema Definition Language (XSD) může mít vnořené typy vnořené uvnitř sebe.</span><span class="sxs-lookup"><span data-stu-id="3d450-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="3d450-104">V takovém případě proces mapování použije výchozí mapování a v <xref:System.Data.DataSet>vytvoří následující:</span><span class="sxs-lookup"><span data-stu-id="3d450-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="3d450-105">Jedna tabulka pro každý ze složitých typů (nadřazených a podřízených).</span><span class="sxs-lookup"><span data-stu-id="3d450-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="3d450-106">Pokud v nadřazeném prvku neexistuje žádné jedinečné omezení, jeden další sloupec primárního klíče na definici tabulky s názvem *TableName*_Id, kde *TableName* je název nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="3d450-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="3d450-107">Omezení primárního klíče v nadřazené tabulce, které identifikuje další sloupec jako primární klíč (nastavením vlastnosti **IsPrimaryKey** na **hodnotu true**).</span><span class="sxs-lookup"><span data-stu-id="3d450-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="3d450-108">Omezení je pojmenované\#, kde \# je 1, 2, 3 atd.</span><span class="sxs-lookup"><span data-stu-id="3d450-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="3d450-109">Výchozím názvem pro první omezení je například Constraint1.</span><span class="sxs-lookup"><span data-stu-id="3d450-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="3d450-110">Omezení cizího klíče v podřízené tabulce identifikující další sloupec jako cizí klíč odkazující na primární klíč nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="3d450-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="3d450-111">Omezení je pojmenované *ParentTable_ChildTable* , kde *Parent* je název nadřazené tabulky a *Podřízená* tabulka je název podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="3d450-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="3d450-112">Vztah dat mezi nadřazenými a podřízenými tabulkami.</span><span class="sxs-lookup"><span data-stu-id="3d450-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="3d450-113">Následující příklad ukazuje schéma, kde **OrderDetail** je podřízeným prvkem **Order**.</span><span class="sxs-lookup"><span data-stu-id="3d450-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="3d450-114">Proces mapování schématu XML vytvoří v **datové sadě**následující:</span><span class="sxs-lookup"><span data-stu-id="3d450-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="3d450-115">**Objednávka** a tabulka **OrderDetail**</span><span class="sxs-lookup"><span data-stu-id="3d450-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="3d450-116">Jedinečné omezení v tabulce **Order** .</span><span class="sxs-lookup"><span data-stu-id="3d450-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="3d450-117">Všimněte si, že vlastnost **IsPrimaryKey** je nastavena na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="3d450-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="3d450-118">Omezení cizího klíče v tabulce **OrderDetail**</span><span class="sxs-lookup"><span data-stu-id="3d450-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- <span data-ttu-id="3d450-119">Vztah mezi tabulkami **Order** a **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="3d450-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="3d450-120">**Vnořená** vlastnost pro tento vztah je nastavena na **hodnotu true** , protože prvky **Order** a **OrderDetail** jsou vnořené ve schématu.</span><span class="sxs-lookup"><span data-stu-id="3d450-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d450-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d450-121">See also</span></span>

- [<span data-ttu-id="3d450-122">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="3d450-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="3d450-123">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="3d450-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="3d450-124">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3d450-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
