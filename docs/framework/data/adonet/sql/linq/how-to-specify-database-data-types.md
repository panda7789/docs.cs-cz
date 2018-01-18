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
# <a name="how-to-specify-database-data-types"></a>Postupy: určení typů dat databáze
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut zadat přesný text, který definuje sloupec v tabulce deklaraci T-SQL.  
  
 Je nutné zadat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost pouze v případě, že máte v úmyslu použít <xref:System.Data.Linq.DataContext.CreateDatabase%2A> k vytvoření instance databáze.  
  
 Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>Pokud chcete zadat text k definování typu dat v tabulce T-SQL  
  
1.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2.  Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> vlastnost přesný text, který je používán T-SQL.  
  
## <a name="see-also"></a>Viz také  
 [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
