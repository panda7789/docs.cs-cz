---
title: ICorDebugType::GetRank – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetRank
helpviewer_keywords:
- GetRank method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetRank method [.NET Framework debugging]
ms.assetid: 72d3d927-f590-4f2d-8f60-448f3dfb96af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e42db5d7ebc9ec9983fe9e56477808415b26968b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751573"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="4315e-102">ICorDebugType::GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="4315e-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="4315e-103">Získá počet dimenzí v typu pole.</span><span class="sxs-lookup"><span data-stu-id="4315e-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4315e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4315e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4315e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4315e-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="4315e-106">[out] Ukazatel na počet rozměrů.</span><span class="sxs-lookup"><span data-stu-id="4315e-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4315e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4315e-107">Requirements</span></span>  
 <span data-ttu-id="4315e-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4315e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4315e-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4315e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4315e-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4315e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4315e-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4315e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
