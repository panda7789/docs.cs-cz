---
title: 'Postupy: Spuštění polymorfního dotazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 49e0a6b44af0729959fabf6278cc6d8ecf37a16b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251514"
---
# <a name="how-to-execute-a-polymorphic-query"></a><span data-ttu-id="25f9a-102">Postupy: Spuštění polymorfního dotazu</span><span class="sxs-lookup"><span data-stu-id="25f9a-102">How to: Execute a Polymorphic Query</span></span>

<span data-ttu-id="25f9a-103">Toto téma ukazuje, jak spustit polymorfní [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz pomocí operátoru [OfType](./language-reference/oftype-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="25f9a-103">This topic shows how to execute a polymorphic [!INCLUDE[esql](../../../../../includes/esql-md.md)] query using the [OFTYPE](./language-reference/oftype-entity-sql.md) operator.</span></span>

### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="25f9a-104">Spuštění kódu v tomto příkladu</span><span class="sxs-lookup"><span data-stu-id="25f9a-104">To run the code in this example</span></span>

1. <span data-ttu-id="25f9a-105">Přidejte do svého projektu [školní model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) a nakonfigurujte projekt tak, aby používal Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="25f9a-105">Add the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="25f9a-106">Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).</span><span class="sxs-lookup"><span data-stu-id="25f9a-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

2. <span data-ttu-id="25f9a-107">Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="25f9a-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. <span data-ttu-id="25f9a-108">Upravte koncepční model tak, aby měl dědičnost tabulky na hierarchii, podle kroků v [návodu: Mapování dědičnosti – tabulka na hierarchii](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="25f9a-108">Modify the conceptual model to have a table-per-hierarchy inheritance by following the steps in [Walkthrough: Mapping Inheritance - Table-per-Hierarchy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="25f9a-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="25f9a-109">Example</span></span>

<span data-ttu-id="25f9a-110">Následující příklad používá operátor OfType k získání a zobrazení kolekce pouze `OnsiteCourses` z `Courses`kolekce.</span><span class="sxs-lookup"><span data-stu-id="25f9a-110">The following example uses an OFTYPE operator to get and display a collection of only `OnsiteCourses` from a collection of `Courses`.</span></span>

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a><span data-ttu-id="25f9a-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25f9a-111">See also</span></span>

- [<span data-ttu-id="25f9a-112">Zprostředkovatel EntityClient pro Entity Framework</span><span class="sxs-lookup"><span data-stu-id="25f9a-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="25f9a-113">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="25f9a-113">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
