---
title: Vlastnosti rozhraní (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: bfa03c7ebe82f3f6a03666d908a5fa9d4e386172
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325406"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="7678c-102">Vlastnosti rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="7678c-102">Interface Properties (C# Programming Guide)</span></span>
<span data-ttu-id="7678c-103">Vlastnosti lze deklarovat na [rozhraní](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="7678c-103">Properties can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="7678c-104">Následuje příklad přistupující objekt indexer rozhraní:</span><span class="sxs-lookup"><span data-stu-id="7678c-104">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 <span data-ttu-id="7678c-105">Přistupující objekt vlastnosti rozhraní nemá text.</span><span class="sxs-lookup"><span data-stu-id="7678c-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="7678c-106">Účelem přístupové objekty tedy k označení, zda je vlastnost pro čtení a zápis, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="7678c-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7678c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="7678c-107">Example</span></span>  
 <span data-ttu-id="7678c-108">V tomto příkladu rozhraní `IEmployee` má vlastnost pro čtení a zápis, `Name`a vlastnost určenou jen pro čtení, `Counter`.</span><span class="sxs-lookup"><span data-stu-id="7678c-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="7678c-109">Třída `Employee` implementuje `IEmployee` rozhraní a používá tyto dvě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7678c-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="7678c-110">Program načte název nového zaměstnance a aktuální počet zaměstnanců a zobrazí zaměstnanec název a číslo počítaný.</span><span class="sxs-lookup"><span data-stu-id="7678c-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>  
  
 <span data-ttu-id="7678c-111">Můžete použít plně kvalifikovaný název vlastnosti, která odkazuje na rozhraní, ve kterém je deklarovaná člena.</span><span class="sxs-lookup"><span data-stu-id="7678c-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="7678c-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="7678c-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="7678c-113">To se označuje jako [explicitní implementace rozhraní](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="7678c-113">This is called [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="7678c-114">Například pokud třída `Employee` je implementace dvě rozhraní `ICitizen` a `IEmployee` a mít obě rozhraní `Name` vlastnost člena implementace explicitního rozhraní bude nutné.</span><span class="sxs-lookup"><span data-stu-id="7678c-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="7678c-115">To znamená, deklarace následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="7678c-115">That is, the following property declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="7678c-116">implementuje `Name` vlastnost `IEmployee` rozhraní při následující prohlášení:</span><span class="sxs-lookup"><span data-stu-id="7678c-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 <span data-ttu-id="7678c-117">implementuje `Name` vlastnost `ICitizen` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7678c-117">implements the `Name` property on the `ICitizen` interface.</span></span>  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a><span data-ttu-id="7678c-118">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="7678c-118">Sample Output</span></span>  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a><span data-ttu-id="7678c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7678c-119">See Also</span></span>  
 [<span data-ttu-id="7678c-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7678c-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7678c-121">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7678c-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="7678c-122">Použití vlastností</span><span class="sxs-lookup"><span data-stu-id="7678c-122">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="7678c-123">Porovnání mezi vlastnostmi a indexery</span><span class="sxs-lookup"><span data-stu-id="7678c-123">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
 [<span data-ttu-id="7678c-124">Indexery</span><span class="sxs-lookup"><span data-stu-id="7678c-124">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="7678c-125">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="7678c-125">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
