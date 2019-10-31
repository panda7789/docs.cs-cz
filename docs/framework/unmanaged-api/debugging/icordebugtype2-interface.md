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
ms.openlocfilehash: 7b56f0f3ba62efb48ac8d79aad4480b5f22771ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110216"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="37630-102">ICorDebugType2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37630-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="37630-103">Rozšiřuje rozhraní ICorDebugType, aby získal identifikátor typu základního typu nebo komplexního (uživatelsky definovaného) typu.</span><span class="sxs-lookup"><span data-stu-id="37630-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37630-104">Metody</span><span class="sxs-lookup"><span data-stu-id="37630-104">Methods</span></span>  
  
|<span data-ttu-id="37630-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="37630-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="37630-106">GetTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="37630-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="37630-107">Načte [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pro tento typ.</span><span class="sxs-lookup"><span data-stu-id="37630-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37630-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37630-108">Remarks</span></span>  
 <span data-ttu-id="37630-109">Toto rozhraní je logickou příponou rozhraní ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="37630-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37630-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="37630-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37630-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="37630-111">Example</span></span>  
 <span data-ttu-id="37630-112">Následující fragment kódu ukazuje použití metody [ICorDebugType2:: GetTypeId.](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="37630-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="37630-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37630-113">Requirements</span></span>  
 <span data-ttu-id="37630-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37630-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37630-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="37630-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37630-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="37630-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37630-117">**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37630-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37630-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37630-118">See also</span></span>

- [<span data-ttu-id="37630-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="37630-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
