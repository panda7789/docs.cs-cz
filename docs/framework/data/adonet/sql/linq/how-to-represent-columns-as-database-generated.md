---
title: "Postupy: představují sloupce jako generované databáze"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a0b36e7035b885985e70203146957cdfca92148b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="8bf43-102">Postupy: představují sloupce jako generované databáze</span><span class="sxs-lookup"><span data-stu-id="8bf43-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="8bf43-103">Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> vlastnost na <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení pole nebo vlastnost jako představující generované sloupec.</span><span class="sxs-lookup"><span data-stu-id="8bf43-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="8bf43-104">Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="8bf43-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="8bf43-105">K určení pole nebo vlastnost jako představující sloupec generované databáze</span><span class="sxs-lookup"><span data-stu-id="8bf43-105">To designate a field or property as representing a database-generated column</span></span>  
  
1.  <span data-ttu-id="8bf43-106">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="8bf43-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="8bf43-107">Nastavit hodnotu vlastnosti `true`.</span><span class="sxs-lookup"><span data-stu-id="8bf43-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf43-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bf43-108">See Also</span></span>  
 [<span data-ttu-id="8bf43-109">Technologie LINQ to SQL objektový Model</span><span class="sxs-lookup"><span data-stu-id="8bf43-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="8bf43-110">Postupy: přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="8bf43-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
