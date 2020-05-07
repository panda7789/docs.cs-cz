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
ms.openlocfilehash: 2cb4c79601061ab8473d6d7ca50c4ed2f92b01c4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893431"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="8c6f1-102">ICorDebugCode3::GetReturnValueLiveOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="8c6f1-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="8c6f1-103">U zadaného posunu IL Získá nativní posuny, kde by měla být umístěna zarážka, aby ladicí program mohl získat návratovou hodnotu z funkce.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c6f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c6f1-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,
    [out] ULONG32 *pFetched,
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c6f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c6f1-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="8c6f1-106">Posun IL</span><span class="sxs-lookup"><span data-stu-id="8c6f1-106">The IL offset.</span></span> <span data-ttu-id="8c6f1-107">Musí se jednat o web volání funkce nebo se volání funkce nezdaří.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="8c6f1-108">Počet bajtů, které jsou k dispozici pro uložení `pOffsets`.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="8c6f1-109">Ukazatel na počet skutečně vrácených posunů.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="8c6f1-110">Obvykle je jeho hodnota 1, ale jedna instrukce IL může být mapována na více `CALL` instrukcí sestavení.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="8c6f1-111">Pole nativních posunů.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-111">An array of native offsets.</span></span> <span data-ttu-id="8c6f1-112">Obvykle `pOffsets` obsahuje jeden posun, přestože jedna instrukce Il může být mapována na více než více instrukcí `CALL` sestavení.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c6f1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c6f1-113">Remarks</span></span>  
 <span data-ttu-id="8c6f1-114">Tato metoda se používá společně s metodou [ICorDebugILFrame3:: GetReturnValueForILOffset –](icordebugilframe3-getreturnvalueforiloffset-method.md) k získání návratové hodnoty metody, která vrací typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="8c6f1-115">Předání posunu IL k webu volání funkce této metodě vrátí jedno nebo více nativních posunů.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="8c6f1-116">Ladicí program pak může nastavit zarážky na těchto nativních posunech ve funkci.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="8c6f1-117">Když ladicí program narazí na jednu ze zarážek, můžete předat stejný posun IL, který jste předali do této metody, do metody [ICorDebugILFrame3:: GetReturnValueForILOffset –](icordebugilframe3-getreturnvalueforiloffset-method.md) pro získání návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="8c6f1-118">Ladicí program by pak měl vymazat všechny zarážky, které nastavily.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="8c6f1-119">Metody `ICorDebugCode3::GetReturnValueLiveOffset` a [ICorDebugILFrame3:: GetReturnValueForILOffset –](icordebugilframe3-getreturnvalueforiloffset-method.md) umožňují získat informace o vrácených hodnotách pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="8c6f1-120">Načítání informací o vrácených hodnotách z typů hodnot (tj. všechny typy, <xref:System.ValueType>které jsou odvozeny z), nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="8c6f1-121">Funkce vrátí `HRESULT` hodnoty uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="8c6f1-122">`HRESULT`osa</span><span class="sxs-lookup"><span data-stu-id="8c6f1-122">`HRESULT` value</span></span>|<span data-ttu-id="8c6f1-123">Popis</span><span class="sxs-lookup"><span data-stu-id="8c6f1-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="8c6f1-124">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="8c6f1-125">Daná lokalita posunu IL není instrukcí volání, nebo vrátí `void`funkce.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="8c6f1-126">Daný posun IL je správného volání, ale návratový typ není podporován pro získání návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="8c6f1-127">Tato `ICorDebugCode3::GetReturnValueLiveOffset` metoda je k dispozici pouze v systémech založených na platformě x86 a amd64.</span><span class="sxs-lookup"><span data-stu-id="8c6f1-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c6f1-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c6f1-128">Requirements</span></span>  
 <span data-ttu-id="8c6f1-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c6f1-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c6f1-130">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8c6f1-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c6f1-131">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8c6f1-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c6f1-132">**Verze .NET Framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c6f1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c6f1-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c6f1-133">See also</span></span>

- [<span data-ttu-id="8c6f1-134">GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="8c6f1-134">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="8c6f1-135">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c6f1-135">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
