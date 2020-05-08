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
ms.openlocfilehash: 9f0fda803ba3a1ce35017d85e84b3bf6f567eda0
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976366"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="8f02a-102">ICorDebugEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="8f02a-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="8f02a-103">Vytvoří kopii tohoto objektu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="8f02a-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f02a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f02a-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f02a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f02a-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="8f02a-106">mimo Ukazatel na adresu `ICorDebugEnum` objektu, který je kopií tohoto `ICorDebugEnum` objektu.</span><span class="sxs-lookup"><span data-stu-id="8f02a-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f02a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f02a-107">Requirements</span></span>  
 <span data-ttu-id="8f02a-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f02a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f02a-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8f02a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f02a-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8f02a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f02a-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f02a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
