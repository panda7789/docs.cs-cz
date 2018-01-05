---
title: "ICorDebugProcess5::GetTypeID – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugProcess5.GetTypeID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeID
helpviewer_keywords:
- ICorDebugProcess5::GetTypeID method [.NET Framework debugging]
- GetTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 47dbaea4-8857-462e-93ba-fff880fc9e50
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f76285fceaa32f7c8b62b5cdf2ae7b4e9ec00de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="6b47d-102">ICorDebugProcess5::GetTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="6b47d-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="6b47d-103">Převede adresu objektu pro [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifikátor.</span><span class="sxs-lookup"><span data-stu-id="6b47d-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b47d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b47d-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b47d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b47d-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="6b47d-106">[v] Adresa objektu.</span><span class="sxs-lookup"><span data-stu-id="6b47d-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="6b47d-107">Ukazatel [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) hodnotu, která určuje objekt.</span><span class="sxs-lookup"><span data-stu-id="6b47d-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b47d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b47d-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b47d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b47d-109">Requirements</span></span>  
 <span data-ttu-id="6b47d-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b47d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b47d-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b47d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b47d-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b47d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b47d-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b47d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b47d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b47d-114">See Also</span></span>  
 [<span data-ttu-id="6b47d-115">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b47d-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="6b47d-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6b47d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
