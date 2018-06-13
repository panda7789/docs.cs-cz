---
title: ICorDebugThread::GetObject – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad2dd4cded6800ce016d821f8e3ffe01dcb6264b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418256"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="2e953-102">ICorDebugThread::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="2e953-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="2e953-103">Získá ukazatele rozhraní pro běžné vlákno language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2e953-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e953-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e953-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e953-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e953-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="2e953-106">[out] Ukazatel na adresu ICorDebugValue rozhraní objekt, který reprezentuje vlákno CLR.</span><span class="sxs-lookup"><span data-stu-id="2e953-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e953-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e953-107">Requirements</span></span>  
 <span data-ttu-id="2e953-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e953-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e953-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e953-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e953-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e953-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e953-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e953-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e953-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e953-112">See Also</span></span>  
 <xref:System.Threading.Thread>
