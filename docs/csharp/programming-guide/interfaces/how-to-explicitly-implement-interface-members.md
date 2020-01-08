---
title: Explicitní implementace členů rozhraní – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 4efc325b3587ee790cce739727506a28c3a1f524
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635402"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="794ca-102">Postup explicitní implementace členů rozhraní (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="794ca-102">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="794ca-103">Tento příklad deklaruje [rozhraní](../../language-reference/keywords/interface.md), `IDimensions`a třídu, `Box`, která explicitně implementuje členy rozhraní `getLength` a `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="794ca-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="794ca-104">Členové jsou k dispozici prostřednictvím instance rozhraní `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="794ca-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="794ca-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="794ca-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="794ca-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="794ca-106">Robust Programming</span></span>  
  
- <span data-ttu-id="794ca-107">Všimněte si, že následující řádky v metodě `Main` jsou zakomentovány, protože by vznikly chyby při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="794ca-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="794ca-108">Člen rozhraní, který je explicitně implementován, není k dispozici z instance [třídy](../../language-reference/keywords/class.md) :</span><span class="sxs-lookup"><span data-stu-id="794ca-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="794ca-109">Všimněte si také, že následující řádky v metodě `Main` úspěšně vytiskly rozměry pole, protože metody jsou volány z instance rozhraní:</span><span class="sxs-lookup"><span data-stu-id="794ca-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="794ca-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="794ca-110">See also</span></span>

- [<span data-ttu-id="794ca-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="794ca-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="794ca-112">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="794ca-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="794ca-113">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="794ca-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="794ca-114">Postup explicitní implementace členů dvou rozhraní</span><span class="sxs-lookup"><span data-stu-id="794ca-114">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
