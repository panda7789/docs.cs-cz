---
title: 'Postupy: Zadání datových typů v databázi'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 67f23ff06aefbcff4ba7e2eaab63d9b8493b9717
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333207"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="2ac72-102">Postupy: Zadání datových typů v databázi</span><span class="sxs-lookup"><span data-stu-id="2ac72-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="2ac72-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnosti <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut zadat přesný text, který definuje sloupce v tabulce deklaraci T-SQL.</span><span class="sxs-lookup"><span data-stu-id="2ac72-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="2ac72-104">Je nutné zadat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost jenom v případě, že máte v plánu používat <xref:System.Data.Linq.DataContext.CreateDatabase%2A> vytvořit instanci databáze.</span><span class="sxs-lookup"><span data-stu-id="2ac72-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="2ac72-105">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="2ac72-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="2ac72-106">Pokud chcete zadat text k definování typů dat v tabulce T-SQL</span><span class="sxs-lookup"><span data-stu-id="2ac72-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1. <span data-ttu-id="2ac72-107">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="2ac72-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="2ac72-108">Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost přesný text, který používá T-SQL.</span><span class="sxs-lookup"><span data-stu-id="2ac72-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac72-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ac72-109">See also</span></span>

- [<span data-ttu-id="2ac72-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2ac72-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="2ac72-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="2ac72-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
