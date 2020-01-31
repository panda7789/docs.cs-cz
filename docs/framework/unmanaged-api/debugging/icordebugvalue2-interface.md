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
ms.openlocfilehash: c6f20b0f7927d79ee56b5b6962137d668dc048d1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791108"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="ded0a-102">ICorDebugValue2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ded0a-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="ded0a-103">Rozšiřuje rozhraní "ICorDebugValue", aby poskytoval podporu pro objekty "ICorDebugType".</span><span class="sxs-lookup"><span data-stu-id="ded0a-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ded0a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ded0a-104">Methods</span></span>  
  
|<span data-ttu-id="ded0a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ded0a-105">Method</span></span>|<span data-ttu-id="ded0a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ded0a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ded0a-107">GetExactType – metoda</span><span class="sxs-lookup"><span data-stu-id="ded0a-107">GetExactType Method</span></span>](icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="ded0a-108">Získá ukazatel rozhraní na objekt `ICorDebugType`, který představuje <xref:System.Type> této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ded0a-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ded0a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ded0a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ded0a-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="ded0a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ded0a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ded0a-111">Requirements</span></span>  
 <span data-ttu-id="ded0a-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ded0a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ded0a-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ded0a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ded0a-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ded0a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ded0a-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ded0a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ded0a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ded0a-116">See also</span></span>

- [<span data-ttu-id="ded0a-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ded0a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

- [<span data-ttu-id="ded0a-118">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ded0a-118">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
