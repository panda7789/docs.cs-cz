---
title: 'Postupy: Zápis kopírovacího konstruktoru – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: bdc352566052f4cec1686176131e9b1e1b768794
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596603"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="9a72a-102">Postupy: Zápis kopírovacího konstruktoru (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="9a72a-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="9a72a-103">C#neposkytuje kopírovací konstruktor pro objekty, ale můžete si ho napsat sami.</span><span class="sxs-lookup"><span data-stu-id="9a72a-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a72a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a72a-104">Example</span></span>  
 <span data-ttu-id="9a72a-105">V následujícím příkladu `Person` [Třída](../../language-reference/keywords/class.md) definuje kopírovací konstruktor, který přebírá jako svůj argument instanci `Person`.</span><span class="sxs-lookup"><span data-stu-id="9a72a-105">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="9a72a-106">Hodnoty vlastností argumentu jsou přiřazeny vlastnostem nové instance `Person`.</span><span class="sxs-lookup"><span data-stu-id="9a72a-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="9a72a-107">Kód obsahuje alternativní kopírovací konstruktor, který odesílá `Name` vlastnosti a `Age` instance, kterou chcete zkopírovat do konstruktoru instance třídy.</span><span class="sxs-lookup"><span data-stu-id="9a72a-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="9a72a-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a72a-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="9a72a-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9a72a-109">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9a72a-110">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="9a72a-110">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="9a72a-111">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="9a72a-111">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="9a72a-112">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="9a72a-112">Finalizers</span></span>](./destructors.md)
