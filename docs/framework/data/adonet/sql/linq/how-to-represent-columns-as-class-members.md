---
title: "Postupy: představují sloupce jako členy třídy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f0e797886b5e2fedafccf08b71e8cbb2791ea72b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-columns-as-class-members"></a>Postupy: představují sloupce jako členy třídy
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut přiřaďte pole nebo vlastnost sloupci databáze.  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a>Pro mapování pole nebo vlastnost ke sloupci databáze  
  
-   Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut deklarace vlastnost nebo pole.  
  
## <a name="example"></a>Příklad  
 Následující kód mapy `CustomerID` pole `Customer` třídy k `CustomerID` sloupec v `Customers` databázové tabulky.  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 Není nutné zadat <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> vlastnost, pokud název lze odvodit. Pokud název nezadáte, název se předpokládá, že se stejným názvem jako vlastnost nebo pole.  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to SQL objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Postupy: přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
