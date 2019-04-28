---
title: 'Postupy: Explicitní implementace členů rozhraní - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: d5630065ae1fbfceca9ce3b5180664bba3a104a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710261"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="aa2d7-102">Postupy: Explicitní implementace členů rozhraní (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="aa2d7-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="aa2d7-103">V tomto příkladu deklaruje [rozhraní](../../../csharp/language-reference/keywords/interface.md), `IDimensions`a třídu, `Box`, které explicitně implementuje členy rozhraní `getLength` a `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="aa2d7-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="aa2d7-104">Členy jsou přístupné prostřednictvím instance rozhraní `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="aa2d7-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa2d7-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa2d7-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="aa2d7-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="aa2d7-106">Robust Programming</span></span>  
  
- <span data-ttu-id="aa2d7-107">Všimněte si, že následující řádky v `Main` metody, jsou zakomentované vzhledem k tomu, že se vytvoří chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="aa2d7-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="aa2d7-108">Explicitně implementovaný člen rozhraní, není přístupná z [třídy](../../../csharp/language-reference/keywords/class.md) instance:</span><span class="sxs-lookup"><span data-stu-id="aa2d7-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="aa2d7-109">Všimněte si také, že následující řádky v `Main` metoda úspěšně vytiskne rozměry pole vzhledem k tomu, že se z instance rozhraní volání těchto metod:</span><span class="sxs-lookup"><span data-stu-id="aa2d7-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="aa2d7-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa2d7-110">See also</span></span>

- [<span data-ttu-id="aa2d7-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="aa2d7-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="aa2d7-112">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="aa2d7-112">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="aa2d7-113">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa2d7-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
- [<span data-ttu-id="aa2d7-114">Postupy: Explicitní implementace členů dvou rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa2d7-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
