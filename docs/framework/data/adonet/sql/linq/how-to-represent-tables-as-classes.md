---
title: 'Postupy: Znázornění tabulek jako tříd'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: ff943fbc7ae137128d6c635fd2366ad14cf70d15
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620023"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="90011-102">Postupy: Znázornění tabulek jako tříd</span><span class="sxs-lookup"><span data-stu-id="90011-102">How to: Represent Tables as Classes</span></span>
<span data-ttu-id="90011-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> atribut k určení třídy jako třídu entity přidružené k databázové tabulky.</span><span class="sxs-lookup"><span data-stu-id="90011-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="90011-104">K mapování třídy do tabulky databáze</span><span class="sxs-lookup"><span data-stu-id="90011-104">To map a class to a database table</span></span>  
  
- <span data-ttu-id="90011-105">Přidat <xref:System.Data.Linq.Mapping.TableAttribute> atribut deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="90011-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90011-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="90011-106">Example</span></span>  
 <span data-ttu-id="90011-107">Následující kód vytvoří `Customer` třída jako třída entity, který je přidružen `Customers` databázové tabulky.</span><span class="sxs-lookup"><span data-stu-id="90011-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="90011-108">Není nutné určit <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> vlastnosti, pokud název jde odvodit.</span><span class="sxs-lookup"><span data-stu-id="90011-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="90011-109">Pokud název nezadáte, název se považuje za stejný název jako vlastnost nebo pole.</span><span class="sxs-lookup"><span data-stu-id="90011-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90011-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90011-110">See also</span></span>

- [<span data-ttu-id="90011-111">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="90011-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="90011-112">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="90011-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
