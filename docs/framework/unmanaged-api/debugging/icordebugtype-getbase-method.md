---
title: ICorDebugType::GetBase – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
ms.openlocfilehash: cff527aa7cde6a13667d47d030a0ef7db96ad5ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122334"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="d086d-102">ICorDebugType::GetBase – metoda</span><span class="sxs-lookup"><span data-stu-id="d086d-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="d086d-103">Získá ukazatel rozhraní na ICorDebugType, který představuje základní typ, pokud existuje, typu reprezentovaného tímto `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="d086d-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d086d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d086d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d086d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d086d-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="d086d-106">mimo Ukazatel na adresu `ICorDebugType`ho objektu, který představuje základní typ.</span><span class="sxs-lookup"><span data-stu-id="d086d-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d086d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d086d-107">Remarks</span></span>  
 <span data-ttu-id="d086d-108">Vyhledávání základního typu pro typ je užitečné pro implementaci běžných funkcí ladicího programu, jako je například tisk všech polí objektu nebo jeho nadřazených tříd.</span><span class="sxs-lookup"><span data-stu-id="d086d-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d086d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d086d-109">Requirements</span></span>  
 <span data-ttu-id="d086d-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d086d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d086d-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d086d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d086d-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d086d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d086d-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d086d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
