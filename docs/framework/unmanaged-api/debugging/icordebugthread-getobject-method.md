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
ms.openlocfilehash: 3695f150797e6a59a2fb1d58c99f233a35d687ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771846"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="7332c-102">ICorDebugThread::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="7332c-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="7332c-103">Získá ukazatel rozhraní k společným pojítkem language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7332c-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7332c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7332c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7332c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7332c-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="7332c-106">[out] Ukazatel na adresu objektu rozhraní ICorDebugValue, který představuje vlákna modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="7332c-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7332c-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7332c-107">Requirements</span></span>  
 <span data-ttu-id="7332c-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7332c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7332c-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7332c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7332c-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7332c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7332c-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7332c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7332c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7332c-112">See also</span></span>

- <xref:System.Threading.Thread>
