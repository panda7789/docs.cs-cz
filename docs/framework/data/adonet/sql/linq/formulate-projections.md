---
title: Formulování projekcí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 0dfd5d951750de2ab918c51dd9f4f2deeb8a6318
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793828"
---
# <a name="formulate-projections"></a><span data-ttu-id="c70d4-102">Formulování projekcí</span><span class="sxs-lookup"><span data-stu-id="c70d4-102">Formulate Projections</span></span>
<span data-ttu-id="c70d4-103">Následující příklady ukazují, jak `select` lze příkaz v C# příkazu `Select` a v Visual Basic zkombinovat s jinými funkcemi a vytvořit tak projekce dotazů.</span><span class="sxs-lookup"><span data-stu-id="c70d4-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c70d4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c70d4-104">Example</span></span>  
 <span data-ttu-id="c70d4-105">Následující příklad používá `Select` klauzuli v klauzuli Visual Basic (`select` klauzule in C#) k vrácení posloupnosti názvů kontaktů pro `Customers`.</span><span class="sxs-lookup"><span data-stu-id="c70d4-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="c70d4-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="c70d4-106">Example</span></span>  
 <span data-ttu-id="c70d4-107">V následujícím příkladu je použita `Select` klauzule v klauzuli Visual Basic`select` (klauzule C#in) a *anonymní typy* pro vrácení posloupnosti jména kontaktů a telefonní čísla pro `Customers`.</span><span class="sxs-lookup"><span data-stu-id="c70d4-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="c70d4-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c70d4-108">Example</span></span>  
 <span data-ttu-id="c70d4-109">V následujícím příkladu je použita `Select` klauzule v klauzuli Visual Basic`select` (klauzule C#in) a *anonymní typy* pro vrácení posloupnosti názvů a telefonních čísel pro zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="c70d4-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="c70d4-110">`Phone` `Name` `HomePhone` Pole a jsoukombinovánadojednohopole()apolejevevýslednésekvencipřejmenováno.`LastName` `FirstName`</span><span class="sxs-lookup"><span data-stu-id="c70d4-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="c70d4-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="c70d4-111">Example</span></span>  
 <span data-ttu-id="c70d4-112">V následujícím příkladu je použita `Select` klauzule v klauzuli Visual Basic`select` (klauzule C#in) a *anonymní typy* pro vrácení sekvence všech `ProductID`s a vypočtené hodnoty s názvem. `HalfPrice`</span><span class="sxs-lookup"><span data-stu-id="c70d4-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="c70d4-113">Tato hodnota je nastavená na `UnitPrice` děleno 2.</span><span class="sxs-lookup"><span data-stu-id="c70d4-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="c70d4-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="c70d4-114">Example</span></span>  
 <span data-ttu-id="c70d4-115">V následujícím příkladu je použita `Select` klauzule v klauzuli Visual Basic`select` (klauzule C#in) a *podmíněný příkaz* pro vrácení posloupnosti názvu produktu a dostupnosti produktu.</span><span class="sxs-lookup"><span data-stu-id="c70d4-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="c70d4-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="c70d4-116">Example</span></span>  
 <span data-ttu-id="c70d4-117">Následující příklad používá klauzuli `Select` Visual Basic (`select` klauzule in C#) a *známý typ* (Name) pro vrácení posloupnosti názvů zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="c70d4-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="c70d4-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="c70d4-118">Example</span></span>  
 <span data-ttu-id="c70d4-119">`Select` Následující příklad používá a `Where` v Visual Basic (`select` a `where` C#) pro vrácení *filtrované posloupnosti* názvů kontaktů pro zákazníky v Londýně.</span><span class="sxs-lookup"><span data-stu-id="c70d4-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="c70d4-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="c70d4-120">Example</span></span>  
 <span data-ttu-id="c70d4-121">V následujícím příkladu je použita `Select` klauzule v Visual Basic (`select` klauzule in C#) a *anonymní typy* pro vrácení *podmnožiny* dat o zákaznících.</span><span class="sxs-lookup"><span data-stu-id="c70d4-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="c70d4-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="c70d4-122">Example</span></span>  
 <span data-ttu-id="c70d4-123">Následující příklad používá vnořené dotazy k vrácení následujících výsledků:</span><span class="sxs-lookup"><span data-stu-id="c70d4-123">The following example uses nested queries to return the following results:</span></span>  
  
- <span data-ttu-id="c70d4-124">Sekvence všech objednávek a jejich odpovídajících `OrderID`s.</span><span class="sxs-lookup"><span data-stu-id="c70d4-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
- <span data-ttu-id="c70d4-125">Dílčí sekvence položek v pořadí, pro které existuje sleva.</span><span class="sxs-lookup"><span data-stu-id="c70d4-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
- <span data-ttu-id="c70d4-126">Objem uložených peněz, pokud nejsou zahrnuté náklady na expedici.</span><span class="sxs-lookup"><span data-stu-id="c70d4-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="c70d4-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c70d4-127">See also</span></span>

- [<span data-ttu-id="c70d4-128">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="c70d4-128">Query Examples</span></span>](query-examples.md)
