---
title: ICorDebugProcess5::GetTypeForTypeID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: 39f5c1813b08f4d72c610820b1434e29eb4aec8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121278"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="57a3b-102">ICorDebugProcess5::GetTypeForTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="57a3b-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="57a3b-103">Převede identifikátor typu na hodnotu ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="57a3b-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57a3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57a3b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57a3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57a3b-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="57a3b-106">pro Identifikátor typu.</span><span class="sxs-lookup"><span data-stu-id="57a3b-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="57a3b-107">mimo Ukazatel na adresu ICorDebugType objektu.</span><span class="sxs-lookup"><span data-stu-id="57a3b-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57a3b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57a3b-108">Remarks</span></span>  
 <span data-ttu-id="57a3b-109">V některých případech metody, které vracejí identifikátor typu, mohou vracet hodnotu null `COR_TYPEID`.</span><span class="sxs-lookup"><span data-stu-id="57a3b-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="57a3b-110">Pokud je tato hodnota předána jako argument `id`, metoda `GetTypeForTypeID` se nezdaří a vrátí `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="57a3b-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57a3b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57a3b-111">Requirements</span></span>  
 <span data-ttu-id="57a3b-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57a3b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57a3b-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="57a3b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57a3b-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="57a3b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57a3b-115">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57a3b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57a3b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57a3b-116">See also</span></span>

- [<span data-ttu-id="57a3b-117">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57a3b-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="57a3b-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="57a3b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
