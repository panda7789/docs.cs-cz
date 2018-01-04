---
title: "ICorDebugSymbolProvider::GetObjectSize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8817eb79c825a02ec5654ec340dedd6c77889a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="aeebd-102">ICorDebugSymbolProvider::GetObjectSize – metoda</span><span class="sxs-lookup"><span data-stu-id="aeebd-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="aeebd-103">Vrátí velikost objektu pro objekt podle jeho typ typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="aeebd-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeebd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aeebd-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aeebd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aeebd-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="aeebd-106">[v] Počet bajtů v typ typespec podpisu.</span><span class="sxs-lookup"><span data-stu-id="aeebd-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="aeebd-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="aeebd-107">typeSig</span></span>  
 <span data-ttu-id="aeebd-108">[v] Typ typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="aeebd-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="aeebd-109">[out] Ukazatel na velikost objektu.</span><span class="sxs-lookup"><span data-stu-id="aeebd-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aeebd-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aeebd-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aeebd-111">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="aeebd-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeebd-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aeebd-112">Requirements</span></span>  
 <span data-ttu-id="aeebd-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeebd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeebd-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aeebd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aeebd-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aeebd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aeebd-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeebd-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeebd-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="aeebd-117">See Also</span></span>  
 [<span data-ttu-id="aeebd-118">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aeebd-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="aeebd-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="aeebd-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
