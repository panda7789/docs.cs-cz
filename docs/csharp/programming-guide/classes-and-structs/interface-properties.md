---
title: "Vlastnosti rozhraní (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1da48adf73cccb28d9cff641948db52b40b8c1bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="2d870-102">Vlastnosti rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="2d870-102">Interface Properties (C# Programming Guide)</span></span>
<span data-ttu-id="2d870-103">Vlastnosti lze deklarovat na [rozhraní](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="2d870-103">Properties can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="2d870-104">Následuje příklad přistupující objekt indexer rozhraní:</span><span class="sxs-lookup"><span data-stu-id="2d870-104">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 <span data-ttu-id="2d870-105">Přistupující objekt vlastnosti rozhraní nemá text.</span><span class="sxs-lookup"><span data-stu-id="2d870-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="2d870-106">Účelem přístupové objekty tedy k označení, zda je vlastnost pro čtení a zápis, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="2d870-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d870-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d870-107">Example</span></span>  
 <span data-ttu-id="2d870-108">V tomto příkladu rozhraní `IEmployee` má vlastnost pro čtení a zápis, `Name`a vlastnost určenou jen pro čtení, `Counter`.</span><span class="sxs-lookup"><span data-stu-id="2d870-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="2d870-109">Třída `Employee` implementuje `IEmployee` rozhraní a používá tyto dvě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2d870-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="2d870-110">Program načte název nového zaměstnance a aktuální počet zaměstnanců a zobrazí zaměstnanec název a číslo počítaný.</span><span class="sxs-lookup"><span data-stu-id="2d870-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>  
  
 <span data-ttu-id="2d870-111">Můžete použít plně kvalifikovaný název vlastnosti, která odkazuje na rozhraní, ve kterém je deklarovaná člena.</span><span class="sxs-lookup"><span data-stu-id="2d870-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="2d870-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2d870-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="2d870-113">To se označuje jako [explicitní implementace rozhraní](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="2d870-113">This is called [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="2d870-114">Například pokud třída `Employee` je implementace dvě rozhraní `ICitizen` a `IEmployee` a mít obě rozhraní `Name` vlastnost člena implementace explicitního rozhraní bude nutné.</span><span class="sxs-lookup"><span data-stu-id="2d870-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="2d870-115">To znamená, deklarace následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2d870-115">That is, the following property declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="2d870-116">implementuje `Name` vlastnost `IEmployee` rozhraní při následující prohlášení:</span><span class="sxs-lookup"><span data-stu-id="2d870-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 <span data-ttu-id="2d870-117">implementuje `Name` vlastnost `ICitizen` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d870-117">implements the `Name` property on the `ICitizen` interface.</span></span>  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a><span data-ttu-id="2d870-118">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="2d870-118">Sample Output</span></span>  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a><span data-ttu-id="2d870-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d870-119">See Also</span></span>  
 [<span data-ttu-id="2d870-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="2d870-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2d870-121">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2d870-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="2d870-122">Pomocí vlastností</span><span class="sxs-lookup"><span data-stu-id="2d870-122">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="2d870-123">Porovnání mezi vlastnostmi a indexery</span><span class="sxs-lookup"><span data-stu-id="2d870-123">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
 [<span data-ttu-id="2d870-124">Indexery</span><span class="sxs-lookup"><span data-stu-id="2d870-124">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="2d870-125">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d870-125">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
