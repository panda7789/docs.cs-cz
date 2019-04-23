---
title: 'Postupy: Znázornění sloupců jako generovaných databází'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 2803697c668a8e1dbbeb426ea41b64878f70c145
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307909"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="ab6af-102">Postupy: Znázornění sloupců jako generovaných databází</span><span class="sxs-lookup"><span data-stu-id="ab6af-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="ab6af-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení pole nebo vlastnost jako generovaných databází sloupec.</span><span class="sxs-lookup"><span data-stu-id="ab6af-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="ab6af-104">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="ab6af-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="ab6af-105">K určení pole nebo vlastnost jako sloupec generovaných databází</span><span class="sxs-lookup"><span data-stu-id="ab6af-105">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="ab6af-106">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="ab6af-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="ab6af-107">Nastavte hodnotu vlastnosti na `true`.</span><span class="sxs-lookup"><span data-stu-id="ab6af-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab6af-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab6af-108">See also</span></span>

- [<span data-ttu-id="ab6af-109">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ab6af-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="ab6af-110">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="ab6af-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
