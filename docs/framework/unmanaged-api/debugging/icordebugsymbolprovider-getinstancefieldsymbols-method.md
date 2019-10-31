---
title: 'ICorDebugSymbolProvider:: GetInstanceFieldSymbols – metoda'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 0ad8ddd78d963681c0b2f69bf0f211ad464dc7b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138873"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="92051-102">ICorDebugSymbolProvider:: GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="92051-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="92051-103">Načte symboly pole instance, které odpovídají token TypeSpec podpisu.</span><span class="sxs-lookup"><span data-stu-id="92051-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92051-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92051-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92051-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92051-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="92051-106">pro Počet bajtů v poli `typeSig`.</span><span class="sxs-lookup"><span data-stu-id="92051-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="92051-107">pro Bajtové pole obsahující podpis `typespec`.</span><span class="sxs-lookup"><span data-stu-id="92051-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="92051-108">pro Počet požadovaných symbolů.</span><span class="sxs-lookup"><span data-stu-id="92051-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="92051-109">mimo Ukazatel na počet symbolů načtených metodou.</span><span class="sxs-lookup"><span data-stu-id="92051-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="92051-110">mimo Ukazatel na pole [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) , které obsahuje symboly pole požadované instance.</span><span class="sxs-lookup"><span data-stu-id="92051-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92051-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92051-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92051-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="92051-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92051-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92051-113">Requirements</span></span>  
 <span data-ttu-id="92051-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92051-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92051-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="92051-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92051-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="92051-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92051-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92051-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92051-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92051-118">See also</span></span>

- [<span data-ttu-id="92051-119">GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="92051-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="92051-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92051-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="92051-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="92051-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
