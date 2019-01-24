---
title: 'Postupy: Připojení k databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: 8b30e6226b7663761b520258a37df0ebdda81fa6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739099"
---
# <a name="how-to-connect-to-a-database"></a>Postupy: Připojení k databázi
<xref:System.Data.Linq.DataContext> Je hlavní přenos, podle kterého připojení k databázi, načtení objektů z něj a odeslat změny zpět do něj. Můžete použít <xref:System.Data.Linq.DataContext> stejně jako byste použili [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>. Ve skutečnosti <xref:System.Data.Linq.DataContext> je inicializována s připojení nebo připojovací řetězec, který zadáte. Další informace najdete v tématu [metod DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 Účelem <xref:System.Data.Linq.DataContext> je převod žádostí pro objekty na dotazy SQL má být provedeno proti databázi a potom sestavit objektů mimo výsledky. <xref:System.Data.Linq.DataContext> Umožňuje [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] implementací stejný vzor jako standardní operátory dotazu operátor `Where` a `Select`.  
  
> [!IMPORTANT]
>  Zachování zabezpečené připojení má nejvyšší význam. Další informace najdete v tématu [zabezpečení v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Data.Linq.DataContext> slouží k připojení k ukázkové databázi Northwind a k načítání řádků zákazníků, jejichž Město je London.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Každá databázová tabulka je vyjádřena jako `Table` kolekce, které jsou k dispozici prostřednictvím <xref:System.Data.Linq.DataContext.GetTable%2A> metodu, pomocí třídy entity pro jeho rozpoznání.  
  
## <a name="example"></a>Příklad  
 Osvědčeným postupem je deklarovat silného typu <xref:System.Data.Linq.DataContext> aniž byste museli spoléhat na základní <xref:System.Data.Linq.DataContext> třídy a <xref:System.Data.Linq.DataContext.GetTable%2A> metoda. Silného typu <xref:System.Data.Linq.DataContext> deklaruje všechny `Table` kolekce jako členy kontextu, jako v následujícím příkladu.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Potom můžete vyjádřit dotaz Zákazníci z Londýna jednoduše jako:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také:
- [Komunikace s databází](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
