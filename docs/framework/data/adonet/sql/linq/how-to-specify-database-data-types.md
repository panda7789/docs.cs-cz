---
title: 'Postupy: Zadání datových typů v databázi'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 09ca8dc6fa440138523bcd2905335a04517dd806
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793268"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="7340e-102">Postupy: Zadání datových typů v databázi</span><span class="sxs-lookup"><span data-stu-id="7340e-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="7340e-103">Použijte vlastnost u<xref:System.Data.Linq.Mapping.ColumnAttribute> atributu k určení přesného textu, který definuje sloupec v deklaraci tabulky T-SQL. <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7340e-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="7340e-104">Vlastnost je nutné zadat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> pouze v případě, že plánujete použít <xref:System.Data.Linq.DataContext.CreateDatabase%2A> k vytvoření instance databáze.</span><span class="sxs-lookup"><span data-stu-id="7340e-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="7340e-105">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="7340e-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="7340e-106">Určení textu pro definování datového typu v tabulce T-SQL</span><span class="sxs-lookup"><span data-stu-id="7340e-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1. <span data-ttu-id="7340e-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.</span><span class="sxs-lookup"><span data-stu-id="7340e-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="7340e-108">Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnosti na přesný text, který je používán T-SQL.</span><span class="sxs-lookup"><span data-stu-id="7340e-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7340e-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7340e-109">See also</span></span>

- [<span data-ttu-id="7340e-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7340e-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="7340e-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="7340e-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
