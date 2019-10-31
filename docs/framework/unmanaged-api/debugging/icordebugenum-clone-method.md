---
title: ICorDebugEnum::Clone – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Clone
helpviewer_keywords:
- Clone method, ICorDebugEnum interface [.NET Framework debugging]
- ICorDebugEnum::Clone method [.NET Framework debugging]
ms.assetid: 57eefaf3-75cf-4496-bc94-88c0706861b7
topic_type:
- apiref
ms.openlocfilehash: 2ec769c343ad055132c6d84e64600fc459357a85
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124710"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="15499-102">ICorDebugEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="15499-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="15499-103">Vytvoří kopii tohoto objektu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="15499-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15499-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15499-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15499-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15499-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="15499-106">mimo Ukazatel na adresu `ICorDebugEnum` objektu, který je kopií tohoto objektu `ICorDebugEnum`.</span><span class="sxs-lookup"><span data-stu-id="15499-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15499-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15499-107">Requirements</span></span>  
 <span data-ttu-id="15499-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15499-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15499-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="15499-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15499-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="15499-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15499-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15499-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
