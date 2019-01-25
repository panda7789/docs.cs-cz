---
title: ICorDebugSymbolProvider2 Interface
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea60ecd542300bf3833c4977b7f0910399a2e409
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504025"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="fc58d-102">ICorDebugSymbolProvider2 Interface</span><span class="sxs-lookup"><span data-stu-id="fc58d-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="fc58d-103">Logicky rozšiřuje [icordebugsymbolprovider –](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) rozhraní pro načtení informací o symbolu další ladění.</span><span class="sxs-lookup"><span data-stu-id="fc58d-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc58d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fc58d-104">Methods</span></span>  
  
|<span data-ttu-id="fc58d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fc58d-105">Method</span></span>|<span data-ttu-id="fc58d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fc58d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc58d-107">GetFrameProps – metoda</span><span class="sxs-lookup"><span data-stu-id="fc58d-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="fc58d-108">Vrátí metodu počáteční relativní virtuální adresa metodu a daný kód relativní virtuální adresu nadřazeného rámce.</span><span class="sxs-lookup"><span data-stu-id="fc58d-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="fc58d-109">GetGenericDictionaryInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="fc58d-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="fc58d-110">Načte mapování generický slovník.</span><span class="sxs-lookup"><span data-stu-id="fc58d-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc58d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc58d-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc58d-112">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fc58d-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="fc58d-113">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fc58d-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc58d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc58d-114">Requirements</span></span>  
 <span data-ttu-id="fc58d-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc58d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc58d-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc58d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc58d-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc58d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc58d-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc58d-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc58d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc58d-119">See also</span></span>
- [<span data-ttu-id="fc58d-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc58d-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="fc58d-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fc58d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fc58d-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="fc58d-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
