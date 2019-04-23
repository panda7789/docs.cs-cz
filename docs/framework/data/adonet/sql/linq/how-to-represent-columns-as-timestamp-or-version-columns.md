---
title: 'Postupy: Znázornění sloupců jako sloupců časového razítka nebo verze'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: db73bf4880d8f5556247f7b037fca24b0ddc56d6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297886"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="afd44-102">Postupy: Znázornění sloupců jako sloupců časového razítka nebo verze</span><span class="sxs-lookup"><span data-stu-id="afd44-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="afd44-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení pole nebo vlastnost jako představuje sloupci databáze, který obsahuje čísla časová razítka nebo verze databáze.</span><span class="sxs-lookup"><span data-stu-id="afd44-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="afd44-104">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="afd44-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="afd44-105">K určení pole nebo vlastnost jako sloupec časového razítka nebo verze</span><span class="sxs-lookup"><span data-stu-id="afd44-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1. <span data-ttu-id="afd44-106">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="afd44-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="afd44-107">Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> hodnoty vlastnosti `true`.</span><span class="sxs-lookup"><span data-stu-id="afd44-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd44-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afd44-108">See also</span></span>

- [<span data-ttu-id="afd44-109">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="afd44-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="afd44-110">Postupy: Určete, že které členy jsou testovat na konflikty souběžnosti</span><span class="sxs-lookup"><span data-stu-id="afd44-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="afd44-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="afd44-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
