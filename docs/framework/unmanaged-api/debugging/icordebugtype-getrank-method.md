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
ms.openlocfilehash: 9a00177faabfcad56d70ec5c64328c90675c1532
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138764"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="011bc-102">ICorDebugType::GetRank – metoda</span><span class="sxs-lookup"><span data-stu-id="011bc-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="011bc-103">Získá počet rozměrů v typu pole.</span><span class="sxs-lookup"><span data-stu-id="011bc-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="011bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="011bc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="011bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="011bc-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="011bc-106">mimo Ukazatel na počet rozměrů.</span><span class="sxs-lookup"><span data-stu-id="011bc-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="011bc-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="011bc-107">Requirements</span></span>  
 <span data-ttu-id="011bc-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="011bc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="011bc-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="011bc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="011bc-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="011bc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="011bc-111">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="011bc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
