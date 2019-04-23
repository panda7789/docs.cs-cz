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
ms.openlocfilehash: 6718bbfdb1825b9f01698d76deec3fab16cb2ac6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091600"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="dfc3f-102">ICorDebugValue2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dfc3f-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="dfc3f-103">Rozšiřuje rozhraní "ICorDebugValue" a poskytuje podporu pro objekty "ICorDebugType".</span><span class="sxs-lookup"><span data-stu-id="dfc3f-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dfc3f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dfc3f-104">Methods</span></span>  
  
|<span data-ttu-id="dfc3f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dfc3f-105">Method</span></span>|<span data-ttu-id="dfc3f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="dfc3f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dfc3f-107">GetExactType – metoda</span><span class="sxs-lookup"><span data-stu-id="dfc3f-107">GetExactType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="dfc3f-108">Získá ukazatel rozhraní k `ICorDebugType` objekt, který reprezentuje <xref:System.Type> z této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dfc3f-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfc3f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dfc3f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfc3f-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="dfc3f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfc3f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dfc3f-111">Requirements</span></span>  
 <span data-ttu-id="dfc3f-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfc3f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfc3f-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfc3f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfc3f-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfc3f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfc3f-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfc3f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc3f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfc3f-116">See also</span></span>

- [<span data-ttu-id="dfc3f-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dfc3f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

- [<span data-ttu-id="dfc3f-118">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dfc3f-118">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
