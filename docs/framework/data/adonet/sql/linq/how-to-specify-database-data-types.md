---
title: "Postupy: určení typů dat databáze"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 17ac588a8cf6815b244cf0b515603263f41b53ad
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="1dda2-102">Postupy: určení typů dat databáze</span><span class="sxs-lookup"><span data-stu-id="1dda2-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="1dda2-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut zadat přesný text, který definuje sloupec v tabulce deklaraci T-SQL.</span><span class="sxs-lookup"><span data-stu-id="1dda2-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="1dda2-104">Je nutné zadat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost pouze v případě, že máte v úmyslu použít <xref:System.Data.Linq.DataContext.CreateDatabase%2A> k vytvoření instance databáze.</span><span class="sxs-lookup"><span data-stu-id="1dda2-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="1dda2-105">Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="1dda2-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="1dda2-106">Pokud chcete zadat text k definování typu dat v tabulce T-SQL</span><span class="sxs-lookup"><span data-stu-id="1dda2-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1.  <span data-ttu-id="1dda2-107">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="1dda2-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="1dda2-108">Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost přesný text, který je používán T-SQL.</span><span class="sxs-lookup"><span data-stu-id="1dda2-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dda2-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="1dda2-109">See Also</span></span>  
 [<span data-ttu-id="1dda2-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1dda2-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="1dda2-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="1dda2-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
