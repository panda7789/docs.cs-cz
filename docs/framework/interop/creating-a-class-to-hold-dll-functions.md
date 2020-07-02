---
title: Vytvoření třídy k umístění funkcí DLL
description: Vytvořte obálku spravované třídy v rozhraní .NET, která bude uchovávat funkce knihovny DLL, což pomáhá zapouzdřit funkce platformy.
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
ms.openlocfilehash: b8aa0361ee5213cb947a102f903d1a7a35331f17
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622169"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="8a035-103">Vytvoření třídy k umístění funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="8a035-103">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="8a035-104">Zabalení často používané funkce knihovny DLL ve spravované třídě představuje účinný přístup k zapouzdření funkčnosti platformy.</span><span class="sxs-lookup"><span data-stu-id="8a035-104">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="8a035-105">I když není nutné tak učinit v každém případě, poskytnutí obálky třídy je pohodlné, protože definování funkcí knihovny DLL může být náročné a náchylné k chybám.</span><span class="sxs-lookup"><span data-stu-id="8a035-105">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="8a035-106">Pokud programujete v Visual Basic nebo C#, musíte deklarovat funkce knihovny DLL v rámci třídy nebo modulu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8a035-106">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="8a035-107">V rámci třídy definujete statickou metodu pro každou funkci knihovny DLL, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="8a035-107">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="8a035-108">Definice může obsahovat další informace, jako je například znaková sada nebo konvence volání používané při předávání argumentů metody; Vynecháte-li tyto informace, vyberte výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="8a035-108">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="8a035-109">Úplný seznam možností deklarace a jejich výchozí nastavení naleznete v tématu [vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="8a035-109">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="8a035-110">Po zabalení můžete volat metody pro třídu při volání statických metod na jakékoli jiné třídě.</span><span class="sxs-lookup"><span data-stu-id="8a035-110">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="8a035-111">Volání platformy zpracovává základní exportovanou funkci automaticky.</span><span class="sxs-lookup"><span data-stu-id="8a035-111">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="8a035-112">Při navrhování spravované třídy pro vyvolání platformy zvažte vztahy mezi třídami a funkcemi knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="8a035-112">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="8a035-113">Můžete například provést následující věci:</span><span class="sxs-lookup"><span data-stu-id="8a035-113">For example, you can:</span></span>  
  
- <span data-ttu-id="8a035-114">Deklarujete funkce knihovny DLL v rámci existující třídy.</span><span class="sxs-lookup"><span data-stu-id="8a035-114">Declare DLL functions within an existing class.</span></span>  
  
- <span data-ttu-id="8a035-115">Vytvořte pro každou funkci knihovny DLL jednotlivou třídu, zachováte funkce izolované a snadno najít.</span><span class="sxs-lookup"><span data-stu-id="8a035-115">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
- <span data-ttu-id="8a035-116">Vytvořte jednu třídu pro sadu souvisejících funkcí knihoven DLL pro vytváření logických seskupení a snížení režie.</span><span class="sxs-lookup"><span data-stu-id="8a035-116">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="8a035-117">Můžete pojmenovat třídu a její metody, které jste si zařadíte.</span><span class="sxs-lookup"><span data-stu-id="8a035-117">You can name the class and its methods as you please.</span></span> <span data-ttu-id="8a035-118">Příklady, které ukazují, jak vytvořit. Deklarace založené na síti, které se mají použít s voláním platformy, najdete v tématu [zařazování dat pomocí vyvolání platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="8a035-118">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a035-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a035-119">See also</span></span>

- [<span data-ttu-id="8a035-120">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="8a035-120">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="8a035-121">Identifikace funkcí ve knihovnách DLL</span><span class="sxs-lookup"><span data-stu-id="8a035-121">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="8a035-122">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="8a035-122">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="8a035-123">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="8a035-123">Calling a DLL Function</span></span>](calling-a-dll-function.md)
