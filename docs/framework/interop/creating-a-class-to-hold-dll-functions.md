---
title: Vytvoření třídy k umístění funkcí DLL
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
ms.openlocfilehash: 765d4344553a6e65b930a7bf586a41144d220fc6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123628"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="8fbe6-102">Vytvoření třídy k umístění funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="8fbe6-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="8fbe6-103">Zabalení často používané funkce knihovny DLL ve spravované třídě představuje účinný přístup k zapouzdření funkčnosti platformy.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="8fbe6-104">I když není nutné tak učinit v každém případě, poskytnutí obálky třídy je pohodlné, protože definování funkcí knihovny DLL může být náročné a náchylné k chybám.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="8fbe6-105">Pokud programujete v Visual Basic nebo C#, musíte deklarovat funkce knihovny DLL v rámci třídy nebo modulu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="8fbe6-106">V rámci třídy definujete statickou metodu pro každou funkci knihovny DLL, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="8fbe6-107">Definice může obsahovat další informace, jako je například znaková sada nebo konvence volání používané při předávání argumentů metody; Vynecháte-li tyto informace, vyberte výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="8fbe6-108">Úplný seznam možností deklarace a jejich výchozí nastavení naleznete v tématu [vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="8fbe6-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="8fbe6-109">Po zabalení můžete volat metody pro třídu při volání statických metod na jakékoli jiné třídě.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-109">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="8fbe6-110">Volání platformy zpracovává základní exportovanou funkci automaticky.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="8fbe6-111">Při navrhování spravované třídy pro vyvolání platformy zvažte vztahy mezi třídami a funkcemi knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="8fbe6-112">Můžete například:</span><span class="sxs-lookup"><span data-stu-id="8fbe6-112">For example, you can:</span></span>  
  
- <span data-ttu-id="8fbe6-113">Deklarujete funkce knihovny DLL v rámci existující třídy.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-113">Declare DLL functions within an existing class.</span></span>  
  
- <span data-ttu-id="8fbe6-114">Vytvořte pro každou funkci knihovny DLL jednotlivou třídu, zachováte funkce izolované a snadno najít.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
- <span data-ttu-id="8fbe6-115">Vytvořte jednu třídu pro sadu souvisejících funkcí knihoven DLL pro vytváření logických seskupení a snížení režie.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="8fbe6-116">Můžete pojmenovat třídu a její metody, které jste si zařadíte.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="8fbe6-117">Příklady, které ukazují, jak vytvořit. Deklarace založené na síti, které se mají použít s voláním platformy, najdete v tématu [zařazování dat pomocí vyvolání platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="8fbe6-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fbe6-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fbe6-118">See also</span></span>

- [<span data-ttu-id="8fbe6-119">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="8fbe6-119">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="8fbe6-120">Identifikace funkcí ve knihovnách DLL</span><span class="sxs-lookup"><span data-stu-id="8fbe6-120">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="8fbe6-121">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="8fbe6-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="8fbe6-122">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="8fbe6-122">Calling a DLL Function</span></span>](calling-a-dll-function.md)
