---
title: 'ICorDebugSymbolProvider:: GetStaticFieldSymbols – metoda'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bd3442adf58250a423438666ec1092bab61958b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955538"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="092ba-102">ICorDebugSymbolProvider:: GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="092ba-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="092ba-103">Získá symboly statického pole, které odpovídají token TypeSpec podpisu.</span><span class="sxs-lookup"><span data-stu-id="092ba-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="092ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="092ba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="092ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="092ba-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="092ba-106">pro Počet bajtů v `typeSig` poli.</span><span class="sxs-lookup"><span data-stu-id="092ba-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="092ba-107">pro Bajtové pole `typespec` obsahující podpis.</span><span class="sxs-lookup"><span data-stu-id="092ba-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="092ba-108">pro Počet požadovaných symbolů.</span><span class="sxs-lookup"><span data-stu-id="092ba-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="092ba-109">mimo Ukazatel na počet symbolů načtených metodou.</span><span class="sxs-lookup"><span data-stu-id="092ba-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="092ba-110">mimo Ukazatel na pole [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) , které obsahuje požadované symboly statických polí.</span><span class="sxs-lookup"><span data-stu-id="092ba-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="092ba-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="092ba-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="092ba-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="092ba-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="092ba-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="092ba-113">Requirements</span></span>  
 <span data-ttu-id="092ba-114">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="092ba-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="092ba-115">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="092ba-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="092ba-116">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="092ba-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="092ba-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="092ba-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="092ba-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="092ba-118">See also</span></span>

- [<span data-ttu-id="092ba-119">GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="092ba-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="092ba-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="092ba-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="092ba-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="092ba-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
