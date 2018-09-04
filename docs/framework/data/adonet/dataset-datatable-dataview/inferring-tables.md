---
title: Odvozování tabulek
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 38709f91e01c7f85d9e8482bdd49bc0892121f09
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528169"
---
# <a name="inferring-tables"></a><span data-ttu-id="815b9-102">Odvozování tabulek</span><span class="sxs-lookup"><span data-stu-id="815b9-102">Inferring Tables</span></span>
<span data-ttu-id="815b9-103">Po odvození schématu pro <xref:System.Data.DataSet> z dokumentu XML, ADO.NET nejdřív zjistí prvky XML, které představují tabulky.</span><span class="sxs-lookup"><span data-stu-id="815b9-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="815b9-104">Tabulka pro za následek následující struktury XML **datovou sadu** schématu:</span><span class="sxs-lookup"><span data-stu-id="815b9-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="815b9-105">Elementy s atributy</span><span class="sxs-lookup"><span data-stu-id="815b9-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="815b9-106">Elementů s podřízenými prvky</span><span class="sxs-lookup"><span data-stu-id="815b9-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="815b9-107">Opakující se elementy</span><span class="sxs-lookup"><span data-stu-id="815b9-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="815b9-108">Elementy s atributy</span><span class="sxs-lookup"><span data-stu-id="815b9-108">Elements with Attributes</span></span>  
 <span data-ttu-id="815b9-109">Prvky, které mají atributy určené v nich za následek odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="815b9-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="815b9-110">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="815b9-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="815b9-111">Odvození proces vytvoří tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="815b9-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="815b9-112">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="815b9-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="815b9-113">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="815b9-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="815b9-114">attr1</span><span class="sxs-lookup"><span data-stu-id="815b9-114">attr1</span></span>|<span data-ttu-id="815b9-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="815b9-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="815b9-116">Hodnota1</span><span class="sxs-lookup"><span data-stu-id="815b9-116">value1</span></span>||  
|<span data-ttu-id="815b9-117">Hodnota2</span><span class="sxs-lookup"><span data-stu-id="815b9-117">value2</span></span>|<span data-ttu-id="815b9-118">Text1</span><span class="sxs-lookup"><span data-stu-id="815b9-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="815b9-119">Elementů s podřízenými prvky</span><span class="sxs-lookup"><span data-stu-id="815b9-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="815b9-120">Prvky, které mají podřízené prvky výsledek v odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="815b9-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="815b9-121">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="815b9-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="815b9-122">Odvození proces vytvoří tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="815b9-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="815b9-123">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="815b9-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="815b9-124">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="815b9-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="815b9-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="815b9-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="815b9-126">Text1</span><span class="sxs-lookup"><span data-stu-id="815b9-126">Text1</span></span>|  
  
 <span data-ttu-id="815b9-127">Dokumentu nebo kořenový element výsledek odvozené tabulky, pokud má atributy nebo podřízené prvky, které jsou odvozeny jako sloupce.</span><span class="sxs-lookup"><span data-stu-id="815b9-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="815b9-128">Pokud má element dokumentu žádné atributy a žádné podřízené prvky, které by odvodit jako sloupce, jako je odvozený element **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="815b9-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="815b9-129">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="815b9-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="815b9-130">Odvození proces vytvoří tabulku s názvem "Prvek DocumentElement."</span><span class="sxs-lookup"><span data-stu-id="815b9-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="815b9-131">**Datová sada:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="815b9-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="815b9-132">**Tabulka:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="815b9-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="815b9-133">element1</span><span class="sxs-lookup"><span data-stu-id="815b9-133">Element1</span></span>|<span data-ttu-id="815b9-134">element2</span><span class="sxs-lookup"><span data-stu-id="815b9-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="815b9-135">Text1</span><span class="sxs-lookup"><span data-stu-id="815b9-135">Text1</span></span>|<span data-ttu-id="815b9-136">Text2</span><span class="sxs-lookup"><span data-stu-id="815b9-136">Text2</span></span>|  
  
 <span data-ttu-id="815b9-137">Vezměte v úvahu taky následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="815b9-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="815b9-138">Odvození proces vytvoří **datovou sadu** s názvem "Prvek DocumentElement", který obsahuje tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="815b9-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="815b9-139">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="815b9-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="815b9-140">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="815b9-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="815b9-141">attr1</span><span class="sxs-lookup"><span data-stu-id="815b9-141">attr1</span></span>|<span data-ttu-id="815b9-142">attr2</span><span class="sxs-lookup"><span data-stu-id="815b9-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="815b9-143">Hodnota1</span><span class="sxs-lookup"><span data-stu-id="815b9-143">value1</span></span>|<span data-ttu-id="815b9-144">Hodnota2</span><span class="sxs-lookup"><span data-stu-id="815b9-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="815b9-145">Opakující se elementy</span><span class="sxs-lookup"><span data-stu-id="815b9-145">Repeating Elements</span></span>  
 <span data-ttu-id="815b9-146">Prvky, které opakují výsledek v jedné odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="815b9-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="815b9-147">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="815b9-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="815b9-148">Odvození proces vytvoří tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="815b9-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="815b9-149">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="815b9-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="815b9-150">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="815b9-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="815b9-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="815b9-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="815b9-152">Text1</span><span class="sxs-lookup"><span data-stu-id="815b9-152">Text1</span></span>|  
|<span data-ttu-id="815b9-153">Text2</span><span class="sxs-lookup"><span data-stu-id="815b9-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="815b9-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="815b9-154">See Also</span></span>  
 [<span data-ttu-id="815b9-155">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="815b9-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="815b9-156">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="815b9-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="815b9-157">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="815b9-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="815b9-158">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="815b9-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="815b9-159">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="815b9-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="815b9-160">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="815b9-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
