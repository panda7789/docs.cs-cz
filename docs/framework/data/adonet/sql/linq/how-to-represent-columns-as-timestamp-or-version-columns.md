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
