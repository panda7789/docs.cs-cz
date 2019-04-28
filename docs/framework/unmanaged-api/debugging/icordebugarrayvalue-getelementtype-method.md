---
title: ICorDebugArrayValue::GetElementType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementType
helpviewer_keywords:
- ICorDebugArrayValue::GetElementType method [.NET Framework debugging]
- GetElementType method [.NET Framework debugging]
ms.assetid: ed71961e-ae9b-4dfc-9554-06637696d697
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6f5f1da94e1ae07a604a616c631a38d02caea9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645627"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="ad893-102">ICorDebugArrayValue::GetElementType – metoda</span><span class="sxs-lookup"><span data-stu-id="ad893-102">ICorDebugArrayValue::GetElementType Method</span></span>
<span data-ttu-id="ad893-103">Získá hodnotu, která určuje jednoduchý typ prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="ad893-103">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad893-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad893-104">Syntax</span></span>  
  
```  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad893-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad893-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="ad893-106">[out] Ukazatel na hodnotu corelementtype – výčet, který označuje typ.</span><span class="sxs-lookup"><span data-stu-id="ad893-106">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad893-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad893-107">Requirements</span></span>  
 <span data-ttu-id="ad893-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad893-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad893-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad893-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad893-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad893-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad893-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad893-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
