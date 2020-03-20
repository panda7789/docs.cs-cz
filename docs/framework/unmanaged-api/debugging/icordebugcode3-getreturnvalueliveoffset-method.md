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
ms.openlocfilehash: 34d543dd76de05bdf55d8187cf192455d1387a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178945"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="09cc0-102">ICorDebugCode3::GetReturnValueLiveOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="09cc0-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="09cc0-103">Pro zadaný posun IL získá nativní posuny, kde by měla být umístěna zarážka tak, aby ladicí program mohl získat vrácenou hodnotu z funkce.</span><span class="sxs-lookup"><span data-stu-id="09cc0-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09cc0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09cc0-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,
    [out] ULONG32 *pFetched,
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09cc0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09cc0-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="09cc0-106">Posun IL.</span><span class="sxs-lookup"><span data-stu-id="09cc0-106">The IL offset.</span></span> <span data-ttu-id="09cc0-107">Musí se jednat o stránku s voláním funkce, jinak se volání funkce nezdaří.</span><span class="sxs-lookup"><span data-stu-id="09cc0-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="09cc0-108">Počet bajtů, které `pOffsets`jsou k dispozici pro uložení .</span><span class="sxs-lookup"><span data-stu-id="09cc0-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="09cc0-109">Ukazatel na počet posunů skutečně vrácených.</span><span class="sxs-lookup"><span data-stu-id="09cc0-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="09cc0-110">Obvykle je jeho hodnota 1, ale jedna instrukce `CALL` IL může mapovat na více instrukcí sestavení.</span><span class="sxs-lookup"><span data-stu-id="09cc0-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="09cc0-111">Pole nativní posuny.</span><span class="sxs-lookup"><span data-stu-id="09cc0-111">An array of native offsets.</span></span> <span data-ttu-id="09cc0-112">Obvykle `pOffsets` obsahuje jeden posun, i když jeden IL instrukce můžete `CALL` mapovat na více map na více instrukcí sestavení.</span><span class="sxs-lookup"><span data-stu-id="09cc0-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09cc0-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09cc0-113">Remarks</span></span>  
 <span data-ttu-id="09cc0-114">Tato metoda se používá spolu s [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) metoda získat vrácenou hodnotu metody, která vrací typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="09cc0-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="09cc0-115">Předání mdloby posunu do webu volání funkce této metodě vrátí jeden nebo více nativní posuny.</span><span class="sxs-lookup"><span data-stu-id="09cc0-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="09cc0-116">Ladicí program pak můžete nastavit zarážky na tyto nativní posuny ve funkci.</span><span class="sxs-lookup"><span data-stu-id="09cc0-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="09cc0-117">Když ladicí program zasáhne jeden z zarážek, můžete pak předat stejný IL posun, který jste předali této metodě [iCorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) metoda získat vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="09cc0-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="09cc0-118">Ladicí program by pak měl vymazat všechny zarážky, které nastaví.</span><span class="sxs-lookup"><span data-stu-id="09cc0-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="09cc0-119">Metody `ICorDebugCode3::GetReturnValueLiveOffset` a a [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) umožňují získat informace o vrácené hodnotě pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="09cc0-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="09cc0-120">Načítání informací o vrácené hodnotě z typů hodnot <xref:System.ValueType>(tj. všechny typy, které jsou odvozeny z ) není podporováno.</span><span class="sxs-lookup"><span data-stu-id="09cc0-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="09cc0-121">Funkce vrátí `HRESULT` hodnoty uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="09cc0-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="09cc0-122">`HRESULT`Hodnotu</span><span class="sxs-lookup"><span data-stu-id="09cc0-122">`HRESULT` value</span></span>|<span data-ttu-id="09cc0-123">Popis</span><span class="sxs-lookup"><span data-stu-id="09cc0-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="09cc0-124">Úspěch</span><span class="sxs-lookup"><span data-stu-id="09cc0-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="09cc0-125">Daný server offset IL není instrukce volání nebo `void`funkce vrátí .</span><span class="sxs-lookup"><span data-stu-id="09cc0-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="09cc0-126">Daný posun IL je správné volání, ale návratový typ není podporován pro získání vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="09cc0-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="09cc0-127">Metoda `ICorDebugCode3::GetReturnValueLiveOffset` je k dispozici pouze v systémech x86 a AMD64.</span><span class="sxs-lookup"><span data-stu-id="09cc0-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09cc0-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09cc0-128">Requirements</span></span>  
 <span data-ttu-id="09cc0-129">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09cc0-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09cc0-130">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09cc0-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09cc0-131">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09cc0-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09cc0-132">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09cc0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09cc0-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="09cc0-133">See also</span></span>

- [<span data-ttu-id="09cc0-134">GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="09cc0-134">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="09cc0-135">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09cc0-135">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
