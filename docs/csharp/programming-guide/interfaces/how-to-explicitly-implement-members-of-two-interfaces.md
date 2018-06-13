---
title: 'Postupy: Explicitní implementace členů dvou rozhraní (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c73089fdbf1350c1aff68ac3e8e78be00e21b931
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339037"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="8e3d2-102">Postupy: Explicitní implementace členů dvou rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="8e3d2-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="8e3d2-103">Explicitní [rozhraní](../../../csharp/language-reference/keywords/interface.md) implementace také umožňuje programátorů implementovat dvě rozhraní, které mají stejné názvy členů a poskytnout každý člen rozhraní samostatné implementace.</span><span class="sxs-lookup"><span data-stu-id="8e3d2-103">Explicit [interface](../../../csharp/language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="8e3d2-104">Tento příklad zobrazí rozměry pole v metrika i anglické jednotky.</span><span class="sxs-lookup"><span data-stu-id="8e3d2-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="8e3d2-105">Do pole [třída](../../../csharp/language-reference/keywords/class.md) implementuje dvě rozhraní IEnglishDimensions a IMetricDimensions, které představují různých měrná systémy.</span><span class="sxs-lookup"><span data-stu-id="8e3d2-105">The Box [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="8e3d2-106">Obě rozhraní mít názvy identické členů, délku a šířku.</span><span class="sxs-lookup"><span data-stu-id="8e3d2-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e3d2-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e3d2-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8e3d2-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="8e3d2-108">Robust Programming</span></span>  
 <span data-ttu-id="8e3d2-109">Pokud chcete, aby měření výchozí v anglické jednotky, obvykle implementovat metody délku a šířku a explicitní implementace metody délku a šířku z rozhraní IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="8e3d2-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 <span data-ttu-id="8e3d2-110">V takovém případě můžete používat anglické jednotky z instance třídy a přístup k metriky jednotky z instance rozhraní:</span><span class="sxs-lookup"><span data-stu-id="8e3d2-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8e3d2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e3d2-111">See Also</span></span>  
 [<span data-ttu-id="8e3d2-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8e3d2-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8e3d2-113">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="8e3d2-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="8e3d2-114">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e3d2-114">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="8e3d2-115">Postupy: Explicitní implementace členů rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e3d2-115">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
