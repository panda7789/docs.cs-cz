---
title: Explicitní implementace členů dvou rozhraní – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 720e265cedcf9ad8be00f5e013365129f38749af
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635246"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="b137c-102">Explicitní implementace členů dvou rozhraní (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="b137c-102">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="b137c-103">Explicitní implementace [rozhraní](../../language-reference/keywords/interface.md) také umožňuje programátorovi implementovat dvě rozhraní, která mají stejné názvy členů a dávají každému členu rozhraní samostatnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="b137c-103">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="b137c-104">Tento příklad zobrazuje rozměry pole v jednotkách metriky a angličtiny.</span><span class="sxs-lookup"><span data-stu-id="b137c-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="b137c-105">[Třída](../../language-reference/keywords/class.md) box implementuje dvě rozhraní IEnglishDimensions a IMetricDimensions, která představuje různé měřicí systémy.</span><span class="sxs-lookup"><span data-stu-id="b137c-105">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="b137c-106">Obě rozhraní mají stejné názvy členů, délku a šířku.</span><span class="sxs-lookup"><span data-stu-id="b137c-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b137c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b137c-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b137c-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="b137c-108">Robust Programming</span></span>  
 <span data-ttu-id="b137c-109">Pokud chcete nastavit výchozí míry v anglických jednotkách, implementujte její délku a šířku obvyklým způsobem a explicitně Implementujte metody délky a šířky z rozhraní IMetricDimensions:</span><span class="sxs-lookup"><span data-stu-id="b137c-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="b137c-110">V tomto případě máte přístup k anglickou jednotkám z instance třídy a získáte přístup ke jednotkám metrik z instance rozhraní:</span><span class="sxs-lookup"><span data-stu-id="b137c-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="b137c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b137c-111">See also</span></span>

- [<span data-ttu-id="b137c-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b137c-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b137c-113">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="b137c-113">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="b137c-114">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="b137c-114">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="b137c-115">Postup explicitní implementace členů rozhraní</span><span class="sxs-lookup"><span data-stu-id="b137c-115">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
