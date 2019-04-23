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
ms.openlocfilehash: 03ee275336d3ae71f63d82add694fe1308efbe8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125929"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="4a99d-102">ICorDebugCode3::GetReturnValueLiveOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="4a99d-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="4a99d-103">Pro zadaný posun IL získá nativní posuny, kde by měl být zarážku umístěn tak, aby ladicí program můžete získat návratová hodnota z funkce.</span><span class="sxs-lookup"><span data-stu-id="4a99d-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a99d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a99d-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a99d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a99d-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="4a99d-106">Posun IL.</span><span class="sxs-lookup"><span data-stu-id="4a99d-106">The IL offset.</span></span> <span data-ttu-id="4a99d-107">Musí to být web pro volání funkce nebo volání funkce se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="4a99d-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="4a99d-108">Počet bajtů dostupných k uložení `pOffsets`.</span><span class="sxs-lookup"><span data-stu-id="4a99d-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="4a99d-109">Ukazatel na počet skutečně vrácených posunů.</span><span class="sxs-lookup"><span data-stu-id="4a99d-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="4a99d-110">Obvykle je jeho hodnota 1, ale jediná instrukce IL může mapovat na více `CALL` pokyny k sestavení.</span><span class="sxs-lookup"><span data-stu-id="4a99d-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="4a99d-111">Pole nativních posunů.</span><span class="sxs-lookup"><span data-stu-id="4a99d-111">An array of native offsets.</span></span> <span data-ttu-id="4a99d-112">Obvykle `pOffsets` obsahuje jediný posun, i když se jediná instrukce IL může mapovat na více k několika `CALL` pokyny k sestavení.</span><span class="sxs-lookup"><span data-stu-id="4a99d-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a99d-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a99d-113">Remarks</span></span>  
 <span data-ttu-id="4a99d-114">Tato metoda se používá spolu s [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metodu k získání vrácené hodnoty metody vracející typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="4a99d-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="4a99d-115">Předání posunu IL pro web volání funkce do této metody vrátí jeden nebo více nativních posunů.</span><span class="sxs-lookup"><span data-stu-id="4a99d-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="4a99d-116">Ladicí program může potom nastavit zarážky u těchto nativních posunů funkce.</span><span class="sxs-lookup"><span data-stu-id="4a99d-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="4a99d-117">Pokud ladicí program narazí na jednu ze zarážek, můžete předat stejné odsazení IL, které jste předali do této metody můžete [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metodu k získání vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4a99d-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="4a99d-118">Ladicí program by měl poté zrušit všechny zarážky, které nastavil.</span><span class="sxs-lookup"><span data-stu-id="4a99d-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4a99d-119">`ICorDebugCode3::GetReturnValueLiveOffset` a [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) metody umožňují získat informace o vrácené hodnotě pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="4a99d-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="4a99d-120">Načítají se informace o vrácené hodnotě z typů hodnot (to znamená, že všechny typy, které jsou odvozeny z <xref:System.ValueType>) se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="4a99d-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="4a99d-121">Funkce vrátí `HRESULT` hodnoty uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="4a99d-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="4a99d-122">`HRESULT` Hodnota</span><span class="sxs-lookup"><span data-stu-id="4a99d-122">`HRESULT` value</span></span>|<span data-ttu-id="4a99d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="4a99d-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="4a99d-124">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="4a99d-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="4a99d-125">Zadaný posun IL není instrukcí volání nebo funkce vrátí `void`.</span><span class="sxs-lookup"><span data-stu-id="4a99d-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="4a99d-126">Zadaný posun IL je správným voláním, ale návratový typ není podporován pro načítání návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4a99d-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="4a99d-127">`ICorDebugCode3::GetReturnValueLiveOffset` Metoda je k dispozici pouze na základě x86 a AMD64 systémy.</span><span class="sxs-lookup"><span data-stu-id="4a99d-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a99d-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a99d-128">Requirements</span></span>  
 <span data-ttu-id="4a99d-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a99d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a99d-130">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a99d-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a99d-131">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a99d-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a99d-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a99d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a99d-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a99d-133">See also</span></span>

- [<span data-ttu-id="4a99d-134">GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="4a99d-134">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="4a99d-135">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a99d-135">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
