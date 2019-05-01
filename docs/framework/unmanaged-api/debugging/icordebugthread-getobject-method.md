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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994003"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="a9d67-102">ICorDebugThread::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="a9d67-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="a9d67-103">Získá ukazatel rozhraní k společným pojítkem language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a9d67-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9d67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9d67-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9d67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9d67-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="a9d67-106">[out] Ukazatel na adresu objektu rozhraní ICorDebugValue, který představuje vlákna modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="a9d67-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9d67-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9d67-107">Requirements</span></span>  
 <span data-ttu-id="a9d67-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9d67-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9d67-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9d67-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9d67-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9d67-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9d67-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9d67-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9d67-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9d67-112">See also</span></span>

- <xref:System.Threading.Thread>
