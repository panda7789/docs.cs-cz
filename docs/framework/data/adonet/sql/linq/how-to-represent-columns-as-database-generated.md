---
title: 'Postupy: představují sloupce jako generované databáze'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: f6b127208ae359b43f273f54d7b5c72933c2eba6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353738"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="0160f-102">Postupy: představují sloupce jako generované databáze</span><span class="sxs-lookup"><span data-stu-id="0160f-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="0160f-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> vlastnost na <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení pole nebo vlastnost jako představující generované sloupec.</span><span class="sxs-lookup"><span data-stu-id="0160f-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="0160f-104">Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="0160f-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="0160f-105">K určení pole nebo vlastnost jako představující sloupec generované databáze</span><span class="sxs-lookup"><span data-stu-id="0160f-105">To designate a field or property as representing a database-generated column</span></span>  
  
1.  <span data-ttu-id="0160f-106">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="0160f-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="0160f-107">Nastavit hodnotu vlastnosti `true`.</span><span class="sxs-lookup"><span data-stu-id="0160f-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0160f-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="0160f-108">See Also</span></span>  
 [<span data-ttu-id="0160f-109">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0160f-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="0160f-110">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="0160f-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
