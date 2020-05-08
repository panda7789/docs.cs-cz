---
title: ICorDebug::DebugActiveProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
ms.openlocfilehash: 3630e25b6c24edaa366f1b0fae088e760e851fa4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895412"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="eb4b6-102">ICorDebug::DebugActiveProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="eb4b6-102">ICorDebug::DebugActiveProcess Method</span></span>
<span data-ttu-id="eb4b6-103">Připojí ladicí program k existujícímu procesu.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb4b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb4b6-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb4b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb4b6-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="eb4b6-106">pro ID procesu, ke kterému má být připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="eb4b6-107">pro Logická hodnota, která je nastavena `true` na, pokud se má ladicí program chovat jako ladicí program Win32 pro proces a odeslání nespravovaných zpětných volání; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="eb4b6-108">mimo Ukazatel na adresu objektu "ICorDebugProcess", který představuje proces, ke kterému byl připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb4b6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb4b6-109">Remarks</span></span>  
 <span data-ttu-id="eb4b6-110">Ladění spolupráce se nepodporuje na platformách, které nejsou založené na platformě IA-64 a platformě AMD64.</span><span class="sxs-lookup"><span data-stu-id="eb4b6-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb4b6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb4b6-111">Requirements</span></span>  
 <span data-ttu-id="eb4b6-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb4b6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb4b6-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eb4b6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb4b6-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eb4b6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb4b6-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb4b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb4b6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb4b6-116">See also</span></span>

- [<span data-ttu-id="eb4b6-117">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb4b6-117">ICorDebug Interface</span></span>](icordebug-interface.md)
