---
title: 'Postupy: Zadání polí privátního úložiště'
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: d127de889fdaa2eb2d03a96dae5aa3d856efe32a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549593"
---
# <a name="how-to-specify-private-storage-fields"></a><span data-ttu-id="d2db5-102">Postupy: Zadání polí privátního úložiště</span><span class="sxs-lookup"><span data-stu-id="d2db5-102">How to: Specify Private Storage Fields</span></span>
<span data-ttu-id="d2db5-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> vlastnost <xref:System.Data.Linq.Mapping.DataAttribute> atribut k určení názvu zdrojové pole úložiště.</span><span class="sxs-lookup"><span data-stu-id="d2db5-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property on the <xref:System.Data.Linq.Mapping.DataAttribute> attribute to designate the name of an underlying storage field.</span></span>  
  
 <span data-ttu-id="d2db5-104">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="d2db5-104">For code examples, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a><span data-ttu-id="d2db5-105">Chcete-li určit název podkladové pole úložiště</span><span class="sxs-lookup"><span data-stu-id="d2db5-105">To specify the name of an underlying storage field</span></span>  
  
1.  <span data-ttu-id="d2db5-106">Přidat <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="d2db5-106">Add the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="d2db5-107">Přiřaďte název pole jako hodnotu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d2db5-107">Assign the name of the field as the value of the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2db5-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2db5-108">See also</span></span>
- [<span data-ttu-id="d2db5-109">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d2db5-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="d2db5-110">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="d2db5-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
