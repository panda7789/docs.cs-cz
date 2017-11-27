---
title: "ICorDebugSymbolProvider2 rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5ff0446ba8646620cb7322f74a81769e41f35b0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="cda20-102">ICorDebugSymbolProvider2 rozhraní</span><span class="sxs-lookup"><span data-stu-id="cda20-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="cda20-103">Logicky rozšiřuje [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) rozhraní k načtení informací o symbolu další ladění.</span><span class="sxs-lookup"><span data-stu-id="cda20-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cda20-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cda20-104">Methods</span></span>  
  
|<span data-ttu-id="cda20-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cda20-105">Method</span></span>|<span data-ttu-id="cda20-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cda20-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cda20-107">GetFrameProps – metoda</span><span class="sxs-lookup"><span data-stu-id="cda20-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="cda20-108">Vrátí metodu počáteční relativní virtuální adresa metodu a nadřazeného rámce zadaný relativní virtuální adresu kódu.</span><span class="sxs-lookup"><span data-stu-id="cda20-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="cda20-109">GetGenericDictionaryInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="cda20-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="cda20-110">Načte mapu obecné slovníku.</span><span class="sxs-lookup"><span data-stu-id="cda20-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cda20-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cda20-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cda20-112">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="cda20-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="cda20-113">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cda20-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cda20-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cda20-114">Requirements</span></span>  
 <span data-ttu-id="cda20-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cda20-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cda20-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cda20-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cda20-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cda20-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cda20-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cda20-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda20-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="cda20-119">See Also</span></span>  
 [<span data-ttu-id="cda20-120">ICorDebugSymbolProvider rozhraní</span><span class="sxs-lookup"><span data-stu-id="cda20-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="cda20-121">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="cda20-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="cda20-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="cda20-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
