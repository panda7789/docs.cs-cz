---
title: ICorDebugDataTarget::GetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
ms.openlocfilehash: 3eace2d91b3bb6e637a659b8b49a31450ebc2c42
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783718"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="daa2c-102">ICorDebugDataTarget::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="daa2c-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="daa2c-103">Vrátí aktuální kontext vlákna pro zadané vlákno.</span><span class="sxs-lookup"><span data-stu-id="daa2c-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daa2c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="daa2c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="daa2c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="daa2c-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="daa2c-106">pro Identifikátor vlákna, jehož kontext má být načten.</span><span class="sxs-lookup"><span data-stu-id="daa2c-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="daa2c-107">Identifikátor je definován operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="daa2c-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="daa2c-108">pro Bitová kombinace příznaků závislých na platformě, která označuje, které části kontextu by měly být čteny.</span><span class="sxs-lookup"><span data-stu-id="daa2c-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="daa2c-109">pro Velikost `pContext`.</span><span class="sxs-lookup"><span data-stu-id="daa2c-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="daa2c-110">mimo Vyrovnávací paměť, kde bude uložen kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="daa2c-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daa2c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="daa2c-111">Remarks</span></span>  
 <span data-ttu-id="daa2c-112">Na platformách systému Windows musí být `pContext` `CONTEXT` struktuře (definované v souboru WinNT. h), která je vhodná pro typ počítače určený metodou [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="daa2c-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="daa2c-113">`contextFlags` musí mít stejné hodnoty jako pole `ContextFlags` struktury `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="daa2c-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="daa2c-114">Struktura `CONTEXT` je specifická pro procesor; Podrobnosti najdete v souboru WinNT. h.</span><span class="sxs-lookup"><span data-stu-id="daa2c-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daa2c-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="daa2c-115">Requirements</span></span>  
 <span data-ttu-id="daa2c-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daa2c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daa2c-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="daa2c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="daa2c-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="daa2c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="daa2c-119">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daa2c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa2c-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="daa2c-120">See also</span></span>

- [<span data-ttu-id="daa2c-121">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="daa2c-121">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="daa2c-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="daa2c-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="daa2c-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="daa2c-123">Debugging</span></span>](index.md)
