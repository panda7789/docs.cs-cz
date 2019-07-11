---
title: ICorDebugType2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e953fa129308527f63df8dd8c5061252f8be57b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772443"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="59f8c-102">ICorDebugType2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="59f8c-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="59f8c-103">Rozšiřuje rozhraní ICorDebugType načtete identifikátor typu základního typu nebo komplexní typ (definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="59f8c-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59f8c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="59f8c-104">Methods</span></span>  
  
|<span data-ttu-id="59f8c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="59f8c-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="59f8c-106">GetTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="59f8c-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="59f8c-107">Získá [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) u tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="59f8c-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59f8c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59f8c-108">Remarks</span></span>  
 <span data-ttu-id="59f8c-109">Toto rozhraní je logickým rozšířením icordebugtype – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="59f8c-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59f8c-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="59f8c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59f8c-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="59f8c-111">Example</span></span>  
 <span data-ttu-id="59f8c-112">Následující fragment kódu ukazuje použití metody [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="59f8c-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="59f8c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59f8c-113">Requirements</span></span>  
 <span data-ttu-id="59f8c-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59f8c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59f8c-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59f8c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59f8c-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59f8c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59f8c-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59f8c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f8c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59f8c-118">See also</span></span>

- [<span data-ttu-id="59f8c-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="59f8c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
