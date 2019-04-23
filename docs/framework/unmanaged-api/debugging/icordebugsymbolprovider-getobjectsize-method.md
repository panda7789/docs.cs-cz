---
title: ICorDebugSymbolProvider::GetObjectSize – metoda
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbcdb5541fdd49944f462321dc24131a32a42391
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107286"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="212af-102">ICorDebugSymbolProvider::GetObjectSize – metoda</span><span class="sxs-lookup"><span data-stu-id="212af-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="212af-103">Vrátí velikost objektu pro objekt závislosti na jeho token typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="212af-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="212af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="212af-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="212af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="212af-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="212af-106">[in] Počet bajtů v podpisu typ typespec.</span><span class="sxs-lookup"><span data-stu-id="212af-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="212af-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="212af-107">typeSig</span></span>  
 <span data-ttu-id="212af-108">[in] Token typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="212af-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="212af-109">[out] Ukazatel na velikost objektu.</span><span class="sxs-lookup"><span data-stu-id="212af-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="212af-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="212af-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="212af-111">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="212af-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="212af-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="212af-112">Requirements</span></span>  
 <span data-ttu-id="212af-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="212af-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="212af-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="212af-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="212af-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="212af-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="212af-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="212af-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="212af-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="212af-117">See also</span></span>

- [<span data-ttu-id="212af-118">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="212af-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="212af-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="212af-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
