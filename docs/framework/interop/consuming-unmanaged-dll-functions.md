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
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="c795d-102">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="c795d-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="c795d-103">Vyvolání platformy je služba, která umožňuje spravovanému kódu volat nespravované funkce implementované v knihovně DLL (Dynamic Link Library), jako jsou ty v rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c795d-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="c795d-104">Vyhledá a vyvolá exportovanou funkci a zařadí argumenty (celá čísla, řetězce, pole, struktury atd.) v rámci hranice mezioperace podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="c795d-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="c795d-105">V této části jsou uvedeny úlohy spojené s používáním nespravovaných funkcí knihovny DLL a další informace o vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="c795d-105">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="c795d-106">Kromě následujících úkolů existují obecné požadavky a odkaz, který poskytuje další informace a příklady.</span><span class="sxs-lookup"><span data-stu-id="c795d-106">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="c795d-107">Využití exportovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="c795d-107">To consume exported DLL functions</span></span>  
  
1. <span data-ttu-id="c795d-108">[Identifikujte funkce v knihovnách DLL](identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="c795d-108">[Identify functions in DLLs](identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="c795d-109">Minimální je nutné zadat název funkce a název knihovny DLL, která ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="c795d-109">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2. <span data-ttu-id="c795d-110">[Vytvořte třídu pro uchovávání funkcí knihovny DLL](creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c795d-110">[Create a class to hold DLL functions](creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="c795d-111">Můžete použít existující třídu, vytvořit jednotlivou třídu pro každou nespravovanou funkci nebo vytvořit jednu třídu, která obsahuje sadu souvisejících nespravovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="c795d-111">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3. <span data-ttu-id="c795d-112">[Vytváření prototypů ve spravovaném kódu](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="c795d-112">[Create prototypes in managed code](creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="c795d-113">[Visual Basic] Použijte příkaz **Declare** s klíčovými slovy **Function** a **lib** .</span><span class="sxs-lookup"><span data-stu-id="c795d-113">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="c795d-114">V některých vzácných případech můžete použít **DllImportAttribute** pomocí klíčových slov **sdílených funkcí** .</span><span class="sxs-lookup"><span data-stu-id="c795d-114">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="c795d-115">Tyto případy jsou vysvětleny dále v této části.</span><span class="sxs-lookup"><span data-stu-id="c795d-115">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="c795d-116">Jazyk Použijte **DllImportAttribute** k identifikaci knihovny DLL a funkce.</span><span class="sxs-lookup"><span data-stu-id="c795d-116">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="c795d-117">Označte metodu **statickými** a **externými** modifikátory.</span><span class="sxs-lookup"><span data-stu-id="c795d-117">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="c795d-118">Volat Použijte **DllImportAttribute** k identifikaci knihovny DLL a funkce.</span><span class="sxs-lookup"><span data-stu-id="c795d-118">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="c795d-119">Označte obálkovou metodu nebo funkci s **extern "C"**.</span><span class="sxs-lookup"><span data-stu-id="c795d-119">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4. <span data-ttu-id="c795d-120">[Volání funkce knihovny DLL](calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="c795d-120">[Call a DLL function](calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="c795d-121">Volejte metodu na spravované třídě stejně jako jakoukoli jinou spravovanou metodu.</span><span class="sxs-lookup"><span data-stu-id="c795d-121">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="c795d-122">[Předání struktur](passing-structures.md) a [implementace funkcí zpětného volání](callback-functions.md) jsou zvláštní případy.</span><span class="sxs-lookup"><span data-stu-id="c795d-122">[Passing structures](passing-structures.md) and [implementing callback functions](callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="c795d-123">Příklady, které ukazují, jak vytvořit. Deklarace založené na síti, které se mají použít s voláním platformy, najdete v tématu [zařazování dat pomocí vyvolání platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="c795d-123">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="c795d-124">Bližší pohled na vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="c795d-124">A closer look at platform invoke</span></span>  
 <span data-ttu-id="c795d-125">Vyvolání platformy spoléhá na metadata pro vyhledání exportovaných funkcí a zařazování jejich argumentů za běhu.</span><span class="sxs-lookup"><span data-stu-id="c795d-125">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="c795d-126">Tento proces je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="c795d-126">The following illustration shows this process.</span></span>  
  
 ![Diagram, který zobrazuje volání vyvolání platformy.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="c795d-128">Když vyvolání platformy volá nespravovanou funkci, provede následující posloupnost akcí:</span><span class="sxs-lookup"><span data-stu-id="c795d-128">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1. <span data-ttu-id="c795d-129">Vyhledá knihovnu DLL obsahující funkci.</span><span class="sxs-lookup"><span data-stu-id="c795d-129">Locates the DLL containing the function.</span></span>  
  
2. <span data-ttu-id="c795d-130">Načte knihovnu DLL do paměti.</span><span class="sxs-lookup"><span data-stu-id="c795d-130">Loads the DLL into memory.</span></span>  
  
3. <span data-ttu-id="c795d-131">Vyhledá adresu funkce v paměti a vloží její argumenty do zásobníku, zařazování dat podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="c795d-131">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c795d-132">Vyhledání a načtení knihovny DLL a vyhledání adresy funkce v paměti dochází pouze při prvním volání funkce.</span><span class="sxs-lookup"><span data-stu-id="c795d-132">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4. <span data-ttu-id="c795d-133">Přenáší řízení na nespravovanou funkci.</span><span class="sxs-lookup"><span data-stu-id="c795d-133">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="c795d-134">Vyvolání platformy vyvolá výjimku vygenerovanou nespravovanou funkcí spravovanému volajícímu.</span><span class="sxs-lookup"><span data-stu-id="c795d-134">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="c795d-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="c795d-135">See also</span></span>

- [<span data-ttu-id="c795d-136">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="c795d-136">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="c795d-137">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="c795d-137">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="c795d-138">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="c795d-138">Interop Marshaling</span></span>](interop-marshaling.md)
