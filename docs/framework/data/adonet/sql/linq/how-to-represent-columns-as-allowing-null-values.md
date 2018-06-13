---
title: 'Postupy: představují sloupce tak, aby umožňoval hodnoty Null'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 6700ee5d4de53dd82da29d48ca7c42785d52afc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355974"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="bd63a-102">Postupy: představují sloupce tak, aby umožňoval hodnoty Null</span><span class="sxs-lookup"><span data-stu-id="bd63a-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="bd63a-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení, že sloupec přidružené databáze může obsahovat hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="bd63a-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="bd63a-104">Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="bd63a-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="bd63a-105">Chcete-li určit sloupec tak, aby umožňoval hodnoty null</span><span class="sxs-lookup"><span data-stu-id="bd63a-105">To designate a column as allowing null values</span></span>  
  
1.  <span data-ttu-id="bd63a-106">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="bd63a-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="bd63a-107">Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> hodnotu vlastnosti na `true`.</span><span class="sxs-lookup"><span data-stu-id="bd63a-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd63a-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd63a-108">See Also</span></span>  
 [<span data-ttu-id="bd63a-109">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="bd63a-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="bd63a-110">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="bd63a-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
