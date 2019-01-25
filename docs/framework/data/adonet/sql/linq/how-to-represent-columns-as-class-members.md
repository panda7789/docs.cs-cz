---
title: 'Postupy: Znázornění sloupců jako členů tříd'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 7a772de27583f35b18a4fa5854e61768443e5ba5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652553"
---
# <a name="how-to-represent-columns-as-class-members"></a><span data-ttu-id="7806f-102">Postupy: Znázornění sloupců jako členů tříd</span><span class="sxs-lookup"><span data-stu-id="7806f-102">How to: Represent Columns as Class Members</span></span>
<span data-ttu-id="7806f-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> atributu na pole nebo vlastnost přidružit sloupce databáze.</span><span class="sxs-lookup"><span data-stu-id="7806f-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to associate a field or property with a database column.</span></span>  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a><span data-ttu-id="7806f-104">Mapovat pole nebo vlastnost ke sloupci databáze</span><span class="sxs-lookup"><span data-stu-id="7806f-104">To map a field or property to a database column</span></span>  
  
-   <span data-ttu-id="7806f-105">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut deklaraci vlastnosti nebo pole.</span><span class="sxs-lookup"><span data-stu-id="7806f-105">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to the property or field declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7806f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7806f-106">Example</span></span>  
 <span data-ttu-id="7806f-107">Následující map kódu `CustomerID` pole `Customer` třídu `CustomerID` sloupec v `Customers` databázové tabulky.</span><span class="sxs-lookup"><span data-stu-id="7806f-107">The following code maps the `CustomerID` field in the `Customer` class to the `CustomerID` column in the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <span data-ttu-id="7806f-108">Není nutné určit <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> vlastnosti, pokud název jde odvodit.</span><span class="sxs-lookup"><span data-stu-id="7806f-108">You do not have to specify the <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="7806f-109">Pokud název nezadáte, název se považuje za stejný název jako vlastnost nebo pole.</span><span class="sxs-lookup"><span data-stu-id="7806f-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7806f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7806f-110">See also</span></span>
- [<span data-ttu-id="7806f-111">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7806f-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="7806f-112">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="7806f-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
