---
title: 'Postupy: Explicitní implementace členů rozhraní (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5f7ae6bae46cdf6596b206abbdeeb94b5c21a13f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332183"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="76326-102">Postupy: Explicitní implementace členů rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="76326-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="76326-103">Tento příklad deklaruje [rozhraní](../../../csharp/language-reference/keywords/interface.md), `IDimensions`a třídu, `Box`, které explicitně implementuje členy rozhraní `getLength` a `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="76326-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="76326-104">Členy jsou přístupné prostřednictvím instance rozhraní `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="76326-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76326-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="76326-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="76326-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="76326-106">Robust Programming</span></span>  
  
-   <span data-ttu-id="76326-107">Všimněte si, že v následujících řádků `Main` metody jsou komentované vzhledem k tomu, že by vytvářejí chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="76326-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="76326-108">Člen rozhraní explicitně implementované není přístupný z [třída](../../../csharp/language-reference/keywords/class.md) instance:</span><span class="sxs-lookup"><span data-stu-id="76326-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   <span data-ttu-id="76326-109">Všimněte si také, následující řádky v `Main` metoda úspěšně tiskové out rozměry pole vzhledem k tomu, že se z instance rozhraní volání těchto metod:</span><span class="sxs-lookup"><span data-stu-id="76326-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="76326-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="76326-110">See Also</span></span>  
 [<span data-ttu-id="76326-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="76326-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="76326-112">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="76326-112">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="76326-113">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="76326-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="76326-114">Postupy: Explicitní implementace členů dvou rozhraní</span><span class="sxs-lookup"><span data-stu-id="76326-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
