---
title: 'Postupy: Znázornění vypočítaných sloupců'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: f624bb49773af2c0053851ac55727b6db8632131
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204117"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="7b62b-102">Postupy: Znázornění vypočítaných sloupců</span><span class="sxs-lookup"><span data-stu-id="7b62b-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="7b62b-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnosti <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k reprezentaci sloupec, jehož obsahem je výsledek výpočtu.</span><span class="sxs-lookup"><span data-stu-id="7b62b-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="7b62b-104">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="7b62b-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7b62b-105">Počítané sloupce nepodporuje jako primární klíče.</span><span class="sxs-lookup"><span data-stu-id="7b62b-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="7b62b-106">K reprezentaci počítaný sloupec</span><span class="sxs-lookup"><span data-stu-id="7b62b-106">To represent a computed column</span></span>  
  
1.  <span data-ttu-id="7b62b-107">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="7b62b-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="7b62b-108">Přiřadit řetězcovou reprezentaci vzorec tak, aby <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7b62b-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b62b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b62b-109">See also</span></span>

- [<span data-ttu-id="7b62b-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7b62b-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="7b62b-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="7b62b-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
