---
title: Jak napsat konstruktor kopie - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: aa6feb1b07f491a90a78684e254910d387b9bccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714844"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="89975-102">Jak napsat konstruktor kopie (C# Programovací průvodce)</span><span class="sxs-lookup"><span data-stu-id="89975-102">How to write a copy constructor (C# Programming Guide)</span></span>
<span data-ttu-id="89975-103">C# neposkytuje konstruktor kopie pro objekty, ale můžete napsat sami.</span><span class="sxs-lookup"><span data-stu-id="89975-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89975-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="89975-104">Example</span></span>  
 <span data-ttu-id="89975-105">V následujícím příkladu `Person` [třída](../../language-reference/keywords/class.md) definuje konstruktor kopie, který bere jako `Person`svůj argument instanci .</span><span class="sxs-lookup"><span data-stu-id="89975-105">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="89975-106">Hodnoty vlastností argumentu jsou přiřazeny vlastnostem nové `Person`instance .</span><span class="sxs-lookup"><span data-stu-id="89975-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="89975-107">Kód obsahuje alternativní kopie konstruktor, `Name` `Age` který odešle a vlastnosti instance, které chcete zkopírovat do konstruktorinstance třídy.</span><span class="sxs-lookup"><span data-stu-id="89975-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="89975-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="89975-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="89975-109">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="89975-109">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="89975-110">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="89975-110">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="89975-111">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="89975-111">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="89975-112">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="89975-112">Finalizers</span></span>](./destructors.md)
