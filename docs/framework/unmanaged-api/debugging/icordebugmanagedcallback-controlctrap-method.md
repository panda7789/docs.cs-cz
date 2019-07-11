---
title: ICorDebugManagedCallback::ControlCTrap – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e0217019aa9b8ff85716c62c27c0f4d5547074a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759790"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="5fc51-102">ICorDebugManagedCallback::ControlCTrap – metoda</span><span class="sxs-lookup"><span data-stu-id="5fc51-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="5fc51-103">Upozorní ladicí program, CTRL + C je zachycena v procesu, který je právě laděna.</span><span class="sxs-lookup"><span data-stu-id="5fc51-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fc51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fc51-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fc51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5fc51-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="5fc51-106">[in] Ukazatel na objekt ICorDebugProcess, který představuje proces, ve kterém je kombinace kláves CTRL + C zachycena.</span><span class="sxs-lookup"><span data-stu-id="5fc51-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fc51-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5fc51-107">Return Value</span></span>  
  
|<span data-ttu-id="5fc51-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5fc51-108">HRESULT</span></span>|<span data-ttu-id="5fc51-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5fc51-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5fc51-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5fc51-110">S_OK</span></span>|<span data-ttu-id="5fc51-111">Ladicí program zpracuje depeše CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="5fc51-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="5fc51-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5fc51-112">S_FALSE</span></span>|<span data-ttu-id="5fc51-113">Ladicí program nebude zpracovávat depeše CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="5fc51-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fc51-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5fc51-114">Remarks</span></span>  
 <span data-ttu-id="5fc51-115">Pro toto zpětné volání se zastaví všechny domény aplikace uvnitř procesu.</span><span class="sxs-lookup"><span data-stu-id="5fc51-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fc51-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5fc51-116">Requirements</span></span>  
 <span data-ttu-id="5fc51-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fc51-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fc51-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fc51-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fc51-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fc51-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fc51-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fc51-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fc51-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fc51-121">See also</span></span>

- [<span data-ttu-id="5fc51-122">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5fc51-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
