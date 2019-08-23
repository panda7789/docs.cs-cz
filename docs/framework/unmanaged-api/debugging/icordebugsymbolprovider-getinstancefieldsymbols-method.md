---
title: 'ICorDebugSymbolProvider:: GetInstanceFieldSymbols – metoda'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6bba47500b024bc1f2a2be21d461a6f5933f0ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964612"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="28168-102">ICorDebugSymbolProvider:: GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="28168-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="28168-103">Načte symboly pole instance, které odpovídají token TypeSpec podpisu.</span><span class="sxs-lookup"><span data-stu-id="28168-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28168-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28168-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28168-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28168-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="28168-106">pro Počet bajtů v `typeSig` poli.</span><span class="sxs-lookup"><span data-stu-id="28168-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="28168-107">pro Bajtové pole `typespec` obsahující podpis.</span><span class="sxs-lookup"><span data-stu-id="28168-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="28168-108">pro Počet požadovaných symbolů.</span><span class="sxs-lookup"><span data-stu-id="28168-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="28168-109">mimo Ukazatel na počet symbolů načtených metodou.</span><span class="sxs-lookup"><span data-stu-id="28168-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="28168-110">mimo Ukazatel na pole [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) , které obsahuje symboly pole požadované instance.</span><span class="sxs-lookup"><span data-stu-id="28168-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28168-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28168-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28168-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28168-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28168-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28168-113">Requirements</span></span>  
 <span data-ttu-id="28168-114">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28168-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28168-115">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="28168-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28168-116">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28168-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28168-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28168-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28168-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28168-118">See also</span></span>

- [<span data-ttu-id="28168-119">GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="28168-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="28168-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28168-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="28168-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="28168-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
