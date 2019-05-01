---
title: 'Postupy: Připojení k databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: f04726bc12fdfbca530ee5533d5b8969addf962e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037840"
---
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="d2492-102">Postupy: Připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="d2492-102">How to: Connect to a Database</span></span>
<span data-ttu-id="d2492-103"><xref:System.Data.Linq.DataContext> Je hlavní přenos, podle kterého připojení k databázi, načtení objektů z něj a odeslat změny zpět do něj.</span><span class="sxs-lookup"><span data-stu-id="d2492-103">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="d2492-104">Můžete použít <xref:System.Data.Linq.DataContext> stejně jako byste použili [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="d2492-104">You use the <xref:System.Data.Linq.DataContext> just as you would use an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="d2492-105">Ve skutečnosti <xref:System.Data.Linq.DataContext> je inicializována s připojení nebo připojovací řetězec, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="d2492-105">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="d2492-106">Další informace najdete v tématu [metod DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="d2492-106">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="d2492-107">Účelem <xref:System.Data.Linq.DataContext> je převod žádostí pro objekty na dotazy SQL má být provedeno proti databázi a potom sestavit objektů mimo výsledky.</span><span class="sxs-lookup"><span data-stu-id="d2492-107">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="d2492-108"><xref:System.Data.Linq.DataContext> Umožňuje [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] implementací stejný vzor jako standardní operátory dotazu operátor `Where` a `Select`.</span><span class="sxs-lookup"><span data-stu-id="d2492-108">The <xref:System.Data.Linq.DataContext> enables [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d2492-109">Zachování zabezpečené připojení má nejvyšší význam.</span><span class="sxs-lookup"><span data-stu-id="d2492-109">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="d2492-110">Další informace najdete v tématu [zabezpečení v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="d2492-110">For more information, see [Security in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2492-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2492-111">Example</span></span>  
 <span data-ttu-id="d2492-112">V následujícím příkladu <xref:System.Data.Linq.DataContext> slouží k připojení k ukázkové databázi Northwind a k načítání řádků zákazníků, jejichž Město je London.</span><span class="sxs-lookup"><span data-stu-id="d2492-112">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="d2492-113">Každá databázová tabulka je vyjádřena jako `Table` kolekce, které jsou k dispozici prostřednictvím <xref:System.Data.Linq.DataContext.GetTable%2A> metodu, pomocí třídy entity pro jeho rozpoznání.</span><span class="sxs-lookup"><span data-stu-id="d2492-113">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2492-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2492-114">Example</span></span>  
 <span data-ttu-id="d2492-115">Osvědčeným postupem je deklarovat silného typu <xref:System.Data.Linq.DataContext> aniž byste museli spoléhat na základní <xref:System.Data.Linq.DataContext> třídy a <xref:System.Data.Linq.DataContext.GetTable%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="d2492-115">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="d2492-116">Silného typu <xref:System.Data.Linq.DataContext> deklaruje všechny `Table` kolekce jako členy kontextu, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d2492-116">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="d2492-117">Potom můžete vyjádřit dotaz Zákazníci z Londýna jednoduše jako:</span><span class="sxs-lookup"><span data-stu-id="d2492-117">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d2492-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2492-118">See also</span></span>

- [<span data-ttu-id="d2492-119">Komunikace s databází</span><span class="sxs-lookup"><span data-stu-id="d2492-119">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
