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
ms.openlocfilehash: 9e9308d6bf0eefaa60af17a721cd1c26827469eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946847"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="59e01-102">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="59e01-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="59e01-103">Vyvolání platformy je služba, která umožňuje spravovanému kódu volat nespravované funkce implementované v knihovně DLL (Dynamic Link Library), jako jsou ty v rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="59e01-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="59e01-104">Vyhledá a vyvolá exportovanou funkci a zařadí argumenty (celá čísla, řetězce, pole, struktury atd.) v rámci hranice mezioperace podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="59e01-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="59e01-105">V této části jsou uvedeny úlohy spojené s používáním nespravovaných funkcí knihovny DLL a další informace o vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="59e01-105">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="59e01-106">Kromě následujících úkolů existují obecné požadavky a odkaz, který poskytuje další informace a příklady.</span><span class="sxs-lookup"><span data-stu-id="59e01-106">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="59e01-107">Využití exportovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="59e01-107">To consume exported DLL functions</span></span>  
  
1. <span data-ttu-id="59e01-108">[Identifikujte funkce v knihovnách DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="59e01-108">[Identify functions in DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="59e01-109">Minimální je nutné zadat název funkce a název knihovny DLL, která ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="59e01-109">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2. <span data-ttu-id="59e01-110">[Vytvořte třídu pro uchovávání funkcí knihovny DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="59e01-110">[Create a class to hold DLL functions](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="59e01-111">Můžete použít existující třídu, vytvořit jednotlivou třídu pro každou nespravovanou funkci nebo vytvořit jednu třídu, která obsahuje sadu souvisejících nespravovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="59e01-111">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3. <span data-ttu-id="59e01-112">[Vytváření prototypů ve spravovaném kódu](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="59e01-112">[Create prototypes in managed code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="59e01-113">[Visual Basic] Použijte příkaz **Declare** s klíčovými slovy **Function** a **lib** .</span><span class="sxs-lookup"><span data-stu-id="59e01-113">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="59e01-114">V některých vzácných případech můžete použít **DllImportAttribute** pomocí klíčových slov **sdílených funkcí** .</span><span class="sxs-lookup"><span data-stu-id="59e01-114">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="59e01-115">Tyto případy jsou vysvětleny dále v této části.</span><span class="sxs-lookup"><span data-stu-id="59e01-115">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="59e01-116">[C#] Použijte **DllImportAttribute** k identifikaci knihovny DLL a funkce.</span><span class="sxs-lookup"><span data-stu-id="59e01-116">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="59e01-117">Označte metodu statickými a externými modifikátory.</span><span class="sxs-lookup"><span data-stu-id="59e01-117">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="59e01-118">[C++] Použijte **DllImportAttribute** k identifikaci knihovny DLL a funkce.</span><span class="sxs-lookup"><span data-stu-id="59e01-118">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="59e01-119">Označte obálkovou metodu nebo funkci s **extern "C"** .</span><span class="sxs-lookup"><span data-stu-id="59e01-119">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4. <span data-ttu-id="59e01-120">[Volání funkce knihovny DLL](../../../docs/framework/interop/calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="59e01-120">[Call a DLL function](../../../docs/framework/interop/calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="59e01-121">Volejte metodu na spravované třídě stejně jako jakoukoli jinou spravovanou metodu.</span><span class="sxs-lookup"><span data-stu-id="59e01-121">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="59e01-122">[Předání struktur](../../../docs/framework/interop/passing-structures.md) a [implementace funkcí zpětného volání](../../../docs/framework/interop/callback-functions.md) jsou zvláštní případy.</span><span class="sxs-lookup"><span data-stu-id="59e01-122">[Passing structures](../../../docs/framework/interop/passing-structures.md) and [implementing callback functions](../../../docs/framework/interop/callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="59e01-123">Příklady, které ukazují, jak vytvořit. Deklarace založené na síti, které se mají použít s voláním platformy, najdete v tématu [zařazování dat pomocí vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="59e01-123">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="59e01-124">Bližší pohled na vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="59e01-124">A closer look at platform invoke</span></span>  
 <span data-ttu-id="59e01-125">Vyvolání platformy spoléhá na metadata pro vyhledání exportovaných funkcí a zařazování jejich argumentů za běhu.</span><span class="sxs-lookup"><span data-stu-id="59e01-125">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="59e01-126">Tento proces je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="59e01-126">The following illustration shows this process.</span></span>  
  
 ![Diagram, který zobrazuje volání vyvolání platformy.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="59e01-128">Když vyvolání platformy volá nespravovanou funkci, provede následující posloupnost akcí:</span><span class="sxs-lookup"><span data-stu-id="59e01-128">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1. <span data-ttu-id="59e01-129">Vyhledá knihovnu DLL obsahující funkci.</span><span class="sxs-lookup"><span data-stu-id="59e01-129">Locates the DLL containing the function.</span></span>  
  
2. <span data-ttu-id="59e01-130">Načte knihovnu DLL do paměti.</span><span class="sxs-lookup"><span data-stu-id="59e01-130">Loads the DLL into memory.</span></span>  
  
3. <span data-ttu-id="59e01-131">Vyhledá adresu funkce v paměti a vloží její argumenty do zásobníku, zařazování dat podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="59e01-131">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="59e01-132">Vyhledání a načtení knihovny DLL a vyhledání adresy funkce v paměti dochází pouze při prvním volání funkce.</span><span class="sxs-lookup"><span data-stu-id="59e01-132">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4. <span data-ttu-id="59e01-133">Přenáší řízení na nespravovanou funkci.</span><span class="sxs-lookup"><span data-stu-id="59e01-133">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="59e01-134">Vyvolání platformy vyvolá výjimku vygenerovanou nespravovanou funkcí spravovanému volajícímu.</span><span class="sxs-lookup"><span data-stu-id="59e01-134">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="59e01-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59e01-135">See also</span></span>

- [<span data-ttu-id="59e01-136">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="59e01-136">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="59e01-137">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="59e01-137">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="59e01-138">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="59e01-138">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
