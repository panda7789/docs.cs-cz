---
title: 'Postupy: Provést parametrizovaného dotazu Entity SQL pomocí EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: e605166fa11fbf6424657e1fefa0a5087a11049c
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825651"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="639f7-102">Postupy: Provést parametrizovaného dotazu Entity SQL pomocí EntityCommand</span><span class="sxs-lookup"><span data-stu-id="639f7-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="639f7-103">Toto téma ukazuje, jak spustit [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazu, který obsahuje parametry s využitím <xref:System.Data.EntityClient.EntityCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="639f7-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="639f7-104">Chcete-li spustit kód v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="639f7-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="639f7-105">Přidat [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do vašeho projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="639f7-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="639f7-106">Další informace najdete v tématu [jak: Použijte Průvodce datovým modelem Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="639f7-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="639f7-107">V kódové stránce pro vaši aplikaci, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="639f7-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="639f7-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="639f7-108">Example</span></span>  
 <span data-ttu-id="639f7-109">Následující příklad ukazuje, jak vytvořit řetězec dotazu se dvěma parametry.</span><span class="sxs-lookup"><span data-stu-id="639f7-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="639f7-110">Potom vytvoří <xref:System.Data.EntityClient.EntityCommand>, přidá dva parametry do <xref:System.Data.EntityClient.EntityParameter> kolekce, která <xref:System.Data.EntityClient.EntityCommand>a Iteruje přes kolekci `Contact` položky.</span><span class="sxs-lookup"><span data-stu-id="639f7-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="639f7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="639f7-111">See also</span></span>
- <span data-ttu-id="639f7-112">[Postupy: Spuštění parametrizovaného dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="639f7-112">[How to: Execute a Parameterized Query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>
- [<span data-ttu-id="639f7-113">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="639f7-113">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
