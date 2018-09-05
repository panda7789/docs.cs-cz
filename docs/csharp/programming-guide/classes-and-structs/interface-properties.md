---
title: Vlastnosti rozhraní (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 619b9167b9b96be2908d833403379e4c2fe78ba5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746915"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="67596-102">Vlastnosti rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="67596-102">Interface Properties (C# Programming Guide)</span></span>
<span data-ttu-id="67596-103">Vlastnosti mohou být deklarovány na [rozhraní](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="67596-103">Properties can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="67596-104">Následuje příklad přistupující objekt vlastnosti rozhraní:</span><span class="sxs-lookup"><span data-stu-id="67596-104">The following is an example of an interface property accessor:</span></span>  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 <span data-ttu-id="67596-105">Přistupující objekt vlastnosti rozhraní nemá tělo.</span><span class="sxs-lookup"><span data-stu-id="67596-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="67596-106">Účelem přistupující objekty tedy označující, zda je vlastnost pro čtení i zápis, jen pro čtení nebo jen pro zápis.</span><span class="sxs-lookup"><span data-stu-id="67596-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67596-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="67596-107">Example</span></span>  
 <span data-ttu-id="67596-108">V tomto příkladu rozhraní `IEmployee` má vlastnost pro čtení i zápis, `Name`a vlastnost jen pro čtení, `Counter`.</span><span class="sxs-lookup"><span data-stu-id="67596-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="67596-109">Třída `Employee` implementuje `IEmployee` rozhraní a používá tyto dvě vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="67596-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="67596-110">Program čte název nového zaměstnance a aktuální počet zaměstnanců a zobrazí jméno zaměstnance a vypočítané číslo.</span><span class="sxs-lookup"><span data-stu-id="67596-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>  
  
 <span data-ttu-id="67596-111">Můžete použít plně kvalifikovaný název vlastnosti, která odkazuje na rozhraní, ve kterém člen je deklarovaný.</span><span class="sxs-lookup"><span data-stu-id="67596-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="67596-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="67596-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="67596-113">Tento postup se nazývá [explicitní implementaci rozhraní](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="67596-113">This is called [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="67596-114">Například pokud třída `Employee` implementuje dvě rozhraní `ICitizen` a `IEmployee` a mít obě rozhraní `Name` vlastnosti, bude explicitní implementace členu rozhraní nezbytné.</span><span class="sxs-lookup"><span data-stu-id="67596-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="67596-115">To znamená, následující deklarace vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="67596-115">That is, the following property declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="67596-116">implementuje `Name` vlastnost `IEmployee` rozhraní při následující deklarace:</span><span class="sxs-lookup"><span data-stu-id="67596-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 <span data-ttu-id="67596-117">implementuje `Name` vlastnost `ICitizen` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67596-117">implements the `Name` property on the `ICitizen` interface.</span></span>  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a><span data-ttu-id="67596-118">Vzorový výstup</span><span class="sxs-lookup"><span data-stu-id="67596-118">Sample Output</span></span>  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a><span data-ttu-id="67596-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="67596-119">See Also</span></span>

- [<span data-ttu-id="67596-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="67596-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="67596-121">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="67596-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [<span data-ttu-id="67596-122">Použití vlastností</span><span class="sxs-lookup"><span data-stu-id="67596-122">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
- [<span data-ttu-id="67596-123">Porovnání mezi vlastnostmi a indexery</span><span class="sxs-lookup"><span data-stu-id="67596-123">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
- [<span data-ttu-id="67596-124">Indexery</span><span class="sxs-lookup"><span data-stu-id="67596-124">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="67596-125">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="67596-125">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
