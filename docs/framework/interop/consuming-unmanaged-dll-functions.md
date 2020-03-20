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
ms.openlocfilehash: 7ec1f129dcc19300dd5a4e7c5e627d9e0edf29a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399971"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="d60ae-102">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="d60ae-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="d60ae-103">Vyvolání platformy je služba, která umožňuje spravovanému kódu volat nespravované funkce implementované v knihovnách dynamických odkazů (DLL), jako jsou ty v rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d60ae-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="d60ae-104">Vyhledá a vyvolá exportovanou funkci a zařazuje její argumenty (celá čísla, řetězce, pole, struktury a tak dále) přes hranice vzájemné spolupráce podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="d60ae-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="d60ae-105">Tato část zavádí úkoly spojené s využíváním nespravovaných funkcí dll a poskytuje další informace o vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="d60ae-105">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="d60ae-106">Kromě následujících úkolů existují obecné aspekty a odkaz poskytující další informace a příklady.</span><span class="sxs-lookup"><span data-stu-id="d60ae-106">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="d60ae-107">Využití exportovaných funkcí dll</span><span class="sxs-lookup"><span data-stu-id="d60ae-107">To consume exported DLL functions</span></span>  
  
1. <span data-ttu-id="d60ae-108">[Identifikujte funkce v knihovnách DLL](identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="d60ae-108">[Identify functions in DLLs](identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="d60ae-109">Minimálně je nutné zadat název funkce a název dll, která ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="d60ae-109">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2. <span data-ttu-id="d60ae-110">[Vytvořte třídu pro funkce dll](creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d60ae-110">[Create a class to hold DLL functions](creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="d60ae-111">Můžete použít existující třídu, vytvořit jednotlivé třídy pro každou nespravovanou funkci nebo vytvořit jednu třídu, která obsahuje sadu souvisejících nespravovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="d60ae-111">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3. <span data-ttu-id="d60ae-112">[Vytvořte prototypy ve spravovaném kódu](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="d60ae-112">[Create prototypes in managed code](creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="d60ae-113">[Visual Basic] Použijte **declare** prohlášení s **funkce** a **Lib** klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="d60ae-113">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="d60ae-114">V některých výjimečných případech můžete použít **DllImportAttribute** s klíčová slova **sdílené funkce.**</span><span class="sxs-lookup"><span data-stu-id="d60ae-114">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="d60ae-115">Tyto případy jsou vysvětleny dále v této části.</span><span class="sxs-lookup"><span data-stu-id="d60ae-115">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="d60ae-116">[C#] Pomocí **atributu DllImportAttribute** můžete identifikovat knihovnu DLL a funkci.</span><span class="sxs-lookup"><span data-stu-id="d60ae-116">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="d60ae-117">Označte metodu **statickými** a **extern** modifikátory.</span><span class="sxs-lookup"><span data-stu-id="d60ae-117">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="d60ae-118">[C++] Pomocí **atributu DllImportAttribute** můžete identifikovat knihovnu DLL a funkci.</span><span class="sxs-lookup"><span data-stu-id="d60ae-118">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="d60ae-119">Označte metodu obálky nebo funkci **extern "C"**.</span><span class="sxs-lookup"><span data-stu-id="d60ae-119">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4. <span data-ttu-id="d60ae-120">[Volání funkce DLL](calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="d60ae-120">[Call a DLL function](calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="d60ae-121">Volání metody na spravované třídy, stejně jako jakékoli jiné spravované metody.</span><span class="sxs-lookup"><span data-stu-id="d60ae-121">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="d60ae-122">[Předávání struktury](passing-structures.md) a [provádění funkcí zpětného volání](callback-functions.md) jsou zvláštní případy.</span><span class="sxs-lookup"><span data-stu-id="d60ae-122">[Passing structures](passing-structures.md) and [implementing callback functions](callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="d60ae-123">Příklady, které ukazují, jak vytvořit . NET založené deklarace, které mají být použity s platformy vyvolat, naleznete v [tématu zařazování dat s platformy invoke](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="d60ae-123">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="d60ae-124">Bližší pohled na vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="d60ae-124">A closer look at platform invoke</span></span>  
 <span data-ttu-id="d60ae-125">Platforma vyvolání spoléhá na metadata vyhledejte exportované funkce a zařazování jejich argumenty za běhu.</span><span class="sxs-lookup"><span data-stu-id="d60ae-125">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="d60ae-126">Tento proces je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="d60ae-126">The following illustration shows this process.</span></span>  
  
 ![Diagram, který znázorňuje volání platformy vyvolat.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="d60ae-128">Když platforma vyvolá volání nespravované funkce, provede následující posloupnost akcí:</span><span class="sxs-lookup"><span data-stu-id="d60ae-128">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1. <span data-ttu-id="d60ae-129">Vyhledá dll obsahující funkci.</span><span class="sxs-lookup"><span data-stu-id="d60ae-129">Locates the DLL containing the function.</span></span>  
  
2. <span data-ttu-id="d60ae-130">Načte dll do paměti.</span><span class="sxs-lookup"><span data-stu-id="d60ae-130">Loads the DLL into memory.</span></span>  
  
3. <span data-ttu-id="d60ae-131">Vyhledá adresu funkce v paměti a odešle své argumenty do zásobníku, zařazování dat podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="d60ae-131">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d60ae-132">Vyhledání a načtení dll a umístění adresy funkce v paměti dojít pouze při prvním volání funkce.</span><span class="sxs-lookup"><span data-stu-id="d60ae-132">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4. <span data-ttu-id="d60ae-133">Přenese řízení na nespravovanou funkci.</span><span class="sxs-lookup"><span data-stu-id="d60ae-133">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="d60ae-134">Vyvolání platformy vyvolá výjimky generované nespravovanou funkcí spravovanému volajícímu.</span><span class="sxs-lookup"><span data-stu-id="d60ae-134">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="d60ae-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="d60ae-135">See also</span></span>

- [<span data-ttu-id="d60ae-136">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="d60ae-136">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="d60ae-137">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="d60ae-137">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="d60ae-138">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="d60ae-138">Interop Marshaling</span></span>](interop-marshaling.md)
