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
ms.openlocfilehash: d0dbac6570fc0af0452a0e44f838124afbf6a4fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419881"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="5b3b1-102">ICorDebugProcess::EnableLogMessages – metoda</span><span class="sxs-lookup"><span data-stu-id="5b3b1-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="5b3b1-103">Povolí nebo zakáže přenos zpráv protokolu pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="5b3b1-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b3b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b3b1-104">Syntax</span></span>  
  
```  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b3b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b3b1-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="5b3b1-106">[v] `true` umožňuje přenos zpráv protokolu; `false` zakáže přenos.</span><span class="sxs-lookup"><span data-stu-id="5b3b1-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b3b1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b3b1-107">Remarks</span></span>  
 <span data-ttu-id="5b3b1-108">Tato metoda je platná pouze po [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) dojde k zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="5b3b1-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b3b1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b3b1-109">Requirements</span></span>  
 <span data-ttu-id="5b3b1-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b3b1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b3b1-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b3b1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b3b1-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b3b1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b3b1-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b3b1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
