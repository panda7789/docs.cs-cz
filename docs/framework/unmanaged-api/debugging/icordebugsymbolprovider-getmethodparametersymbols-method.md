---
title: 'ICorDebugSymbolProvider:: GetMethodParameterSymbols – metoda'
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
ms.openlocfilehash: 051002b547aaa9745ae4efb516211123089c3128
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379601"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="d594c-102">ICorDebugSymbolProvider:: GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="d594c-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="d594c-103">Načte symboly parametrů metody vzhledem k relativní virtuální adrese (RVA) dané metody.</span><span class="sxs-lookup"><span data-stu-id="d594c-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d594c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d594c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d594c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d594c-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="d594c-106">pro Nativní relativní virtuální adresa metody</span><span class="sxs-lookup"><span data-stu-id="d594c-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="d594c-107">pro Počet požadovaných místních symbolů.</span><span class="sxs-lookup"><span data-stu-id="d594c-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="d594c-108">mimo Ukazatel na počet symbolů načtených metodou.</span><span class="sxs-lookup"><span data-stu-id="d594c-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="d594c-109">mimo Ukazatel na pole [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) , které obsahuje místní symboly metody.</span><span class="sxs-lookup"><span data-stu-id="d594c-109">[out] A pointer to an [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d594c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d594c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d594c-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d594c-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d594c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d594c-112">Requirements</span></span>  
 <span data-ttu-id="d594c-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d594c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d594c-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d594c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d594c-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d594c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d594c-116">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d594c-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d594c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d594c-117">See also</span></span>

- [<span data-ttu-id="d594c-118">GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="d594c-118">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="d594c-119">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d594c-119">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="d594c-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d594c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
