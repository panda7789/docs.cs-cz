---
title: 'Postupy: Připojení k databázi'
description: Naučte se používat DataContext pro připojení k databázi v LINQ to SQL. Pokud chcete pro připojení k databázi a získání řádků použít DataContext, přečtěte si tyto příklady.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: c3320a598cb8407ab584530c615c2e5ef0de53c8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286401"
---
# <a name="how-to-connect-to-a-database"></a>Postupy: Připojení k databázi
<xref:System.Data.Linq.DataContext>Je hlavní přenos, ke kterému se připojujete, načítají se z něj objekty a odesílají se do něj změny zpátky. Použijete <xref:System.Data.Linq.DataContext> stejně, jako byste použili ADO.NET <xref:System.Data.SqlClient.SqlConnection> . Ve skutečnosti se <xref:System.Data.Linq.DataContext> inicializuje s připojením nebo připojovacím řetězcem, který zadáte. Další informace naleznete v tématu [metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 Účelem <xref:System.Data.Linq.DataContext> je přeložit požadavky na objekty do dotazů SQL, které mají být provedeny v databázi, a následně sestavit objekty z výsledků. <xref:System.Data.Linq.DataContext>Umožňuje LINQ (Language-Integrated Query) implementací stejného vzoru operátoru jako standardní operátory dotazu, jako jsou `Where` a `Select` .  
  
> [!IMPORTANT]
> Udržování zabezpečeného připojení má nejvyšší důležitost. Další informace najdete v tématu [zabezpečení v LINQ to SQL](security-in-linq-to-sql.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Data.Linq.DataContext> se používá pro připojení k ukázkové databázi Northwind a k načtení řádků zákazníků, jejichž město je Londýn.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Každá databázová tabulka je reprezentována `Table` způsobem, který je k dispozici prostřednictvím <xref:System.Data.Linq.DataContext.GetTable%2A> metody, pomocí třídy entity k její identifikaci.  
  
## <a name="example"></a>Příklad  
 Osvědčeným postupem je deklarace silného typu <xref:System.Data.Linq.DataContext> namísto spoléhání se na základní <xref:System.Data.Linq.DataContext> třídu a <xref:System.Data.Linq.DataContext.GetTable%2A> metodu. Silně typované <xref:System.Data.Linq.DataContext> deklarace deklaruje všechny `Table` kolekce jako členy kontextu, jak je uvedeno v následujícím příkladu.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Dotaz pro zákazníky z Londýna si pak můžete jednoduše vyjádřit jako:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také

- [Komunikace s databází](communicating-with-the-database.md)
