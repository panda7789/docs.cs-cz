---
title: "Odvození sloupce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 858a23fb8fec7b7f2eee95a1365d16e846beb548
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-columns"></a><span data-ttu-id="b770b-102">Odvození sloupce</span><span class="sxs-lookup"><span data-stu-id="b770b-102">Inferring Columns</span></span>
<span data-ttu-id="b770b-103">Po ADO.NET určil z dokumentu XML prvky, které k odvození jako tabulky pro <xref:System.Data.DataSet>, pak odvozeny sloupce pro tyto tabulky.</span><span class="sxs-lookup"><span data-stu-id="b770b-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="b770b-104">ADO.NET 2.0 zavedl nový modul odvození schématu, odvodí typ silného typu dat pro každou **simpleType** elementu.</span><span class="sxs-lookup"><span data-stu-id="b770b-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="b770b-105">V předchozích verzích, datový typ odvozené **simpleType** element byla vždy **xsd:string**.</span><span class="sxs-lookup"><span data-stu-id="b770b-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="b770b-106">Migrace a zpětná kompatibilita</span><span class="sxs-lookup"><span data-stu-id="b770b-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="b770b-107">**ReadXml** metoda přebírá argument typu **InferSchema**.</span><span class="sxs-lookup"><span data-stu-id="b770b-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="b770b-108">Tento argument umožňuje zadat chování odvození kompatibilní s předchozími verzemi.</span><span class="sxs-lookup"><span data-stu-id="b770b-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="b770b-109">Dostupné hodnoty pro **InferSchema** výčtu jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b770b-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="b770b-110">Poskytuje zpětné kompatibility tím, že vždy odvození jednoduchý typ. jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b770b-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="b770b-111">Odvodí typ dat silného typu.</span><span class="sxs-lookup"><span data-stu-id="b770b-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="b770b-112">Vyvolá výjimku, pokud se používá s <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="b770b-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="b770b-113">Ignoruje všechny vložené schéma a čte data do existujících <xref:System.Data.DataSet> schématu.</span><span class="sxs-lookup"><span data-stu-id="b770b-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="b770b-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="b770b-114">Attributes</span></span>  
 <span data-ttu-id="b770b-115">Jak jsou definovány v [odvození tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), bude ji odvodit element s atributy, jako tabulku.</span><span class="sxs-lookup"><span data-stu-id="b770b-115">As defined in [Inferring Tables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="b770b-116">Atributy tohoto prvku bude potom odvodit jako sloupce pro tabulku.</span><span class="sxs-lookup"><span data-stu-id="b770b-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="b770b-117">**ColumnMapping** vlastnost sloupců bude nastavena pro **MappingType.Attribute**, aby bylo zajištěno, že názvy sloupců zapisovat jako atributy, pokud schéma se nezapisují zpět do formátu XML.</span><span class="sxs-lookup"><span data-stu-id="b770b-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="b770b-118">Hodnoty atributů jsou uložené v řádku v tabulce.</span><span class="sxs-lookup"><span data-stu-id="b770b-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="b770b-119">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="b770b-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b770b-120">Proces odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci, **attr1** a **attr2**.</span><span class="sxs-lookup"><span data-stu-id="b770b-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="b770b-121">**ColumnMapping** vlastnost oba sloupce bude nastavena pro **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="b770b-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="b770b-122">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b770b-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b770b-123">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="b770b-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b770b-124">attr1</span><span class="sxs-lookup"><span data-stu-id="b770b-124">attr1</span></span>|<span data-ttu-id="b770b-125">attr2</span><span class="sxs-lookup"><span data-stu-id="b770b-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="b770b-126">value1</span><span class="sxs-lookup"><span data-stu-id="b770b-126">value1</span></span>|<span data-ttu-id="b770b-127">value2</span><span class="sxs-lookup"><span data-stu-id="b770b-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="b770b-128">Elementy bez atributy nebo podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b770b-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="b770b-129">Pokud element má žádné podřízené elementy nebo atributy, bude odvodit jako sloupec.</span><span class="sxs-lookup"><span data-stu-id="b770b-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="b770b-130">**ColumnMapping** vlastnost sloupec bude nastavena pro **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="b770b-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="b770b-131">Text pro podřízené elementy je uložen v řádku v tabulce.</span><span class="sxs-lookup"><span data-stu-id="b770b-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="b770b-132">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="b770b-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b770b-133">Proces odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci, **ChildElement1** a **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="b770b-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="b770b-134">**ColumnMapping** vlastnost oba sloupce bude nastavena pro **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="b770b-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="b770b-135">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b770b-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b770b-136">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="b770b-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b770b-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="b770b-137">ChildElement1</span></span>|<span data-ttu-id="b770b-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="b770b-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="b770b-139">Text1</span><span class="sxs-lookup"><span data-stu-id="b770b-139">Text1</span></span>|<span data-ttu-id="b770b-140">Text2</span><span class="sxs-lookup"><span data-stu-id="b770b-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b770b-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="b770b-141">See Also</span></span>  
 [<span data-ttu-id="b770b-142">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="b770b-142">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="b770b-143">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="b770b-143">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="b770b-144">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="b770b-144">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="b770b-145">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="b770b-145">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="b770b-146">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="b770b-146">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="b770b-147">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="b770b-147">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
