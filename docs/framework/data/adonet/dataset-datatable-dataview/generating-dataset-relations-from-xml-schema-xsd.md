---
title: Generování relací datové sady ze schématu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 29c0e9ee96c376c6da392692febccbbae3c6a33f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170219"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="ecb65-102">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="ecb65-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="ecb65-103">V <xref:System.Data.DataSet>, formuláře přidružení mezi dvěma nebo více sloupců tak, že vytvoříte vztah nadřízenosti a podřízenosti.</span><span class="sxs-lookup"><span data-stu-id="ecb65-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="ecb65-104">Existují tři způsoby, jak reprezentaci **datovou sadu** vztahu v rámci schématu schématu XML definice jazyk (XSD):</span><span class="sxs-lookup"><span data-stu-id="ecb65-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
-   <span data-ttu-id="ecb65-105">Zadejte vnořené komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="ecb65-105">Specify nested complex types.</span></span>  
  
-   <span data-ttu-id="ecb65-106">Použití **msdata:Relationship** poznámky.</span><span class="sxs-lookup"><span data-stu-id="ecb65-106">Use the **msdata:Relationship** annotation.</span></span>  
  
-   <span data-ttu-id="ecb65-107">Zadejte **xs:keyref** bez **msdata:ConstraintOnly** poznámky.</span><span class="sxs-lookup"><span data-stu-id="ecb65-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="ecb65-108">Vnořené komplexní typy</span><span class="sxs-lookup"><span data-stu-id="ecb65-108">Nested Complex Types</span></span>  
 <span data-ttu-id="ecb65-109">Vnořené komplexní typ definice ve schématu označují vztahy nadřazenosti a podřízenosti prvků.</span><span class="sxs-lookup"><span data-stu-id="ecb65-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="ecb65-110">Následující fragment XML schéma ukazuje, že **OrderDetail** je podřízený prvek **pořadí** elementu.</span><span class="sxs-lookup"><span data-stu-id="ecb65-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>          
       <xs:element name="OrderDetail" />  
           <xs:complexType>               
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="ecb65-111">Proces mapování schématu XML vytvoří tabulky v **datovou sadu** , které odpovídají vnořené komplexní typy ve schématu.</span><span class="sxs-lookup"><span data-stu-id="ecb65-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="ecb65-112">Vytvoří také další sloupce, které se používají jako nadřazený**-** podřízené sloupce pro generované tabulky.</span><span class="sxs-lookup"><span data-stu-id="ecb65-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="ecb65-113">Všimněte si, že tyto nadřazené**-** podřízené sloupce zadejte relace, která není stejné jako zadání omezení primárního klíče a cizího klíče.</span><span class="sxs-lookup"><span data-stu-id="ecb65-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="ecb65-114">MSDATA:Relationship poznámky</span><span class="sxs-lookup"><span data-stu-id="ecb65-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="ecb65-115">**Msdata:Relationship** anotace umožňuje explicitně určit vztahů nadřazenosti a podřízenosti mezi elementy ve schématu, které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="ecb65-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="ecb65-116">Následující příklad ukazuje strukturu **vztah** elementu.</span><span class="sxs-lookup"><span data-stu-id="ecb65-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="ecb65-117">Atributy **msdata:Relationship** anotace identifikaci prvků, které jsou zahrnuté ve vztahu nadřazený podřízený, stejně jako **vlastnosti parentkey** a **childkey** elementy a atributy, které jsou součástí relace.</span><span class="sxs-lookup"><span data-stu-id="ecb65-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="ecb65-118">Proces mapování používá tyto informace k vygenerování tabulek v **datovou sadu** a vytvořte primární klíč, cizí klíče vztah mezi těmito tabulkami.</span><span class="sxs-lookup"><span data-stu-id="ecb65-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="ecb65-119">Například následující fragment schéma určuje **pořadí** a **OrderDetail** elementů na stejné úrovni (ne vnořenou).</span><span class="sxs-lookup"><span data-stu-id="ecb65-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="ecb65-120">Určuje schéma **msdata:Relationship** poznámky, které určuje vztah nadřízenosti a podřízenosti mezi těmito dvěma elementy.</span><span class="sxs-lookup"><span data-stu-id="ecb65-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="ecb65-121">V takovém případě explicitního vztahu musí být zadán pomocí **msdata:Relationship** poznámky.</span><span class="sxs-lookup"><span data-stu-id="ecb65-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"   
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 <span data-ttu-id="ecb65-122">Používá proces mapování **vztah** prvku k vytvoření vztahu nadřazený podřízený mezi **OrderNumber** sloupec **pořadí** tabulky a **OrderNo** sloupec v **OrderDetail** v tabulku **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="ecb65-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="ecb65-123">Proces mapování pouze určuje vztah; neurčuje automaticky jakákoliv omezení u hodnot v těchto sloupcích, stejně jako primární klíč nebo omezení cizího klíče v relační databáze.</span><span class="sxs-lookup"><span data-stu-id="ecb65-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="ecb65-124">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ecb65-124">In This Section</span></span>  
 [<span data-ttu-id="ecb65-125">Mapování implicitních relací mezi elementy ve vnořeném schématu</span><span class="sxs-lookup"><span data-stu-id="ecb65-125">Map Implicit Relations Between Nested Schema Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="ecb65-126">Popisuje omezení a vztahy, které se implicitně vytvářejí v **datovou sadu** při výskytu vnořené elementy ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="ecb65-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="ecb65-127">Mapování relací zadaných pro vnořené elementy</span><span class="sxs-lookup"><span data-stu-id="ecb65-127">Map Relations Specified for Nested Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="ecb65-128">Popisuje, jak nastavit explicitně vztahy v **datovou sadu** pro vnořené prvky ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="ecb65-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="ecb65-129">Určení relací mezi elementy bez vnoření</span><span class="sxs-lookup"><span data-stu-id="ecb65-129">Specify Relations Between Elements with No Nesting</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="ecb65-130">Popisuje, jak vytvořit vztahy v **datovou sadu** mezi prvky schématu XML, které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="ecb65-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="ecb65-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ecb65-131">Related Sections</span></span>  
 [<span data-ttu-id="ecb65-132">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="ecb65-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="ecb65-133">Popisuje relační struktury nebo schématu, **datovou sadu** , který je vytvořen z jazyk (XSD) schématu definice schématu XML.</span><span class="sxs-lookup"><span data-stu-id="ecb65-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="ecb65-134">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="ecb65-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="ecb65-135">Popisuje prvky schématu XML použitý k vytvoření jedinečné a cizího klíče omezení **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="ecb65-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb65-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecb65-136">See also</span></span>

- [<span data-ttu-id="ecb65-137">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="ecb65-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
