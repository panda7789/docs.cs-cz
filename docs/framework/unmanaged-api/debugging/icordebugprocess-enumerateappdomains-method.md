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
ms.openlocfilehash: 748a44075f7f73e54bab689bcb8865dee2b14946
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207831"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="500e6-102">ICorDebugProcess::EnumerateAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="500e6-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="500e6-103">Vytvoří výčet všech domén aplikace v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="500e6-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="500e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="500e6-104">Syntax</span></span>  
  
``` cpp
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="500e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="500e6-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="500e6-106">mimo Ukazatel na adresu [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) , která je enumerátorem pro domény aplikace v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="500e6-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="500e6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="500e6-107">Remarks</span></span>  
 <span data-ttu-id="500e6-108">Tuto metodu lze použít před zpětným voláním [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="500e6-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="500e6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="500e6-109">Requirements</span></span>  
 <span data-ttu-id="500e6-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="500e6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="500e6-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="500e6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="500e6-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="500e6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="500e6-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="500e6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
