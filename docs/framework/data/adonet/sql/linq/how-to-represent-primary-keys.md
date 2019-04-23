---
title: 'Postupy: Znázornění primárních klíčů'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: dcb8929c9cd9a7b88f19d760b70117a1092760f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295585"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="0308e-102">Postupy: Znázornění primárních klíčů</span><span class="sxs-lookup"><span data-stu-id="0308e-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="0308e-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení vlastnost nebo pole představující primární klíč pro sloupce databáze.</span><span class="sxs-lookup"><span data-stu-id="0308e-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="0308e-104">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="0308e-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0308e-105">Počítané sloupce nepodporuje jako primární klíče.</span><span class="sxs-lookup"><span data-stu-id="0308e-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="0308e-106">Chcete-li určit vlastnost nebo pole jako primární klíč</span><span class="sxs-lookup"><span data-stu-id="0308e-106">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="0308e-107">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="0308e-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="0308e-108">Zadejte hodnotu jako `true`.</span><span class="sxs-lookup"><span data-stu-id="0308e-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0308e-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0308e-109">See also</span></span>

- [<span data-ttu-id="0308e-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0308e-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="0308e-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="0308e-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
