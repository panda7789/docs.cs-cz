---
title: "Odvození tabulky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2c00dd11d4d93e5d3b0e2f1c3b75765056a10cab
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-tables"></a><span data-ttu-id="9327f-102">Odvození tabulky</span><span class="sxs-lookup"><span data-stu-id="9327f-102">Inferring Tables</span></span>
<span data-ttu-id="9327f-103">Pokud schéma pro odvození <xref:System.Data.DataSet> z dokumentu XML ADO.NET nejdřív zjistí, které elementy XML představují tabulky.</span><span class="sxs-lookup"><span data-stu-id="9327f-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="9327f-104">Následující struktury XML výsledkem tabulka pro **datovou sadu** schématu:</span><span class="sxs-lookup"><span data-stu-id="9327f-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="9327f-105">Elementy s atributy</span><span class="sxs-lookup"><span data-stu-id="9327f-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="9327f-106">Elementy podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9327f-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="9327f-107">Opakující se elementy</span><span class="sxs-lookup"><span data-stu-id="9327f-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="9327f-108">Elementy s atributy</span><span class="sxs-lookup"><span data-stu-id="9327f-108">Elements with Attributes</span></span>  
 <span data-ttu-id="9327f-109">Prvky, které mají mít za následek zadané v nich atributy odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="9327f-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="9327f-110">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="9327f-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="9327f-111">Proces odvození vytvoří tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="9327f-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="9327f-112">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="9327f-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="9327f-113">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="9327f-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="9327f-114">attr1</span><span class="sxs-lookup"><span data-stu-id="9327f-114">attr1</span></span>|<span data-ttu-id="9327f-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="9327f-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="9327f-116">value1</span><span class="sxs-lookup"><span data-stu-id="9327f-116">value1</span></span>||  
|<span data-ttu-id="9327f-117">value2</span><span class="sxs-lookup"><span data-stu-id="9327f-117">value2</span></span>|<span data-ttu-id="9327f-118">Text1</span><span class="sxs-lookup"><span data-stu-id="9327f-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="9327f-119">Elementy podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9327f-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="9327f-120">Prvky, které mají výsledek podřízené elementy v odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="9327f-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="9327f-121">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="9327f-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="9327f-122">Proces odvození vytvoří tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="9327f-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="9327f-123">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="9327f-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="9327f-124">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="9327f-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="9327f-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="9327f-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="9327f-126">Text1</span><span class="sxs-lookup"><span data-stu-id="9327f-126">Text1</span></span>|  
  
 <span data-ttu-id="9327f-127">Dokument nebo kořenové, element výsledek odvozené tabulky, pokud má atributy nebo podřízené prvky, které jsou odvozené jako sloupce.</span><span class="sxs-lookup"><span data-stu-id="9327f-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="9327f-128">Pokud dokument prvek nemá žádné atributy a žádné podřízené prvky, které by odvodit jako sloupce, jako je odvodit elementu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="9327f-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="9327f-129">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="9327f-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="9327f-130">Proces odvození vytvoří tabulku s názvem "Prvek DocumentElement."</span><span class="sxs-lookup"><span data-stu-id="9327f-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="9327f-131">**Datová sada:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="9327f-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="9327f-132">**Tabulka:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="9327f-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="9327f-133">Element1</span><span class="sxs-lookup"><span data-stu-id="9327f-133">Element1</span></span>|<span data-ttu-id="9327f-134">Element2</span><span class="sxs-lookup"><span data-stu-id="9327f-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="9327f-135">Text1</span><span class="sxs-lookup"><span data-stu-id="9327f-135">Text1</span></span>|<span data-ttu-id="9327f-136">Text2</span><span class="sxs-lookup"><span data-stu-id="9327f-136">Text2</span></span>|  
  
 <span data-ttu-id="9327f-137">Případně zvažte následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="9327f-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="9327f-138">Proces odvození vytváří **datovou sadu** s názvem "Prvek DocumentElement" obsahující tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="9327f-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="9327f-139">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="9327f-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="9327f-140">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="9327f-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="9327f-141">attr1</span><span class="sxs-lookup"><span data-stu-id="9327f-141">attr1</span></span>|<span data-ttu-id="9327f-142">attr2</span><span class="sxs-lookup"><span data-stu-id="9327f-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="9327f-143">value1</span><span class="sxs-lookup"><span data-stu-id="9327f-143">value1</span></span>|<span data-ttu-id="9327f-144">value2</span><span class="sxs-lookup"><span data-stu-id="9327f-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="9327f-145">Opakující se elementy</span><span class="sxs-lookup"><span data-stu-id="9327f-145">Repeating Elements</span></span>  
 <span data-ttu-id="9327f-146">Prvky, které opakujte výsledek v jedné odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="9327f-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="9327f-147">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="9327f-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="9327f-148">Proces odvození vytvoří tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="9327f-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="9327f-149">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="9327f-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="9327f-150">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="9327f-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="9327f-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="9327f-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="9327f-152">Text1</span><span class="sxs-lookup"><span data-stu-id="9327f-152">Text1</span></span>|  
|<span data-ttu-id="9327f-153">Text2</span><span class="sxs-lookup"><span data-stu-id="9327f-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9327f-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="9327f-154">See Also</span></span>  
 [<span data-ttu-id="9327f-155">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="9327f-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="9327f-156">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="9327f-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="9327f-157">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="9327f-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="9327f-158">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="9327f-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="9327f-159">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="9327f-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="9327f-160">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="9327f-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
