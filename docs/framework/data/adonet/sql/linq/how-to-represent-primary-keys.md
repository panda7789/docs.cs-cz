---
title: 'Postupy: představují primární klíče'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: dae8603a18318f45182c7148b10b8194e67fd017
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352587"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="f15ea-102">Postupy: představují primární klíče</span><span class="sxs-lookup"><span data-stu-id="f15ea-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="f15ea-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> vlastnost na <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut a nastavit vlastnost nebo pole představující primární klíč pro sloupci databáze.</span><span class="sxs-lookup"><span data-stu-id="f15ea-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="f15ea-104">Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="f15ea-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f15ea-105"> Počítané sloupce nepodporuje jako primární klíče.</span><span class="sxs-lookup"><span data-stu-id="f15ea-105"> does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="f15ea-106">Chcete-li určit vlastnost nebo pole jako primární klíč</span><span class="sxs-lookup"><span data-stu-id="f15ea-106">To designate a property or field as a primary key</span></span>  
  
1.  <span data-ttu-id="f15ea-107">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="f15ea-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="f15ea-108">Zadejte hodnotu jako `true`.</span><span class="sxs-lookup"><span data-stu-id="f15ea-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15ea-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="f15ea-109">See Also</span></span>  
 [<span data-ttu-id="f15ea-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f15ea-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="f15ea-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="f15ea-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
