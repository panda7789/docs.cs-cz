---
title: 'Postupy: Explicitní implementace členů rozhraní - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 11ef4eb3e4da0166ae4753b8028edb217f2a487e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236925"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="d0938-102">Postupy: Explicitní implementace členů rozhraní (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="d0938-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="d0938-103">V tomto příkladu deklaruje [rozhraní](../../../csharp/language-reference/keywords/interface.md), `IDimensions`a třídu, `Box`, které explicitně implementuje členy rozhraní `getLength` a `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="d0938-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="d0938-104">Členy jsou přístupné prostřednictvím instance rozhraní `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="d0938-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0938-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0938-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d0938-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d0938-106">Robust Programming</span></span>  
  
-   <span data-ttu-id="d0938-107">Všimněte si, že následující řádky v `Main` metody, jsou zakomentované vzhledem k tomu, že se vytvoří chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="d0938-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="d0938-108">Explicitně implementovaný člen rozhraní, není přístupná z [třídy](../../../csharp/language-reference/keywords/class.md) instance:</span><span class="sxs-lookup"><span data-stu-id="d0938-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   <span data-ttu-id="d0938-109">Všimněte si také, že následující řádky v `Main` metoda úspěšně vytiskne rozměry pole vzhledem k tomu, že se z instance rozhraní volání těchto metod:</span><span class="sxs-lookup"><span data-stu-id="d0938-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d0938-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0938-110">See Also</span></span>

- [<span data-ttu-id="d0938-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d0938-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d0938-112">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="d0938-112">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="d0938-113">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0938-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
- [<span data-ttu-id="d0938-114">Postupy: Explicitní implementace členů dvou rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0938-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
