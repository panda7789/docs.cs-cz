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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d1226f64df379b5c40304221e9e66eebcdb17b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479230"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="2b07c-102">ICorDebugEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="2b07c-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="2b07c-103">Vytvoří kopii tohoto objektu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="2b07c-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b07c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b07c-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b07c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b07c-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2b07c-106">[out] Ukazatel na adresu `ICorDebugEnum` objekt, který je kopií této `ICorDebugEnum` objektu.</span><span class="sxs-lookup"><span data-stu-id="2b07c-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b07c-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b07c-107">Requirements</span></span>  
 <span data-ttu-id="2b07c-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b07c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b07c-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b07c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b07c-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b07c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b07c-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b07c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
