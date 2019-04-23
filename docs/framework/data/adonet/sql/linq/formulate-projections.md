---
title: Formulování projekcí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: e1f7a7da1ab2ce0ad7d7908ecd1f896d229b8e1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223300"
---
# <a name="formulate-projections"></a><span data-ttu-id="f5c64-102">Formulování projekcí</span><span class="sxs-lookup"><span data-stu-id="f5c64-102">Formulate Projections</span></span>
<span data-ttu-id="f5c64-103">Následující příklady ukazují jak `select` výroky C# a `Select` v sadě Visual Studio je možné kombinovat s další funkce do formuláře projekce dotazů.</span><span class="sxs-lookup"><span data-stu-id="f5c64-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5c64-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5c64-104">Example</span></span>  
 <span data-ttu-id="f5c64-105">V následujícím příkladu `Select` klauzule v jazyce Visual Basic (`select` klauzule C#) k vrácení sekvence jména kontaktů pro `Customers`.</span><span class="sxs-lookup"><span data-stu-id="f5c64-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="f5c64-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5c64-106">Example</span></span>  
 <span data-ttu-id="f5c64-107">V následujícím příkladu `Select` klauzule v jazyce Visual Basic (`select` klauzule C#) a *anonymní typy* k vrácení sekvence jména kontaktů a telefonní čísla pro `Customers`.</span><span class="sxs-lookup"><span data-stu-id="f5c64-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="f5c64-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5c64-108">Example</span></span>  
 <span data-ttu-id="f5c64-109">V následujícím příkladu `Select` klauzule v jazyce Visual Basic (`select` klauzule C#) a *anonymní typy* k vrácení sekvence jména a telefonní čísla pro zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="f5c64-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="f5c64-110">`FirstName` a `LastName` pole jsou sloučeny do jednoho pole (`Name`) a `HomePhone` pole bylo přejmenováno na `Phone` ve výsledné pořadí.</span><span class="sxs-lookup"><span data-stu-id="f5c64-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="f5c64-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5c64-111">Example</span></span>  
 <span data-ttu-id="f5c64-112">V následujícím příkladu `Select` klauzule v jazyce Visual Basic (`select` klauzule C#) a *anonymní typy* k vrácení sekvence všech `ProductID`s a počítanou hodnotu s názvem `HalfPrice`.</span><span class="sxs-lookup"><span data-stu-id="f5c64-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="f5c64-113">Tato hodnota nastavena `UnitPrice` děleno 2.</span><span class="sxs-lookup"><span data-stu-id="f5c64-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="f5c64-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5c64-114">Example</span></span>  
 <span data-ttu-id="f5c64-115">V následujícím příkladu `Select` klauzule v jazyce Visual Basic (`select` klauzule C#) a *podmíněný příkaz* k vrácení sekvence název produktu a dostupnost produktů.</span><span class="sxs-lookup"><span data-stu-id="f5c64-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="f5c64-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5c64-116">Example</span></span>  
 <span data-ttu-id="f5c64-117">Následující příklad používá jazyka Visual Basic `Select` – klauzule (`select` klauzule C#) a *známý typ* (název) k vrácení sekvence názvů zaměstnanci.</span><span class="sxs-lookup"><span data-stu-id="f5c64-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="f5c64-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5c64-118">Example</span></span>  
 <span data-ttu-id="f5c64-119">Následující příklad používá `Select` a `Where` v jazyce Visual Basic (`select` a `where` v C#) se vraťte *filtrované pořadí* kontaktní názvů pro zákazníky v Londýně.</span><span class="sxs-lookup"><span data-stu-id="f5c64-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="f5c64-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5c64-120">Example</span></span>  
 <span data-ttu-id="f5c64-121">V následujícím příkladu `Select` klauzule v jazyce Visual Basic (`select` klauzuli v C#) a *anonymní typy* se vraťte *ve tvaru dílčí* data o zákaznících.</span><span class="sxs-lookup"><span data-stu-id="f5c64-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="f5c64-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5c64-122">Example</span></span>  
 <span data-ttu-id="f5c64-123">Následující příklad používá vnořené dotazy vrátit následující výsledky:</span><span class="sxs-lookup"><span data-stu-id="f5c64-123">The following example uses nested queries to return the following results:</span></span>  
  
-   <span data-ttu-id="f5c64-124">Posloupnost všech objednávek a jejich odpovídající `OrderID`s.</span><span class="sxs-lookup"><span data-stu-id="f5c64-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
-   <span data-ttu-id="f5c64-125">Dílčí sekvenci položek v pořadí, pro kterou se slevou.</span><span class="sxs-lookup"><span data-stu-id="f5c64-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
-   <span data-ttu-id="f5c64-126">Množství peníze uloženy v případě, že náklady na přesouvání není zahrnutý.</span><span class="sxs-lookup"><span data-stu-id="f5c64-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="f5c64-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5c64-127">See also</span></span>

- [<span data-ttu-id="f5c64-128">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="f5c64-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
