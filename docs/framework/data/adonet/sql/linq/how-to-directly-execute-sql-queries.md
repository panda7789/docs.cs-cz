---
title: "Postupy: přímo provádění dotazů SQL"
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
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ccc47a1ea740c5106517f6f53620ddc8097c531
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-directly-execute-sql-queries"></a>Postupy: přímo provádění dotazů SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Přeloží dotazy, které zapisovat do parametrizované dotazy SQL (v textové podobě) a odešle je k systému SQL server pro zpracování.  
  
 SQL nelze provést řadu metod, které mohou být místně dostupné pro vaši aplikaci. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]pokusí se převést tyto místní metody na ekvivalentní operací a funkcí, které jsou k dispozici v prostředí SQL. Většina metody a operátory na [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] vestavěné typy mít přímý převody příkazy SQL. Některé je možné vytvořit z funkcí, které jsou k dispozici. Ty, které není možné vygenerovat výjimky v době běhu. Další informace najdete v tématu [mapování typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 V případech, kde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazu je nedostatečná pro úlohu specializované, můžete použít <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metodu pro spuštění příkazu jazyka SQL a pak převést výsledek dotazu přímo do objektů.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu předpokládáme, že data `Customer` třída je rozdělena ve dvou tabulek (customer1 a customer2). Dotaz vrátí posloupnost `Customer` objekty.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 Tak dlouho, dokud shodovat s názvy sloupců v tabulkové výsledky sloupce vlastnosti třídy entity [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří vašich objektů mimo jakýkoli dotaz SQL.  
  
## <a name="example"></a>Příklad  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda poskytuje také další parametry. Použijte například následující kód k provedení parametrizovaného dotazu.  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 Parametry jsou vyjádřeny v textu dotazu pomocí stejné složené zápisu používané `Console.WriteLine()` a `String.Format()`. Ve skutečnosti `String.Format()` se ve skutečnosti volá na řetězec dotazu, který zadáte, nahraďte složené braced parametry se vygeneruje názvy parametrů jako @p0, @p1 ..., @p(ne).  
  
## <a name="see-also"></a>Viz také  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Dotaz na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
