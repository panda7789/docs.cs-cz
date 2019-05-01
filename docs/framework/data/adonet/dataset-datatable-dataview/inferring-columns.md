---
title: Odvozování sloupců
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 53e77f624c5af8f61a32d5b1399d2728f32011a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034278"
---
# <a name="inferring-columns"></a><span data-ttu-id="30fc3-102">Odvozování sloupců</span><span class="sxs-lookup"><span data-stu-id="30fc3-102">Inferring Columns</span></span>
<span data-ttu-id="30fc3-103">Po ADO.NET bylo zjištěno z dokumentu XML, které prvky k odvození jako tabulka pro <xref:System.Data.DataSet>, pak odvodí sloupce pro tyto tabulky.</span><span class="sxs-lookup"><span data-stu-id="30fc3-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="30fc3-104">ADO.NET 2.0 zavedl nový modul odvození schématu, která odvodí typ dat silného typu pro každou **simpleType** elementu.</span><span class="sxs-lookup"><span data-stu-id="30fc3-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="30fc3-105">V předchozích verzích, datový typ vyvozeným **simpleType** element se vždy **XSD: String**.</span><span class="sxs-lookup"><span data-stu-id="30fc3-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="30fc3-106">Migrace a zpětné kompatibility</span><span class="sxs-lookup"><span data-stu-id="30fc3-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="30fc3-107">**ReadXml** metoda přebírá argument typu **InferSchema**.</span><span class="sxs-lookup"><span data-stu-id="30fc3-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="30fc3-108">Tento argument můžete zadat odvození chování, které jsou kompatibilní s předchozími verzemi.</span><span class="sxs-lookup"><span data-stu-id="30fc3-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="30fc3-109">Dostupné hodnoty pro **InferSchema** výčtu jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="30fc3-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="30fc3-110">Poskytuje zpětnou kompatibilitu tím, že vždy odvození jednoduchý typ jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="30fc3-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="30fc3-111">Odvodí typ dat silného typu.</span><span class="sxs-lookup"><span data-stu-id="30fc3-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="30fc3-112">Vyvolá výjimku, pokud je použita s <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="30fc3-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="30fc3-113">Ignoruje všechny vložené schéma a načte data do existující <xref:System.Data.DataSet> schématu.</span><span class="sxs-lookup"><span data-stu-id="30fc3-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="30fc3-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="30fc3-114">Attributes</span></span>  
 <span data-ttu-id="30fc3-115">Jak jsou definovány v [odvozování tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), element s atributy se odvodit jako tabulku.</span><span class="sxs-lookup"><span data-stu-id="30fc3-115">As defined in [Inferring Tables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="30fc3-116">Atributy daného prvku se pak odvodit jako sloupce pro tabulku.</span><span class="sxs-lookup"><span data-stu-id="30fc3-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="30fc3-117">**ColumnMapping** vlastnost sloupců bude nastavena na **MappingType.Attribute**, aby bylo zajištěno, že názvy sloupců zapisují jako atributy, pokud schéma se zapíšou zpátky do XML.</span><span class="sxs-lookup"><span data-stu-id="30fc3-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="30fc3-118">Hodnoty atributů jsou uloženy v řádku v tabulce.</span><span class="sxs-lookup"><span data-stu-id="30fc3-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="30fc3-119">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="30fc3-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="30fc3-120">Procesu odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci, **attr1** a **attr2**.</span><span class="sxs-lookup"><span data-stu-id="30fc3-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="30fc3-121">**ColumnMapping** vlastnost obou sloupců bude nastavena na **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="30fc3-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="30fc3-122">**DataSet:** Prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="30fc3-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="30fc3-123">**Tabulka:** element1</span><span class="sxs-lookup"><span data-stu-id="30fc3-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="30fc3-124">attr1</span><span class="sxs-lookup"><span data-stu-id="30fc3-124">attr1</span></span>|<span data-ttu-id="30fc3-125">attr2</span><span class="sxs-lookup"><span data-stu-id="30fc3-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="30fc3-126">value1</span><span class="sxs-lookup"><span data-stu-id="30fc3-126">value1</span></span>|<span data-ttu-id="30fc3-127">value2</span><span class="sxs-lookup"><span data-stu-id="30fc3-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="30fc3-128">Prvky bez atributy nebo podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="30fc3-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="30fc3-129">Pokud element nemá žádné podřízené prvky a atributy, se odvodit jako sloupec.</span><span class="sxs-lookup"><span data-stu-id="30fc3-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="30fc3-130">**ColumnMapping** vlastnost sloupec bude nastavena na **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="30fc3-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="30fc3-131">Text pro podřízené prvky je uložen v řádku v tabulce.</span><span class="sxs-lookup"><span data-stu-id="30fc3-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="30fc3-132">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="30fc3-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="30fc3-133">Procesu odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci, **ChildElement1** a **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="30fc3-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="30fc3-134">**ColumnMapping** vlastnost obou sloupců bude nastavena na **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="30fc3-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="30fc3-135">**DataSet:** Prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="30fc3-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="30fc3-136">**Tabulka:** element1</span><span class="sxs-lookup"><span data-stu-id="30fc3-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="30fc3-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="30fc3-137">ChildElement1</span></span>|<span data-ttu-id="30fc3-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="30fc3-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="30fc3-139">Text1</span><span class="sxs-lookup"><span data-stu-id="30fc3-139">Text1</span></span>|<span data-ttu-id="30fc3-140">Text2</span><span class="sxs-lookup"><span data-stu-id="30fc3-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30fc3-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30fc3-141">See also</span></span>

- [<span data-ttu-id="30fc3-142">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="30fc3-142">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="30fc3-143">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="30fc3-143">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="30fc3-144">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="30fc3-144">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="30fc3-145">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="30fc3-145">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="30fc3-146">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="30fc3-146">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="30fc3-147">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="30fc3-147">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
