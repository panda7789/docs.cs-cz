---
title: "Postupy: představují sloupce tak, aby umožňoval hodnoty Null"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: efa6f9d453940151dfe01d27827760521359ab67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a>Postupy: představují sloupce tak, aby umožňoval hodnoty Null
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k určení, že sloupec přidružené databáze může obsahovat hodnoty null.  
  
 Příklady kódu najdete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a>Chcete-li určit sloupec tak, aby umožňoval hodnoty null  
  
1.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2.  Nastavte <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> hodnotu vlastnosti na `true`.  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to SQL objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Postupy: přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
