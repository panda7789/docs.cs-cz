---
title: ICorDebugChain::IsManaged – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8c61cc12e438c0786b6e093b8bb1ea288a42e3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401164"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="75afe-102">ICorDebugChain::IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="75afe-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="75afe-103">Získá hodnotu, která určuje, zda tento řetězec používá spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="75afe-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75afe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75afe-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75afe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75afe-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="75afe-106">[out] `true` Pokud tento řetězec používá spravovaného kódu; jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="75afe-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75afe-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75afe-107">Requirements</span></span>  
 <span data-ttu-id="75afe-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75afe-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75afe-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75afe-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75afe-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75afe-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75afe-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75afe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
