---
title: "Příklady syntaxe výrazu dotazu: Operátory spojení"
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
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f7cc902fe940c4d46d147061abfcd03a5fddae59
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="query-expression-syntax-examples-join-operators"></a>Příklady syntaxe výrazu dotazu: Operátory spojení
Připojení je důležité operace v dotazech, které cílí zdrojů dat, které nemají žádné navigaci relace mezi sebou, jako jsou tabulky relační databáze. Spojení dvou zdrojů dat je přidružení objektů v jeden zdroj dat s objekty, které sdílejí společný atribut v datovém zdroji. Další informace najdete v tématu [standardní přehled operátory dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 V příkladech v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.GroupJoin%2A> a <xref:System.Linq.Enumerable.Join%2A> metody k dotazování [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) pomocí syntaxe výrazu dotazu. Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.  
  
 V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a>GroupJoin  
  
### <a name="example"></a>Příklad  
 Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes SalesOrderHeader a podrobnosti prodejní objednávky tabulky najít číslo objednávky každého zákazníka. Připojení skupiny je ekvivalentem levé vnější spojení, která vrátí hodnotu každý prvek první zdroje dat (levém), i když žádné korelační elementy jsou v datovém zdroji.  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a>Příklad  
 Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes tabulky kontaktů a SalesOrderHeader najít číslo objednávky za kontakt. Zobrazí se počet pořadí a identifikátory pro každý kontakt.  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
### <a name="example"></a>Příklad  
 Následující příklad provádí <xref:System.Linq.Enumerable.GroupJoin%2A> přes kontaktu a SalesOrderHeader tabulky. Připojení skupiny je ekvivalentem levé vnější spojení, která vrátí hodnotu každý prvek první zdroje dat (levém), i když žádné korelační elementy jsou v datovém zdroji.  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a>Join  
  
### <a name="example"></a>Příklad  
 Následující příklad spojí přes SalesOrderHeader a podrobnosti prodejní objednávky tabulky, které chcete získat online objednávky z srpnu.  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Viz také  
 [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
