---
title: "Postupy: představují tabulky jako třídy"
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
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 30bdb3334b574053595565e94993563959f49694
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-represent-tables-as-classes"></a>Postupy: představují tabulky jako třídy
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> atribut určit třídu jako třídu entity, která je přidružená k tabulce databáze.  
  
### <a name="to-map-a-class-to-a-database-table"></a>Pro mapování třídu do databázové tabulky  
  
-   Přidat <xref:System.Data.Linq.Mapping.TableAttribute> atribut deklaraci třídy.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří `Customer` třída jako třídu entity, který je spojen s `Customers` databázové tabulky.  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 Není nutné zadat <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> vlastnost, pokud název lze odvodit. Pokud název nezadáte, název se předpokládá, že se stejným názvem jako vlastnost nebo pole.  
  
## <a name="see-also"></a>Viz také  
 [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
