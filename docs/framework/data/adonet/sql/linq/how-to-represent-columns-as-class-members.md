---
title: 'Postupy: Znázornění sloupců jako členů tříd'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 515a8477b3a9c72934e0ad11d7b1bf599e8b16a2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793512"
---
# <a name="how-to-represent-columns-as-class-members"></a><span data-ttu-id="046a4-102">Postupy: Znázornění sloupců jako členů tříd</span><span class="sxs-lookup"><span data-stu-id="046a4-102">How to: Represent Columns as Class Members</span></span>
<span data-ttu-id="046a4-103">K přidružení pole nebo vlastnosti k databázovému sloupci použijte atribut.<xref:System.Data.Linq.Mapping.ColumnAttribute> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="046a4-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to associate a field or property with a database column.</span></span>  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a><span data-ttu-id="046a4-104">Mapování pole nebo vlastnosti na sloupec databáze</span><span class="sxs-lookup"><span data-stu-id="046a4-104">To map a field or property to a database column</span></span>  
  
- <span data-ttu-id="046a4-105"><xref:System.Data.Linq.Mapping.ColumnAttribute> Přidejte atribut k deklaraci vlastnosti nebo pole.</span><span class="sxs-lookup"><span data-stu-id="046a4-105">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to the property or field declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="046a4-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="046a4-106">Example</span></span>  
 <span data-ttu-id="046a4-107">Následující kód mapuje `CustomerID` pole `Customer` ve `CustomerID` třídě`Customers` na sloupec v tabulce databáze.</span><span class="sxs-lookup"><span data-stu-id="046a4-107">The following code maps the `CustomerID` field in the `Customer` class to the `CustomerID` column in the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <span data-ttu-id="046a4-108"><xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> Vlastnost není nutné zadávat, pokud je možné název odvodit.</span><span class="sxs-lookup"><span data-stu-id="046a4-108">You do not have to specify the <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="046a4-109">Pokud název nezadáte, název se považuje za shodný s názvem vlastnosti nebo pole.</span><span class="sxs-lookup"><span data-stu-id="046a4-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="046a4-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="046a4-110">See also</span></span>

- [<span data-ttu-id="046a4-111">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="046a4-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="046a4-112">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="046a4-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
