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
ms.openlocfilehash: a2462d1de9f1b5f94f2581c1a06ca2987712fd7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421171"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="f20ed-102">ICorDebugValue2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f20ed-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="f20ed-103">Rozšiřuje rozhraní "ICorDebugValue" poskytovat podporu pro objekty "ICorDebugType".</span><span class="sxs-lookup"><span data-stu-id="f20ed-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f20ed-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f20ed-104">Methods</span></span>  
  
|<span data-ttu-id="f20ed-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f20ed-105">Method</span></span>|<span data-ttu-id="f20ed-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f20ed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f20ed-107">GetExactType – metoda</span><span class="sxs-lookup"><span data-stu-id="f20ed-107">GetExactType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="f20ed-108">Získá ukazatele rozhraní k `ICorDebugType` objekt, který reprezentuje <xref:System.Type> této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f20ed-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f20ed-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f20ed-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f20ed-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f20ed-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f20ed-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f20ed-111">Requirements</span></span>  
 <span data-ttu-id="f20ed-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f20ed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f20ed-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f20ed-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f20ed-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f20ed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f20ed-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f20ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f20ed-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f20ed-116">See Also</span></span>  
 [<span data-ttu-id="f20ed-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f20ed-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
    
 [<span data-ttu-id="f20ed-118">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f20ed-118">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
