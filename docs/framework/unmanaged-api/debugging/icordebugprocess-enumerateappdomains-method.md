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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749082"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="1862c-102">ICorDebugProcess::EnumerateAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="1862c-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="1862c-103">Vytvoří výčet všech doménách aplikace v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="1862c-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1862c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1862c-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1862c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1862c-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="1862c-106">[out] Ukazatel na adresu [icordebugappdomainenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) , který je enumerátor v tomto procesu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="1862c-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1862c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1862c-107">Remarks</span></span>  
 <span data-ttu-id="1862c-108">Tato metoda je možné před [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="1862c-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1862c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1862c-109">Requirements</span></span>  
 <span data-ttu-id="1862c-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1862c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1862c-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1862c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1862c-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1862c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1862c-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1862c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
