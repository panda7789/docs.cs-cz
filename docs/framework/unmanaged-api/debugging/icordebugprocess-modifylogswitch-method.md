---
title: ICorDebugProcess::ModifyLogSwitch – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ModifyLogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b1c85499e5269027da2c2a01ab67aab2c5da626
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488172"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="d7ea4-102">ICorDebugProcess::ModifyLogSwitch – metoda</span><span class="sxs-lookup"><span data-stu-id="d7ea4-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="d7ea4-103">Nastaví úroveň závažnosti přepínače zadaný protokol.</span><span class="sxs-lookup"><span data-stu-id="d7ea4-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7ea4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7ea4-104">Syntax</span></span>  
  
```  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7ea4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7ea4-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="d7ea4-106">[in] Ukazatel na řetězec, který určuje název protokolu přepínače.</span><span class="sxs-lookup"><span data-stu-id="d7ea4-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="d7ea4-107">[in] Úroveň závažnosti nastavit pro přepínač zadaný protokol.</span><span class="sxs-lookup"><span data-stu-id="d7ea4-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7ea4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7ea4-108">Remarks</span></span>  
 <span data-ttu-id="d7ea4-109">Tato metoda je platná jenom po [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) zpětného volání došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="d7ea4-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7ea4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7ea4-110">Requirements</span></span>  
 <span data-ttu-id="d7ea4-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7ea4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7ea4-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7ea4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7ea4-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7ea4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7ea4-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7ea4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
