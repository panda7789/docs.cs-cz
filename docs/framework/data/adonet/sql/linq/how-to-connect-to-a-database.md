---
title: 'Postupy: připojení k databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: 837919b1cfcdf46026ccfb37cbbec951c0ae41b8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634674"
---
# <a name="how-to-connect-to-a-database"></a>Postupy: připojení k databázi
<xref:System.Data.Linq.DataContext> je hlavní přenos, ke kterému se připojujete, načítají se z něj objekty a odesílají se do něj změny zpátky. <xref:System.Data.Linq.DataContext> použijete stejně, jako byste použili <xref:System.Data.SqlClient.SqlConnection>ADO.NET. Ve skutečnosti se <xref:System.Data.Linq.DataContext> inicializuje s připojením nebo připojovacím řetězcem, který zadáte. Další informace najdete v tématu [metod DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 Účelem <xref:System.Data.Linq.DataContext> je přeložit požadavky na objekty do dotazů SQL, které se mají provést v databázi, a potom sestavit objekty mimo výsledky. <xref:System.Data.Linq.DataContext> umožňuje LINQ (Language-Integrated Query) implementací stejného vzoru operátoru jako standardní operátory dotazu, jako je například `Where` a `Select`.  
  
> [!IMPORTANT]
> Udržování zabezpečeného připojení má nejvyšší důležitost. Další informace najdete v tématu [zabezpečení v LINQ to SQL](security-in-linq-to-sql.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Data.Linq.DataContext> slouží k připojení k ukázkové databázi Northwind a k načtení řádků zákazníků, jejichž město je Londýn.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Každá databázová tabulka je reprezentována jako kolekce `Table` k dispozici způsobem <xref:System.Data.Linq.DataContext.GetTable%2A> metodou, a to pomocí třídy entity k její identifikaci.  
  
## <a name="example"></a>Příklad  
 Osvědčeným postupem je deklarovat <xref:System.Data.Linq.DataContext> silného typu namísto spoléhání na základní <xref:System.Data.Linq.DataContext> třídu a metodu <xref:System.Data.Linq.DataContext.GetTable%2A>. Silně typované <xref:System.Data.Linq.DataContext> deklaruje všechny kolekce `Table` jako členy kontextu, jak je uvedeno v následujícím příkladu.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Dotaz pro zákazníky z Londýna si pak můžete jednoduše vyjádřit jako:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Komunikace s databází](communicating-with-the-database.md)
