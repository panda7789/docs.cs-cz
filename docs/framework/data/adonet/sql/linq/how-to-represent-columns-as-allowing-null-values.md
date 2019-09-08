---
title: 'Postupy: Znázornění sloupců jako povolujících hodnoty null'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 00a837467010c2d8a9f0ca16d6aba2fc5f4c973f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781808"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="858b5-102">Postupy: Znázornění sloupců jako povolujících hodnoty null</span><span class="sxs-lookup"><span data-stu-id="858b5-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="858b5-103">Pomocí vlastnosti u<xref:System.Data.Linq.Mapping.ColumnAttribute> atributu určete, že sloupec přidružené databáze může obsahovat hodnoty null. <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="858b5-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="858b5-104">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="858b5-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="858b5-105">Určení sloupce tak, aby umožňoval hodnoty null</span><span class="sxs-lookup"><span data-stu-id="858b5-105">To designate a column as allowing null values</span></span>  
  
1. <span data-ttu-id="858b5-106"><xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.</span><span class="sxs-lookup"><span data-stu-id="858b5-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="858b5-107">`true`Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> vlastnosti na.</span><span class="sxs-lookup"><span data-stu-id="858b5-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="858b5-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="858b5-108">See also</span></span>

- [<span data-ttu-id="858b5-109">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="858b5-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="858b5-110">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="858b5-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
