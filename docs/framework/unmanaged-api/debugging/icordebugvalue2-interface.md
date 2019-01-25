---
title: ICorDebugValue2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2
helpviewer_keywords:
- ICorDebugValue2 interface [.NET Framework debugging]
ms.assetid: 3ff2ad2a-da5a-461b-8627-1a8eba49df9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c4d4f5d85fb076748b3f8aae498f024804fb0b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492361"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="da0a5-102">ICorDebugValue2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da0a5-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="da0a5-103">Rozšiřuje rozhraní "ICorDebugValue" a poskytuje podporu pro objekty "ICorDebugType".</span><span class="sxs-lookup"><span data-stu-id="da0a5-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da0a5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="da0a5-104">Methods</span></span>  
  
|<span data-ttu-id="da0a5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="da0a5-105">Method</span></span>|<span data-ttu-id="da0a5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="da0a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da0a5-107">GetExactType – metoda</span><span class="sxs-lookup"><span data-stu-id="da0a5-107">GetExactType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="da0a5-108">Získá ukazatel rozhraní k `ICorDebugType` objekt, který reprezentuje <xref:System.Type> z této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="da0a5-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da0a5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da0a5-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da0a5-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="da0a5-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da0a5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da0a5-111">Requirements</span></span>  
 <span data-ttu-id="da0a5-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da0a5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da0a5-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da0a5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da0a5-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da0a5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da0a5-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da0a5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da0a5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da0a5-116">See also</span></span>
- [<span data-ttu-id="da0a5-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="da0a5-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

- [<span data-ttu-id="da0a5-118">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da0a5-118">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
