---
title: Generování relací datové sady ze schématu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: fd32d024acca393dcc8241f047a305e763682866
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204860"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="226e5-102">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="226e5-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="226e5-103">V a <xref:System.Data.DataSet>tvoří přidružení mezi dvěma nebo více sloupci vytvořením vztahu nadřízený-podřízený.</span><span class="sxs-lookup"><span data-stu-id="226e5-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="226e5-104">Existují tři způsoby, jak znázornit relaci **datové sady** v rámci schématu XSD (XML Schema Definition Language):</span><span class="sxs-lookup"><span data-stu-id="226e5-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="226e5-105">Zadejte vnořené komplexní typy.</span><span class="sxs-lookup"><span data-stu-id="226e5-105">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="226e5-106">Použijte anotaci **msdata: Relationship** .</span><span class="sxs-lookup"><span data-stu-id="226e5-106">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="226e5-107">Určete **xs: keyref** bez anotace **msdata: ConstraintOnly** .</span><span class="sxs-lookup"><span data-stu-id="226e5-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="226e5-108">Vnořené komplexní typy</span><span class="sxs-lookup"><span data-stu-id="226e5-108">Nested Complex Types</span></span>  
 <span data-ttu-id="226e5-109">Vnořené definice komplexního typu ve schématu označují vztahy nadřazenosti a podřízenosti prvků.</span><span class="sxs-lookup"><span data-stu-id="226e5-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="226e5-110">Následující fragment schématu XML ukazuje, že **OrderDetail** je podřízeným prvkem elementu **Order** .</span><span class="sxs-lookup"><span data-stu-id="226e5-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="226e5-111">Proces mapování schématu XML vytvoří tabulky v **datové sadě** , které odpovídají vnořeným komplexním typům ve schématu.</span><span class="sxs-lookup"><span data-stu-id="226e5-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="226e5-112">Vytvoří také další sloupce, které jsou používány jako nadřazené **-** podřízené sloupce pro vygenerované tabulky.</span><span class="sxs-lookup"><span data-stu-id="226e5-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="226e5-113">Všimněte si, že **-** tyto nadřazené podřízené sloupce určují relace, které se neshodují s určením omezení primárního klíče nebo cizího klíče.</span><span class="sxs-lookup"><span data-stu-id="226e5-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="226e5-114">msdata: Poznámka vztahu</span><span class="sxs-lookup"><span data-stu-id="226e5-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="226e5-115">Anotace **msdata: Relationship** umožňuje explicitně zadat vztahy nadřazenosti a podřízenosti mezi prvky ve schématu, které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="226e5-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="226e5-116">Následující příklad ukazuje strukturu elementu **Relationship** .</span><span class="sxs-lookup"><span data-stu-id="226e5-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="226e5-117">Atributy **msdata:** anotace Relationship identifikují prvky zahrnuté v relaci nadřazený-podřízený a také elementy **vlastnosti ParentKey** a **ChildKey** a atributy, které jsou součástí relace.</span><span class="sxs-lookup"><span data-stu-id="226e5-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="226e5-118">Proces mapování používá tyto informace ke generování tabulek v **datové sadě** a k vytvoření vztahu primárního klíče/cizího klíče mezi těmito tabulkami.</span><span class="sxs-lookup"><span data-stu-id="226e5-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="226e5-119">Například následující fragment schématu určuje **pořadí** a **OrderDetail** prvky na stejné úrovni (nevnořený).</span><span class="sxs-lookup"><span data-stu-id="226e5-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="226e5-120">Schéma určuje anotaci **msdata: Relationship** , která určuje vztah nadřazenosti a podřízenosti mezi těmito dvěma prvky.</span><span class="sxs-lookup"><span data-stu-id="226e5-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="226e5-121">V takovém případě je nutné zadat explicitní relaci pomocí poznámky **msdata: Relationship** .</span><span class="sxs-lookup"><span data-stu-id="226e5-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
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
  
 <span data-ttu-id="226e5-122">Proces mapování používá element **Relationship** k vytvoření vztahu nadřízený-podřízený mezi sloupcem **OrderNumber** v tabulce **Order** a sloupcem **OrderNo** v tabulce **OrderDetail** v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="226e5-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="226e5-123">Proces mapování určuje pouze vztah; neurčuje automaticky žádná omezení pro hodnoty v těchto sloupcích, stejně jako omezení primárního klíče a cizího klíče v relačních databázích.</span><span class="sxs-lookup"><span data-stu-id="226e5-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="226e5-124">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="226e5-124">In This Section</span></span>  
 [<span data-ttu-id="226e5-125">Mapování implicitních relací mezi elementy ve vnořeném schématu</span><span class="sxs-lookup"><span data-stu-id="226e5-125">Map Implicit Relations Between Nested Schema Elements</span></span>](map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="226e5-126">Popisuje omezení a vztahy, které jsou implicitně vytvořeny v **datové sadě** , pokud jsou ve schématu XML zjištěny vnořené prvky.</span><span class="sxs-lookup"><span data-stu-id="226e5-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="226e5-127">Mapování relací zadaných pro vnořené elementy</span><span class="sxs-lookup"><span data-stu-id="226e5-127">Map Relations Specified for Nested Elements</span></span>](map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="226e5-128">Popisuje způsob explicitního nastavování vztahů v **datové sadě** pro vnořené prvky ve schématu XML.</span><span class="sxs-lookup"><span data-stu-id="226e5-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="226e5-129">Určení relací mezi elementy bez vnoření</span><span class="sxs-lookup"><span data-stu-id="226e5-129">Specify Relations Between Elements with No Nesting</span></span>](specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="226e5-130">Popisuje, jak vytvořit relace v **datové sadě** mezi prvky schématu XML, které nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="226e5-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="226e5-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="226e5-131">Related Sections</span></span>  
 [<span data-ttu-id="226e5-132">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="226e5-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="226e5-133">Popisuje relační strukturu neboli schéma pro **datovou sadu** , která je vytvořena ze schématu XSD (XML Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="226e5-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="226e5-134">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="226e5-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="226e5-135">Popisuje prvky schématu XML, které slouží k vytváření omezení jedinečného a cizího klíče v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="226e5-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226e5-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="226e5-136">See also</span></span>

- [<span data-ttu-id="226e5-137">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="226e5-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
