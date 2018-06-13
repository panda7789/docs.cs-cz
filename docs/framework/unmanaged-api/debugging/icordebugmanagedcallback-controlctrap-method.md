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
ms.openlocfilehash: a9758de5c2801f2c55b7eca149569016ec5b9243
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412750"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="7a66b-102">ICorDebugManagedCallback::ControlCTrap – metoda</span><span class="sxs-lookup"><span data-stu-id="7a66b-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="7a66b-103">Do pasti CTRL + C v procesu, který je právě laděn upozorní ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="7a66b-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a66b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a66b-104">Syntax</span></span>  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a66b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a66b-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="7a66b-106">[v] Ukazatel na ICorDebugProcess objekt, který představuje proces, ve kterém je do pasti CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="7a66b-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a66b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7a66b-107">Return Value</span></span>  
  
|<span data-ttu-id="7a66b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7a66b-108">HRESULT</span></span>|<span data-ttu-id="7a66b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7a66b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7a66b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a66b-110">S_OK</span></span>|<span data-ttu-id="7a66b-111">Ladicí program, bude zpracovávat depeše CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="7a66b-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="7a66b-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7a66b-112">S_FALSE</span></span>|<span data-ttu-id="7a66b-113">Ladicí program nebude zpracování depeše CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="7a66b-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a66b-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a66b-114">Remarks</span></span>  
 <span data-ttu-id="7a66b-115">Všechny aplikační domény v rámci procesu se zastaví pro tento zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7a66b-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a66b-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7a66b-116">Requirements</span></span>  
 <span data-ttu-id="7a66b-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a66b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a66b-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a66b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a66b-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a66b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a66b-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a66b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a66b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a66b-121">See Also</span></span>  
 [<span data-ttu-id="7a66b-122">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7a66b-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
