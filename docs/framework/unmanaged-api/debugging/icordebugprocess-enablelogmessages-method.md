---
title: ICorDebugProcess::EnableLogMessages – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b199d3226ec391fadc356b5efacdbf10a3e25adf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766155"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="84025-102">ICorDebugProcess::EnableLogMessages – metoda</span><span class="sxs-lookup"><span data-stu-id="84025-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="84025-103">Povolí nebo zakáže přenos zpráv protokolu v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="84025-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84025-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84025-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84025-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84025-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="84025-106">[in] `true` umožňuje přenos zprávy protokolu. `false` zakáže přenosu.</span><span class="sxs-lookup"><span data-stu-id="84025-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84025-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84025-107">Remarks</span></span>  
 <span data-ttu-id="84025-108">Tato metoda je platná jenom po [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) vyvolá zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="84025-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84025-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84025-109">Requirements</span></span>  
 <span data-ttu-id="84025-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84025-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84025-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84025-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84025-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84025-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84025-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84025-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
