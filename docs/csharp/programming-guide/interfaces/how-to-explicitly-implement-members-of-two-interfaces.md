---
title: "Postupy: Explicitní implementace členů dvou rozhraní (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f0820328f037008c152b2e23071ae0ba8dba02bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="feb2d-102">Postupy: Explicitní implementace členů dvou rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="feb2d-102">How to: Explicitly Implement Members of Two Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="feb2d-103">Explicitní [rozhraní](../../../csharp/language-reference/keywords/interface.md) implementace také umožňuje programátorů implementovat dvě rozhraní, které mají stejné názvy členů a poskytnout každý člen rozhraní samostatné implementace.</span><span class="sxs-lookup"><span data-stu-id="feb2d-103">Explicit [interface](../../../csharp/language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="feb2d-104">Tento příklad zobrazí rozměry pole v metrika i anglické jednotky.</span><span class="sxs-lookup"><span data-stu-id="feb2d-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="feb2d-105">Do pole [třída](../../../csharp/language-reference/keywords/class.md) implementuje dvě rozhraní IEnglishDimensions a IMetricDimensions, které představují různých měrná systémy.</span><span class="sxs-lookup"><span data-stu-id="feb2d-105">The Box [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="feb2d-106">Obě rozhraní mít názvy identické členů, délku a šířku.</span><span class="sxs-lookup"><span data-stu-id="feb2d-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="feb2d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="feb2d-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="feb2d-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="feb2d-108">Robust Programming</span></span>  
 <span data-ttu-id="feb2d-109">Pokud chcete, aby měření výchozí v anglické jednotky, obvykle implementovat metody délku a šířku a explicitní implementace metody délku a šířku z rozhraní IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="feb2d-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 <span data-ttu-id="feb2d-110">V takovém případě můžete používat anglické jednotky z instance třídy a přístup k metriky jednotky z instance rozhraní:</span><span class="sxs-lookup"><span data-stu-id="feb2d-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="feb2d-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="feb2d-111">See Also</span></span>  
 [<span data-ttu-id="feb2d-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="feb2d-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="feb2d-113">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="feb2d-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="feb2d-114">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="feb2d-114">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="feb2d-115">Postupy: explicitní implementace členů rozhraní</span><span class="sxs-lookup"><span data-stu-id="feb2d-115">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
