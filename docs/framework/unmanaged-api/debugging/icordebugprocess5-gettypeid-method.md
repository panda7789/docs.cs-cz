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
ms.openlocfilehash: b63c6ca8ead2a401f907ea6569e966c6470aca13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421948"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="2ff92-102">ICorDebugProcess5::GetTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="2ff92-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="2ff92-103">Převede adresu objektu pro [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifikátor.</span><span class="sxs-lookup"><span data-stu-id="2ff92-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ff92-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ff92-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ff92-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="2ff92-106">[v] Adresa objektu.</span><span class="sxs-lookup"><span data-stu-id="2ff92-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="2ff92-107">Ukazatel [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) hodnotu, která určuje objekt.</span><span class="sxs-lookup"><span data-stu-id="2ff92-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ff92-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ff92-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ff92-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ff92-109">Requirements</span></span>  
 <span data-ttu-id="2ff92-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ff92-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ff92-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ff92-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ff92-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ff92-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ff92-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ff92-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff92-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ff92-114">See Also</span></span>  
 [<span data-ttu-id="2ff92-115">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ff92-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="2ff92-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2ff92-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
