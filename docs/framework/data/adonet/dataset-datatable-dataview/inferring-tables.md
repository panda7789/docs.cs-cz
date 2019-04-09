---
title: Odvozování tabulek
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 2c2a93d413f301dc3006b701e4bc7979a3fa7a1d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181828"
---
# <a name="inferring-tables"></a><span data-ttu-id="2852f-102">Odvozování tabulek</span><span class="sxs-lookup"><span data-stu-id="2852f-102">Inferring Tables</span></span>
<span data-ttu-id="2852f-103">Po odvození schématu pro <xref:System.Data.DataSet> z dokumentu XML, ADO.NET nejdřív zjistí prvky XML, které představují tabulky.</span><span class="sxs-lookup"><span data-stu-id="2852f-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="2852f-104">Tabulka pro za následek následující struktury XML **datovou sadu** schématu:</span><span class="sxs-lookup"><span data-stu-id="2852f-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="2852f-105">Elementy s atributy</span><span class="sxs-lookup"><span data-stu-id="2852f-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="2852f-106">Elementů s podřízenými prvky</span><span class="sxs-lookup"><span data-stu-id="2852f-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="2852f-107">Opakující se elementy</span><span class="sxs-lookup"><span data-stu-id="2852f-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="2852f-108">Elementy s atributy</span><span class="sxs-lookup"><span data-stu-id="2852f-108">Elements with Attributes</span></span>  
 <span data-ttu-id="2852f-109">Prvky, které mají atributy určené v nich za následek odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="2852f-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="2852f-110">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="2852f-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="2852f-111">Odvození proces vytvoří tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="2852f-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="2852f-112">**DataSet:** Prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="2852f-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="2852f-113">**Tabulka:** element1</span><span class="sxs-lookup"><span data-stu-id="2852f-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="2852f-114">attr1</span><span class="sxs-lookup"><span data-stu-id="2852f-114">attr1</span></span>|<span data-ttu-id="2852f-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="2852f-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="2852f-116">value1</span><span class="sxs-lookup"><span data-stu-id="2852f-116">value1</span></span>||  
|<span data-ttu-id="2852f-117">value2</span><span class="sxs-lookup"><span data-stu-id="2852f-117">value2</span></span>|<span data-ttu-id="2852f-118">Text1</span><span class="sxs-lookup"><span data-stu-id="2852f-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="2852f-119">Elementů s podřízenými prvky</span><span class="sxs-lookup"><span data-stu-id="2852f-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="2852f-120">Prvky, které mají podřízené prvky výsledek v odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="2852f-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="2852f-121">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="2852f-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="2852f-122">Odvození proces vytvoří tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="2852f-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="2852f-123">**DataSet:** Prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="2852f-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="2852f-124">**Tabulka:** element1</span><span class="sxs-lookup"><span data-stu-id="2852f-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="2852f-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="2852f-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="2852f-126">Text1</span><span class="sxs-lookup"><span data-stu-id="2852f-126">Text1</span></span>|  
  
 <span data-ttu-id="2852f-127">Dokumentu nebo kořenový element výsledek odvozené tabulky, pokud má atributy nebo podřízené prvky, které jsou odvozeny jako sloupce.</span><span class="sxs-lookup"><span data-stu-id="2852f-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="2852f-128">Pokud má element dokumentu žádné atributy a žádné podřízené prvky, které by odvodit jako sloupce, jako je odvozený element **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="2852f-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="2852f-129">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="2852f-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="2852f-130">Odvození proces vytvoří tabulku s názvem "Prvek DocumentElement."</span><span class="sxs-lookup"><span data-stu-id="2852f-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="2852f-131">**DataSet:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="2852f-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="2852f-132">**Tabulka:** Prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="2852f-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="2852f-133">element1</span><span class="sxs-lookup"><span data-stu-id="2852f-133">Element1</span></span>|<span data-ttu-id="2852f-134">element2</span><span class="sxs-lookup"><span data-stu-id="2852f-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="2852f-135">Text1</span><span class="sxs-lookup"><span data-stu-id="2852f-135">Text1</span></span>|<span data-ttu-id="2852f-136">Text2</span><span class="sxs-lookup"><span data-stu-id="2852f-136">Text2</span></span>|  
  
 <span data-ttu-id="2852f-137">Vezměte v úvahu taky následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="2852f-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="2852f-138">Odvození proces vytvoří **datovou sadu** s názvem "Prvek DocumentElement", který obsahuje tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="2852f-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="2852f-139">**DataSet:** Prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="2852f-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="2852f-140">**Tabulka:** element1</span><span class="sxs-lookup"><span data-stu-id="2852f-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="2852f-141">attr1</span><span class="sxs-lookup"><span data-stu-id="2852f-141">attr1</span></span>|<span data-ttu-id="2852f-142">attr2</span><span class="sxs-lookup"><span data-stu-id="2852f-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="2852f-143">value1</span><span class="sxs-lookup"><span data-stu-id="2852f-143">value1</span></span>|<span data-ttu-id="2852f-144">value2</span><span class="sxs-lookup"><span data-stu-id="2852f-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="2852f-145">Opakující se elementy</span><span class="sxs-lookup"><span data-stu-id="2852f-145">Repeating Elements</span></span>  
 <span data-ttu-id="2852f-146">Prvky, které opakují výsledek v jedné odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="2852f-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="2852f-147">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="2852f-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="2852f-148">Odvození proces vytvoří tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="2852f-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="2852f-149">**DataSet:** Prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="2852f-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="2852f-150">**Tabulka:** element1</span><span class="sxs-lookup"><span data-stu-id="2852f-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="2852f-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="2852f-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="2852f-152">Text1</span><span class="sxs-lookup"><span data-stu-id="2852f-152">Text1</span></span>|  
|<span data-ttu-id="2852f-153">Text2</span><span class="sxs-lookup"><span data-stu-id="2852f-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2852f-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2852f-154">See also</span></span>

- [<span data-ttu-id="2852f-155">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="2852f-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="2852f-156">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="2852f-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="2852f-157">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="2852f-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="2852f-158">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="2852f-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="2852f-159">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="2852f-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="2852f-160">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="2852f-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
