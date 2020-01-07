---
title: Jak definovat konstanty v jazyce C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 15526655de8af6fed464376db1ac761468215210
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337658"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="f7bdf-102">Definování konstant v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="f7bdf-102">How to define constants in C\#</span></span>
<span data-ttu-id="f7bdf-103">Konstanty jsou pole, jejichž hodnoty jsou nastaveny v době kompilace a nelze je nikdy změnit.</span><span class="sxs-lookup"><span data-stu-id="f7bdf-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="f7bdf-104">Použijte konstanty k poskytnutí smysluplných názvů namísto číselných literálů ("Magic Numbers") pro speciální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f7bdf-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7bdf-105">V C# direktivě preprocesoru [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) nelze použít k definování konstant způsobem, který se obvykle používá v C a C++.</span><span class="sxs-lookup"><span data-stu-id="f7bdf-105">In C# the [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="f7bdf-106">Pro definování konstantních hodnot integrálních typů (`int`, `byte`atd.) použijte Výčtový typ.</span><span class="sxs-lookup"><span data-stu-id="f7bdf-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="f7bdf-107">Další informace naleznete v tématu [Enum](../../language-reference/builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="f7bdf-107">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="f7bdf-108">Chcete-li definovat Neceločíselné konstanty, jeden z nich je seskupit do jedné statické třídy s názvem `Constants`.</span><span class="sxs-lookup"><span data-stu-id="f7bdf-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="f7bdf-109">To bude vyžadovat, aby všechny odkazy na konstanty byly uvozeny názvem třídy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f7bdf-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7bdf-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7bdf-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 <span data-ttu-id="f7bdf-111">Použití kvalifikátoru názvu třídy pomáhá zajistit, aby vy a ostatní uživatelé používali konstantu, což znamená, že je konstantní a nelze ji upravit.</span><span class="sxs-lookup"><span data-stu-id="f7bdf-111">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7bdf-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7bdf-112">See also</span></span>

- [<span data-ttu-id="f7bdf-113">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="f7bdf-113">Classes and Structs</span></span>](./index.md)
