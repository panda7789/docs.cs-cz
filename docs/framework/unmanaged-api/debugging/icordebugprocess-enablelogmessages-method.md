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
ms.openlocfilehash: 6b1ccffa4f24122e643a64270f44945afdbc8fff
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792649"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="8b863-102">ICorDebugProcess::EnableLogMessages – metoda</span><span class="sxs-lookup"><span data-stu-id="8b863-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="8b863-103">Povolí nebo zakáže přenos zpráv protokolu do ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="8b863-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b863-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b863-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b863-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b863-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="8b863-106">[in] `true` povoluje přenos zpráv protokolu; `false` zakáže přenos.</span><span class="sxs-lookup"><span data-stu-id="8b863-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b863-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b863-107">Remarks</span></span>  
 <span data-ttu-id="8b863-108">Tato metoda je platná pouze po výskytu zpětného volání [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8b863-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b863-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b863-109">Requirements</span></span>  
 <span data-ttu-id="8b863-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b863-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b863-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8b863-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b863-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8b863-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b863-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b863-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
