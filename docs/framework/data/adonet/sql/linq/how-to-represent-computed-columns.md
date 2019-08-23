---
title: 'Postupy: Znázornění vypočítaných sloupců'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: 01c3442448285893ebb476ed11889e073065d4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943535"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="38bb8-102">Postupy: Znázornění vypočítaných sloupců</span><span class="sxs-lookup"><span data-stu-id="38bb8-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="38bb8-103">Použijte vlastnost u<xref:System.Data.Linq.Mapping.ColumnAttribute> atributu pro reprezentaci sloupce, jehož obsah je výsledkem výpočtu. <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38bb8-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="38bb8-104">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="38bb8-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="38bb8-105">nepodporuje počítané sloupce jako primární klíče.</span><span class="sxs-lookup"><span data-stu-id="38bb8-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="38bb8-106">Reprezentace vypočítaného sloupce</span><span class="sxs-lookup"><span data-stu-id="38bb8-106">To represent a computed column</span></span>  
  
1. <span data-ttu-id="38bb8-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.</span><span class="sxs-lookup"><span data-stu-id="38bb8-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="38bb8-108">Do <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnosti přiřaďte řetězcovou reprezentaci vzorce.</span><span class="sxs-lookup"><span data-stu-id="38bb8-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38bb8-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38bb8-109">See also</span></span>

- [<span data-ttu-id="38bb8-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="38bb8-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="38bb8-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="38bb8-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
