---
title: 'ICorDebugSymbolProvider:: GetMethodLocalSymbols – metoda'
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
ms.openlocfilehash: 41fc8e94ec8a5c8794674bebb32494bb3806e69d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791606"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="155df-102">ICorDebugSymbolProvider:: GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="155df-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="155df-103">Načte místní symboly metody s relativní virtuální adresou (RVA) dané metody.</span><span class="sxs-lookup"><span data-stu-id="155df-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="155df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="155df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="155df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="155df-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="155df-106">pro Nativní relativní virtuální adresa metody</span><span class="sxs-lookup"><span data-stu-id="155df-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="155df-107">pro Počet požadovaných místních symbolů.</span><span class="sxs-lookup"><span data-stu-id="155df-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="155df-108">mimo Ukazatel na počet symbolů načtených metodou.</span><span class="sxs-lookup"><span data-stu-id="155df-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="155df-109">mimo Ukazatel na pole [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) , které obsahuje místní symboly metody.</span><span class="sxs-lookup"><span data-stu-id="155df-109">[out] A pointer to an [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="155df-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="155df-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="155df-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="155df-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="155df-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="155df-112">Requirements</span></span>  
 <span data-ttu-id="155df-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="155df-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="155df-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="155df-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="155df-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="155df-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="155df-116">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="155df-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="155df-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="155df-117">See also</span></span>

- [<span data-ttu-id="155df-118">GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="155df-118">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="155df-119">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="155df-119">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="155df-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="155df-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
