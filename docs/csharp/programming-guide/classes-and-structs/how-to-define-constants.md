---
title: Jak definovat konstanty v jazyce C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 15526655de8af6fed464376db1ac761468215210
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75337658"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="22d2e-102">Jak definovat konstanty v C\#</span><span class="sxs-lookup"><span data-stu-id="22d2e-102">How to define constants in C\#</span></span>
<span data-ttu-id="22d2e-103">Konstanty jsou pole, jejichž hodnoty jsou nastaveny v době kompilace a nikdy je nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="22d2e-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="22d2e-104">Konstanty slouží k poskytnutí smysluplných názvů namísto číselných literál ("magická čísla") pro speciální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="22d2e-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22d2e-105">V jazyce C# direktivu preprocesoru [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) nelze použít k definování konstant způsobem, který se obvykle používá v jazyce C a C++.</span><span class="sxs-lookup"><span data-stu-id="22d2e-105">In C# the [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="22d2e-106">Chcete-li definovat konstantní`int`hodnoty `byte`integrálních typů ( , , a tak dále) použijte ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="22d2e-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="22d2e-107">Další informace naleznete [v tématu výčet](../../language-reference/builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="22d2e-107">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="22d2e-108">Chcete-li definovat neintegrální konstanty, jeden přístup `Constants`je jejich seskupení v jedné statické třídy s názvem .</span><span class="sxs-lookup"><span data-stu-id="22d2e-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="22d2e-109">To bude vyžadovat, aby všechny odkazy na konstanty byly označeny názvem třídy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="22d2e-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22d2e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="22d2e-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 <span data-ttu-id="22d2e-111">Použití kvalifikátoru názvu třídy pomáhá zajistit, že vy a ostatní, kteří používají konstantu, pochopíte, že je konstantní a nelze ji změnit.</span><span class="sxs-lookup"><span data-stu-id="22d2e-111">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d2e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="22d2e-112">See also</span></span>

- [<span data-ttu-id="22d2e-113">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="22d2e-113">Classes and Structs</span></span>](./index.md)
