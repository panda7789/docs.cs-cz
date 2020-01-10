---
title: Zápis kopírovacího konstruktoru – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: aa6feb1b07f491a90a78684e254910d387b9bccd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714844"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="bf637-102">Zápis kopírovacího konstruktoru (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="bf637-102">How to write a copy constructor (C# Programming Guide)</span></span>
<span data-ttu-id="bf637-103">C#neposkytuje kopírovací konstruktor pro objekty, ale můžete si ho napsat sami.</span><span class="sxs-lookup"><span data-stu-id="bf637-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf637-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf637-104">Example</span></span>  
 <span data-ttu-id="bf637-105">V následujícím příkladu [třída](../../language-reference/keywords/class.md) `Person`definuje kopírovací konstruktor, který přebírá jako svůj argument instanci `Person`.</span><span class="sxs-lookup"><span data-stu-id="bf637-105">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="bf637-106">Hodnoty vlastností argumentu jsou přiřazeny vlastnostem nové instance `Person`.</span><span class="sxs-lookup"><span data-stu-id="bf637-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="bf637-107">Kód obsahuje alternativní kopírovací konstruktor, který odesílá `Name` a vlastnosti `Age` instance, kterou chcete zkopírovat do konstruktoru instance třídy.</span><span class="sxs-lookup"><span data-stu-id="bf637-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="bf637-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf637-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="bf637-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bf637-109">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bf637-110">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="bf637-110">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="bf637-111">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="bf637-111">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="bf637-112">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="bf637-112">Finalizers</span></span>](./destructors.md)
