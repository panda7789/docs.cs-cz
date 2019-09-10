---
title: 'Postupy: Spuštění parametrizovaného dotazu Entity SQL pomocí EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: aa750ef088ee045c8d1045b2509d8fc4bde014ce
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854624"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="c6183-102">Postupy: Spuštění parametrizovaného dotazu Entity SQL pomocí EntityCommand</span><span class="sxs-lookup"><span data-stu-id="c6183-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="c6183-103">Toto téma ukazuje, jak spustit [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz, který má parametry <xref:System.Data.EntityClient.EntityCommand> pomocí objektu.</span><span class="sxs-lookup"><span data-stu-id="c6183-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="c6183-104">Spuštění kódu v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="c6183-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="c6183-105">Přidejte do svého projektu [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) a nakonfigurujte projekt tak, aby používal Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c6183-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="c6183-106">Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).</span><span class="sxs-lookup"><span data-stu-id="c6183-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="c6183-107">Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="c6183-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="c6183-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6183-108">Example</span></span>  
 <span data-ttu-id="c6183-109">Následující příklad ukazuje, jak vytvořit řetězec dotazu se dvěma parametry.</span><span class="sxs-lookup"><span data-stu-id="c6183-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="c6183-110">Potom vytvoří <xref:System.Data.EntityClient.EntityCommand>, přidá dva parametry <xref:System.Data.EntityClient.EntityParameter> do kolekce <xref:System.Data.EntityClient.EntityCommand>a provede iteraci kolekce `Contact` položek.</span><span class="sxs-lookup"><span data-stu-id="c6183-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="c6183-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6183-111">See also</span></span>

- <span data-ttu-id="c6183-112">[Postupy: Provedení parametrizovaného dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c6183-112">[How to: Execute a Parameterized Query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>
- [<span data-ttu-id="c6183-113">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c6183-113">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
