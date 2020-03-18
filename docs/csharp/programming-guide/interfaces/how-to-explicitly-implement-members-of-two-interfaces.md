---
title: Jak explicitně implementovat členy dvou rozhraní - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c7adc08f62a7f8a14b8e10f8b5ecdd6e37db811d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75701235"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="b8ee1-102">Jak explicitně implementovat členy dvou rozhraní (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="b8ee1-102">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="b8ee1-103">Explicitní implementace [rozhraní](../../language-reference/keywords/interface.md) také umožňuje programátorovi implementovat dvě rozhraní, která mají stejné názvy členů a poskytují každému členovi rozhraní samostatnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="b8ee1-103">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="b8ee1-104">Tento příklad zobrazuje rozměry pole v metrických i anglických jednotkách.</span><span class="sxs-lookup"><span data-stu-id="b8ee1-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="b8ee1-105">Třída [Box](../../language-reference/keywords/class.md) implementuje dvě rozhraní IEnglishDimensions a IMetricDimensions, které představují různé systémy měření.</span><span class="sxs-lookup"><span data-stu-id="b8ee1-105">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="b8ee1-106">Obě rozhraní mají identické názvy členů, Délka a Šířka.</span><span class="sxs-lookup"><span data-stu-id="b8ee1-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8ee1-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8ee1-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b8ee1-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="b8ee1-108">Robust Programming</span></span>  
 <span data-ttu-id="b8ee1-109">Pokud chcete provést výchozí měření v anglických jednotkách, implementujte metody Délka a šířka normálně a explicitně implementujte metody Length and Width z rozhraní IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="b8ee1-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="b8ee1-110">V takovém případě můžete přistupovat k anglickým jednotkám z instance třídy a přistupovat k jednotkám metrik y z instance rozhraní:</span><span class="sxs-lookup"><span data-stu-id="b8ee1-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="b8ee1-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8ee1-111">See also</span></span>

- [<span data-ttu-id="b8ee1-112">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b8ee1-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b8ee1-113">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="b8ee1-113">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="b8ee1-114">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8ee1-114">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="b8ee1-115">Jak explicitně implementovat členy rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8ee1-115">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
