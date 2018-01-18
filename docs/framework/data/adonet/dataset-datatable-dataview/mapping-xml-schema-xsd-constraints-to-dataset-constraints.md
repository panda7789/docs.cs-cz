---
title: "Omezení (XSD) schématu XML mapování k omezení datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f403dc974e4fe67d239688f587061cd23a8deff6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="4d9f4-102">Omezení (XSD) schématu XML mapování k omezení datové sady</span><span class="sxs-lookup"><span data-stu-id="4d9f4-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="4d9f4-103">Jazyk definice schématu XML (XSD) umožňuje omezení ho zadat na elementy a atributy, které ho definuje.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="4d9f4-104">Při mapování schématu XML na relační schéma v <xref:System.Data.DataSet>, schématu XML omezení jsou namapované na příslušné relační omezení tabulek a sloupců v rámci **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="4d9f4-105">Tato část popisuje mapování schématu XML následující omezení:</span><span class="sxs-lookup"><span data-stu-id="4d9f4-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
-   <span data-ttu-id="4d9f4-106">Omezení jedinečnosti zadán pomocí **jedinečný** elementu.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
-   <span data-ttu-id="4d9f4-107">Omezení klíč zadaný pomocí **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-107">The key constraint specified using the **key** element.</span></span>  
  
-   <span data-ttu-id="4d9f4-108">Omezení keyref zadán pomocí **keyref** elementu.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="4d9f4-109">Pomocí omezení k elementu nebo atributu zadejte určitá omezení na hodnotách element v žádné instanci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="4d9f4-110">Například klíče omezení **CustomerID** podřízený prvek **zákazníka** element ve schématu znamená, že hodnoty **CustomerID** podřízený element musí být v žádné instanci dokumentu jedinečný a že hodnoty null nejsou povolené.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="4d9f4-111">Omezení lze zadat také mezi elementy a atributy v dokumentu, aby bylo možné vytvořit vztah v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="4d9f4-112">Klíč a keyref omezení lze ve schématu zadejte omezení v tomto dokumentu, výsledkem je vztah mezi dokumentu elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="4d9f4-113">Proces mapování převede těchto omezení schématu odpovídající omezení tabulky v rámci vytvořili **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4d9f4-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4d9f4-114">In This Section</span></span>  
 [<span data-ttu-id="4d9f4-115">Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="4d9f4-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="4d9f4-116">Popisuje elementy schématu XML použitý k vytvoření jedinečné omezení **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="4d9f4-117">Mapování klíčových omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="4d9f4-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="4d9f4-118">Popisuje elementy schématu XML použitý k vytvoření klíče omezení (kde hodnoty null nejsou povolené jedinečná omezení) **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="4d9f4-119">Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="4d9f4-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="4d9f4-120">Popisuje elementy schématu XML použitý k vytvoření keyref omezení (cizí klíč) **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4d9f4-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4d9f4-121">Related Sections</span></span>  
 [<span data-ttu-id="4d9f4-122">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="4d9f4-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="4d9f4-123">Popisuje relační struktura nebo schéma z **datovou sadu** vytvořený z schématu XSD.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="4d9f4-124">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="4d9f4-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="4d9f4-125">Popisuje elementy schématu XML použitý k vytvoření relace mezi sloupci tabulky v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="4d9f4-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d9f4-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d9f4-126">See Also</span></span>  
 [<span data-ttu-id="4d9f4-127">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="4d9f4-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
