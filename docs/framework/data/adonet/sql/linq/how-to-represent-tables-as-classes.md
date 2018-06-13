---
title: 'Postupy: představují tabulky jako třídy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 363efa4e4a6e3e7cfb757ee554e24a7963882278
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362974"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="69c88-102">Postupy: představují tabulky jako třídy</span><span class="sxs-lookup"><span data-stu-id="69c88-102">How to: Represent Tables as Classes</span></span>
<span data-ttu-id="69c88-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> atribut určit třídu jako třídu entity, která je přidružená k tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="69c88-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="69c88-104">Pro mapování třídu do databázové tabulky</span><span class="sxs-lookup"><span data-stu-id="69c88-104">To map a class to a database table</span></span>  
  
-   <span data-ttu-id="69c88-105">Přidat <xref:System.Data.Linq.Mapping.TableAttribute> atribut deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="69c88-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69c88-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="69c88-106">Example</span></span>  
 <span data-ttu-id="69c88-107">Následující kód vytvoří `Customer` třída jako třídu entity, který je spojen s `Customers` databázové tabulky.</span><span class="sxs-lookup"><span data-stu-id="69c88-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="69c88-108">Není nutné zadat <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> vlastnost, pokud název lze odvodit.</span><span class="sxs-lookup"><span data-stu-id="69c88-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="69c88-109">Pokud název nezadáte, název se předpokládá, že se stejným názvem jako vlastnost nebo pole.</span><span class="sxs-lookup"><span data-stu-id="69c88-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c88-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="69c88-110">See Also</span></span>  
 [<span data-ttu-id="69c88-111">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="69c88-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="69c88-112">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="69c88-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
