---
title: 'Postupy: Inicializace objektů pomocí inicializátoru objektů (Průvodce programováním v C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8e9130983aabe991660ff4cca90b33609f86c158
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="fdeec-102">Postupy: Inicializace objektů pomocí inicializátoru objektů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="fdeec-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="fdeec-103">Inicializátory objektů můžete použít třeba inicializovat objekty typu deklarativní způsobem bez explicitně vyvolání konstruktor pro typ.</span><span class="sxs-lookup"><span data-stu-id="fdeec-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
 <span data-ttu-id="fdeec-104">Následující příklady ukazují, jak pomocí pojmenovaných objektů inicializátory objektů.</span><span class="sxs-lookup"><span data-stu-id="fdeec-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="fdeec-105">Procesy kompilátoru objekt inicializátory první přístup k výchozí konstruktor instance a pak zpracování inicializacích člen.</span><span class="sxs-lookup"><span data-stu-id="fdeec-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="fdeec-106">Proto pokud výchozí konstruktor je deklarován jako `private` ve třídě, se nezdaří inicializátory objektů, které vyžadují veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="fdeec-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>  
  
 <span data-ttu-id="fdeec-107">Pokud definujete anonymního typu, je nutné použít inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="fdeec-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="fdeec-108">Další informace najdete v tématu [postupy: vrácení podmnožin z vlastností elementů v dotazu](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="fdeec-108">For more information, see [How to: Return Subsets of Element Properties in a Query](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdeec-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="fdeec-109">Example</span></span>  
 <span data-ttu-id="fdeec-110">Následující příklad ukazuje, jak k chybě při inicializaci novou `StudentName` typu pomocí inicializátory objektů.</span><span class="sxs-lookup"><span data-stu-id="fdeec-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="fdeec-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="fdeec-111">Example</span></span>  
 <span data-ttu-id="fdeec-112">Následující příklad ukazuje, jak k chybě při inicializaci kolekce `StudentName` typy pomocí inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="fdeec-112">The following example shows how to initialize a collection of `StudentName` types by using a collection initializer.</span></span> <span data-ttu-id="fdeec-113">Všimněte si, že inicializátoru kolekce řadu inicializátory objektů oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="fdeec-113">Note that a collection initializer is a series of comma-separated object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fdeec-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="fdeec-114">Compiling the Code</span></span>  
 <span data-ttu-id="fdeec-115">Pokud chcete spustit tento kód, zkopírujte a vložte třídy do Visual C# projektu konzolové aplikace vytvořené v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fdeec-115">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdeec-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdeec-116">See Also</span></span>  
 [<span data-ttu-id="fdeec-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fdeec-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fdeec-118">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="fdeec-118">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
