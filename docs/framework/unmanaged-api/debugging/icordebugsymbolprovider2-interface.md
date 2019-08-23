---
title: ICorDebugSymbolProvider2 – rozhraní
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 587fc29edce72edca7c811c737d67d96b7cafd27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955472"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="a1779-102">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1779-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="a1779-103">Logicky rozšiřuje rozhraní [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) a načítá Další informace o symbolech ladění.</span><span class="sxs-lookup"><span data-stu-id="a1779-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1779-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a1779-104">Methods</span></span>  
  
|<span data-ttu-id="a1779-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1779-105">Method</span></span>|<span data-ttu-id="a1779-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a1779-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1779-107">GetFrameProps – metoda</span><span class="sxs-lookup"><span data-stu-id="a1779-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="a1779-108">Vrátí metodu, která spouští relativní virtuální adresu metody a nadřazený rámec pro relativní virtuální adresu kódu.</span><span class="sxs-lookup"><span data-stu-id="a1779-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="a1779-109">GetGenericDictionaryInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="a1779-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="a1779-110">Načte mapu obecného slovníku.</span><span class="sxs-lookup"><span data-stu-id="a1779-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1779-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1779-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1779-112">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a1779-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="a1779-113">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="a1779-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1779-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1779-114">Requirements</span></span>  
 <span data-ttu-id="a1779-115">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1779-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1779-116">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a1779-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1779-117">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1779-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1779-118">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1779-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1779-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1779-119">See also</span></span>

- [<span data-ttu-id="a1779-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1779-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="a1779-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a1779-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a1779-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="a1779-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
