---
title: "Vytvoření třídy k umístění funkcí DLL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ac3c3542e46168f5903ff0425740a29f16253733
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="2f74d-102">Vytvoření třídy k umístění funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="2f74d-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="2f74d-103">Zabalení často používané funkce DLL v třídě spravované je efektivní přístup k zapouzdření funkce platformy.</span><span class="sxs-lookup"><span data-stu-id="2f74d-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="2f74d-104">Přestože není povinný Uděláte to tak v každém případě, za předpokladu, že třída obálky je vhodné, protože definice funkcí knihovny DLL může být pracné a k chybám.</span><span class="sxs-lookup"><span data-stu-id="2f74d-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="2f74d-105">Pokud programujete v jazyce Visual Basic nebo C#, je potřeba deklarovat funkcí knihovny DLL v rámci třídy nebo modulu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2f74d-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="2f74d-106">V rámci třídy zadejte statickou metodu pro každou funkci knihovny DLL, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="2f74d-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="2f74d-107">Definice může obsahovat další informace, jako je znaková sada nebo konvence volání, které jsou používány předání argumentů metoda; Díky vynechání tyto informace, vyberte výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="2f74d-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="2f74d-108">Úplný seznam možností deklarace a výchozí nastavení, najdete v části [vytváření prototypů ve spravovaného kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="2f74d-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="2f74d-109">Jakmile zabalená, jak můžete volat metody pro funkci volat metody pro jiné statické funkce.</span><span class="sxs-lookup"><span data-stu-id="2f74d-109">Once wrapped, you can call methods on the function as you call methods on any other static function.</span></span> <span data-ttu-id="2f74d-110">Vyvolání platformy zpracovává základní exportované funkce automaticky.</span><span class="sxs-lookup"><span data-stu-id="2f74d-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="2f74d-111">Při navrhování spravované třídy pro platformu vyvolání, zvažte vztahy mezi třídami a funkcí knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="2f74d-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="2f74d-112">Například můžete:</span><span class="sxs-lookup"><span data-stu-id="2f74d-112">For example, you can:</span></span>  
  
-   <span data-ttu-id="2f74d-113">Deklarace funkcí knihovny DLL v rámci existující třídy.</span><span class="sxs-lookup"><span data-stu-id="2f74d-113">Declare DLL functions within an existing class.</span></span>  
  
-   <span data-ttu-id="2f74d-114">Vytvořte jednotlivých tříd pro jednotlivé funkce DLL zachování funkce izolované a snadno najít.</span><span class="sxs-lookup"><span data-stu-id="2f74d-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
-   <span data-ttu-id="2f74d-115">Vytvořte jednu třídu pro sadu souvisejících funkcí knihovny DLL na formuláři logické seskupení a snížit režii.</span><span class="sxs-lookup"><span data-stu-id="2f74d-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="2f74d-116">Třída a její metody, jako je můžete prosím název.</span><span class="sxs-lookup"><span data-stu-id="2f74d-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="2f74d-117">Příklady, které ukazují, jak vytvořit. Na základě NET deklarace, který se má použít s platformou vyvolání najdete v tématu [zařazování dat s vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="2f74d-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f74d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f74d-118">See Also</span></span>  
 [<span data-ttu-id="2f74d-119">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="2f74d-119">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="2f74d-120">Identifikace funkcí ve knihovnách DLL</span><span class="sxs-lookup"><span data-stu-id="2f74d-120">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [<span data-ttu-id="2f74d-121">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="2f74d-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="2f74d-122">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="2f74d-122">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
