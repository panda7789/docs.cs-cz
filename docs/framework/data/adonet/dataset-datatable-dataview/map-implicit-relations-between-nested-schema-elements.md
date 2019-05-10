---
title: Mapování implicitních relací mezi elementy ve vnořeném schématu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 6fcb0b9bb7c947359c2334d3d116f5317f84af83
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586809"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="94666-102">Mapování implicitních relací mezi elementy ve vnořeném schématu</span><span class="sxs-lookup"><span data-stu-id="94666-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="94666-103">Jazyk (XSD) schématu definice schématu XML může mít složité typy vnořené do jiné.</span><span class="sxs-lookup"><span data-stu-id="94666-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="94666-104">V takovém případě proces mapování použije výchozí mapování a vytvoří v následující <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="94666-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="94666-105">Jednu tabulku pro každý z komplexních typů (nadřazené a podřízené).</span><span class="sxs-lookup"><span data-stu-id="94666-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="94666-106">Pokud neexistuje žádné omezení unique u nadřazené, jeden další sloupec primárního klíče na definici tabulky s názvem *TableName*_Id kde *TableName* je název nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="94666-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="94666-107">Omezení primárního klíče na identifikaci další sloupec jako primární klíč nadřazené tabulky (nastavením **isprimarykey hodnotu** vlastnost **True**).</span><span class="sxs-lookup"><span data-stu-id="94666-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="94666-108">Omezení jmenuje omezení\# kde \# je 1, 2, 3 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="94666-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="94666-109">Například výchozí název pro první omezení je Constraint1.</span><span class="sxs-lookup"><span data-stu-id="94666-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="94666-110">Omezení cizího klíče v podřízené tabulce, určení dalších sloupců jako cizí klíč odkazující na primární klíč nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="94666-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="94666-111">Název omezení *ParentTable_ChildTable* kde *ParentTable* je název nadřazené tabulky a *tabulka* je název podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="94666-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="94666-112">Datová relace mezi nadřazenými a podřízenými tabulkami.</span><span class="sxs-lookup"><span data-stu-id="94666-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="94666-113">Následující příklad ukazuje schématu kde **OrderDetail** je podřízený prvek **pořadí**.</span><span class="sxs-lookup"><span data-stu-id="94666-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="94666-114">Proces mapování schématu XML vytvoří následující **datovou sadu**:</span><span class="sxs-lookup"><span data-stu-id="94666-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="94666-115">**Pořadí** a **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="94666-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="94666-116">Omezení unique u **pořadí** tabulky.</span><span class="sxs-lookup"><span data-stu-id="94666-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="94666-117">Všimněte si, že **isprimarykey hodnotu** je nastavena na **True**.</span><span class="sxs-lookup"><span data-stu-id="94666-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="94666-118">Omezení cizího klíče na **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="94666-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- <span data-ttu-id="94666-119">Vztah mezi **pořadí** a **OrderDetail** tabulky.</span><span class="sxs-lookup"><span data-stu-id="94666-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="94666-120">**Vnořené** pro tento vztah je nastavena na **True** vzhledem k tomu, **pořadí** a **OrderDetail** elementů je vnořeno ve schématu .</span><span class="sxs-lookup"><span data-stu-id="94666-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="94666-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94666-121">See also</span></span>

- [<span data-ttu-id="94666-122">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="94666-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="94666-123">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="94666-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="94666-124">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="94666-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
