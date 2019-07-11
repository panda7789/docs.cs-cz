---
title: ICorDebugAppDomain::GetProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetProcess method [.NET Framework debugging]
ms.assetid: 9d0b9628-a91c-40d0-b9bc-00b34a396b8f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eebb0c39cb8ae69dfce1e865f2784bbe9a408786
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737841"
---
# <a name="icordebugappdomaingetprocess-method"></a><span data-ttu-id="ae0b5-102">ICorDebugAppDomain::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="ae0b5-102">ICorDebugAppDomain::GetProcess Method</span></span>
<span data-ttu-id="ae0b5-103">Získá proces obsahující domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae0b5-103">Gets the process containing the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae0b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae0b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae0b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae0b5-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="ae0b5-106">[out] Ukazatel na adresu ICorDebugProcess objekt reprezentující proces.</span><span class="sxs-lookup"><span data-stu-id="ae0b5-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae0b5-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae0b5-107">Requirements</span></span>  
 <span data-ttu-id="ae0b5-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae0b5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae0b5-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae0b5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae0b5-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae0b5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae0b5-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae0b5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
