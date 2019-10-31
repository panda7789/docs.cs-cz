---
title: ICorDebugMemoryBuffer – rozhraní
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 9e43f9a2297eb56755c7a6bba73e994441cbfeaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127976"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="0adb1-102">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0adb1-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="0adb1-103">Představuje vyrovnávací paměť v paměti.</span><span class="sxs-lookup"><span data-stu-id="0adb1-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0adb1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0adb1-104">Methods</span></span>  
  
|<span data-ttu-id="0adb1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0adb1-105">Method</span></span>|<span data-ttu-id="0adb1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0adb1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0adb1-107">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="0adb1-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="0adb1-108">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0adb1-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="0adb1-109">GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="0adb1-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="0adb1-110">Získá počáteční adresu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="0adb1-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0adb1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0adb1-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0adb1-112">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0adb1-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0adb1-113">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="0adb1-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0adb1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0adb1-114">Requirements</span></span>  
 <span data-ttu-id="0adb1-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0adb1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0adb1-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0adb1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0adb1-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0adb1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0adb1-118">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0adb1-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0adb1-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0adb1-119">See also</span></span>

- [<span data-ttu-id="0adb1-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0adb1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0adb1-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="0adb1-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
