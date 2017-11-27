---
title: "Používání nespravovaných funkcí DLL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec93728566d6aa16d4b9b15b171d79831cc0dbeb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="119c8-102">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="119c8-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="119c8-103">Vyvolání platformy je služba, což umožňuje spravovat kódu volání nespravovaných funkcí, které jsou implementované v dynamické knihovny (DLL), například v rozhraní API Win32.</span><span class="sxs-lookup"><span data-stu-id="119c8-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Win32 API.</span></span> <span data-ttu-id="119c8-104">Vyhledá a vyvolá exportované funkce a zařazuje její argumenty (celá čísla, řetězce, pole, struktur a tak dále) přes součinnosti hranice, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="119c8-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span> <span data-ttu-id="119c8-105">Další informace o této službě najdete v tématu [A blíže podívejte se na vyvolání platformy](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243).</span><span class="sxs-lookup"><span data-stu-id="119c8-105">For more information about this service, see [A Closer Look at Platform Invoke](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243).</span></span>  
  
 <span data-ttu-id="119c8-106">Tato část obsahuje několik úloh, které jsou přidružené k využívání nespravovaných funkcí knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="119c8-106">This section introduces several tasks associated with consuming unmanaged DLL functions.</span></span> <span data-ttu-id="119c8-107">Kromě následující úlohy jsou obecné požadavky a poskytuje další informace a příklady odkaz.</span><span class="sxs-lookup"><span data-stu-id="119c8-107">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="119c8-108">Využívat exportované funkce DLL</span><span class="sxs-lookup"><span data-stu-id="119c8-108">To consume exported DLL functions</span></span>  
  
1.  <span data-ttu-id="119c8-109">[Identifikace funkcí ve knihovnách DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="119c8-109">[Identify functions in DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="119c8-110">Minimálně musíte zadat název funkce a název knihovny DLL, která ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="119c8-110">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2.  <span data-ttu-id="119c8-111">[Vytvoření třídy k umístění funkcí DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="119c8-111">[Create a class to hold DLL functions](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="119c8-112">Můžete použít existující třídy, vytvoření jednotlivých tříd pro jednotlivé nespravované funkce nebo vytvořte jednu třídu, která obsahuje sadu související nespravovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="119c8-112">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3.  <span data-ttu-id="119c8-113">[Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="119c8-113">[Create prototypes in managed code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="119c8-114">[Visual Basic] Použití **Declare** příkaz s **funkce** a **Lib** klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="119c8-114">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="119c8-115">Ve výjimečných případech, můžete použít **DllImportAttribute** s **sdílené funkce** klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="119c8-115">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="119c8-116">Těchto případech jsou vysvětleny později v této části.</span><span class="sxs-lookup"><span data-stu-id="119c8-116">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="119c8-117">[C#] Použití **DllImportAttribute** k identifikaci knihovny DLL a funkce.</span><span class="sxs-lookup"><span data-stu-id="119c8-117">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="119c8-118">Označit metodu s **statické** a **extern** modifikátory.</span><span class="sxs-lookup"><span data-stu-id="119c8-118">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="119c8-119">[C++] Použití **DllImportAttribute** k identifikaci knihovny DLL a funkce.</span><span class="sxs-lookup"><span data-stu-id="119c8-119">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="119c8-120">Označit obálku metody nebo funkce s **extern "C"**.</span><span class="sxs-lookup"><span data-stu-id="119c8-120">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4.  <span data-ttu-id="119c8-121">[Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="119c8-121">[Call a DLL function](../../../docs/framework/interop/calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="119c8-122">Volejte metodu v třídě spravované stejně jako jiné spravované metody.</span><span class="sxs-lookup"><span data-stu-id="119c8-122">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="119c8-123">[Předávání struktur](../../../docs/framework/interop/passing-structures.md) a [implementace funkce zpětného volání](../../../docs/framework/interop/callback-functions.md) jsou zvláštní případy.</span><span class="sxs-lookup"><span data-stu-id="119c8-123">[Passing structures](../../../docs/framework/interop/passing-structures.md) and [implementing callback functions](../../../docs/framework/interop/callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="119c8-124">Příklady, které ukazují, jak vytvořit. Na základě NET deklarace, který se má použít s platformou vyvolání najdete v tématu [zařazování dat s vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="119c8-124">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="119c8-125">Vyvolání bližší pohled na platformy</span><span class="sxs-lookup"><span data-stu-id="119c8-125">A closer look at platform invoke</span></span>  
 <span data-ttu-id="119c8-126">Vyvolání platformy spoléhá na metadata pro vyhledání exportovaných funkcí a jejich argumentů zařazování v době běhu.</span><span class="sxs-lookup"><span data-stu-id="119c8-126">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="119c8-127">Tento proces je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="119c8-127">The following illustration shows this process.</span></span>  
  
 <span data-ttu-id="119c8-128">![Vyvolání platformy](../../../docs/framework/interop/media/pinvoke.gif "pinvoke")</span><span class="sxs-lookup"><span data-stu-id="119c8-128">![Platform invoke](../../../docs/framework/interop/media/pinvoke.gif "pinvoke")</span></span>  
<span data-ttu-id="119c8-129">Nespravovaného volání nespravovaného funkce DLL</span><span class="sxs-lookup"><span data-stu-id="119c8-129">A platform invoke call to an unmanaged DLL function</span></span>  
  
 <span data-ttu-id="119c8-130">Při vyvolání platformy volání nespravované funkce, provede následující posloupnost akcí:</span><span class="sxs-lookup"><span data-stu-id="119c8-130">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1.  <span data-ttu-id="119c8-131">Vyhledá knihovnu DLL obsahující danou funkci.</span><span class="sxs-lookup"><span data-stu-id="119c8-131">Locates the DLL containing the function.</span></span>  
  
2.  <span data-ttu-id="119c8-132">Knihovnu DLL načte do paměti.</span><span class="sxs-lookup"><span data-stu-id="119c8-132">Loads the DLL into memory.</span></span>  
  
3.  <span data-ttu-id="119c8-133">Vyhledá adresu funkce v paměti a nabízených oznámení její argumenty do zásobníku, zařazování dat podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="119c8-133">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="119c8-134">Vyhledání a načtení knihovny DLL a adresu funkce vyhledávání v paměti se provádějí pouze při prvním volání funkce.</span><span class="sxs-lookup"><span data-stu-id="119c8-134">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4.  <span data-ttu-id="119c8-135">Ovládací prvek přenos nespravovaného funkce.</span><span class="sxs-lookup"><span data-stu-id="119c8-135">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="119c8-136">Vyvolání platformy generuje výjimky generované funkci nespravované na spravované volajícího.</span><span class="sxs-lookup"><span data-stu-id="119c8-136">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119c8-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="119c8-137">See Also</span></span>  
 [<span data-ttu-id="119c8-138">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="119c8-138">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="119c8-139">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="119c8-139">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="119c8-140">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="119c8-140">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 [<span data-ttu-id="119c8-141">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="119c8-141">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
