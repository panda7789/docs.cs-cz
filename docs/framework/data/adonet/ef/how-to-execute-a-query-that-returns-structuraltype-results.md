---
title: 'Postupy: Provedení dotazu, který vrátí výsledky typu StructuralType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
ms.openlocfilehash: 7b649abb21b8f6ebbbd8aadc279b2902b3e21e25
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854545"
---
# <a name="how-to-execute-a-query-that-returns-structuraltype-results"></a><span data-ttu-id="4b501-102">Postupy: Provedení dotazu, který vrátí výsledky typu StructuralType</span><span class="sxs-lookup"><span data-stu-id="4b501-102">How to: Execute a Query that Returns StructuralType Results</span></span>
<span data-ttu-id="4b501-103">Toto téma ukazuje, jak spustit příkaz pro koncepční model pomocí <xref:System.Data.EntityClient.EntityCommand> objektu a jak <xref:System.Data.Metadata.Edm.StructuralType> načíst výsledky pomocí <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="4b501-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.StructuralType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="4b501-104">Třídy <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> a<xref:System.Data.Metadata.Edm.ComplexType>jsou odvozeny z třídy.<xref:System.Data.Metadata.Edm.StructuralType></span><span class="sxs-lookup"><span data-stu-id="4b501-104">The <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> and <xref:System.Data.Metadata.Edm.ComplexType> classes derive from the <xref:System.Data.Metadata.Edm.StructuralType> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="4b501-105">Spuštění kódu v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="4b501-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="4b501-106">Přidejte do svého projektu [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) a nakonfigurujte projekt tak, aby používal Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="4b501-106">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="4b501-107">Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).</span><span class="sxs-lookup"><span data-stu-id="4b501-107">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="4b501-108">Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="4b501-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="4b501-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b501-109">Example</span></span>  
 <span data-ttu-id="4b501-110">Tento příklad spustí dotaz, který vrátí <xref:System.Data.Metadata.Edm.EntityType> výsledky.</span><span class="sxs-lookup"><span data-stu-id="4b501-110">This example executes a query that returns <xref:System.Data.Metadata.Edm.EntityType> results.</span></span> <span data-ttu-id="4b501-111">Pokud předáte následující dotaz jako argument `ExecuteStructuralTypeQuery` funkci, funkce zobrazí podrobnosti `Products`o:</span><span class="sxs-lookup"><span data-stu-id="4b501-111">If you pass the following query as an argument to the `ExecuteStructuralTypeQuery` function, the function displays details about the `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#selectproduct)]  
  
 <span data-ttu-id="4b501-112">Pokud předáte parametrizovaný dotaz, podobně jako následující, přidejte <xref:System.Data.EntityClient.EntityParameter> objekty <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> do vlastnosti <xref:System.Data.EntityClient.EntityCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="4b501-112">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## <a name="see-also"></a><span data-ttu-id="4b501-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b501-113">See also</span></span>

- [<span data-ttu-id="4b501-114">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4b501-114">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="4b501-115">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4b501-115">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
