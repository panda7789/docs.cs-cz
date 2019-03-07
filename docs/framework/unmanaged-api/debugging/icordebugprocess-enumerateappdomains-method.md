---
title: ICorDebugProcess::EnumerateAppDomains – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnumerateAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02e051d311e447475bea724b0bd7420ee8b590f6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495725"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="b057b-102">ICorDebugProcess::EnumerateAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="b057b-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="b057b-103">Vytvoří výčet všech doménách aplikace v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="b057b-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b057b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b057b-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b057b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b057b-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="b057b-106">[out] Ukazatel na adresu [icordebugappdomainenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) , který je enumerátor v tomto procesu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b057b-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b057b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b057b-107">Remarks</span></span>  
 <span data-ttu-id="b057b-108">Tato metoda je možné před [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="b057b-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b057b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b057b-109">Requirements</span></span>  
 <span data-ttu-id="b057b-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b057b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b057b-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b057b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b057b-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b057b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b057b-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b057b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
