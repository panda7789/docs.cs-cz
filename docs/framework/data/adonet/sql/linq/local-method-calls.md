---
title: Volání místních metod
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: ec288d5ac2f6466860362be82c619c89204e8f31
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781416"
---
# <a name="local-method-calls"></a><span data-ttu-id="23a6d-102">Volání místních metod</span><span class="sxs-lookup"><span data-stu-id="23a6d-102">Local Method Calls</span></span>
<span data-ttu-id="23a6d-103">Volání místní metody je jeden, který je spuštěn v rámci objektového modelu.</span><span class="sxs-lookup"><span data-stu-id="23a6d-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="23a6d-104">Vzdálené volání metody je jeden, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se překládá na SQL a odesílá databázovému stroji ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="23a6d-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="23a6d-105">Volání místní metody jsou nutná, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Pokud nelze přeložit volání do jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="23a6d-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="23a6d-106">V opačném případě je vyvolána výjimka. <xref:System.InvalidOperationException></span><span class="sxs-lookup"><span data-stu-id="23a6d-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="23a6d-107">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="23a6d-107">Example 1</span></span>  
 <span data-ttu-id="23a6d-108">V následujícím příkladu `Order` je třída namapována na tabulku Orders v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="23a6d-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="23a6d-109">Do třídy byla přidána metoda místní instance.</span><span class="sxs-lookup"><span data-stu-id="23a6d-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="23a6d-110">V dotazu 1 je konstruktor `Order` třídy spouštěn místně.</span><span class="sxs-lookup"><span data-stu-id="23a6d-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="23a6d-111">Pokud [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se při pokusu o překlad do `LocalInstanceMethod()`kódu SQL pokusil <xref:System.InvalidOperationException> o převod na SQL, pokus selže a vyvolá se výjimka.</span><span class="sxs-lookup"><span data-stu-id="23a6d-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="23a6d-112">Ale vzhledem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] k tomu, že poskytuje podporu pro volání místních metod, query2 nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="23a6d-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="23a6d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23a6d-113">See also</span></span>

- [<span data-ttu-id="23a6d-114">Základní informace</span><span class="sxs-lookup"><span data-stu-id="23a6d-114">Background Information</span></span>](background-information.md)
