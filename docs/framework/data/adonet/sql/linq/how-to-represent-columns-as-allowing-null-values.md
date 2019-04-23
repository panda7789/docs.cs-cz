---
title: 'Postupy: Znázornění sloupců jako povolujících hodnoty null'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: ef8fa87963b91ef7140fbaefb657fc7904604b5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331153"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="337c8-102">Postupy: Znázornění sloupců jako povolujících hodnoty null</span><span class="sxs-lookup"><span data-stu-id="337c8-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="337c8-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení, že sloupec přidružená databáze může obsahovat hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="337c8-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="337c8-104">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="337c8-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="337c8-105">K označení sloupce jako povolujících hodnoty null</span><span class="sxs-lookup"><span data-stu-id="337c8-105">To designate a column as allowing null values</span></span>  
  
1. <span data-ttu-id="337c8-106">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="337c8-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="337c8-107">Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> hodnoty vlastnosti `true`.</span><span class="sxs-lookup"><span data-stu-id="337c8-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="337c8-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="337c8-108">See also</span></span>

- [<span data-ttu-id="337c8-109">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="337c8-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="337c8-110">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="337c8-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
