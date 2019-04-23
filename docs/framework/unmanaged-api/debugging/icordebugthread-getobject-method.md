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
ms.openlocfilehash: 7fa90aff73d94baf2cbf7d01f41710cb2aa10213
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178734"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="06e6c-102">ICorDebugThread::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="06e6c-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="06e6c-103">Získá ukazatel rozhraní k společným pojítkem language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="06e6c-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06e6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06e6c-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06e6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06e6c-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="06e6c-106">[out] Ukazatel na adresu objektu rozhraní ICorDebugValue, který představuje vlákna modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="06e6c-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06e6c-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06e6c-107">Requirements</span></span>  
 <span data-ttu-id="06e6c-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06e6c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06e6c-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06e6c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06e6c-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06e6c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06e6c-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06e6c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e6c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06e6c-112">See also</span></span>

- <xref:System.Threading.Thread>
