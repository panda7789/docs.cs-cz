---
title: "Přidání obchodní logiky pomocí částečné metody"
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
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f9cbaa156fd794a6f9faf44d8d980159f8ae520e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="fbfaf-102">Přidání obchodní logiky pomocí částečné metody</span><span class="sxs-lookup"><span data-stu-id="fbfaf-102">Adding Business Logic By Using Partial Methods</span></span>
<span data-ttu-id="fbfaf-103">Můžete přizpůsobit [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] a C# generovaného kódu v vaše [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektů pomocí *částečné metody*.</span><span class="sxs-lookup"><span data-stu-id="fbfaf-103">You can customize [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="fbfaf-104">Kód který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje definuje podpisy jako jednu součást částečné metoda.</span><span class="sxs-lookup"><span data-stu-id="fbfaf-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="fbfaf-105">Pokud chcete implementovat metodu, můžete přidat vlastní částečné metodu.</span><span class="sxs-lookup"><span data-stu-id="fbfaf-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="fbfaf-106">Pokud je nemůžete přidat vlastní implementace, kompilátor zruší podpis částečné metody a volá metody, výchozí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbfaf-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbfaf-107">Pokud používáte [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Přidání ověření a další přizpůsobení do tříd entit.</span><span class="sxs-lookup"><span data-stu-id="fbfaf-107">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="fbfaf-108">Například výchozí mapování `Customer` třídy v ukázkové databázi Northwind zahrnuje následující částečné metodu:</span><span class="sxs-lookup"><span data-stu-id="fbfaf-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="fbfaf-109">Můžete implementovat vlastní metodu přidáním například následující kód do vlastní partial `Customer` třídy:</span><span class="sxs-lookup"><span data-stu-id="fbfaf-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="fbfaf-110">Tento přístup se obvykle používá v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přepsat výchozí metody pro `Insert`, `Update`, `Delete`a k ověření vlastnosti během události životního cyklu objektu.</span><span class="sxs-lookup"><span data-stu-id="fbfaf-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="fbfaf-111">Další informace najdete v tématu [částečné metody](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) nebo [partial (metoda) (referenční dokumentace jazyka C#)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).</span><span class="sxs-lookup"><span data-stu-id="fbfaf-111">For more information, see [Partial Methods](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) or [partial (Method) (C# Reference)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbfaf-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="fbfaf-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="fbfaf-113">Popis</span><span class="sxs-lookup"><span data-stu-id="fbfaf-113">Description</span></span>  
 <span data-ttu-id="fbfaf-114">Následující příklad ukazuje `ExampleClass` nejprve může být definovaná generování kódu nástroje, jako je SQLMetal a jak může implementovat pouze jedním ze dvou způsobů.</span><span class="sxs-lookup"><span data-stu-id="fbfaf-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fbfaf-115">Kód</span><span class="sxs-lookup"><span data-stu-id="fbfaf-115">Code</span></span>  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="fbfaf-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="fbfaf-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="fbfaf-117">Popis</span><span class="sxs-lookup"><span data-stu-id="fbfaf-117">Description</span></span>  
 <span data-ttu-id="fbfaf-118">Následující příklad používá vztah mezi `Shipper` a `Order` entity.</span><span class="sxs-lookup"><span data-stu-id="fbfaf-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="fbfaf-119">Poznámka: mezi metody částečné metody `InsertShipper` a `DeleteShipper`.</span><span class="sxs-lookup"><span data-stu-id="fbfaf-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="fbfaf-120">Částečné metody výchozí poskytl přepsat tyto metody [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapování.</span><span class="sxs-lookup"><span data-stu-id="fbfaf-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fbfaf-121">Kód</span><span class="sxs-lookup"><span data-stu-id="fbfaf-121">Code</span></span>  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fbfaf-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbfaf-122">See Also</span></span>  
 [<span data-ttu-id="fbfaf-123">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="fbfaf-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="fbfaf-124">Přizpůsobení vložit, aktualizovat a odstraňovat operací</span><span class="sxs-lookup"><span data-stu-id="fbfaf-124">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
