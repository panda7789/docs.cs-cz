---
title: ICorDebugSymbolProvider::GetObjectSize – metoda
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1da526ac133604fa43081f86988459c4238517c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421500"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="16e75-102">ICorDebugSymbolProvider::GetObjectSize – metoda</span><span class="sxs-lookup"><span data-stu-id="16e75-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="16e75-103">Vrátí velikost objektu pro objekt podle jeho typ typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="16e75-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16e75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16e75-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16e75-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16e75-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="16e75-106">[v] Počet bajtů v typ typespec podpisu.</span><span class="sxs-lookup"><span data-stu-id="16e75-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="16e75-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="16e75-107">typeSig</span></span>  
 <span data-ttu-id="16e75-108">[v] Typ typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="16e75-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="16e75-109">[out] Ukazatel na velikost objektu.</span><span class="sxs-lookup"><span data-stu-id="16e75-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16e75-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16e75-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16e75-111">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="16e75-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16e75-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16e75-112">Requirements</span></span>  
 <span data-ttu-id="16e75-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16e75-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16e75-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16e75-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16e75-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16e75-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16e75-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16e75-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16e75-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="16e75-117">See Also</span></span>  
 [<span data-ttu-id="16e75-118">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16e75-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="16e75-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="16e75-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
