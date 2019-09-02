---
title: Odvození textu elementu
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: d8d64c0cbb0aecf736a54fa6816e286ab7efa191
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203539"
---
# <a name="inferring-element-text"></a><span data-ttu-id="20197-102">Odvození textu elementu</span><span class="sxs-lookup"><span data-stu-id="20197-102">Inferring Element Text</span></span>
<span data-ttu-id="20197-103">Pokud element obsahuje text a nemá odvoditelné žádné podřízené prvky jako tabulky (například elementy s atributy nebo opakujícími se prvky), přidá se do tabulky, která je odvozena pro prvek, nový sloupec s názvem **TableName_Text** .</span><span class="sxs-lookup"><span data-stu-id="20197-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="20197-104">Text obsažený v elementu se přidá do řádku v tabulce a uloží se do nového sloupce.</span><span class="sxs-lookup"><span data-stu-id="20197-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="20197-105">Vlastnost **ColumnMapping** nového sloupce bude nastavena na **MappingType. SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="20197-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="20197-106">Zvažte například následující kód XML.</span><span class="sxs-lookup"><span data-stu-id="20197-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="20197-107">Proces odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci: **attr1** a **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="20197-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="20197-108">Vlastnost **ColumnMapping** sloupce **attr1** bude nastavena na **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="20197-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="20197-109">Vlastnost **ColumnMapping** sloupce **Element1_Text** bude nastavena na **MappingType. SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="20197-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="20197-110">**Integrován** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="20197-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="20197-111">**Stolní** Element1</span><span class="sxs-lookup"><span data-stu-id="20197-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="20197-112">attr1</span><span class="sxs-lookup"><span data-stu-id="20197-112">attr1</span></span>|<span data-ttu-id="20197-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="20197-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="20197-114">Hodnota1</span><span class="sxs-lookup"><span data-stu-id="20197-114">value1</span></span>|<span data-ttu-id="20197-115">Text1</span><span class="sxs-lookup"><span data-stu-id="20197-115">Text1</span></span>|  
  
 <span data-ttu-id="20197-116">Pokud element obsahuje text, ale také obsahuje podřízené prvky, které obsahují text, sloupec nebude přidán do tabulky, aby ukládal text obsažený v elementu.</span><span class="sxs-lookup"><span data-stu-id="20197-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="20197-117">Text obsažený v elementu bude ignorován, zatímco text v podřízených prvcích je zahrnut do řádku v tabulce.</span><span class="sxs-lookup"><span data-stu-id="20197-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="20197-118">Zvažte například následující kód XML.</span><span class="sxs-lookup"><span data-stu-id="20197-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="20197-119">Proces odvození vytvoří tabulku s názvem **Element1** s jedním sloupcem s názvem **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="20197-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="20197-120">Text elementu **ChildElement1** bude zahrnut do řádku v tabulce.</span><span class="sxs-lookup"><span data-stu-id="20197-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="20197-121">Druhý text bude ignorován.</span><span class="sxs-lookup"><span data-stu-id="20197-121">The other text will be ignored.</span></span> <span data-ttu-id="20197-122">Vlastnost **ColumnMapping** sloupce **ChildElement1** bude nastavena na **MappingType. element**.</span><span class="sxs-lookup"><span data-stu-id="20197-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="20197-123">**Integrován** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="20197-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="20197-124">**Stolní** Element1</span><span class="sxs-lookup"><span data-stu-id="20197-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="20197-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="20197-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="20197-126">Text2</span><span class="sxs-lookup"><span data-stu-id="20197-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20197-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20197-127">See also</span></span>

- [<span data-ttu-id="20197-128">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="20197-128">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="20197-129">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="20197-129">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="20197-130">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="20197-130">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="20197-131">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="20197-131">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="20197-132">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="20197-132">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="20197-133">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="20197-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
