---
title: 'Postupy: Připojení k databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: ebf630c08714a2e5162ba072f88b7fbdef7ca0f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964049"
---
# <a name="how-to-connect-to-a-database"></a>Postupy: Připojení k databázi
<xref:System.Data.Linq.DataContext> Je hlavní přenos, ke kterému se připojujete, načítají se z něj objekty a odesílají se do něj změny zpátky. Použijete <xref:System.Data.Linq.DataContext> stejně, jako byste použili ADO.NET <xref:System.Data.SqlClient.SqlConnection>. Ve skutečnosti <xref:System.Data.Linq.DataContext> se inicializuje s připojením nebo připojovacím řetězcem, který zadáte. Další informace najdete v tématu [metod DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 Účelem <xref:System.Data.Linq.DataContext> je přeložit požadavky na objekty do dotazů SQL, které mají být provedeny v databázi, a následně sestavit objekty z výsledků. Umožňuje implementaci stejného vzoru operátoru jako standardní operátory `Where` dotazu, například a `Select`. <xref:System.Data.Linq.DataContext> [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)]  
  
> [!IMPORTANT]
> Udržování zabezpečeného připojení má nejvyšší důležitost. Další informace najdete v tématu [zabezpečení v LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Data.Linq.DataContext> se používá pro připojení k ukázkové databázi Northwind a k načtení řádků zákazníků, jejichž město je Londýn.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Každá databázová tabulka je reprezentována `Table` způsobem <xref:System.Data.Linq.DataContext.GetTable%2A> , který je k dispozici prostřednictvím metody, pomocí třídy entity k její identifikaci.  
  
## <a name="example"></a>Příklad  
 Osvědčeným postupem je deklarace silného typu <xref:System.Data.Linq.DataContext> namísto spoléhání se na základní <xref:System.Data.Linq.DataContext> třídu a <xref:System.Data.Linq.DataContext.GetTable%2A> metodu. Silně typované <xref:System.Data.Linq.DataContext> deklarace deklaruje všechny `Table` kolekce jako členy kontextu, jak je uvedeno v následujícím příkladu.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Dotaz pro zákazníky z Londýna si pak můžete jednoduše vyjádřit jako:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Komunikace s databází](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
