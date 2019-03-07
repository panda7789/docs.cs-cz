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
ms.openlocfilehash: 4cd5a7696e7630b21c8bdfa7e4d2f902d6f36995
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490252"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="d5fa9-102">ICorDebugThread::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="d5fa9-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="d5fa9-103">Získá ukazatel rozhraní k společným pojítkem language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d5fa9-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5fa9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5fa9-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5fa9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5fa9-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="d5fa9-106">[out] Ukazatel na adresu objektu rozhraní ICorDebugValue, který představuje vlákna modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="d5fa9-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5fa9-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5fa9-107">Requirements</span></span>  
 <span data-ttu-id="d5fa9-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5fa9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5fa9-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5fa9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5fa9-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5fa9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5fa9-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5fa9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5fa9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5fa9-112">See also</span></span>
- <xref:System.Threading.Thread>
