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
ms.openlocfilehash: 7f4794fb0383435f828626497036ad3458df2173
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204988"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="4f34d-102">ICorDebugManagedCallback::ControlCTrap – metoda</span><span class="sxs-lookup"><span data-stu-id="4f34d-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="4f34d-103">Upozorní ladicí program, CTRL + C je zachycena v procesu, který je právě laděna.</span><span class="sxs-lookup"><span data-stu-id="4f34d-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f34d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f34d-104">Syntax</span></span>  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f34d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f34d-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="4f34d-106">[in] Ukazatel na objekt ICorDebugProcess, který představuje proces, ve kterém je kombinace kláves CTRL + C zachycena.</span><span class="sxs-lookup"><span data-stu-id="4f34d-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f34d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4f34d-107">Return Value</span></span>  
  
|<span data-ttu-id="4f34d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4f34d-108">HRESULT</span></span>|<span data-ttu-id="4f34d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4f34d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f34d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4f34d-110">S_OK</span></span>|<span data-ttu-id="4f34d-111">Ladicí program zpracuje depeše CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="4f34d-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="4f34d-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4f34d-112">S_FALSE</span></span>|<span data-ttu-id="4f34d-113">Ladicí program nebude zpracovávat depeše CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="4f34d-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f34d-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f34d-114">Remarks</span></span>  
 <span data-ttu-id="4f34d-115">Pro toto zpětné volání se zastaví všechny domény aplikace uvnitř procesu.</span><span class="sxs-lookup"><span data-stu-id="4f34d-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f34d-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f34d-116">Requirements</span></span>  
 <span data-ttu-id="4f34d-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f34d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f34d-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f34d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f34d-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f34d-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4f34d-120">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4f34d-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4f34d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f34d-121">See also</span></span>

- [<span data-ttu-id="4f34d-122">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f34d-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
