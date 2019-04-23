---
title: Přidání obchodní logiky pomocí částečných metod
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: ea7dbc4f760a446440cb7291413d69b1202f80e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162656"
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="53661-102">Přidání obchodní logiky pomocí částečných metod</span><span class="sxs-lookup"><span data-stu-id="53661-102">Adding Business Logic By Using Partial Methods</span></span>
<span data-ttu-id="53661-103">Můžete přizpůsobit jazyka Visual Basic a C# generovaného kódu v vaše [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektů s použitím *částečné metody*.</span><span class="sxs-lookup"><span data-stu-id="53661-103">You can customize Visual Basic and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="53661-104">Kód, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vygeneruje podpisy definuje částečné metody v rámci jedné.</span><span class="sxs-lookup"><span data-stu-id="53661-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="53661-105">Pokud chcete implementovat metodu, můžete přidat vlastní částečnou metodu.</span><span class="sxs-lookup"><span data-stu-id="53661-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="53661-106">Pokud nemůžete přidat vlastní implementaci, kompilátor zahodí podpis částečné metody a volání výchozí metody [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="53661-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53661-107">Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] přidat ověřování a další vlastní nastavení do tříd entit.</span><span class="sxs-lookup"><span data-stu-id="53661-107">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="53661-108">Například výchozí mapování `Customer` třída v ukázkové databázi Northwind zahrnuje následující částečné metody:</span><span class="sxs-lookup"><span data-stu-id="53661-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="53661-109">Můžete implementovat vlastní metodu tak, že přidáte následující kód k vlastním částečné `Customer` třídy:</span><span class="sxs-lookup"><span data-stu-id="53661-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="53661-110">Tento přístup se obvykle používá v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přepsat výchozí metody pro `Insert`, `Update`, `Delete`a pro vlastnosti ověření během události životního cyklu objektu.</span><span class="sxs-lookup"><span data-stu-id="53661-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="53661-111">Další informace najdete v tématu [částečné metody](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) nebo [partial (metoda) (C# odkaz)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).</span><span class="sxs-lookup"><span data-stu-id="53661-111">For more information, see [Partial Methods](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) or [partial (Method) (C# Reference)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="53661-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="53661-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="53661-113">Popis</span><span class="sxs-lookup"><span data-stu-id="53661-113">Description</span></span>  
 <span data-ttu-id="53661-114">Následující příklad ukazuje `ExampleClass` nejprve může být definovaná generování kódu nástroje, jako je SQLMetal a jak může implementovat jenom jedním ze dvou způsobů.</span><span class="sxs-lookup"><span data-stu-id="53661-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="53661-115">Kód</span><span class="sxs-lookup"><span data-stu-id="53661-115">Code</span></span>  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="53661-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="53661-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="53661-117">Popis</span><span class="sxs-lookup"><span data-stu-id="53661-117">Description</span></span>  
 <span data-ttu-id="53661-118">Následující příklad používá vztah mezi `Shipper` a `Order` entity.</span><span class="sxs-lookup"><span data-stu-id="53661-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="53661-119">Mějte na paměti mezi metody částečné metody `InsertShipper` a `DeleteShipper`.</span><span class="sxs-lookup"><span data-stu-id="53661-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="53661-120">Tyto metody přepsat výchozí částečné metody poskytnuté [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapování.</span><span class="sxs-lookup"><span data-stu-id="53661-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="53661-121">Kód</span><span class="sxs-lookup"><span data-stu-id="53661-121">Code</span></span>  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="53661-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53661-122">See also</span></span>

- [<span data-ttu-id="53661-123">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="53661-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="53661-124">Přizpůsobení operací vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="53661-124">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
