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
ms.openlocfilehash: ea9e0fcae9f98869884ad887a6c24de342512b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="53b77-102">ICorDebugSymbolProvider::GetObjectSize – metoda</span><span class="sxs-lookup"><span data-stu-id="53b77-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="53b77-103">Vrátí velikost objektu pro objekt podle jeho typ typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="53b77-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53b77-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53b77-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53b77-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53b77-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="53b77-106">[v] Počet bajtů v typ typespec podpisu.</span><span class="sxs-lookup"><span data-stu-id="53b77-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="53b77-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="53b77-107">typeSig</span></span>  
 <span data-ttu-id="53b77-108">[v] Typ typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="53b77-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="53b77-109">[out] Ukazatel na velikost objektu.</span><span class="sxs-lookup"><span data-stu-id="53b77-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53b77-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53b77-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53b77-111">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="53b77-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53b77-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53b77-112">Requirements</span></span>  
 <span data-ttu-id="53b77-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53b77-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53b77-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53b77-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53b77-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53b77-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53b77-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53b77-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b77-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="53b77-117">See Also</span></span>  
 [<span data-ttu-id="53b77-118">ICorDebugSymbolProvider rozhraní</span><span class="sxs-lookup"><span data-stu-id="53b77-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="53b77-119">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="53b77-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
