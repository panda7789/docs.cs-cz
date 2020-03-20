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
ms.openlocfilehash: 4489238df05edef384b4073ee738a184ff8809ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178676"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="70630-102">ICorDebugProcess::EnumerateAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="70630-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="70630-103">Vyjmenovává všechny aplikační domény v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="70630-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70630-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70630-104">Syntax</span></span>  
  
``` cpp
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70630-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70630-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="70630-106">[out] Ukazatel na adresu [ICorDebugAppDomainEnum,](icordebugappdomainenum-interface.md) který je čítač pro aplikační domény v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="70630-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70630-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70630-107">Remarks</span></span>  
 <span data-ttu-id="70630-108">Tuto metodu lze použít před [iCorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="70630-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70630-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70630-109">Requirements</span></span>  
 <span data-ttu-id="70630-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70630-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70630-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70630-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70630-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70630-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70630-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70630-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
