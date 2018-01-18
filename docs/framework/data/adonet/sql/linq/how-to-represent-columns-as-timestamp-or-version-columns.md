---
title: "Postupy: představují sloupce jako časové razítko nebo verze sloupce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2f97b87b2070ea39dbd16d03a967d80dcfc8f500
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="ed454-102">Postupy: představují sloupce jako časové razítko nebo verze sloupce</span><span class="sxs-lookup"><span data-stu-id="ed454-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="ed454-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení pole nebo vlastnost jako představující databáze sloupec obsahující čísla verze nebo časová razítka v databázi.</span><span class="sxs-lookup"><span data-stu-id="ed454-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="ed454-104">Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed454-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="ed454-105">K určení pole nebo vlastnost jako představující sloupec časového razítka nebo verze</span><span class="sxs-lookup"><span data-stu-id="ed454-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1.  <span data-ttu-id="ed454-106">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="ed454-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="ed454-107">Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> hodnotu vlastnosti na `true`.</span><span class="sxs-lookup"><span data-stu-id="ed454-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed454-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed454-108">See Also</span></span>  
 [<span data-ttu-id="ed454-109">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ed454-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="ed454-110">Postupy: Určení, kdy se mají členové testovat na konflikty souběžnosti</span><span class="sxs-lookup"><span data-stu-id="ed454-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 [<span data-ttu-id="ed454-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="ed454-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
