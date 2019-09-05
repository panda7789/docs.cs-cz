---
title: Přidání obchodní logiky pomocí částečných metod
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: 251d7a05971ff7940f85ec9d555d26f2e57067c3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248126"
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="fe678-102">Přidání obchodní logiky pomocí částečných metod</span><span class="sxs-lookup"><span data-stu-id="fe678-102">Adding Business Logic By Using Partial Methods</span></span>
<span data-ttu-id="fe678-103">Můžete přizpůsobit Visual Basic a C# generovaný kód v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektech pomocí *částečných metod*.</span><span class="sxs-lookup"><span data-stu-id="fe678-103">You can customize Visual Basic and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="fe678-104">Kód, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje, definuje signatury jako jednu část částečné metody.</span><span class="sxs-lookup"><span data-stu-id="fe678-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="fe678-105">Pokud chcete implementovat metodu, můžete přidat vlastní částečnou metodu.</span><span class="sxs-lookup"><span data-stu-id="fe678-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="fe678-106">Pokud nepřidáte vlastní implementaci, kompilátor zruší signaturu částečných metod a zavolá výchozí metody v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fe678-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe678-107">Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů k přidání ověřování a dalších úprav do tříd entit.</span><span class="sxs-lookup"><span data-stu-id="fe678-107">If you are using Visual Studio, you can use the Object Relational Designer to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="fe678-108">Například výchozí mapování pro `Customer` třídu v ukázkové databázi Northwind obsahuje následující částečnou metodu:</span><span class="sxs-lookup"><span data-stu-id="fe678-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="fe678-109">Můžete implementovat vlastní metodu přidáním kódu, jako je například následující, do vlastní částečné `Customer` třídy:</span><span class="sxs-lookup"><span data-stu-id="fe678-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="fe678-110">Tento přístup se obvykle používá v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] k přepsání výchozích metod pro `Insert`, `Update`, `Delete`a pro ověření vlastností během událostí životního cyklu objektu.</span><span class="sxs-lookup"><span data-stu-id="fe678-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="fe678-111">Další informace naleznete v tématu [částečné metody](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) nebo [Partial (metoda) (C# referenční](../../../../../csharp/language-reference/keywords/partial-method.md) dokumentace)C#().</span><span class="sxs-lookup"><span data-stu-id="fe678-111">For more information, see [Partial Methods](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) or [partial (Method) (C# Reference)](../../../../../csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe678-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="fe678-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="fe678-113">Popis</span><span class="sxs-lookup"><span data-stu-id="fe678-113">Description</span></span>  
 <span data-ttu-id="fe678-114">Následující příklad ukazuje `ExampleClass` , že je možné ho definovat pomocí nástroje pro generování kódu, jako je SQLMetal, a potom jak můžete implementovat jenom jednu ze dvou metod.</span><span class="sxs-lookup"><span data-stu-id="fe678-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fe678-115">Kód</span><span class="sxs-lookup"><span data-stu-id="fe678-115">Code</span></span>  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="fe678-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="fe678-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="fe678-117">Popis</span><span class="sxs-lookup"><span data-stu-id="fe678-117">Description</span></span>  
 <span data-ttu-id="fe678-118">V následujícím příkladu je použita relace mezi `Shipper` entitami a `Order` .</span><span class="sxs-lookup"><span data-stu-id="fe678-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="fe678-119">Všimněte si, `InsertShipper` že mezi metodami jsou částečné `DeleteShipper`metody a.</span><span class="sxs-lookup"><span data-stu-id="fe678-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="fe678-120">Tyto metody přepíšou výchozí částečné metody poskytované [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapováním.</span><span class="sxs-lookup"><span data-stu-id="fe678-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fe678-121">Kód</span><span class="sxs-lookup"><span data-stu-id="fe678-121">Code</span></span>  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fe678-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe678-122">See also</span></span>

- [<span data-ttu-id="fe678-123">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="fe678-123">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="fe678-124">Přizpůsobení operací vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="fe678-124">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
