---
title: 'Postupy: Znázornění sloupců jako generovaných databází'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: bb9510986581ad6d3bcd0711aed681ef3a7c4e45
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781779"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="2f561-102">Postupy: Znázornění sloupců jako generovaných databází</span><span class="sxs-lookup"><span data-stu-id="2f561-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="2f561-103">Pomocí vlastnosti u<xref:System.Data.Linq.Mapping.ColumnAttribute> atributu určete pole nebo vlastnost, která představuje sloupec generovaný databází. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f561-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="2f561-104">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f561-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="2f561-105">Určení pole nebo vlastnosti jako reprezentace sloupce generovaného databází</span><span class="sxs-lookup"><span data-stu-id="2f561-105">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="2f561-106"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.</span><span class="sxs-lookup"><span data-stu-id="2f561-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="2f561-107">Nastavte hodnotu vlastnosti na `true`.</span><span class="sxs-lookup"><span data-stu-id="2f561-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f561-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f561-108">See also</span></span>

- [<span data-ttu-id="2f561-109">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2f561-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="2f561-110">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="2f561-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
