---
title: Jak definovat konstanty v jazyce C#
description: Naučte se definovat konstanty v jazyce C#, což jsou pole, jejichž hodnoty jsou nastaveny v době kompilace. Použijte konstanty k poskytnutí smysluplných názvů pro speciální hodnoty.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: afa2799cf76f976e332f91b631dc90e2799a0aa0
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864641"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="7ee1f-104">Definování konstant v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="7ee1f-104">How to define constants in C\#</span></span>
<span data-ttu-id="7ee1f-105">Konstanty jsou pole, jejichž hodnoty jsou nastaveny v době kompilace a nelze je nikdy změnit.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-105">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="7ee1f-106">Použijte konstanty k poskytnutí smysluplných názvů namísto číselných literálů ("Magic Numbers") pro speciální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-106">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ee1f-107">V jazyce C# nelze pomocí direktivy preprocesoru [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) definovat konstanty způsobem, který je obvykle používán v jazyce C a C++.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-107">In C# the [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="7ee1f-108">Pro definování konstantních hodnot integrálních typů ( `int` , a `byte` tak dále) použijte Výčtový typ.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-108">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="7ee1f-109">Další informace naleznete v tématu [Enum](../../language-reference/builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="7ee1f-109">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="7ee1f-110">Chcete-li definovat Neceločíselné konstanty, jedním z přístupů je seskupit do jedné statické třídy s názvem `Constants` .</span><span class="sxs-lookup"><span data-stu-id="7ee1f-110">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="7ee1f-111">To bude vyžadovat, aby všechny odkazy na konstanty byly uvozeny názvem třídy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-111">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ee1f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ee1f-112">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 <span data-ttu-id="7ee1f-113">Použití kvalifikátoru názvu třídy pomáhá zajistit, aby vy a ostatní uživatelé používali konstantu, což znamená, že je konstantní a nelze ji upravit.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-113">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee1f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ee1f-114">See also</span></span>

- [<span data-ttu-id="7ee1f-115">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="7ee1f-115">Classes and Structs</span></span>](./index.md)
