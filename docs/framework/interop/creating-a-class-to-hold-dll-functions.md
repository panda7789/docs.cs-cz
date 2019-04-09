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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 399ad6649016e53d91d5d9d30ecc031ae8a97a4a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149354"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="f1d81-102">Vytvoření třídy k umístění funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="f1d81-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="f1d81-103">Obtékání často používané funkce knihovny DLL ve spravované třídě je efektivního přístupu k zapouzdření funkce platformy.</span><span class="sxs-lookup"><span data-stu-id="f1d81-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="f1d81-104">Ačkoli to není nutné provést ve všech případech, za předpokladu, že třída obálky je pohodlné, protože definice funkcí knihovny DLL může být náročné a náchylné k chybě.</span><span class="sxs-lookup"><span data-stu-id="f1d81-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="f1d81-105">Pokud programujete v jazyce Visual Basic nebo C#, je třeba deklarovat funkce knihovny DLL v rámci třídy nebo modulu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f1d81-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="f1d81-106">V rámci třídy můžete definovat statické metody pro každou funkci knihovny DLL, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="f1d81-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="f1d81-107">Definice může obsahovat další informace, jako je znaková sada nebo použití předání argumentů metody; konvence volání vynecháním tyto informace, vyberte výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="f1d81-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="f1d81-108">Úplný seznam možností deklarace a výchozí nastavení, najdete v části [vytváření prototypů ve spravovaného kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="f1d81-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="f1d81-109">Jakmile zabalená, můžete volat metody ve třídě jako volání statické metody na jinou třídu.</span><span class="sxs-lookup"><span data-stu-id="f1d81-109">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="f1d81-110">Vyvolání platformy zpracovává základní exportované funkce automaticky.</span><span class="sxs-lookup"><span data-stu-id="f1d81-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="f1d81-111">Při navrhování spravovanou třídu pro platformu vyvolání, vezměte v úvahu vztahy mezi třídami a funkcí knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="f1d81-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="f1d81-112">Například můžete:</span><span class="sxs-lookup"><span data-stu-id="f1d81-112">For example, you can:</span></span>  
  
-   <span data-ttu-id="f1d81-113">Deklarování funkcí knihovny DLL v rámci existující třídy.</span><span class="sxs-lookup"><span data-stu-id="f1d81-113">Declare DLL functions within an existing class.</span></span>  
  
-   <span data-ttu-id="f1d81-114">Vytvoření jednotlivých tříd pro každou funkci knihovny DLL, udržování funkce izolované a snadno najít.</span><span class="sxs-lookup"><span data-stu-id="f1d81-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
-   <span data-ttu-id="f1d81-115">Vytvořte jednu třídu sady souvisejících funkcí knihovny DLL tvoří logické seskupení a snížit režii.</span><span class="sxs-lookup"><span data-stu-id="f1d81-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="f1d81-116">Název třídy a můžete její metody, jako je prosím.</span><span class="sxs-lookup"><span data-stu-id="f1d81-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="f1d81-117">Příklady, které ukazují, jak vytvořit. Na základě NET deklarace pro použití s platformu vyvolání, naleznete v tématu [zařazování dat pomocí vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="f1d81-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d81-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1d81-118">See also</span></span>

- [<span data-ttu-id="f1d81-119">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="f1d81-119">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="f1d81-120">Identifikace funkcí ve knihovnách DLL</span><span class="sxs-lookup"><span data-stu-id="f1d81-120">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)
- [<span data-ttu-id="f1d81-121">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="f1d81-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="f1d81-122">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="f1d81-122">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
