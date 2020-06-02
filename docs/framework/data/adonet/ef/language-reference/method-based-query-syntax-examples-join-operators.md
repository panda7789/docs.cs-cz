---
title: 'Příklady syntaxe dotazů založených na volání metody: Operátory spojení'
description: Pomocí těchto příkladů se naučíte používat metody join a GroupJoin k dotazování modelu pomocí syntaxe dotazu založeného na metodách v LINQ to Entities.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: 3b1445b39bdcd9a9b4d0672be0598233319cb85d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286828"
---
# <a name="method-based-query-syntax-examples-join-operators"></a>Příklady syntaxe dotazů založených na volání metody: Operátory spojení
Příklady v tomto tématu ukazují, jak používat <xref:System.Linq.Enumerable.Join%2A> <xref:System.Linq.Enumerable.GroupJoin%2A> metody a k dotazování [modelu prodeje společnosti AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) pomocí syntaxe dotazu založeného na metodách. Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.  
  
 Příklady v tomto tématu používají následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a>GroupJoin  
  
### <a name="example"></a>Příklad  
 Následující příklad provede v <xref:System.Linq.Enumerable.GroupJoin%2A> tabulkách SalesOrderHeader a SalesOrderDetail, aby našli počet objednávek na zákazníka. Spojení se skupinou je ekvivalentem levého vnějšího spojení, které vrátí každý prvek prvního (levého) zdroje dat, a to i v případě, že v jiném zdroji dat nejsou žádné korelační prvky.  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad provede <xref:System.Linq.Enumerable.GroupJoin%2A> tabulku Contacts a SalesOrderHeader k vyhledání počtu objednávek na kontakt. Zobrazí se počet objednávek a ID jednotlivých kontaktů.  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a>Spojit  
  
### <a name="example"></a>Příklad  
 Následující příklad provádí spojení s tabulkami Contact a SalesOrderHeader.  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a>Příklad  
 Následující příklad provádí spojení s tabulkami Contact a SalesOrderHeader a seskupí výsledky podle ID kontaktu.  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a>Viz také

- [Dotazy v technologii LINQ to Entities](queries-in-linq-to-entities.md)
