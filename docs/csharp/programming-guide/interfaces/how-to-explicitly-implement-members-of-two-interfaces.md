---
title: Postup explicitní implementace členů dvou rozhraní – Průvodce programováním v C#
description: Naučte se explicitně implementovat dvě rozhraní, která mají stejné názvy členů a každý člen rozhraní přidělte samostatné implementaci v tomto příkladu jazyka C#.
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: d60ec43f734d5e8bfa7f467874440bd3514877fe
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303059"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="492af-103">Explicitní implementace členů dvou rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="492af-103">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="492af-104">Explicitní implementace [rozhraní](../../language-reference/keywords/interface.md) také umožňuje programátorovi implementovat dvě rozhraní, která mají stejné názvy členů a dávají každému členu rozhraní samostatnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="492af-104">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="492af-105">Tento příklad zobrazuje rozměry pole v jednotkách metriky a angličtiny.</span><span class="sxs-lookup"><span data-stu-id="492af-105">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="492af-106">[Třída](../../language-reference/keywords/class.md) box implementuje dvě rozhraní IEnglishDimensions a IMetricDimensions, která představuje různé měřicí systémy.</span><span class="sxs-lookup"><span data-stu-id="492af-106">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="492af-107">Obě rozhraní mají stejné názvy členů, délku a šířku.</span><span class="sxs-lookup"><span data-stu-id="492af-107">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="492af-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="492af-108">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="492af-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="492af-109">Robust Programming</span></span>  
 <span data-ttu-id="492af-110">Pokud chcete nastavit výchozí míry v anglických jednotkách, implementujte její délku a šířku obvyklým způsobem a explicitně Implementujte metody délky a šířky z rozhraní IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="492af-110">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="492af-111">V tomto případě máte přístup k anglickou jednotkám z instance třídy a získáte přístup ke jednotkám metrik z instance rozhraní:</span><span class="sxs-lookup"><span data-stu-id="492af-111">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="492af-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="492af-112">See also</span></span>

- [<span data-ttu-id="492af-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="492af-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="492af-114">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="492af-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="492af-115">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="492af-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="492af-116">Jak explicitně implementovat členy rozhraní</span><span class="sxs-lookup"><span data-stu-id="492af-116">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
