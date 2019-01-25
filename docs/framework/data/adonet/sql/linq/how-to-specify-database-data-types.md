---
title: 'Postupy: Zadejte databázi datové typy'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 566ff545cd493eed637093c378aacc865a7f5e20
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620484"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="61579-102">Postupy: Zadejte databázi datové typy</span><span class="sxs-lookup"><span data-stu-id="61579-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="61579-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnosti <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut zadat přesný text, který definuje sloupce v tabulce deklaraci T-SQL.</span><span class="sxs-lookup"><span data-stu-id="61579-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="61579-104">Je nutné zadat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost jenom v případě, že máte v plánu používat <xref:System.Data.Linq.DataContext.CreateDatabase%2A> vytvořit instanci databáze.</span><span class="sxs-lookup"><span data-stu-id="61579-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="61579-105">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="61579-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="61579-106">Pokud chcete zadat text k definování typů dat v tabulce T-SQL</span><span class="sxs-lookup"><span data-stu-id="61579-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1.  <span data-ttu-id="61579-107">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="61579-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="61579-108">Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost přesný text, který používá T-SQL.</span><span class="sxs-lookup"><span data-stu-id="61579-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61579-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61579-109">See also</span></span>
- [<span data-ttu-id="61579-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="61579-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="61579-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="61579-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
