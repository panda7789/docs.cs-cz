---
title: Odvozování sloupců
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 2718cbcf29799f99c8648b129fdb6079a6f6d344
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786173"
---
# <a name="inferring-columns"></a><span data-ttu-id="bc63e-102">Odvozování sloupců</span><span class="sxs-lookup"><span data-stu-id="bc63e-102">Inferring Columns</span></span>
<span data-ttu-id="bc63e-103">Jakmile ADO.NET zjistí z dokumentu XML <xref:System.Data.DataSet>, které prvky mají být odvozeny jako tabulky pro,, pak odvodí sloupce pro tyto tabulky.</span><span class="sxs-lookup"><span data-stu-id="bc63e-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="bc63e-104">ADO.NET 2,0 představil nový modul odvození schématu, který odvodí datový typ silného typu pro každý element **simpleType** .</span><span class="sxs-lookup"><span data-stu-id="bc63e-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="bc63e-105">V předchozích verzích byl datový typ odvozeného elementu **simpleType** vždy **xsd: String**.</span><span class="sxs-lookup"><span data-stu-id="bc63e-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="bc63e-106">Migrace a zpětná kompatibilita</span><span class="sxs-lookup"><span data-stu-id="bc63e-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="bc63e-107">Metoda **ReadXml** přebírá argument typu **InferSchema**.</span><span class="sxs-lookup"><span data-stu-id="bc63e-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="bc63e-108">Tento argument umožňuje určit chování při odvozování kompatibilní s předchozími verzemi.</span><span class="sxs-lookup"><span data-stu-id="bc63e-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="bc63e-109">Dostupné hodnoty pro výčet **InferSchema** jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="bc63e-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="bc63e-110">Poskytuje zpětnou kompatibilitu tím, že vždy odvozuje jednoduchý typ <xref:System.String>jako.</span><span class="sxs-lookup"><span data-stu-id="bc63e-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="bc63e-111">Odvodí datový typ silného typu.</span><span class="sxs-lookup"><span data-stu-id="bc63e-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="bc63e-112">Vyvolá výjimku, pokud se používá s <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="bc63e-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="bc63e-113">Ignoruje všechna vložená schémata a čte data do <xref:System.Data.DataSet> stávajícího schématu.</span><span class="sxs-lookup"><span data-stu-id="bc63e-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="bc63e-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="bc63e-114">Attributes</span></span>  
 <span data-ttu-id="bc63e-115">Jak je definováno v [tabulkách odvození](inferring-tables.md), element s atributy bude odvozen jako tabulka.</span><span class="sxs-lookup"><span data-stu-id="bc63e-115">As defined in [Inferring Tables](inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="bc63e-116">Atributy daného prvku budou následně odvozeny jako sloupce pro tabulku.</span><span class="sxs-lookup"><span data-stu-id="bc63e-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="bc63e-117">Vlastnost **ColumnMapping** sloupců bude nastavena na **MappingType. Attribute**, aby bylo zajištěno, že názvy sloupců budou zapsány jako atributy, pokud je schéma zapsáno zpět do formátu XML.</span><span class="sxs-lookup"><span data-stu-id="bc63e-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="bc63e-118">Hodnoty atributů jsou uloženy v řádku tabulky.</span><span class="sxs-lookup"><span data-stu-id="bc63e-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="bc63e-119">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="bc63e-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="bc63e-120">Proces odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci, **attr1** a **attr2**.</span><span class="sxs-lookup"><span data-stu-id="bc63e-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="bc63e-121">Vlastnost **ColumnMapping** obou sloupců bude nastavena na **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="bc63e-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="bc63e-122">**Integrován** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="bc63e-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="bc63e-123">**Stolní** Element1</span><span class="sxs-lookup"><span data-stu-id="bc63e-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="bc63e-124">attr1</span><span class="sxs-lookup"><span data-stu-id="bc63e-124">attr1</span></span>|<span data-ttu-id="bc63e-125">attr2</span><span class="sxs-lookup"><span data-stu-id="bc63e-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="bc63e-126">Hodnota1</span><span class="sxs-lookup"><span data-stu-id="bc63e-126">value1</span></span>|<span data-ttu-id="bc63e-127">Argument</span><span class="sxs-lookup"><span data-stu-id="bc63e-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="bc63e-128">Prvky bez atributů nebo podřízených elementů</span><span class="sxs-lookup"><span data-stu-id="bc63e-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="bc63e-129">Pokud element nemá žádné podřízené elementy nebo atributy, bude odvozen jako sloupec.</span><span class="sxs-lookup"><span data-stu-id="bc63e-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="bc63e-130">Vlastnost **ColumnMapping** sloupce bude nastavena na **MappingType. element**.</span><span class="sxs-lookup"><span data-stu-id="bc63e-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="bc63e-131">Text podřízených elementů je uložený v řádku v tabulce.</span><span class="sxs-lookup"><span data-stu-id="bc63e-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="bc63e-132">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="bc63e-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="bc63e-133">Proces odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci, **ChildElement1** a **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="bc63e-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="bc63e-134">Vlastnost **ColumnMapping** obou sloupců bude nastavena na **MappingType. element**.</span><span class="sxs-lookup"><span data-stu-id="bc63e-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="bc63e-135">**Integrován** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="bc63e-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="bc63e-136">**Stolní** Element1</span><span class="sxs-lookup"><span data-stu-id="bc63e-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="bc63e-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="bc63e-137">ChildElement1</span></span>|<span data-ttu-id="bc63e-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="bc63e-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="bc63e-139">Text1</span><span class="sxs-lookup"><span data-stu-id="bc63e-139">Text1</span></span>|<span data-ttu-id="bc63e-140">Text2</span><span class="sxs-lookup"><span data-stu-id="bc63e-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc63e-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc63e-141">See also</span></span>

- [<span data-ttu-id="bc63e-142">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="bc63e-142">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="bc63e-143">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="bc63e-143">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="bc63e-144">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="bc63e-144">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="bc63e-145">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="bc63e-145">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="bc63e-146">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="bc63e-146">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="bc63e-147">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bc63e-147">ADO.NET Overview</span></span>](../ado-net-overview.md)
