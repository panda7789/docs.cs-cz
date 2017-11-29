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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ae6f7827b7206544ff7547cc04f44b7cda34bef8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-tables"></a><span data-ttu-id="d3ae4-102">Odvození tabulky</span><span class="sxs-lookup"><span data-stu-id="d3ae4-102">Inferring Tables</span></span>
<span data-ttu-id="d3ae4-103">Pokud schéma pro odvození <xref:System.Data.DataSet> z dokumentu XML ADO.NET nejdřív zjistí, které elementy XML představují tabulky.</span><span class="sxs-lookup"><span data-stu-id="d3ae4-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="d3ae4-104">Následující struktury XML výsledkem tabulka pro **datovou sadu** schématu:</span><span class="sxs-lookup"><span data-stu-id="d3ae4-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="d3ae4-105">Elementy s atributy</span><span class="sxs-lookup"><span data-stu-id="d3ae4-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="d3ae4-106">Elementy podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d3ae4-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="d3ae4-107">Opakující se elementy</span><span class="sxs-lookup"><span data-stu-id="d3ae4-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="d3ae4-108">Elementy s atributy</span><span class="sxs-lookup"><span data-stu-id="d3ae4-108">Elements with Attributes</span></span>  
 <span data-ttu-id="d3ae4-109">Prvky, které mají mít za následek zadané v nich atributy odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="d3ae4-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="d3ae4-110">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="d3ae4-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d3ae4-111">Proces odvození vytvoří tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="d3ae4-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="d3ae4-112">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d3ae4-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d3ae4-113">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d3ae4-114">attr1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-114">attr1</span></span>|<span data-ttu-id="d3ae4-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="d3ae4-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="d3ae4-116">value1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-116">value1</span></span>||  
|<span data-ttu-id="d3ae4-117">Value2</span><span class="sxs-lookup"><span data-stu-id="d3ae4-117">value2</span></span>|<span data-ttu-id="d3ae4-118">Text1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="d3ae4-119">Elementy podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d3ae4-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="d3ae4-120">Prvky, které mají výsledek podřízené elementy v odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="d3ae4-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="d3ae4-121">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="d3ae4-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d3ae4-122">Proces odvození vytvoří tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="d3ae4-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="d3ae4-123">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d3ae4-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d3ae4-124">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d3ae4-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="d3ae4-126">Text1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-126">Text1</span></span>|  
  
 <span data-ttu-id="d3ae4-127">Dokument nebo kořenové, element výsledek odvozené tabulky, pokud má atributy nebo podřízené prvky, které jsou odvozené jako sloupce.</span><span class="sxs-lookup"><span data-stu-id="d3ae4-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="d3ae4-128">Pokud dokument prvek nemá žádné atributy a žádné podřízené prvky, které by odvodit jako sloupce, jako je odvodit elementu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="d3ae4-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="d3ae4-129">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="d3ae4-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d3ae4-130">Proces odvození vytvoří tabulku s názvem "Prvek DocumentElement."</span><span class="sxs-lookup"><span data-stu-id="d3ae4-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="d3ae4-131">**Datová sada:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="d3ae4-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="d3ae4-132">**Tabulka:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d3ae4-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="d3ae4-133">Element1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-133">Element1</span></span>|<span data-ttu-id="d3ae4-134">Element2</span><span class="sxs-lookup"><span data-stu-id="d3ae4-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="d3ae4-135">Text1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-135">Text1</span></span>|<span data-ttu-id="d3ae4-136">Text2</span><span class="sxs-lookup"><span data-stu-id="d3ae4-136">Text2</span></span>|  
  
 <span data-ttu-id="d3ae4-137">Případně zvažte následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="d3ae4-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d3ae4-138">Proces odvození vytváří **datovou sadu** s názvem "Prvek DocumentElement" obsahující tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="d3ae4-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="d3ae4-139">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d3ae4-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d3ae4-140">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d3ae4-141">attr1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-141">attr1</span></span>|<span data-ttu-id="d3ae4-142">attr2</span><span class="sxs-lookup"><span data-stu-id="d3ae4-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="d3ae4-143">value1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-143">value1</span></span>|<span data-ttu-id="d3ae4-144">Value2</span><span class="sxs-lookup"><span data-stu-id="d3ae4-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="d3ae4-145">Opakující se elementy</span><span class="sxs-lookup"><span data-stu-id="d3ae4-145">Repeating Elements</span></span>  
 <span data-ttu-id="d3ae4-146">Prvky, které opakujte výsledek v jedné odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="d3ae4-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="d3ae4-147">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="d3ae4-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d3ae4-148">Proces odvození vytvoří tabulku s názvem "Element1."</span><span class="sxs-lookup"><span data-stu-id="d3ae4-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="d3ae4-149">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d3ae4-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d3ae4-150">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d3ae4-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="d3ae4-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="d3ae4-152">Text1</span><span class="sxs-lookup"><span data-stu-id="d3ae4-152">Text1</span></span>|  
|<span data-ttu-id="d3ae4-153">Text2</span><span class="sxs-lookup"><span data-stu-id="d3ae4-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3ae4-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3ae4-154">See Also</span></span>  
 [<span data-ttu-id="d3ae4-155">Odvození relační strukturu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="d3ae4-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="d3ae4-156">Načítání datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="d3ae4-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="d3ae4-157">Načítání informací o schématu sady dat z XML</span><span class="sxs-lookup"><span data-stu-id="d3ae4-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="d3ae4-158">Pomocí XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="d3ae4-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="d3ae4-159">Datové sady, DataTables a DataView</span><span class="sxs-lookup"><span data-stu-id="d3ae4-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="d3ae4-160">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="d3ae4-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
