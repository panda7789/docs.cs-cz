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
ms.openlocfilehash: 04ae3c4dd663351eaf1a58646e24e8ae95aeb9ad
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378283"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="db89d-102">ICorDebugRegisterSet::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="db89d-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="db89d-103">Získá kontext aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="db89d-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db89d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db89d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db89d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db89d-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="db89d-106">pro Velikost pole v bajtech `context` .</span><span class="sxs-lookup"><span data-stu-id="db89d-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="db89d-107">[in, out] Pole bajtů, které tvoří `CONTEXT` strukturu Win32 pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="db89d-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db89d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db89d-108">Remarks</span></span>  
 <span data-ttu-id="db89d-109">Ladicí program by měl zavolat tuto funkci namísto funkce Win32 `GetThreadContext` , protože vlákno může být ve stavu "napadeno", kde byl jeho kontext dočasně změněn.</span><span class="sxs-lookup"><span data-stu-id="db89d-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="db89d-110">Vrácená data jsou `CONTEXT` strukturou Win32 pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="db89d-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="db89d-111">Pro jiné než koncové snímky by klienti měli ověřit, které Registry jsou platné, pomocí [ICorDebugRegisterSet:: GetRegistersAvailable –](icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="db89d-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db89d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db89d-112">Requirements</span></span>  
 <span data-ttu-id="db89d-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db89d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db89d-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="db89d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db89d-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="db89d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db89d-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db89d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db89d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="db89d-117">See also</span></span>

- [<span data-ttu-id="db89d-118">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db89d-118">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="db89d-119">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db89d-119">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
