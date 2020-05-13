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
ms.openlocfilehash: 499e1fd859a66bb6992c6d02a46e38c514503bd8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205587"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="66f15-102">ICorDebugProcess5::GetTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="66f15-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="66f15-103">Převede adresu objektu na identifikátor [COR_TYPEID](cor-typeid-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="66f15-103">Converts an object address to a [COR_TYPEID](cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66f15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66f15-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66f15-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66f15-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="66f15-106">pro Adresa objektu.</span><span class="sxs-lookup"><span data-stu-id="66f15-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="66f15-107">Ukazatel na hodnotu [COR_TYPEID](cor-typeid-structure.md) , která identifikuje objekt.</span><span class="sxs-lookup"><span data-stu-id="66f15-107">A pointer to the [COR_TYPEID](cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66f15-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66f15-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66f15-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66f15-109">Requirements</span></span>  
 <span data-ttu-id="66f15-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66f15-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66f15-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="66f15-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66f15-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="66f15-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66f15-113">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66f15-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f15-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="66f15-114">See also</span></span>

- [<span data-ttu-id="66f15-115">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66f15-115">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="66f15-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66f15-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
