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
ms.openlocfilehash: 86b8737577bdb5f61f1061cb217620fae03ebd0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139369"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="9d055-102">ICorDebugProcess::ModifyLogSwitch – metoda</span><span class="sxs-lookup"><span data-stu-id="9d055-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="9d055-103">Nastaví úroveň závažnosti určeného přepínače protokolu.</span><span class="sxs-lookup"><span data-stu-id="9d055-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d055-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d055-104">Syntax</span></span>  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d055-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d055-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="9d055-106">pro Ukazatel na řetězec, který určuje název přepínače protokolu.</span><span class="sxs-lookup"><span data-stu-id="9d055-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="9d055-107">pro Úroveň závažnosti, která se má nastavit pro zadaný přepínač protokolu.</span><span class="sxs-lookup"><span data-stu-id="9d055-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d055-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d055-108">Remarks</span></span>  
 <span data-ttu-id="9d055-109">Tato metoda je platná až po výskytu zpětného volání [ICorDebugManagedCallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9d055-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d055-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d055-110">Requirements</span></span>  
 <span data-ttu-id="9d055-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d055-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d055-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9d055-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d055-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9d055-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d055-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d055-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
