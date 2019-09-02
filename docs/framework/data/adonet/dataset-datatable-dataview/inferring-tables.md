---
title: Odvozování tabulek
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 84cee828f2d3c918a12e449da5b01a3d72d86333
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203517"
---
# <a name="inferring-tables"></a><span data-ttu-id="bc27f-102">Odvozování tabulek</span><span class="sxs-lookup"><span data-stu-id="bc27f-102">Inferring Tables</span></span>
<span data-ttu-id="bc27f-103">Při odvozování schématu pro <xref:System.Data.DataSet> z dokumentu XML ADO.NET nejprve Určuje, které elementy XML reprezentují tabulky.</span><span class="sxs-lookup"><span data-stu-id="bc27f-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="bc27f-104">Následující struktury XML vedou v tabulce pro schéma **datové sady** :</span><span class="sxs-lookup"><span data-stu-id="bc27f-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="bc27f-105">Elementy s atributy</span><span class="sxs-lookup"><span data-stu-id="bc27f-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="bc27f-106">Prvky s podřízenými prvky</span><span class="sxs-lookup"><span data-stu-id="bc27f-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="bc27f-107">Opakující se elementy</span><span class="sxs-lookup"><span data-stu-id="bc27f-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="bc27f-108">Elementy s atributy</span><span class="sxs-lookup"><span data-stu-id="bc27f-108">Elements with Attributes</span></span>  
 <span data-ttu-id="bc27f-109">Prvky, které mají v nich atributy, mají za následek odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="bc27f-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="bc27f-110">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="bc27f-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="bc27f-111">Proces odvození vytvoří tabulku s názvem "Element1".</span><span class="sxs-lookup"><span data-stu-id="bc27f-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="bc27f-112">**Integrován** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="bc27f-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="bc27f-113">**Stolní** Element1</span><span class="sxs-lookup"><span data-stu-id="bc27f-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="bc27f-114">attr1</span><span class="sxs-lookup"><span data-stu-id="bc27f-114">attr1</span></span>|<span data-ttu-id="bc27f-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="bc27f-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="bc27f-116">Hodnota1</span><span class="sxs-lookup"><span data-stu-id="bc27f-116">value1</span></span>||  
|<span data-ttu-id="bc27f-117">Argument</span><span class="sxs-lookup"><span data-stu-id="bc27f-117">value2</span></span>|<span data-ttu-id="bc27f-118">Text1</span><span class="sxs-lookup"><span data-stu-id="bc27f-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="bc27f-119">Prvky s podřízenými prvky</span><span class="sxs-lookup"><span data-stu-id="bc27f-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="bc27f-120">Elementy, které mají podřízené elementy, mají za následek odvozené tabulky.</span><span class="sxs-lookup"><span data-stu-id="bc27f-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="bc27f-121">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="bc27f-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="bc27f-122">Proces odvození vytvoří tabulku s názvem "Element1".</span><span class="sxs-lookup"><span data-stu-id="bc27f-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="bc27f-123">**Integrován** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="bc27f-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="bc27f-124">**Stolní** Element1</span><span class="sxs-lookup"><span data-stu-id="bc27f-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="bc27f-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="bc27f-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="bc27f-126">Text1</span><span class="sxs-lookup"><span data-stu-id="bc27f-126">Text1</span></span>|  
  
 <span data-ttu-id="bc27f-127">Pokud obsahuje atributy nebo podřízené elementy, které jsou odvozeny jako sloupce, je výsledkem dokumentu nebo kořenového prvku odvozená tabulka.</span><span class="sxs-lookup"><span data-stu-id="bc27f-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="bc27f-128">Pokud element dokumentu nemá žádné atributy a žádné podřízené prvky, které by byly odvozeny jako sloupce, je element odvozen jako **datová sada**.</span><span class="sxs-lookup"><span data-stu-id="bc27f-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="bc27f-129">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="bc27f-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="bc27f-130">Proces odvození vytvoří tabulku s názvem "DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="bc27f-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="bc27f-131">**Integrován** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="bc27f-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="bc27f-132">**Stolní** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="bc27f-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="bc27f-133">Element1</span><span class="sxs-lookup"><span data-stu-id="bc27f-133">Element1</span></span>|<span data-ttu-id="bc27f-134">Element2</span><span class="sxs-lookup"><span data-stu-id="bc27f-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="bc27f-135">Text1</span><span class="sxs-lookup"><span data-stu-id="bc27f-135">Text1</span></span>|<span data-ttu-id="bc27f-136">Text2</span><span class="sxs-lookup"><span data-stu-id="bc27f-136">Text2</span></span>|  
  
 <span data-ttu-id="bc27f-137">Případně zvažte následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="bc27f-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="bc27f-138">Proces odvození vytvoří datovou **sadu** s názvem "DocumentElement", která obsahuje tabulku s názvem "Element1".</span><span class="sxs-lookup"><span data-stu-id="bc27f-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="bc27f-139">**Integrován** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="bc27f-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="bc27f-140">**Stolní** Element1</span><span class="sxs-lookup"><span data-stu-id="bc27f-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="bc27f-141">attr1</span><span class="sxs-lookup"><span data-stu-id="bc27f-141">attr1</span></span>|<span data-ttu-id="bc27f-142">attr2</span><span class="sxs-lookup"><span data-stu-id="bc27f-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="bc27f-143">Hodnota1</span><span class="sxs-lookup"><span data-stu-id="bc27f-143">value1</span></span>|<span data-ttu-id="bc27f-144">Argument</span><span class="sxs-lookup"><span data-stu-id="bc27f-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="bc27f-145">Opakující se elementy</span><span class="sxs-lookup"><span data-stu-id="bc27f-145">Repeating Elements</span></span>  
 <span data-ttu-id="bc27f-146">Prvky, které se opakují, v jedné odvozené tabulce.</span><span class="sxs-lookup"><span data-stu-id="bc27f-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="bc27f-147">Zvažte například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="bc27f-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="bc27f-148">Proces odvození vytvoří tabulku s názvem "Element1".</span><span class="sxs-lookup"><span data-stu-id="bc27f-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="bc27f-149">**Integrován** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="bc27f-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="bc27f-150">**Stolní** Element1</span><span class="sxs-lookup"><span data-stu-id="bc27f-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="bc27f-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="bc27f-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="bc27f-152">Text1</span><span class="sxs-lookup"><span data-stu-id="bc27f-152">Text1</span></span>|  
|<span data-ttu-id="bc27f-153">Text2</span><span class="sxs-lookup"><span data-stu-id="bc27f-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc27f-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc27f-154">See also</span></span>

- [<span data-ttu-id="bc27f-155">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="bc27f-155">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="bc27f-156">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="bc27f-156">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="bc27f-157">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="bc27f-157">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="bc27f-158">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="bc27f-158">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="bc27f-159">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="bc27f-159">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="bc27f-160">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="bc27f-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
