---
title: "Odvození relační strukturu datové sady z XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bae6e82eaf0f01847c304e094d98fe420e6f8b65
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-dataset-relational-structure-from-xml"></a><span data-ttu-id="2a0a4-102">Odvození relační strukturu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="2a0a4-102">Inferring DataSet Relational Structure from XML</span></span>
<span data-ttu-id="2a0a4-103">Relační struktura nebo schéma z <xref:System.Data.DataSet> se skládá z tabulky, sloupce, omezení a vztahů.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-103">The relational structure, or schema, of a <xref:System.Data.DataSet> is made up of tables, columns, constraints, and relations.</span></span> <span data-ttu-id="2a0a4-104">Při načítání <xref:System.Data.DataSet> ze souboru XML, můžete předem definovaná schématu, ale mohou být vytvořeny, explicitně nebo prostřednictvím odvozená z XML načítá.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-104">When loading a <xref:System.Data.DataSet> from XML, the schema can be predefined, or it can be created, either explicitly or through inference, from the XML being loaded.</span></span> <span data-ttu-id="2a0a4-105">Další informace o načítání schématu a obsah <xref:System.Data.DataSet> ze souboru XML, najdete v části [načítání datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) a [načítání datovou sadu informace o schématu z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2a0a4-105">For more information about loading the schema and contents of a <xref:System.Data.DataSet> from XML, see [Loading a DataSet from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) and [Loading DataSet Schema Information from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).</span></span>  
  
 <span data-ttu-id="2a0a4-106">Pokud schéma <xref:System.Data.DataSet> se vytváří z XML, je upřednostňovanou metodou k explicitnímu zadání schématu pomocí schématu XML definice jazyka (XSD) (jak je popsáno v [odvozování relační strukturu datové sady z schématu XML (XSD) ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)) nebo XML Data snížit (XDR).</span><span class="sxs-lookup"><span data-stu-id="2a0a4-106">If the schema of a <xref:System.Data.DataSet> is being created from XML, the preferred method is to explicitly specify the schema using either the XML Schema definition language (XSD) (as described in [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)) or the XML-Data Reduced (XDR).</span></span> <span data-ttu-id="2a0a4-107">Pokud je k dispozici v souboru XML, schéma žádné schéma schématu XML nebo XDR <xref:System.Data.DataSet> lze odvodit z strukturu XML elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-107">If no XML Schema or XDR schema is available in the XML, the schema of the <xref:System.Data.DataSet> can be inferred from the structure of the XML elements and attributes.</span></span>  
  
 <span data-ttu-id="2a0a4-108">Tato část popisuje pravidla pro <xref:System.Data.DataSet> odvození schématu zobrazením elementů XML a atributy a jejich struktura a výsledná odvodit <xref:System.Data.DataSet> schématu.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-108">This section describes the rules for <xref:System.Data.DataSet> schema inference by showing XML elements and attributes and their structure, and the resulting inferred <xref:System.Data.DataSet> schema.</span></span>  
  
 <span data-ttu-id="2a0a4-109">Všechny atributy, které se nachází v dokumentu XML by měl být součástí procesu odvození.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-109">Not all attributes present in an XML document should be included in the inference process.</span></span> <span data-ttu-id="2a0a4-110">Namespace kvalifikovaný atributy mohou zahrnovat metadata, která je důležité pro dokument XML, ale ne <xref:System.Data.DataSet> schématu.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-110">Namespace-qualified attributes can include metadata that is important for the XML document but not for the <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="2a0a4-111">Pomocí <xref:System.Data.DataSet.InferXmlSchema%2A>, můžete určit obory názvů, který se má ignorovat během procesu odvození.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-111">Using <xref:System.Data.DataSet.InferXmlSchema%2A>, you can specify namespaces to be ignored during the inference process.</span></span> <span data-ttu-id="2a0a4-112">Další informace najdete v tématu [načítání datovou sadu informace o schématu z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2a0a4-112">For more information, see [Loading DataSet Schema Information from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a0a4-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2a0a4-113">In This Section</span></span>  
 [<span data-ttu-id="2a0a4-114">Souhrn procesu odvození schématu datové sady</span><span class="sxs-lookup"><span data-stu-id="2a0a4-114">Summary of the DataSet Schema Inference Process</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/summary-of-the-dataset-schema-inference-process.md)  
 <span data-ttu-id="2a0a4-115">Poskytuje shrnutí pravidel pro odvození schéma <xref:System.Data.DataSet> ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-115">Provides a high-level summary of the rules for inferring the schema of a <xref:System.Data.DataSet> from XML.</span></span>  
  
 [<span data-ttu-id="2a0a4-116">Odvozování tabulek</span><span class="sxs-lookup"><span data-stu-id="2a0a4-116">Inferring Tables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)  
 <span data-ttu-id="2a0a4-117">Popisuje elementy XML, které jsou odvozené jako tabulky <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-117">Describes the XML elements that are inferred as tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="2a0a4-118">Odvozování sloupců</span><span class="sxs-lookup"><span data-stu-id="2a0a4-118">Inferring Columns</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-columns.md)  
 <span data-ttu-id="2a0a4-119">Popisuje elementy XML a atributů, které jsou odvozené jako sloupců tabulky.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-119">Describes the XML elements and attributes that are inferred as table columns.</span></span>  
  
 [<span data-ttu-id="2a0a4-120">Odvozování relací</span><span class="sxs-lookup"><span data-stu-id="2a0a4-120">Inferring Relationships</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-relationships.md)  
 <span data-ttu-id="2a0a4-121">Popisuje <xref:System.Data.DataRelation> a <xref:System.Data.ForeignKeyConstraint> objekty vytvořené pro vnořený, odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-121">Describes the <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects created for nested, inferred tables.</span></span>  
  
 [<span data-ttu-id="2a0a4-122">Odvození textu elementu</span><span class="sxs-lookup"><span data-stu-id="2a0a4-122">Inferring Element Text</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-element-text.md)  
 <span data-ttu-id="2a0a4-123">Popisuje sloupce, které jsou vytvořené pro text v kódu XML elementů a vysvětluje, pokud je text v elementů XML ignoruje.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-123">Describes the columns that are created for text in XML elements, and explains when text in XML elements is ignored.</span></span>  
  
 [<span data-ttu-id="2a0a4-124">Odvození omezení</span><span class="sxs-lookup"><span data-stu-id="2a0a4-124">Inference Limitations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inference-limitations.md)  
 <span data-ttu-id="2a0a4-125">Popisuje omezení odvození schématu.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-125">Discusses the limitations of schema inference.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2a0a4-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2a0a4-126">Related Sections</span></span>  
 [<span data-ttu-id="2a0a4-127">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="2a0a4-127">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="2a0a4-128">Popisuje, jak <xref:System.Data.DataSet> objekt komunikuje se službou XML data.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-128">Describes how the <xref:System.Data.DataSet> object interacts with XML data.</span></span>  
  
 [<span data-ttu-id="2a0a4-129">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="2a0a4-129">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="2a0a4-130">Popisuje relační struktura nebo schéma z <xref:System.Data.DataSet> vytvořený ze schématu XML definition language (XSD) schématu.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-130">Describes the relational structure, or schema, of a <xref:System.Data.DataSet> that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="2a0a4-131">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2a0a4-131">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 <span data-ttu-id="2a0a4-132">Popisuje technologie ADO.NET architektura a komponenty a jak je používat pro přístup k existující zdroje dat a spravovat data aplikací.</span><span class="sxs-lookup"><span data-stu-id="2a0a4-132">Describes the ADO.NET architecture and components and how to use them to access existing data sources and manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a0a4-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a0a4-133">See Also</span></span>  
 [<span data-ttu-id="2a0a4-134">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="2a0a4-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
