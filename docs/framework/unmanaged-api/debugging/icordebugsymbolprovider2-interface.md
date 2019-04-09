---
title: ICorDebugSymbolProvider2 – rozhraní
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b787302902779695c48df6e02e2ee00b28f44cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142464"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="e2e10-102">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2e10-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="e2e10-103">Logicky rozšiřuje [icordebugsymbolprovider –](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) rozhraní pro načtení informací o symbolu další ladění.</span><span class="sxs-lookup"><span data-stu-id="e2e10-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2e10-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e2e10-104">Methods</span></span>  
  
|<span data-ttu-id="e2e10-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2e10-105">Method</span></span>|<span data-ttu-id="e2e10-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e2e10-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2e10-107">GetFrameProps – metoda</span><span class="sxs-lookup"><span data-stu-id="e2e10-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="e2e10-108">Vrátí metodu počáteční relativní virtuální adresa metodu a daný kód relativní virtuální adresu nadřazeného rámce.</span><span class="sxs-lookup"><span data-stu-id="e2e10-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="e2e10-109">GetGenericDictionaryInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="e2e10-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="e2e10-110">Načte mapování generický slovník.</span><span class="sxs-lookup"><span data-stu-id="e2e10-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2e10-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2e10-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2e10-112">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e2e10-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e2e10-113">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e2e10-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2e10-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2e10-114">Requirements</span></span>  
 <span data-ttu-id="e2e10-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2e10-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2e10-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2e10-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2e10-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2e10-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e2e10-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e2e10-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e2e10-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2e10-119">See also</span></span>

- [<span data-ttu-id="e2e10-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2e10-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="e2e10-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2e10-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e2e10-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="e2e10-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
