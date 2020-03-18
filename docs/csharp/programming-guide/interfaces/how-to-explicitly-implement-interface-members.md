---
title: Jak explicitně implementovat členy rozhraní - Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627782"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="7e2a1-102">Jak explicitně implementovat členy rozhraní (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7e2a1-102">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="7e2a1-103">Tento příklad deklaruje [rozhraní](../../language-reference/keywords/interface.md) `IDimensions`a třídu , `Box`která `GetLength` `GetWidth`explicitně implementuje členy rozhraní a .</span><span class="sxs-lookup"><span data-stu-id="7e2a1-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `GetLength` and `GetWidth`.</span></span> <span data-ttu-id="7e2a1-104">Členové jsou přístupné prostřednictvím `dimensions`instance rozhraní .</span><span class="sxs-lookup"><span data-stu-id="7e2a1-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e2a1-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e2a1-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="7e2a1-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="7e2a1-106">Robust Programming</span></span>  
  
- <span data-ttu-id="7e2a1-107">Všimněte si, že `Main` následující řádky v metodě jsou zakomentovány, protože by způsobit chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="7e2a1-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="7e2a1-108">Člen rozhraní, který je explicitně implementován nelze získat přístup z instance [třídy:](../../language-reference/keywords/class.md)</span><span class="sxs-lookup"><span data-stu-id="7e2a1-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="7e2a1-109">Všimněte si také, že `Main` následující řádky v metodě úspěšně vytisknout rozměry pole, protože metody jsou volány z instance rozhraní:</span><span class="sxs-lookup"><span data-stu-id="7e2a1-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="7e2a1-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e2a1-110">See also</span></span>

- [<span data-ttu-id="7e2a1-111">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7e2a1-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7e2a1-112">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="7e2a1-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="7e2a1-113">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e2a1-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="7e2a1-114">Jak explicitně implementovat členy dvou rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e2a1-114">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
