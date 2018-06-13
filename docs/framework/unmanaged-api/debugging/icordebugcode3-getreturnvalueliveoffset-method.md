---
title: ICorDebugCode3::GetReturnValueLiveOffset – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c75db784a404298b86ed42692573a509ea56cf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415526"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="b2d76-102">ICorDebugCode3::GetReturnValueLiveOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="b2d76-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="b2d76-103">Pro zadaný korekce IL získá nativní posuny, kde má být umístěn zarážku tak, aby ladicí program můžete získat návratovou hodnotou z funkce.</span><span class="sxs-lookup"><span data-stu-id="b2d76-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2d76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2d76-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2d76-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2d76-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="b2d76-106">Korekce IL.</span><span class="sxs-lookup"><span data-stu-id="b2d76-106">The IL offset.</span></span> <span data-ttu-id="b2d76-107">Musí být funkce lokality volání nebo volání funkce se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="b2d76-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="b2d76-108">Počet bajtů, které jsou k dispozici pro uložení `pOffsets`.</span><span class="sxs-lookup"><span data-stu-id="b2d76-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="b2d76-109">Ukazatel na počet posuny ve skutečnosti vrátila.</span><span class="sxs-lookup"><span data-stu-id="b2d76-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="b2d76-110">Obvykle jeho hodnota je 1, ale jeden instrukce IL je možné namapovat více `CALL` pokyny sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2d76-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="b2d76-111">Pole nativní odsazení.</span><span class="sxs-lookup"><span data-stu-id="b2d76-111">An array of native offsets.</span></span> <span data-ttu-id="b2d76-112">Obvykle `pOffsets` obsahuje jeden posun, i když jako jedinou instrukci IL je možné namapovat více mapy do několika `CALL` pokyny sestavení.</span><span class="sxs-lookup"><span data-stu-id="b2d76-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2d76-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2d76-113">Remarks</span></span>  
 <span data-ttu-id="b2d76-114">Tato metoda se používá spolu s [icordebugilframe3::getreturnvalueforiloffset –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metoda získat návratovou hodnotu metody, která vrátí hodnotu typu odkaz.</span><span class="sxs-lookup"><span data-stu-id="b2d76-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="b2d76-115">Předávání IL posun do lokality volání funkce tato metoda vrátí jeden nebo více nativní posun.</span><span class="sxs-lookup"><span data-stu-id="b2d76-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="b2d76-116">Ladicí program pak můžete nastavit zarážky na tyto nativní posuny ve funkci.</span><span class="sxs-lookup"><span data-stu-id="b2d76-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="b2d76-117">Pokud se ladicí program dotkne některé zarážce, potom můžete předat stejnou korekce IL, který je předán tuto metodu za účelem [icordebugilframe3::getreturnvalueforiloffset –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metoda získat návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b2d76-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="b2d76-118">Ladicí program by měl zrušte zaškrtnutí všech zarážek, které ji nastavit.</span><span class="sxs-lookup"><span data-stu-id="b2d76-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b2d76-119">`ICorDebugCode3::GetReturnValueLiveOffset` a [icordebugilframe3::getreturnvalueforiloffset –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metody vám umožňují získat informace o návratovou hodnotu pro odkazové typy pouze.</span><span class="sxs-lookup"><span data-stu-id="b2d76-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="b2d76-120">Získávání informací o návratová hodnota z typů hodnot (to znamená, že všechny typy, které jsou odvozeny od <xref:System.ValueType>) není podporován.</span><span class="sxs-lookup"><span data-stu-id="b2d76-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="b2d76-121">Funkce vrátí hodnotu `HRESULT` hodnoty zobrazené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b2d76-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="b2d76-122">`HRESULT` Hodnota</span><span class="sxs-lookup"><span data-stu-id="b2d76-122">`HRESULT` value</span></span>|<span data-ttu-id="b2d76-123">Popis</span><span class="sxs-lookup"><span data-stu-id="b2d76-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="b2d76-124">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="b2d76-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="b2d76-125">Daný server posunutí IL není volání pokyn nebo funkce vrátí hodnotu `void`.</span><span class="sxs-lookup"><span data-stu-id="b2d76-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="b2d76-126">Daný korekce IL je správné volání, ale návratový typ není podporován pro získání návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b2d76-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="b2d76-127">`ICorDebugCode3::GetReturnValueLiveOffset` Metoda je k dispozici pouze na základě x86 a AMD64 systémy.</span><span class="sxs-lookup"><span data-stu-id="b2d76-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2d76-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2d76-128">Requirements</span></span>  
 <span data-ttu-id="b2d76-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2d76-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2d76-130">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2d76-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2d76-131">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2d76-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2d76-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2d76-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d76-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2d76-133">See Also</span></span>  
 [<span data-ttu-id="b2d76-134">GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="b2d76-134">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)  
 [<span data-ttu-id="b2d76-135">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2d76-135">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
