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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a404451b1dca085707d05d1db54047cd0db0c986
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-represent-columns-as-database-generated"></a>Postupy: představují sloupce jako generované databáze
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> vlastnost na <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení pole nebo vlastnost jako představující generované sloupec.  
  
 Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a>K určení pole nebo vlastnost jako představující sloupec generované databáze  
  
1.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2.  Nastavit hodnotu vlastnosti `true`.  
  
## <a name="see-also"></a>Viz také  
 [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
