---
title: ICorDebugRegisterSet::GetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
ms.openlocfilehash: 8137d5477b75b864e223852cf524ac8c5b6c0f2b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792095"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="7fc72-102">ICorDebugRegisterSet::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="7fc72-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="7fc72-103">Získá kontext aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="7fc72-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fc72-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fc72-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fc72-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7fc72-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="7fc72-106">pro Velikost pole `context` v bajtech</span><span class="sxs-lookup"><span data-stu-id="7fc72-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="7fc72-107">[in, out] Pole bajtů, které tvoří strukturu `CONTEXT` Win32 pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="7fc72-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fc72-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7fc72-108">Remarks</span></span>  
 <span data-ttu-id="7fc72-109">Ladicí program by měl zavolat tuto funkci namísto funkce Win32 `GetThreadContext`, protože vlákno může být ve stavu "napadeno", kde byl jeho kontext dočasně změněn.</span><span class="sxs-lookup"><span data-stu-id="7fc72-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="7fc72-110">Vrácená data jsou strukturou `CONTEXT` Win32 pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="7fc72-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="7fc72-111">Pro jiné než koncové snímky by klienti měli ověřit, které Registry jsou platné, pomocí [ICorDebugRegisterSet:: GetRegistersAvailable –](icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="7fc72-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fc72-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7fc72-112">Requirements</span></span>  
 <span data-ttu-id="7fc72-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fc72-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fc72-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7fc72-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fc72-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7fc72-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fc72-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fc72-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fc72-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7fc72-117">See also</span></span>

- [<span data-ttu-id="7fc72-118">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7fc72-118">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="7fc72-119">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7fc72-119">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
