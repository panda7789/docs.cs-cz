---
title: Souhrn procesu odvození schématu datové sady
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: b0dd22412ddda86aa2883a26353abb1516a94e17
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785939"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="79361-102">Souhrn procesu odvození schématu datové sady</span><span class="sxs-lookup"><span data-stu-id="79361-102">Summary of the DataSet Schema Inference Process</span></span>
<span data-ttu-id="79361-103">Nejprve proces odvození určuje z dokumentu XML, které prvky budou odvozeny jako tabulky.</span><span class="sxs-lookup"><span data-stu-id="79361-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="79361-104">Ze zbývajícího souboru XML určí proces odvození sloupce pro tyto tabulky.</span><span class="sxs-lookup"><span data-stu-id="79361-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="79361-105">Pro vnořené tabulky vytvoří odvozený proces vnořené <xref:System.Data.DataRelation> objekty a. <xref:System.Data.ForeignKeyConstraint></span><span class="sxs-lookup"><span data-stu-id="79361-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="79361-106">Následuje stručný souhrn odvozených pravidel:</span><span class="sxs-lookup"><span data-stu-id="79361-106">Following is a brief summary of inference rules:</span></span>  
  
- <span data-ttu-id="79361-107">Prvky, které mají atributy, jsou odvozeny jako tabulky.</span><span class="sxs-lookup"><span data-stu-id="79361-107">Elements that have attributes are inferred as tables.</span></span>  
  
- <span data-ttu-id="79361-108">Prvky, které mají podřízené prvky, jsou odvozeny jako tabulky.</span><span class="sxs-lookup"><span data-stu-id="79361-108">Elements that have child elements are inferred as tables.</span></span>  
  
- <span data-ttu-id="79361-109">Prvky, které se opakují, jsou odvozeny jako jedna tabulka.</span><span class="sxs-lookup"><span data-stu-id="79361-109">Elements that repeat are inferred as a single table.</span></span>  
  
- <span data-ttu-id="79361-110">Pokud dokument nebo root, element nemá žádné atributy a žádné podřízené prvky, které by byly odvozeny jako sloupce, je odvozena jako <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="79361-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="79361-111">V opačném případě je element dokumentu odvozen jako tabulka.</span><span class="sxs-lookup"><span data-stu-id="79361-111">Otherwise, the document element is inferred as a table.</span></span>  
  
- <span data-ttu-id="79361-112">Atributy jsou odvozeny jako sloupce.</span><span class="sxs-lookup"><span data-stu-id="79361-112">Attributes are inferred as columns.</span></span>  
  
- <span data-ttu-id="79361-113">Prvky, které nemají žádné atributy ani podřízené prvky a které se neopakují, jsou odvozeny jako sloupce.</span><span class="sxs-lookup"><span data-stu-id="79361-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
- <span data-ttu-id="79361-114">Pro prvky, které jsou odvozeny jako vnořené tabulky v rámci jiných prvků, které jsou rovněž odvozeny jako tabulky, je mezi dvěma tabulkami vytvořen vnořený objekt **DataRelation** .</span><span class="sxs-lookup"><span data-stu-id="79361-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="79361-115">Do obou tabulek se přidá nový sloupec primárního klíče s názvem **TableName_Id** , který se používá v **datarelationu**.</span><span class="sxs-lookup"><span data-stu-id="79361-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="79361-116">**Objekt ForeignKeyConstraint** se vytvoří mezi dvěma tabulkami pomocí sloupce **TableName_Id** .</span><span class="sxs-lookup"><span data-stu-id="79361-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
- <span data-ttu-id="79361-117">Pro prvky, které jsou odvozeny jako tabulky a které obsahují text, ale nemají žádné podřízené prvky, je vytvořen nový sloupec s názvem **TableName_Text** pro text každého prvku.</span><span class="sxs-lookup"><span data-stu-id="79361-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="79361-118">Pokud je element odvozen jako tabulka a má text, ale také má podřízené prvky, text se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="79361-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79361-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79361-119">See also</span></span>

- [<span data-ttu-id="79361-120">Odvození relační struktury datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="79361-120">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="79361-121">Načtení datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="79361-121">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="79361-122">Načtení informací o schématu datové sady z XML</span><span class="sxs-lookup"><span data-stu-id="79361-122">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="79361-123">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="79361-123">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="79361-124">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="79361-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="79361-125">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="79361-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
