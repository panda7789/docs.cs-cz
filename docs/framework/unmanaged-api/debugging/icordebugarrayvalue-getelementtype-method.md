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
ms.openlocfilehash: 403adfbfe96558196e5ba64ddcbe0be637ba1b1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403250"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="cfb8b-102">ICorDebugArrayValue::GetElementType – metoda</span><span class="sxs-lookup"><span data-stu-id="cfb8b-102">ICorDebugArrayValue::GetElementType Method</span></span>
<span data-ttu-id="cfb8b-103">Získá hodnotu, která určuje jednoduchý typ elementů v poli.</span><span class="sxs-lookup"><span data-stu-id="cfb8b-103">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfb8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfb8b-104">Syntax</span></span>  
  
```  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfb8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cfb8b-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="cfb8b-106">[out] Ukazatel na hodnotu CorElementType – výčet, který určuje typ.</span><span class="sxs-lookup"><span data-stu-id="cfb8b-106">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfb8b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cfb8b-107">Requirements</span></span>  
 <span data-ttu-id="cfb8b-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfb8b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfb8b-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfb8b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfb8b-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfb8b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfb8b-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfb8b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
