---
title: Postup explicitní implementace členů rozhraní – Průvodce programováním v C#
description: Naučte se explicitně implementovat členy rozhraní v tomto příkladu C#. Členové jsou k dispozici prostřednictvím instance rozhraní.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 35b512ff6cbee1dd942f5b3476db660481808297
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303072"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="51516-104">Postup explicitní implementace členů rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="51516-104">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="51516-105">Tento příklad deklaruje [rozhraní](../../language-reference/keywords/interface.md), `IDimensions` , a třídu, `Box` ,, která explicitně implementuje členy rozhraní `GetLength` a `GetWidth` .</span><span class="sxs-lookup"><span data-stu-id="51516-105">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `GetLength` and `GetWidth`.</span></span> <span data-ttu-id="51516-106">Členové jsou k dispozici prostřednictvím instance rozhraní `dimensions` .</span><span class="sxs-lookup"><span data-stu-id="51516-106">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51516-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="51516-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="51516-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="51516-108">Robust Programming</span></span>  
  
- <span data-ttu-id="51516-109">Všimněte si, že následující řádky v `Main` metodě jsou zakomentovány, protože by vznikly chyby při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="51516-109">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="51516-110">Člen rozhraní, který je explicitně implementován, není k dispozici z instance [třídy](../../language-reference/keywords/class.md) :</span><span class="sxs-lookup"><span data-stu-id="51516-110">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="51516-111">Všimněte si také, že následující řádky v `Main` metodě úspěšně vytiskly rozměry pole, protože metody jsou volány z instance rozhraní:</span><span class="sxs-lookup"><span data-stu-id="51516-111">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="51516-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51516-112">See also</span></span>

- [<span data-ttu-id="51516-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="51516-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="51516-114">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="51516-114">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="51516-115">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="51516-115">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="51516-116">Jak explicitně implementovat členy dvou rozhraní</span><span class="sxs-lookup"><span data-stu-id="51516-116">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
