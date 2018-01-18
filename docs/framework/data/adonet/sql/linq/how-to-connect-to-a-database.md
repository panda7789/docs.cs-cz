---
title: "Postupy: připojení k databázi"
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
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a5447ce64803405668a2d486c7b3071b5ff923cb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-connect-to-a-database"></a>Postupy: připojení k databázi
<xref:System.Data.Linq.DataContext> Je hlavní přenos, podle kterého připojení k databázi, načtení objektů z něj a odeslání změn zpět do ní. Můžete použít <xref:System.Data.Linq.DataContext> stejně, jako byste použili [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>. Ve skutečnosti <xref:System.Data.Linq.DataContext> je inicializován s připojením nebo připojovací řetězec, který zadáte. Další informace najdete v tématu [DataContext metody (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
 Účelem <xref:System.Data.Linq.DataContext> je převod své žádosti pro objekty do dotazů SQL, které musí být v databázi a potom ke kompilaci objekty mimo výsledky. <xref:System.Data.Linq.DataContext> Umožňuje [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] implementací stejného vzoru operátor jako standardní operátory dotazu `Where` a `Select`.  
  
> [!IMPORTANT]
>  Zachování zabezpečené připojení je nejvyšší důležité. Další informace najdete v tématu [zabezpečení v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Data.Linq.DataContext> se používá pro připojení k ukázková databáze Northwind a načtení řádků zákazníků, jejichž města je Londýně.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 Každá tabulka databáze je reprezentována jako `Table` kolekce, které jsou k dispozici prostřednictvím <xref:System.Data.Linq.DataContext.GetTable%2A> metoda pomocí třídy entita pro identifikaci.  
  
## <a name="example"></a>Příklad  
 Osvědčeným postupem je deklarovat silného typu <xref:System.Data.Linq.DataContext> aniž byste museli spoléhat na základní <xref:System.Data.Linq.DataContext> třídy a <xref:System.Data.Linq.DataContext.GetTable%2A> metoda. Silného typu <xref:System.Data.Linq.DataContext> deklaruje všechny `Table` kolekce jako členy kontextu, jako v následujícím příkladu.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 Dotaz můžete pak express pro zákazníky z Londýna jednodušeji jako:  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 [Komunikace s databází](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
