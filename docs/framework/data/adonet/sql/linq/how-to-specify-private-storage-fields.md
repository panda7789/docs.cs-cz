---
title: 'Postupy: Zadání polí privátního úložiště'
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: e6e6a4e28fbfb327f25874844f28bcbafa6d2805
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793217"
---
# <a name="how-to-specify-private-storage-fields"></a><span data-ttu-id="16288-102">Postupy: Zadání polí privátního úložiště</span><span class="sxs-lookup"><span data-stu-id="16288-102">How to: Specify Private Storage Fields</span></span>
<span data-ttu-id="16288-103">Pomocí vlastnosti u<xref:System.Data.Linq.Mapping.DataAttribute> atributu určete název podkladového pole úložiště. <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16288-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property on the <xref:System.Data.Linq.Mapping.DataAttribute> attribute to designate the name of an underlying storage field.</span></span>  
  
 <span data-ttu-id="16288-104">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="16288-104">For code examples, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a><span data-ttu-id="16288-105">Určení názvu základního pole úložiště</span><span class="sxs-lookup"><span data-stu-id="16288-105">To specify the name of an underlying storage field</span></span>  
  
1. <span data-ttu-id="16288-106"><xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.</span><span class="sxs-lookup"><span data-stu-id="16288-106">Add the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="16288-107">Přiřaďte název pole jako hodnotu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="16288-107">Assign the name of the field as the value of the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16288-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16288-108">See also</span></span>

- [<span data-ttu-id="16288-109">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="16288-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="16288-110">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="16288-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
