---
title: 'Postupy: připojení k databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: 924fe4fadd5dae9907fca61a556506db1e583669
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362074"
---
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="aff35-102">Postupy: připojení k databázi</span><span class="sxs-lookup"><span data-stu-id="aff35-102">How to: Connect to a Database</span></span>
<span data-ttu-id="aff35-103"><xref:System.Data.Linq.DataContext> Je hlavní přenos, podle kterého připojení k databázi, načtení objektů z něj a odeslání změn zpět do ní.</span><span class="sxs-lookup"><span data-stu-id="aff35-103">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="aff35-104">Můžete použít <xref:System.Data.Linq.DataContext> stejně, jako byste použili [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="aff35-104">You use the <xref:System.Data.Linq.DataContext> just as you would use an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="aff35-105">Ve skutečnosti <xref:System.Data.Linq.DataContext> je inicializován s připojením nebo připojovací řetězec, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="aff35-105">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="aff35-106">Další informace najdete v tématu [DataContext metody (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="aff35-106">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="aff35-107">Účelem <xref:System.Data.Linq.DataContext> je převod své žádosti pro objekty do dotazů SQL, které musí být v databázi a potom ke kompilaci objekty mimo výsledky.</span><span class="sxs-lookup"><span data-stu-id="aff35-107">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="aff35-108"><xref:System.Data.Linq.DataContext> Umožňuje [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] implementací stejného vzoru operátor jako standardní operátory dotazu `Where` a `Select`.</span><span class="sxs-lookup"><span data-stu-id="aff35-108">The <xref:System.Data.Linq.DataContext> enables [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aff35-109">Zachování zabezpečené připojení je nejvyšší důležité.</span><span class="sxs-lookup"><span data-stu-id="aff35-109">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="aff35-110">Další informace najdete v tématu [zabezpečení v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="aff35-110">For more information, see [Security in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aff35-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="aff35-111">Example</span></span>  
 <span data-ttu-id="aff35-112">V následujícím příkladu <xref:System.Data.Linq.DataContext> se používá pro připojení k ukázková databáze Northwind a načtení řádků zákazníků, jejichž města je Londýně.</span><span class="sxs-lookup"><span data-stu-id="aff35-112">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="aff35-113">Každá tabulka databáze je reprezentována jako `Table` kolekce, které jsou k dispozici prostřednictvím <xref:System.Data.Linq.DataContext.GetTable%2A> metoda pomocí třídy entita pro identifikaci.</span><span class="sxs-lookup"><span data-stu-id="aff35-113">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aff35-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="aff35-114">Example</span></span>  
 <span data-ttu-id="aff35-115">Osvědčeným postupem je deklarovat silného typu <xref:System.Data.Linq.DataContext> aniž byste museli spoléhat na základní <xref:System.Data.Linq.DataContext> třídy a <xref:System.Data.Linq.DataContext.GetTable%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="aff35-115">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="aff35-116">Silného typu <xref:System.Data.Linq.DataContext> deklaruje všechny `Table` kolekce jako členy kontextu, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="aff35-116">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="aff35-117">Dotaz můžete pak express pro zákazníky z Londýna jednodušeji jako:</span><span class="sxs-lookup"><span data-stu-id="aff35-117">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="aff35-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="aff35-118">See Also</span></span>  
 [<span data-ttu-id="aff35-119">Komunikace s databází</span><span class="sxs-lookup"><span data-stu-id="aff35-119">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
