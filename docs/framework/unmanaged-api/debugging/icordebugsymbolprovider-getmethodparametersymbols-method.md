---
title: 'ICorDebugSymbolProvider:: GetMethodParameterSymbols – metoda'
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
ms.openlocfilehash: 1f7da156e5a164dc753e2283bc7ab24d18983173
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138846"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="20c16-102">ICorDebugSymbolProvider:: GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="20c16-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="20c16-103">Načte symboly parametrů metody vzhledem k relativní virtuální adrese (RVA) dané metody.</span><span class="sxs-lookup"><span data-stu-id="20c16-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20c16-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20c16-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20c16-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20c16-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="20c16-106">pro Nativní relativní virtuální adresa metody</span><span class="sxs-lookup"><span data-stu-id="20c16-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="20c16-107">pro Počet požadovaných místních symbolů.</span><span class="sxs-lookup"><span data-stu-id="20c16-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="20c16-108">mimo Ukazatel na počet symbolů načtených metodou.</span><span class="sxs-lookup"><span data-stu-id="20c16-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="20c16-109">mimo Ukazatel na pole [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) , které obsahuje místní symboly metody.</span><span class="sxs-lookup"><span data-stu-id="20c16-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20c16-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20c16-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20c16-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="20c16-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20c16-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20c16-112">Requirements</span></span>  
 <span data-ttu-id="20c16-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20c16-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20c16-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="20c16-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20c16-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="20c16-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20c16-116">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20c16-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20c16-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20c16-117">See also</span></span>

- [<span data-ttu-id="20c16-118">GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="20c16-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="20c16-119">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20c16-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="20c16-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="20c16-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
