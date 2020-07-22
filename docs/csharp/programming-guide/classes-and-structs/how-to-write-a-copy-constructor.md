---
title: Postup psaní konstruktoru kopírování – Průvodce programováním v C#
description: Naučte se, jak napsat kopírovací konstruktor v jazyce C#, který přebírá instanci třídy a vrací novou instanci s hodnotami vstupu.
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: beb2fcfaa36303eeaabd5278cf5e7a128282270e
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864225"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="a6f2b-103">Zápis kopírovacího konstruktoru (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="a6f2b-103">How to write a copy constructor (C# Programming Guide)</span></span>
<span data-ttu-id="a6f2b-104">C# neposkytuje kopírovací konstruktor pro objekty, ale můžete si ho napsat sami.</span><span class="sxs-lookup"><span data-stu-id="a6f2b-104">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6f2b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6f2b-105">Example</span></span>  
 <span data-ttu-id="a6f2b-106">V následujícím příkladu `Person` [Třída](../../language-reference/keywords/class.md) definuje kopírovací konstruktor, který přebírá jako svůj argument instanci `Person` .</span><span class="sxs-lookup"><span data-stu-id="a6f2b-106">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="a6f2b-107">Hodnoty vlastností argumentu jsou přiřazeny vlastnostem nové instance `Person` .</span><span class="sxs-lookup"><span data-stu-id="a6f2b-107">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="a6f2b-108">Kód obsahuje alternativní kopírovací konstruktor, který odesílá `Name` `Age` vlastnosti a instance, kterou chcete zkopírovat do konstruktoru instance třídy.</span><span class="sxs-lookup"><span data-stu-id="a6f2b-108">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="a6f2b-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6f2b-109">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="a6f2b-110">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a6f2b-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a6f2b-111">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="a6f2b-111">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="a6f2b-112">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="a6f2b-112">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="a6f2b-113">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="a6f2b-113">Finalizers</span></span>](./destructors.md)
