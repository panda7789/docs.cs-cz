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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 465be5cc0125d0ac45c0a00d7f1f238f3de8a390
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>Postupy: představují sloupce jako časové razítko nebo verze sloupce
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení pole nebo vlastnost jako představující databáze sloupec obsahující čísla verze nebo časová razítka v databázi.  
  
 Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>K určení pole nebo vlastnost jako představující sloupec časového razítka nebo verze  
  
1.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2.  Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> hodnotu vlastnosti na `true`.  
  
## <a name="see-also"></a>Viz také  
 [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Postupy: Určení, kdy se mají členové testovat na konflikty souběžnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
