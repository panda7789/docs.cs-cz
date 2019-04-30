---
title: ICorDebugHandleValue::GetHandleType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.GetHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecc0b46618cd00ba4442e30c23a7b7e950382fee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775687"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="01b15-102">ICorDebugHandleValue::GetHandleType – metoda</span><span class="sxs-lookup"><span data-stu-id="01b15-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="01b15-103">Získá hodnotu, která určuje typ, který odkazuje tento objekt icordebughandlevalue – popisovač.</span><span class="sxs-lookup"><span data-stu-id="01b15-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01b15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01b15-104">Syntax</span></span>  
  
```  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01b15-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01b15-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="01b15-106">[out] Ukazatel na hodnotu cordebughandletype – výčet, který určuje typ tohoto popisovače.</span><span class="sxs-lookup"><span data-stu-id="01b15-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01b15-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01b15-107">Requirements</span></span>  
 <span data-ttu-id="01b15-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01b15-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01b15-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01b15-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01b15-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01b15-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01b15-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01b15-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
