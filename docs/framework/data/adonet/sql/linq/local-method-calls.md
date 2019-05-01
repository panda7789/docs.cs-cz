---
title: Volání místních metod
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: c8a4c29b1faa3c05f2cf32e9a60104b43a9b1c40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033511"
---
# <a name="local-method-calls"></a><span data-ttu-id="d017f-102">Volání místních metod</span><span class="sxs-lookup"><span data-stu-id="d017f-102">Local Method Calls</span></span>
<span data-ttu-id="d017f-103">Volání místních metod je ten, který se spouští v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="d017f-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="d017f-104">Volání vzdálené metody je jeden, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se přeloží na SQL a odesílá do databázového stroje pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="d017f-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="d017f-105">Volání místních metod jsou potřeba při [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nemůže překládat volání do SQL.</span><span class="sxs-lookup"><span data-stu-id="d017f-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="d017f-106">V opačném případě <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d017f-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="d017f-107">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="d017f-107">Example 1</span></span>  
 <span data-ttu-id="d017f-108">V následujícím příkladu `Order` třídy je namapována na tabulce objednávky v ukázkové databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="d017f-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="d017f-109">Metoda místní instance byla přidána do třídy.</span><span class="sxs-lookup"><span data-stu-id="d017f-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="d017f-110">V konstruktoru pro dotaz 1 `Order` třídy je spuštěn lokálně.</span><span class="sxs-lookup"><span data-stu-id="d017f-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="d017f-111">V dotazu 2, pokud [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokusila přeložit `LocalInstanceMethod()`do databáze SQL, je tento pokus selže a <xref:System.InvalidOperationException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d017f-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="d017f-112">Ale protože [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje podporu pro volání místních metod, nebude dotaz2 vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="d017f-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d017f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d017f-113">See also</span></span>

- [<span data-ttu-id="d017f-114">Základní informace</span><span class="sxs-lookup"><span data-stu-id="d017f-114">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
