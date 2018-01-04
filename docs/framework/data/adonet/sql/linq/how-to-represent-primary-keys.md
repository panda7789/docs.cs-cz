---
title: "Postupy: představují primární klíče"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: cf1ba7d0f08d6b0a7dc37af233ad27695cde2a19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="5a8d7-102">Postupy: představují primární klíče</span><span class="sxs-lookup"><span data-stu-id="5a8d7-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="5a8d7-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> vlastnost na <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut a nastavit vlastnost nebo pole představující primární klíč pro sloupci databáze.</span><span class="sxs-lookup"><span data-stu-id="5a8d7-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="5a8d7-104">Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a8d7-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5a8d7-105">Počítané sloupce nepodporuje jako primární klíče.</span><span class="sxs-lookup"><span data-stu-id="5a8d7-105"> does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="5a8d7-106">Chcete-li určit vlastnost nebo pole jako primární klíč</span><span class="sxs-lookup"><span data-stu-id="5a8d7-106">To designate a property or field as a primary key</span></span>  
  
1.  <span data-ttu-id="5a8d7-107">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="5a8d7-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="5a8d7-108">Zadejte hodnotu jako `true`.</span><span class="sxs-lookup"><span data-stu-id="5a8d7-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8d7-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a8d7-109">See Also</span></span>  
 [<span data-ttu-id="5a8d7-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5a8d7-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="5a8d7-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="5a8d7-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
