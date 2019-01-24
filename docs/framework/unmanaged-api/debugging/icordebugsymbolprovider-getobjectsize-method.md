---
title: ICorDebugSymbolProvider::GetObjectSize – metoda
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99714a50d0b3966476cea2f7ed02f04a2ebf6cea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512408"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="8c6ef-102">ICorDebugSymbolProvider::GetObjectSize – metoda</span><span class="sxs-lookup"><span data-stu-id="8c6ef-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="8c6ef-103">Vrátí velikost objektu pro objekt závislosti na jeho token typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c6ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c6ef-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c6ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c6ef-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="8c6ef-106">[in] Počet bajtů v podpisu typ typespec.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="8c6ef-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="8c6ef-107">typeSig</span></span>  
 <span data-ttu-id="8c6ef-108">[in] Token typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="8c6ef-109">[out] Ukazatel na velikost objektu.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c6ef-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c6ef-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c6ef-111">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c6ef-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c6ef-112">Requirements</span></span>  
 <span data-ttu-id="8c6ef-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c6ef-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c6ef-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c6ef-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c6ef-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c6ef-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c6ef-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c6ef-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c6ef-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c6ef-117">See also</span></span>
- [<span data-ttu-id="8c6ef-118">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c6ef-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="8c6ef-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8c6ef-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
