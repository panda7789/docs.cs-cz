---
title: ICorDebugArrayValue::GetCount – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetCount
helpviewer_keywords:
- ICorDebugArrayValue::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 44cd98cf-2127-4d46-8c6a-da4e857bb6b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d00c04f3719d6fb340541d3301d4dc4a3f95ca40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645718"
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="e5aa9-102">ICorDebugArrayValue::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="e5aa9-102">ICorDebugArrayValue::GetCount Method</span></span>
<span data-ttu-id="e5aa9-103">Získá celkový počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="e5aa9-103">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5aa9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5aa9-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5aa9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5aa9-105">Parameters</span></span>  
 `pnCount`  
 <span data-ttu-id="e5aa9-106">[out] Ukazatel na celkový počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="e5aa9-106">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5aa9-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5aa9-107">Requirements</span></span>  
 <span data-ttu-id="e5aa9-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5aa9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5aa9-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5aa9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5aa9-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5aa9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5aa9-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5aa9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
