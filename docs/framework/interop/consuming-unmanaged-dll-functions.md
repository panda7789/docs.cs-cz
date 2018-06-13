---
title: Používání nespravovaných funkcí DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- platform invoke, about platform invoke
- DLL functions, consuming unmanaged
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke
- DLL functions
ms.assetid: eca7606e-ebfb-4f47-b8d9-289903fdc045
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3166d6c95532706781188da0c56ebf9022038a50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388375"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="0c5fe-102">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="0c5fe-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="0c5fe-103">Vyvolání platformy je služba, což umožňuje spravovat kódu volání nespravovaných funkcí, které jsou implementované v dynamické knihovny (DLL), například v rozhraní API Win32.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Win32 API.</span></span> <span data-ttu-id="0c5fe-104">Vyhledá a vyvolá exportované funkce a zařazuje její argumenty (celá čísla, řetězce, pole, struktur a tak dále) přes součinnosti hranice, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="0c5fe-105">Tato část uvádí úkoly spojené s využívání nespravovaných funkcí DLL a poskytuje další informace o platformě vyvolání.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-105">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="0c5fe-106">Kromě následující úlohy jsou obecné požadavky a poskytuje další informace a příklady odkaz.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-106">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="0c5fe-107">Využívat exportované funkce DLL</span><span class="sxs-lookup"><span data-stu-id="0c5fe-107">To consume exported DLL functions</span></span>  
  
1.  <span data-ttu-id="0c5fe-108">[Identifikace funkcí ve knihovnách DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="0c5fe-108">[Identify functions in DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="0c5fe-109">Minimálně musíte zadat název funkce a název knihovny DLL, která ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-109">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2.  <span data-ttu-id="0c5fe-110">[Vytvoření třídy k umístění funkcí DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0c5fe-110">[Create a class to hold DLL functions](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="0c5fe-111">Můžete použít existující třídy, vytvoření jednotlivých tříd pro jednotlivé nespravované funkce nebo vytvořte jednu třídu, která obsahuje sadu související nespravovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-111">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3.  <span data-ttu-id="0c5fe-112">[Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="0c5fe-112">[Create prototypes in managed code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="0c5fe-113">[Visual Basic] Použití **Declare** příkaz s **funkce** a **Lib** klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-113">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="0c5fe-114">Ve výjimečných případech, můžete použít **DllImportAttribute** s **sdílené funkce** klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-114">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="0c5fe-115">Těchto případech jsou vysvětleny později v této části.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-115">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="0c5fe-116">[C#] Použití **DllImportAttribute** k identifikaci knihovny DLL a funkce.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-116">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="0c5fe-117">Označit metodu s **statické** a **extern** modifikátory.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-117">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="0c5fe-118">[C++] Použití **DllImportAttribute** k identifikaci knihovny DLL a funkce.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-118">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="0c5fe-119">Označit obálku metody nebo funkce s **extern "C"**.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-119">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4.  <span data-ttu-id="0c5fe-120">[Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="0c5fe-120">[Call a DLL function](../../../docs/framework/interop/calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="0c5fe-121">Volejte metodu v třídě spravované stejně jako jiné spravované metody.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-121">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="0c5fe-122">[Předávání struktur](../../../docs/framework/interop/passing-structures.md) a [implementace funkce zpětného volání](../../../docs/framework/interop/callback-functions.md) jsou zvláštní případy.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-122">[Passing structures](../../../docs/framework/interop/passing-structures.md) and [implementing callback functions](../../../docs/framework/interop/callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="0c5fe-123">Příklady, které ukazují, jak vytvořit. Na základě NET deklarace, který se má použít s platformou vyvolání najdete v tématu [zařazování dat s vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="0c5fe-123">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="0c5fe-124">Vyvolání bližší pohled na platformy</span><span class="sxs-lookup"><span data-stu-id="0c5fe-124">A closer look at platform invoke</span></span>  
 <span data-ttu-id="0c5fe-125">Vyvolání platformy spoléhá na metadata pro vyhledání exportovaných funkcí a jejich argumentů zařazování v době běhu.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-125">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="0c5fe-126">Tento proces je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-126">The following illustration shows this process.</span></span>  
  
 <span data-ttu-id="0c5fe-127">![Vyvolání platformy](../../../docs/framework/interop/media/pinvoke.gif "pinvoke")</span><span class="sxs-lookup"><span data-stu-id="0c5fe-127">![Platform invoke](../../../docs/framework/interop/media/pinvoke.gif "pinvoke")</span></span>  
<span data-ttu-id="0c5fe-128">Nespravovaného volání nespravovaného funkce DLL</span><span class="sxs-lookup"><span data-stu-id="0c5fe-128">A platform invoke call to an unmanaged DLL function</span></span>  
  
 <span data-ttu-id="0c5fe-129">Při vyvolání platformy volání nespravované funkce, provede následující posloupnost akcí:</span><span class="sxs-lookup"><span data-stu-id="0c5fe-129">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1.  <span data-ttu-id="0c5fe-130">Vyhledá knihovnu DLL obsahující danou funkci.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-130">Locates the DLL containing the function.</span></span>  
  
2.  <span data-ttu-id="0c5fe-131">Knihovnu DLL načte do paměti.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-131">Loads the DLL into memory.</span></span>  
  
3.  <span data-ttu-id="0c5fe-132">Vyhledá adresu funkce v paměti a nabízených oznámení její argumenty do zásobníku, zařazování dat podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-132">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c5fe-133">Vyhledání a načtení knihovny DLL a adresu funkce vyhledávání v paměti se provádějí pouze při prvním volání funkce.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-133">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4.  <span data-ttu-id="0c5fe-134">Ovládací prvek přenos nespravovaného funkce.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-134">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="0c5fe-135">Vyvolání platformy generuje výjimky generované funkci nespravované na spravované volajícího.</span><span class="sxs-lookup"><span data-stu-id="0c5fe-135">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c5fe-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c5fe-136">See Also</span></span>  
 [<span data-ttu-id="0c5fe-137">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="0c5fe-137">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="0c5fe-138">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="0c5fe-138">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="0c5fe-139">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="0c5fe-139">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
