---
title: Explicitní implementace členů rozhraní – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627782"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="42f95-102">Postup explicitní implementace členů rozhraní (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="42f95-102">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="42f95-103">Tento příklad deklaruje [rozhraní](../../language-reference/keywords/interface.md), `IDimensions`a třídu, `Box`, která explicitně implementuje členy rozhraní `GetLength` a `GetWidth`.</span><span class="sxs-lookup"><span data-stu-id="42f95-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `GetLength` and `GetWidth`.</span></span> <span data-ttu-id="42f95-104">Členové jsou k dispozici prostřednictvím instance rozhraní `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="42f95-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42f95-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="42f95-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="42f95-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="42f95-106">Robust Programming</span></span>  
  
- <span data-ttu-id="42f95-107">Všimněte si, že následující řádky v metodě `Main` jsou zakomentovány, protože by vznikly chyby při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="42f95-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="42f95-108">Člen rozhraní, který je explicitně implementován, není k dispozici z instance [třídy](../../language-reference/keywords/class.md) :</span><span class="sxs-lookup"><span data-stu-id="42f95-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="42f95-109">Všimněte si také, že následující řádky v metodě `Main` úspěšně vytiskly rozměry pole, protože metody jsou volány z instance rozhraní:</span><span class="sxs-lookup"><span data-stu-id="42f95-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="42f95-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="42f95-110">See also</span></span>

- [<span data-ttu-id="42f95-111">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="42f95-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="42f95-112">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="42f95-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="42f95-113">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="42f95-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="42f95-114">Postup explicitní implementace členů dvou rozhraní</span><span class="sxs-lookup"><span data-stu-id="42f95-114">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
