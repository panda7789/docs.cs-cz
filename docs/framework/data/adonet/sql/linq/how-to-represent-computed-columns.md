---
title: 'Postupy: představují vypočítaného sloupce'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: c53c781e8d4ec6836e032120816c3ef55de2ae0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353100"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="7d1b8-102">Postupy: představují vypočítaného sloupce</span><span class="sxs-lookup"><span data-stu-id="7d1b8-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="7d1b8-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut představují sloupce, jejichž obsah je výsledek výpočtu.</span><span class="sxs-lookup"><span data-stu-id="7d1b8-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="7d1b8-104">Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d1b8-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7d1b8-105"> Počítané sloupce nepodporuje jako primární klíče.</span><span class="sxs-lookup"><span data-stu-id="7d1b8-105"> does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="7d1b8-106">Představují počítaný sloupec</span><span class="sxs-lookup"><span data-stu-id="7d1b8-106">To represent a computed column</span></span>  
  
1.  <span data-ttu-id="7d1b8-107">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="7d1b8-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="7d1b8-108">Přiřadit řetězcovou reprezentaci vzorec k <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7d1b8-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d1b8-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d1b8-109">See Also</span></span>  
 [<span data-ttu-id="7d1b8-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7d1b8-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="7d1b8-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="7d1b8-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
