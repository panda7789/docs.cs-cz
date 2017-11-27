---
title: "Postupy: Inicializace objektů pomocí inicializátoru objektů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d1e65f8519062f6bceeb466a3b72c5719c0918f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="467f8-102">Postupy: Inicializace objektů pomocí inicializátoru objektů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="467f8-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="467f8-103">Inicializátory objektů můžete použít třeba inicializovat objekty typu deklarativní způsobem bez explicitně vyvolání konstruktor pro typ.</span><span class="sxs-lookup"><span data-stu-id="467f8-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
 <span data-ttu-id="467f8-104">Následující příklady ukazují, jak pomocí pojmenovaných objektů inicializátory objektů.</span><span class="sxs-lookup"><span data-stu-id="467f8-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="467f8-105">Procesy kompilátoru objekt inicializátory první přístup k výchozí konstruktor instance a pak zpracování inicializacích člen.</span><span class="sxs-lookup"><span data-stu-id="467f8-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="467f8-106">Proto pokud výchozí konstruktor je deklarován jako `private` ve třídě, se nezdaří inicializátory objektů, které vyžadují veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="467f8-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>  
  
 <span data-ttu-id="467f8-107">Pokud definujete anonymního typu, je nutné použít inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="467f8-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="467f8-108">Další informace najdete v tématu [postupy: vrácení podmnožin z vlastností elementů v dotazu](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="467f8-108">For more information, see [How to: Return Subsets of Element Properties in a Query](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="467f8-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="467f8-109">Example</span></span>  
 <span data-ttu-id="467f8-110">Následující příklad ukazuje, jak k chybě při inicializaci novou `StudentName` typu pomocí inicializátory objektů.</span><span class="sxs-lookup"><span data-stu-id="467f8-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="467f8-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="467f8-111">Example</span></span>  
 <span data-ttu-id="467f8-112">Následující příklad ukazuje, jak k chybě při inicializaci kolekce `StudentName` typy pomocí inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="467f8-112">The following example shows how to initialize a collection of `StudentName` types by using a collection initializer.</span></span> <span data-ttu-id="467f8-113">Všimněte si, že inicializátoru kolekce řadu inicializátory objektů oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="467f8-113">Note that a collection initializer is a series of comma-separated object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="467f8-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="467f8-114">Compiling the Code</span></span>  
 <span data-ttu-id="467f8-115">Pokud chcete spustit tento kód, zkopírujte a vložte třídy do Visual C# projektu konzolové aplikace vytvořené v [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="467f8-115">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="467f8-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="467f8-116">See Also</span></span>  
 [<span data-ttu-id="467f8-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="467f8-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="467f8-118">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="467f8-118">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
