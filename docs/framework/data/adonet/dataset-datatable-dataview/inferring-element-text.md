---
title: Odvození textu elementu
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: d457985bfbec924748d1a418e318609b6837b9d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745156"
---
# <a name="inferring-element-text"></a><span data-ttu-id="35cda-102">Odvození textu elementu</span><span class="sxs-lookup"><span data-stu-id="35cda-102">Inferring Element Text</span></span>
<span data-ttu-id="35cda-103">Pokud element obsahuje text a nemá žádný podřízený element odvození podle tabulky jako je například (elementy s atributy) nebo opakované prvků, nový sloupec s názvem **TableName_Text** se přidá do tabulky, kterou si odvozuje pro element.</span><span class="sxs-lookup"><span data-stu-id="35cda-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="35cda-104">Text obsažen v elementu bude přidána na řádek v tabulce a uložená v novém sloupci.</span><span class="sxs-lookup"><span data-stu-id="35cda-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="35cda-105">**ColumnMapping** vlastnost nového sloupce, který bude nastavena na **MappingType.SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="35cda-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="35cda-106">Zvažte například následující kód XML.</span><span class="sxs-lookup"><span data-stu-id="35cda-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="35cda-107">Procesu odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci: **attr1** a **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="35cda-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="35cda-108">**ColumnMapping** vlastnost **attr1** sloupec bude nastaven na **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="35cda-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="35cda-109">**ColumnMapping** vlastnost **Element1_Text** sloupec bude nastaven na **MappingType.SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="35cda-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="35cda-110">**DataSet:** Prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="35cda-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="35cda-111">**Tabulka:** element1</span><span class="sxs-lookup"><span data-stu-id="35cda-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="35cda-112">attr1</span><span class="sxs-lookup"><span data-stu-id="35cda-112">attr1</span></span>|<span data-ttu-id="35cda-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="35cda-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="35cda-114">value1</span><span class="sxs-lookup"><span data-stu-id="35cda-114">value1</span></span>|<span data-ttu-id="35cda-115">Text1</span><span class="sxs-lookup"><span data-stu-id="35cda-115">Text1</span></span>|  
  
 <span data-ttu-id="35cda-116">Pokud element obsahuje text, ale má také podřízené prvky, které obsahují text, nebude na tabulku pro ukládání textu obsaženy v prvku přidán sloupec.</span><span class="sxs-lookup"><span data-stu-id="35cda-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="35cda-117">Text obsažen v elementu budou ignorovány, zatímco je zahrnut text podřízené elementy v řádku v tabulce.</span><span class="sxs-lookup"><span data-stu-id="35cda-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="35cda-118">Zvažte například následující kód XML.</span><span class="sxs-lookup"><span data-stu-id="35cda-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="35cda-119">Procesu odvození vytvoří tabulku s názvem **Element1** s jedním sloupcem s názvem **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="35cda-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="35cda-120">Text **ChildElement1** element bude obsahovat řádek v tabulce.</span><span class="sxs-lookup"><span data-stu-id="35cda-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="35cda-121">Další text se bude ignorovat.</span><span class="sxs-lookup"><span data-stu-id="35cda-121">The other text will be ignored.</span></span> <span data-ttu-id="35cda-122">**ColumnMapping** vlastnost **ChildElement1** sloupec bude nastaven na **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="35cda-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="35cda-123">**DataSet:** Prvek DocumentElement</span><span class="sxs-lookup"><span data-stu-id="35cda-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="35cda-124">**Tabulka:** element1</span><span class="sxs-lookup"><span data-stu-id="35cda-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="35cda-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="35cda-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="35cda-126">Text2</span><span class="sxs-lookup"><span data-stu-id="35cda-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35cda-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35cda-127">See also</span></span>
- [<span data-ttu-id="35cda-128">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="35cda-128">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="35cda-129">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="35cda-129">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="35cda-130">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="35cda-130">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="35cda-131">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="35cda-131">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="35cda-132">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="35cda-132">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="35cda-133">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="35cda-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
