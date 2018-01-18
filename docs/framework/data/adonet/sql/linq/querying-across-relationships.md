---
title: "Dotazování napříč relacemi"
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
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f06297f79807a1548a6b5ac77aed45f52c8d03af
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="querying-across-relationships"></a><span data-ttu-id="544af-102">Dotazování napříč relacemi</span><span class="sxs-lookup"><span data-stu-id="544af-102">Querying Across Relationships</span></span>
<span data-ttu-id="544af-103">Odkazy na jiné objekty nebo kolekce jiných objektů ve vaší definice tříd přímo odpovídají relace cizího klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="544af-103">References to other objects or collections of other objects in your class definitions directly correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="544af-104">Tyto relace můžete použít při dotazování podle pomocí zápisu s tečkou přístup k vlastnosti vztahu a přejít z jednoho objektu na jiný.</span><span class="sxs-lookup"><span data-stu-id="544af-104">You can use these relationships when you query by using dot notation to access the relationship properties and navigate from one object to another.</span></span> <span data-ttu-id="544af-105">Tyto operace přístupu převede složitější spojení nebo korelační poddotazy v ekvivalentní SQL.</span><span class="sxs-lookup"><span data-stu-id="544af-105">These access operations translate to more complex joins or correlated subqueries in the equivalent SQL.</span></span>  
  
 <span data-ttu-id="544af-106">Například následující dotaz přejde z objednávek zákazníků jako způsob, jak omezit výsledky pouze příkazy pro zákazníky, které jsou umístěny v Londýně.</span><span class="sxs-lookup"><span data-stu-id="544af-106">For example, the following query navigates from orders to customers as a way to restrict the results to only those orders for customers located in London.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 <span data-ttu-id="544af-107">Vlastnosti vztahu neexistovala bude potřeba je napsat ručně jako *spojení*, stejně, jako byste to udělali v dotazu SQL, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="544af-107">If relationship properties did not exist you would have to write them manually as *joins*, just as you would do in a SQL query, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 <span data-ttu-id="544af-108">Můžete použít *vztah* vlastnost k definování této konkrétní relace jednou.</span><span class="sxs-lookup"><span data-stu-id="544af-108">You can use the *relationship* property to define this particular relationship one time.</span></span> <span data-ttu-id="544af-109">Potom můžete pohodlnější tečkové syntaxe.</span><span class="sxs-lookup"><span data-stu-id="544af-109">You can then use the more convenient dot syntax.</span></span> <span data-ttu-id="544af-110">Ale vlastnosti vztahu existovat je důležité, protože specifické pro doménu objektové modely jsou obvykle definovány jako hierarchie nebo grafy.</span><span class="sxs-lookup"><span data-stu-id="544af-110">But relationship properties exist more importantly because domain-specific object models are typically defined as hierarchies or graphs.</span></span> <span data-ttu-id="544af-111">Objekty, které plánujete mít odkazy na jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="544af-111">The objects that you program against have references to other objects.</span></span> <span data-ttu-id="544af-112">Je pouze radostí shoda, která odpovídají objekt objektu relace cizího klíče ve vztahy v databázích.</span><span class="sxs-lookup"><span data-stu-id="544af-112">It is only a happy coincidence that object-to-object relationships correspond to foreign-key-styled relationships in databases.</span></span> <span data-ttu-id="544af-113">Přístup k vlastnosti pak představuje pohodlný způsob pro zápis spojení.</span><span class="sxs-lookup"><span data-stu-id="544af-113">Property access then provides a convenient way to write joins.</span></span>  
  
 <span data-ttu-id="544af-114">S ohledem na to jsou důležitější na straně výsledků dotazu než jako součást dotazu, samotné vlastnosti vztahu.</span><span class="sxs-lookup"><span data-stu-id="544af-114">With regard to this, relationship properties are more important on the results side of a query than as part of the query itself.</span></span> <span data-ttu-id="544af-115">Po dotazu byla načtena data o konkrétního zákazníka, definice třídy znamená, že zákazníci mají objednávky.</span><span class="sxs-lookup"><span data-stu-id="544af-115">After the query has retrieved data about a particular customer, the class definition indicates that customers have orders.</span></span> <span data-ttu-id="544af-116">Jinými slovy, byste měli `Orders` vlastnost konkrétního zákazníka jako kolekce, která se zobrazí v všechny objednávky z tohoto zákazníka.</span><span class="sxs-lookup"><span data-stu-id="544af-116">In other words, you expect the `Orders` property of a particular customer to be a collection that is populated with all the orders from that customer.</span></span> <span data-ttu-id="544af-117">To je ve skutečnosti smlouvu, kterou deklarovaná definice tříd tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="544af-117">That is in fact the contract you declared by defining the classes in this manner.</span></span> <span data-ttu-id="544af-118">Byste měli vidět objednávky existuje i v případě, že dotaz nepožádali objednávky.</span><span class="sxs-lookup"><span data-stu-id="544af-118">You expect to see the orders there even if the query did not request orders.</span></span> <span data-ttu-id="544af-119">Očekáváte objekt modelu k udržování dojem, že je v paměti rozšíření databáze s souvisejících objektů, které okamžitě k dispozici.</span><span class="sxs-lookup"><span data-stu-id="544af-119">You expect your object model to maintain an illusion that it is an in-memory extension of the database with related objects immediately available.</span></span>  
  
 <span data-ttu-id="544af-120">Teď, když máte relace, můžete psát dotazy tím, že odkazuje na relaci vlastnosti definované v tříd.</span><span class="sxs-lookup"><span data-stu-id="544af-120">Now that you have relationships, you can write queries by referring to the relationship properties defined in your classes.</span></span> <span data-ttu-id="544af-121">Tyto odkazy vztah odpovídají relace cizího klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="544af-121">These relationship references correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="544af-122">Operace, které používají tyto vztahy se převede do složitější spojení v ekvivalentní SQL.</span><span class="sxs-lookup"><span data-stu-id="544af-122">Operations that use these relationships translate to more complex joins in the equivalent SQL.</span></span> <span data-ttu-id="544af-123">Tak dlouho, dokud jste definovali vztahu (pomocí <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut), nemusíte kód explicitní spojení v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="544af-123">As long as you have defined a relationship (using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute), you do not have to code an explicit join in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="544af-124">Které pomáhají udržovat tento iluzi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje techniku zvanou *odložené načítání*.</span><span class="sxs-lookup"><span data-stu-id="544af-124">To help maintain this illusion, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implements a technique called *deferred loading*.</span></span> <span data-ttu-id="544af-125">Další informace najdete v tématu [odložení versus okamžitou načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="544af-125">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
 <span data-ttu-id="544af-126">Vezměte v úvahu následující dotaz SQL, do projektu seznam `CustomerID` - `OrderID` páry:</span><span class="sxs-lookup"><span data-stu-id="544af-126">Consider the following SQL query to project a list of `CustomerID`-`OrderID` pairs:</span></span>  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 <span data-ttu-id="544af-127">Získat stejné výsledky pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], můžete použít `Orders` vlastnost odkazovat, již existuje v `Customer` třídy.</span><span class="sxs-lookup"><span data-stu-id="544af-127">To obtain the same results by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the `Orders` property reference already existing in the `Customer` class.</span></span> <span data-ttu-id="544af-128">`Orders` Odkaz poskytuje informace potřebné k provedení dotazu a projekt `CustomerID` - `OrderID` páry, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="544af-128">The `Orders` reference provides the necessary information to execute the query and project the `CustomerID`-`OrderID` pairs, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 <span data-ttu-id="544af-129">Můžete také provést naopak.</span><span class="sxs-lookup"><span data-stu-id="544af-129">You can also do the reverse.</span></span> <span data-ttu-id="544af-130">To znamená, že se můžete dotazovat `Orders` a použít jeho `Customer` vztah odkaz na přístup k informacím o přidruženého `Customer` objektu.</span><span class="sxs-lookup"><span data-stu-id="544af-130">That is, you can query `Orders` and use its `Customer` relationship reference to access information about the associated `Customer` object.</span></span> <span data-ttu-id="544af-131">Následující kód projekty stejné `CustomerID` - `OrderID` páry jako předtím, ale tentokrát dotazováním `Orders` místo `Customers`.</span><span class="sxs-lookup"><span data-stu-id="544af-131">The following code projects the same `CustomerID`-`OrderID` pairs as before, but this time by querying `Orders` instead of `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="544af-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="544af-132">See Also</span></span>  
 [<span data-ttu-id="544af-133">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="544af-133">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
