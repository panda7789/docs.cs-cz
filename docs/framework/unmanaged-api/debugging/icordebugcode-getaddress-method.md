---
title: ICorDebugCode::GetAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7df668487601e4278b56e196a43d1154b643fd29
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700736"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="df421-102">ICorDebugCode::GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="df421-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="df421-103">Získá relativní virtuální adresu (RVA) segmentu kódu, který představuje toto rozhraní "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="df421-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df421-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df421-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df421-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df421-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="df421-106">mimo Ukazatel na adresu RVA segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="df421-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df421-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df421-107">Requirements</span></span>  
 <span data-ttu-id="df421-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df421-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df421-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="df421-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df421-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="df421-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df421-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df421-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
