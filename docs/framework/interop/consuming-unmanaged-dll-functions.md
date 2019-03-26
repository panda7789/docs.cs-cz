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
ms.openlocfilehash: 50bfcf5c27236ca704a24f49128becfbee716c21
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463082"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="f2eef-102">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="f2eef-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="f2eef-103">Vyvolání platformy je služba, umožňuje spravovaným kódu volat nespravované funkce implementované v dynamické knihovny (DLL), jako jsou ty v rozhraní Windows API.</span><span class="sxs-lookup"><span data-stu-id="f2eef-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="f2eef-104">Vyhledá a volá exportované funkce a zařadí argumenty (celá čísla, řetězce, pole, struktury a tak dále) napříč hranicemi podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="f2eef-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="f2eef-105">Tato část představuje úloh přidružených k používání nespravovaných funkcí DLL a poskytuje další informace o platformě vyvolat.</span><span class="sxs-lookup"><span data-stu-id="f2eef-105">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="f2eef-106">Kromě následujících úloh jsou obecné požadavky a odkaz Další informace a příklady.</span><span class="sxs-lookup"><span data-stu-id="f2eef-106">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="f2eef-107">Chcete-li využívají exportované funkce DLL</span><span class="sxs-lookup"><span data-stu-id="f2eef-107">To consume exported DLL functions</span></span>  
  
1.  <span data-ttu-id="f2eef-108">[Identifikace funkcí ve knihovnách DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="f2eef-108">[Identify functions in DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="f2eef-109">Minimálně musíte zadat název funkce a název knihovny DLL, která ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="f2eef-109">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2.  <span data-ttu-id="f2eef-110">[Vytvoření třídy k umístění funkcí DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f2eef-110">[Create a class to hold DLL functions](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="f2eef-111">Můžete použít existující třídu, vytvoření jednotlivých tříd pro každou nespravovanou funkci nebo vytvořit jednu třídu, která obsahuje sadu souvisejících nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="f2eef-111">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3.  <span data-ttu-id="f2eef-112">[Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="f2eef-112">[Create prototypes in managed code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="f2eef-113">[Visual Basic] Použití **Declare** příkaz **funkce** a **Lib** klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="f2eef-113">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="f2eef-114">Ve výjimečných případech, můžete použít **DllImportAttribute** s **sdílené funkce** klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="f2eef-114">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="f2eef-115">Tyto případy jsou vysvětleny dále v této části.</span><span class="sxs-lookup"><span data-stu-id="f2eef-115">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="f2eef-116">[C#] Použití **DllImportAttribute** k identifikaci knihovny DLL a funkce.</span><span class="sxs-lookup"><span data-stu-id="f2eef-116">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="f2eef-117">Označení metody **statické** a **extern** modifikátory.</span><span class="sxs-lookup"><span data-stu-id="f2eef-117">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="f2eef-118">[C++] Použití **DllImportAttribute** k identifikaci knihovny DLL a funkce.</span><span class="sxs-lookup"><span data-stu-id="f2eef-118">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="f2eef-119">Označit obalující metodu nebo s funkcí **extern "C"**.</span><span class="sxs-lookup"><span data-stu-id="f2eef-119">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4.  <span data-ttu-id="f2eef-120">[Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="f2eef-120">[Call a DLL function](../../../docs/framework/interop/calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="f2eef-121">Volejte metodu na spravovanou třídu, stejně jako jiné spravované metody.</span><span class="sxs-lookup"><span data-stu-id="f2eef-121">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="f2eef-122">[Předávání struktur](../../../docs/framework/interop/passing-structures.md) a [implementace funkcí zpětného volání](../../../docs/framework/interop/callback-functions.md) jsou zvláštní případy.</span><span class="sxs-lookup"><span data-stu-id="f2eef-122">[Passing structures](../../../docs/framework/interop/passing-structures.md) and [implementing callback functions](../../../docs/framework/interop/callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="f2eef-123">Příklady, které ukazují, jak vytvořit. Na základě NET deklarace pro použití s platformu vyvolání, naleznete v tématu [zařazování dat pomocí vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="f2eef-123">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="f2eef-124">Bližší pohled na vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="f2eef-124">A closer look at platform invoke</span></span>  
 <span data-ttu-id="f2eef-125">Vyvolání platformy spoléhá na metadata k vyhledání exportovaných funkcí a jejich argumenty zařazování v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f2eef-125">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="f2eef-126">Tento proces je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="f2eef-126">The following illustration shows this process.</span></span>  
  
 ![Diagram zobrazující platformu vyvolání volání.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="f2eef-128">Při vyvolání platformy volá nespravovaná funkce provádí následující posloupnost akcí:</span><span class="sxs-lookup"><span data-stu-id="f2eef-128">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1.  <span data-ttu-id="f2eef-129">Vyhledá knihovny DLL obsahující tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="f2eef-129">Locates the DLL containing the function.</span></span>  
  
2.  <span data-ttu-id="f2eef-130">Knihovnu DLL načte do paměti.</span><span class="sxs-lookup"><span data-stu-id="f2eef-130">Loads the DLL into memory.</span></span>  
  
3.  <span data-ttu-id="f2eef-131">Vyhledá adresu funkce v paměti a nabízených oznámení do zásobníku, zařazování dat podle potřeby svých argumentů.</span><span class="sxs-lookup"><span data-stu-id="f2eef-131">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2eef-132">Vyhledání a načtení knihovny DLL a adresu funkce vyhledávání v paměti dojít pouze při prvním volání funkce.</span><span class="sxs-lookup"><span data-stu-id="f2eef-132">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4.  <span data-ttu-id="f2eef-133">Přenosy ovládacího prvku nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="f2eef-133">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="f2eef-134">Vyvolání platformy vyvolá výjimky generované nespravovanou funkci spravované volajícímu.</span><span class="sxs-lookup"><span data-stu-id="f2eef-134">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2eef-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2eef-135">See also</span></span>
- [<span data-ttu-id="f2eef-136">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="f2eef-136">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="f2eef-137">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="f2eef-137">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="f2eef-138">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="f2eef-138">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
