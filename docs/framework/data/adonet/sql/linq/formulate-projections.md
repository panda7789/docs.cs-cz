---
title: Formulovali projekce
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
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 67c196b5c693e36e45d4cad4fa75e08145dd699d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="formulate-projections"></a><span data-ttu-id="ce35f-102">Formulovali projekce</span><span class="sxs-lookup"><span data-stu-id="ce35f-102">Formulate Projections</span></span>
<span data-ttu-id="ce35f-103">Následující příklady zobrazují jak `select` příkaz v jazyce C# a `Select` příkaz v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] zkombinovat s jinými funkcemi do formuláře dotazu projekce.</span><span class="sxs-lookup"><span data-stu-id="ce35f-103">The following examples show how the `select` statement in C# and `Select` statement in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce35f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce35f-104">Example</span></span>  
 <span data-ttu-id="ce35f-105">Následující příklad používá `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) se vrátíte pořadí kontaktní názvů pro `Customers`.</span><span class="sxs-lookup"><span data-stu-id="ce35f-105">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="ce35f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce35f-106">Example</span></span>  
 <span data-ttu-id="ce35f-107">Následující příklad používá `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) a *anonymní typy* se vrátíte pořadí názvů kontaktní telefonní čísla pro `Customers`.</span><span class="sxs-lookup"><span data-stu-id="ce35f-107">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="ce35f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce35f-108">Example</span></span>  
 <span data-ttu-id="ce35f-109">Následující příklad používá `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) a *anonymní typy* se vrátíte pořadí názvů telefonní čísla pro zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="ce35f-109">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="ce35f-110">`FirstName` a `LastName` pole jsou sloučeny do jednoho pole (`Name`) a `HomePhone` pole je přejmenován na `Phone` v výsledné pořadí.</span><span class="sxs-lookup"><span data-stu-id="ce35f-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="ce35f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce35f-111">Example</span></span>  
 <span data-ttu-id="ce35f-112">Následující příklad používá `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) a *anonymní typy* vrátit pořadí všech `ProductID`s a počítanou hodnotu s názvem `HalfPrice`.</span><span class="sxs-lookup"><span data-stu-id="ce35f-112">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="ce35f-113">Tato hodnota nastavena na `UnitPrice` dělený 2.</span><span class="sxs-lookup"><span data-stu-id="ce35f-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="ce35f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce35f-114">Example</span></span>  
 <span data-ttu-id="ce35f-115">Následující příklad používá `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) a *podmíněného příkaz* vrátit pořadí název produktu a dostupnosti produktu.</span><span class="sxs-lookup"><span data-stu-id="ce35f-115">The following example uses the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="ce35f-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce35f-116">Example</span></span>  
 <span data-ttu-id="ce35f-117">Následující příklad používá [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select` – klauzule (`select` klauzule v jazyce C#) a *známý typ* (název) vrátit posloupnost jména zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="ce35f-117">The following example uses a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="ce35f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce35f-118">Example</span></span>  
 <span data-ttu-id="ce35f-119">Následující příklad používá `Select` a `Where` v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` a `where` v jazyce C#) se vrátíte *filtrované pořadí* kontaktní názvů zákazníků v Londýně.</span><span class="sxs-lookup"><span data-stu-id="ce35f-119">The following example uses `Select` and `Where` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="ce35f-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce35f-120">Example</span></span>  
 <span data-ttu-id="ce35f-121">Následující příklad používá `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) a *anonymní typy* vrátit *ve tvaru podmnožina* dat o zákaznících.</span><span class="sxs-lookup"><span data-stu-id="ce35f-121">The following example uses a `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="ce35f-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce35f-122">Example</span></span>  
 <span data-ttu-id="ce35f-123">Následující příklad používá vnořené dotazy vrátit následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="ce35f-123">The following example uses nested queries to return the following results:</span></span>  
  
-   <span data-ttu-id="ce35f-124">Pořadí všechny objednávek a jejich odpovídajících `OrderID`s.</span><span class="sxs-lookup"><span data-stu-id="ce35f-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
-   <span data-ttu-id="ce35f-125">Dalším položek v pořadí, pro kterou je slevu.</span><span class="sxs-lookup"><span data-stu-id="ce35f-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
-   <span data-ttu-id="ce35f-126">Množství peníze uloženy v případě, že náklady na přesouvání není zahrnutý.</span><span class="sxs-lookup"><span data-stu-id="ce35f-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="ce35f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce35f-127">See Also</span></span>  
 [<span data-ttu-id="ce35f-128">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="ce35f-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
