---
title: "Generování datovou sadu vztahů ze schématu XML (XSD)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bda9ff0052c6dc2462f007e3febb3cbf9ca7d5ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="58b45-102">Generování datovou sadu vztahů ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="58b45-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="58b45-103">V <xref:System.Data.DataSet>, vytvoří přidružení mezi dvěma nebo více sloupců tak, že vytvoříte vztah nadřazený podřízený.</span><span class="sxs-lookup"><span data-stu-id="58b45-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="58b45-104">Existují tři způsoby, jak představují **datovou sadu** vztahu v rámci schématu schématu XML definition language (XSD):</span><span class="sxs-lookup"><span data-stu-id="58b45-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
-   <span data-ttu-id="58b45-105">Zadejte vnořené komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="58b45-105">Specify nested complex types.</span></span>  
  
-   <span data-ttu-id="58b45-106">Použití **msdata:Relationship** poznámky.</span><span class="sxs-lookup"><span data-stu-id="58b45-106">Use the **msdata:Relationship** annotation.</span></span>  
  
-   <span data-ttu-id="58b45-107">Zadejte **xs:keyref** bez **msdata:ConstraintOnly** poznámky.</span><span class="sxs-lookup"><span data-stu-id="58b45-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="58b45-108">Vnořené komplexní typy</span><span class="sxs-lookup"><span data-stu-id="58b45-108">Nested Complex Types</span></span>  
 <span data-ttu-id="58b45-109">Vnořené komplexní typ definice ve schématu označte vztahy nadřazených a podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="58b45-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="58b45-110">Následující fragment kódu XML schéma ukazuje, že **OrderDetail** je podřízený element **pořadí** elementu.</span><span class="sxs-lookup"><span data-stu-id="58b45-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="58b45-111">Proces mapování schématu XML vytváří tabulky v **datovou sadu** , odpovídají vnořené komplexní typy ve schématu.</span><span class="sxs-lookup"><span data-stu-id="58b45-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="58b45-112">Vytvoří také další sloupce, které se používají jako nadřazený**-**podřízené sloupce pro generovaný tabulky.</span><span class="sxs-lookup"><span data-stu-id="58b45-112">It also creates additional columns that are used as parent**-**child columns for the generated tables.</span></span> <span data-ttu-id="58b45-113">Všimněte si, že tyto nadřazených**-**podřízené sloupce zadejte relace, který není stejný jako při zadání omezení primárního klíče a cizího klíče.</span><span class="sxs-lookup"><span data-stu-id="58b45-113">Note that these parent**-**child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="58b45-114">MSDATA:Relationship – Poznámka</span><span class="sxs-lookup"><span data-stu-id="58b45-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="58b45-115">**Msdata:Relationship** poznámky umožňuje explicitně zadat vztahů nadřazenosti a podřízenosti mezi elementy ve schématu, které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="58b45-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="58b45-116">Následující příklad ukazuje strukturu **vztah** elementu.</span><span class="sxs-lookup"><span data-stu-id="58b45-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="58b45-117">Atributy **msdata:Relationship** poznámky identifikovat elementy zahrnutých v relaci nadřazený podřízený, stejně jako **vlastnosti parentkey** a **childkey** elementy a atributy, které jsou součástí relace.</span><span class="sxs-lookup"><span data-stu-id="58b45-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="58b45-118">Proces mapování používá tyto informace k vygenerování tabulky v **datovou sadu** a vytvořte primární klíč, cizí klíče relace mezi těmito tabulkami.</span><span class="sxs-lookup"><span data-stu-id="58b45-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="58b45-119">Například následující schéma fragment Určuje **pořadí** a **OrderDetail** prvků na stejné úrovni (nevnořené).</span><span class="sxs-lookup"><span data-stu-id="58b45-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="58b45-120">Určuje schéma **msdata:Relationship** poznámky, která určuje relaci nadřazený podřízený mezi tyto dva prvky.</span><span class="sxs-lookup"><span data-stu-id="58b45-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="58b45-121">V takovém případě explicitní relace musí být určen pomocí **msdata:Relationship** poznámky.</span><span class="sxs-lookup"><span data-stu-id="58b45-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
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
  
 <span data-ttu-id="58b45-122">Proces mapování používá **vztah** elementu, který chcete vytvořit relaci nadřazený podřízený mezi **OrderNumber** sloupec v **pořadí** tabulky a **OrderNo** sloupec v **OrderDetail** tabulky v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="58b45-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="58b45-123">Proces mapování určuje pouze relace; neurčuje automaticky žádná omezení na hodnoty v těchto sloupcích, stejně jako primární klíč, cizí klíče omezení relačních databází.</span><span class="sxs-lookup"><span data-stu-id="58b45-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="58b45-124">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="58b45-124">In This Section</span></span>  
 [<span data-ttu-id="58b45-125">Mapa implicitní vztahy mezi elementy vnořené schématu</span><span class="sxs-lookup"><span data-stu-id="58b45-125">Map Implicit Relations Between Nested Schema Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="58b45-126">Popisuje omezení a vztahy, které jsou implicitně vytvořené v **datovou sadu** když dojde k vnořených elementů v schématu XML.</span><span class="sxs-lookup"><span data-stu-id="58b45-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="58b45-127">Mapování vztahy zadané pro vnořené prvky</span><span class="sxs-lookup"><span data-stu-id="58b45-127">Map Relations Specified for Nested Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="58b45-128">Popisuje, jak nastavit explicitně vztahů v **datovou sadu** pro vnořené prvky ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="58b45-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="58b45-129">Určit vztahy mezi elementy s bez vnoření</span><span class="sxs-lookup"><span data-stu-id="58b45-129">Specify Relations Between Elements with No Nesting</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="58b45-130">Popisuje postup vytvoření vztahů v **datovou sadu** mezi elementy schématu XML, které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="58b45-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="58b45-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="58b45-131">Related Sections</span></span>  
 [<span data-ttu-id="58b45-132">Odvozování relační strukturu datové sady z schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="58b45-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="58b45-133">Popisuje relační struktura nebo schéma z **datovou sadu** vytvořený ze schématu XML definition language (XSD) schématu.</span><span class="sxs-lookup"><span data-stu-id="58b45-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="58b45-134">Omezení (XSD) schématu XML mapování k omezení datové sady</span><span class="sxs-lookup"><span data-stu-id="58b45-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="58b45-135">Popisuje elementy schématu XML použitý k vytvoření jedinečné a cizí klíče omezení **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="58b45-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b45-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="58b45-136">See Also</span></span>  
 [<span data-ttu-id="58b45-137">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="58b45-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
