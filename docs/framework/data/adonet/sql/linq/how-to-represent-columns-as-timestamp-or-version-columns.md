---
title: 'Postupy: Znázornění sloupců jako sloupců časového razítka nebo verze'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: ef99e0420b328f94686e08256ecf229000467810
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793497"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="b1723-102">Postupy: Znázornění sloupců jako sloupců časového razítka nebo verze</span><span class="sxs-lookup"><span data-stu-id="b1723-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="b1723-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Pomocí<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> vlastnosti atributu<xref:System.Data.Linq.Mapping.ColumnAttribute> určete pole nebo vlastnost, které představují sloupec databáze, který obsahuje časové razítka databáze nebo čísla verzí.</span><span class="sxs-lookup"><span data-stu-id="b1723-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="b1723-104">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="b1723-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="b1723-105">Určení pole nebo vlastnosti představující sloupec časového razítka nebo verze</span><span class="sxs-lookup"><span data-stu-id="b1723-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1. <span data-ttu-id="b1723-106"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.</span><span class="sxs-lookup"><span data-stu-id="b1723-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="b1723-107">`true`Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> vlastnosti na.</span><span class="sxs-lookup"><span data-stu-id="b1723-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1723-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1723-108">See also</span></span>

- [<span data-ttu-id="b1723-109">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b1723-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="b1723-110">Postupy: Určení členů, kteří jsou testováni pro konflikty souběžnosti</span><span class="sxs-lookup"><span data-stu-id="b1723-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="b1723-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="b1723-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
