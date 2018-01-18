---
title: "Odvození textu elementu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 239c70ca0e7f8894b988f17d248b2e5b3b98bf6a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-element-text"></a><span data-ttu-id="d980c-102">Odvození textu elementu</span><span class="sxs-lookup"><span data-stu-id="d980c-102">Inferring Element Text</span></span>
<span data-ttu-id="d980c-103">Pokud element obsahuje text a nemá žádné podřízené prvky k odvodit, protože tabulky, jako je například (elementy s atributy) nebo opakujících se prvků, nový sloupec s názvem **TableName_Text** přidá do tabulky, který je používán pro daný element.</span><span class="sxs-lookup"><span data-stu-id="d980c-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="d980c-104">Text obsažené v elementu budou přidány do řádek v tabulce a uložená do nového sloupce.</span><span class="sxs-lookup"><span data-stu-id="d980c-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="d980c-105">**ColumnMapping** vlastnost nového sloupce, bude nastavena pro **MappingType.SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="d980c-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="d980c-106">Zvažte například následující kód XML.</span><span class="sxs-lookup"><span data-stu-id="d980c-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d980c-107">Proces odvození vytvoří tabulku s názvem **Element1** s dva sloupce: **attr1** a **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="d980c-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="d980c-108">**ColumnMapping** vlastnost **attr1** sloupec bude nastavena pro **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="d980c-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="d980c-109">**ColumnMapping** vlastnost **Element1_Text** sloupec bude nastavena pro **MappingType.SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="d980c-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="d980c-110">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d980c-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d980c-111">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="d980c-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d980c-112">attr1</span><span class="sxs-lookup"><span data-stu-id="d980c-112">attr1</span></span>|<span data-ttu-id="d980c-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="d980c-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="d980c-114">value1</span><span class="sxs-lookup"><span data-stu-id="d980c-114">value1</span></span>|<span data-ttu-id="d980c-115">Text1</span><span class="sxs-lookup"><span data-stu-id="d980c-115">Text1</span></span>|  
  
 <span data-ttu-id="d980c-116">Pokud element obsahuje text, ale také obsahuje podřízené elementy, které obsahují text, nepřidají sloupce pro tabulku pro ukládání textu obsažené v elementu.</span><span class="sxs-lookup"><span data-stu-id="d980c-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="d980c-117">Text obsažené v elementu budou ignorovány, zatímco text v podřízených elementů je součástí řádek v tabulce.</span><span class="sxs-lookup"><span data-stu-id="d980c-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="d980c-118">Zvažte například následující kód XML.</span><span class="sxs-lookup"><span data-stu-id="d980c-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="d980c-119">Proces odvození vytvoří tabulku s názvem **Element1** s jedním sloupcem s názvem **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="d980c-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="d980c-120">Text pro **ChildElement1** element budou zahrnuty do řádek v tabulce.</span><span class="sxs-lookup"><span data-stu-id="d980c-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="d980c-121">Další text se budou ignorovat.</span><span class="sxs-lookup"><span data-stu-id="d980c-121">The other text will be ignored.</span></span> <span data-ttu-id="d980c-122">**ColumnMapping** vlastnost **ChildElement1** sloupec bude nastavena pro **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="d980c-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="d980c-123">**Datová sada:** prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d980c-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d980c-124">**Tabulka:** Element1</span><span class="sxs-lookup"><span data-stu-id="d980c-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d980c-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="d980c-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="d980c-126">Text2</span><span class="sxs-lookup"><span data-stu-id="d980c-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d980c-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="d980c-127">See Also</span></span>  
 [<span data-ttu-id="d980c-128">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="d980c-128">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="d980c-129">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="d980c-129">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="d980c-130">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="d980c-130">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="d980c-131">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="d980c-131">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="d980c-132">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="d980c-132">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="d980c-133">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="d980c-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
