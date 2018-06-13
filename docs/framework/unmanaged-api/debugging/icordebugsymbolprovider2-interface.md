---
title: ICorDebugSymbolProvider2 rozhraní
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7db1bba48f4685338f4531e2c11506de338e5c52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423218"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="05e6f-102">ICorDebugSymbolProvider2 rozhraní</span><span class="sxs-lookup"><span data-stu-id="05e6f-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="05e6f-103">Logicky rozšiřuje [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) rozhraní k načtení informací o symbolu další ladění.</span><span class="sxs-lookup"><span data-stu-id="05e6f-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05e6f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="05e6f-104">Methods</span></span>  
  
|<span data-ttu-id="05e6f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="05e6f-105">Method</span></span>|<span data-ttu-id="05e6f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="05e6f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05e6f-107">GetFrameProps – metoda</span><span class="sxs-lookup"><span data-stu-id="05e6f-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="05e6f-108">Vrátí metodu počáteční relativní virtuální adresa metodu a nadřazeného rámce zadaný relativní virtuální adresu kódu.</span><span class="sxs-lookup"><span data-stu-id="05e6f-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="05e6f-109">GetGenericDictionaryInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="05e6f-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="05e6f-110">Načte mapu obecné slovníku.</span><span class="sxs-lookup"><span data-stu-id="05e6f-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05e6f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05e6f-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05e6f-112">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="05e6f-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="05e6f-113">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="05e6f-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05e6f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05e6f-114">Requirements</span></span>  
 <span data-ttu-id="05e6f-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05e6f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05e6f-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05e6f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05e6f-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05e6f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05e6f-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05e6f-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05e6f-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="05e6f-119">See Also</span></span>  
 [<span data-ttu-id="05e6f-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05e6f-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="05e6f-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="05e6f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="05e6f-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="05e6f-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
