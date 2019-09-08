---
title: 'Postupy: Připojení k databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: 48ff4af2c881104d5699910e20ef86eea0466d2a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793858"
---
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="72da1-102">Postupy: Připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="72da1-102">How to: Connect to a Database</span></span>
<span data-ttu-id="72da1-103"><xref:System.Data.Linq.DataContext> Je hlavní přenos, ke kterému se připojujete, načítají se z něj objekty a odesílají se do něj změny zpátky.</span><span class="sxs-lookup"><span data-stu-id="72da1-103">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="72da1-104">Použijete <xref:System.Data.Linq.DataContext> stejně, jako byste použili ADO.NET <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="72da1-104">You use the <xref:System.Data.Linq.DataContext> just as you would use an ADO.NET <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="72da1-105">Ve skutečnosti <xref:System.Data.Linq.DataContext> se inicializuje s připojením nebo připojovacím řetězcem, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="72da1-105">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="72da1-106">Další informace najdete v tématu [metod DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="72da1-106">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="72da1-107">Účelem <xref:System.Data.Linq.DataContext> je přeložit požadavky na objekty do dotazů SQL, které mají být provedeny v databázi, a následně sestavit objekty z výsledků.</span><span class="sxs-lookup"><span data-stu-id="72da1-107">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="72da1-108">Umožňuje implementaci stejného vzoru operátoru jako standardní operátory `Where` dotazu, například a `Select`. <xref:System.Data.Linq.DataContext> [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72da1-108">The <xref:System.Data.Linq.DataContext> enables [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="72da1-109">Udržování zabezpečeného připojení má nejvyšší důležitost.</span><span class="sxs-lookup"><span data-stu-id="72da1-109">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="72da1-110">Další informace najdete v tématu [zabezpečení v LINQ to SQL](security-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="72da1-110">For more information, see [Security in LINQ to SQL](security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72da1-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="72da1-111">Example</span></span>  
 <span data-ttu-id="72da1-112">V následujícím příkladu <xref:System.Data.Linq.DataContext> se používá pro připojení k ukázkové databázi Northwind a k načtení řádků zákazníků, jejichž město je Londýn.</span><span class="sxs-lookup"><span data-stu-id="72da1-112">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="72da1-113">Každá databázová tabulka je reprezentována `Table` způsobem <xref:System.Data.Linq.DataContext.GetTable%2A> , který je k dispozici prostřednictvím metody, pomocí třídy entity k její identifikaci.</span><span class="sxs-lookup"><span data-stu-id="72da1-113">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72da1-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="72da1-114">Example</span></span>  
 <span data-ttu-id="72da1-115">Osvědčeným postupem je deklarace silného typu <xref:System.Data.Linq.DataContext> namísto spoléhání se na základní <xref:System.Data.Linq.DataContext> třídu a <xref:System.Data.Linq.DataContext.GetTable%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="72da1-115">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="72da1-116">Silně typované <xref:System.Data.Linq.DataContext> deklarace deklaruje všechny `Table` kolekce jako členy kontextu, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="72da1-116">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="72da1-117">Dotaz pro zákazníky z Londýna si pak můžete jednoduše vyjádřit jako:</span><span class="sxs-lookup"><span data-stu-id="72da1-117">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="72da1-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72da1-118">See also</span></span>

- [<span data-ttu-id="72da1-119">Komunikace s databází</span><span class="sxs-lookup"><span data-stu-id="72da1-119">Communicating with the Database</span></span>](communicating-with-the-database.md)
