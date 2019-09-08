---
title: 'Postupy: Znázornění tabulek jako tříd'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 1169def4e0180b1d14103d4a968ff3ed56f63d0c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781759"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="b058e-102">Postupy: Znázornění tabulek jako tříd</span><span class="sxs-lookup"><span data-stu-id="b058e-102">How to: Represent Tables as Classes</span></span>
<span data-ttu-id="b058e-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Použijteatributkoznačenítřídyjakotřídyentity<xref:System.Data.Linq.Mapping.TableAttribute> přidružené k tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="b058e-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="b058e-104">Mapování třídy na databázovou tabulku</span><span class="sxs-lookup"><span data-stu-id="b058e-104">To map a class to a database table</span></span>  
  
- <span data-ttu-id="b058e-105"><xref:System.Data.Linq.Mapping.TableAttribute> Přidejte atribut do deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="b058e-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b058e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b058e-106">Example</span></span>  
 <span data-ttu-id="b058e-107">Následující kód vytvoří `Customer` třídu jako třídu entity, která je přidružena `Customers` k tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="b058e-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="b058e-108"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Vlastnost není nutné zadávat, pokud je možné název odvodit.</span><span class="sxs-lookup"><span data-stu-id="b058e-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="b058e-109">Pokud název nezadáte, název se považuje za shodný s názvem vlastnosti nebo pole.</span><span class="sxs-lookup"><span data-stu-id="b058e-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b058e-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b058e-110">See also</span></span>

- [<span data-ttu-id="b058e-111">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b058e-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="b058e-112">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="b058e-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
