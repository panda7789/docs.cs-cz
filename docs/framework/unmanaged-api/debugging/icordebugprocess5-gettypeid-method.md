---
title: ICorDebugProcess5::GetTypeID – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess5.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeID
helpviewer_keywords:
- ICorDebugProcess5::GetTypeID method [.NET Framework debugging]
- GetTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 47dbaea4-8857-462e-93ba-fff880fc9e50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07c23a32037e83a878bb3136c48176f19249b207
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948691"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="63118-102">ICorDebugProcess5::GetTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="63118-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="63118-103">Převede adresu objektu [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifikátor.</span><span class="sxs-lookup"><span data-stu-id="63118-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63118-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63118-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63118-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63118-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="63118-106">[in] Adresa objektu.</span><span class="sxs-lookup"><span data-stu-id="63118-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="63118-107">Ukazatel [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) hodnotu, která určuje objekt.</span><span class="sxs-lookup"><span data-stu-id="63118-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63118-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63118-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63118-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63118-109">Requirements</span></span>  
 <span data-ttu-id="63118-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63118-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63118-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63118-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63118-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63118-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63118-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63118-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63118-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63118-114">See also</span></span>

- [<span data-ttu-id="63118-115">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63118-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="63118-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="63118-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
