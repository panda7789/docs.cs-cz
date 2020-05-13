---
title: 'ICorDebugSymbolProvider:: GetMethodLocalSymbols – metoda'
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
ms.openlocfilehash: 7e9aa01a3fa1c90b0ab4f85970c4eb294b9a4904
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379616"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="3dc3e-102">ICorDebugSymbolProvider:: GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="3dc3e-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="3dc3e-103">Načte místní symboly metody s relativní virtuální adresou (RVA) dané metody.</span><span class="sxs-lookup"><span data-stu-id="3dc3e-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dc3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dc3e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dc3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3dc3e-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="3dc3e-106">pro Nativní relativní virtuální adresa metody</span><span class="sxs-lookup"><span data-stu-id="3dc3e-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="3dc3e-107">pro Počet požadovaných místních symbolů.</span><span class="sxs-lookup"><span data-stu-id="3dc3e-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="3dc3e-108">mimo Ukazatel na počet symbolů načtených metodou.</span><span class="sxs-lookup"><span data-stu-id="3dc3e-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="3dc3e-109">mimo Ukazatel na pole [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) , které obsahuje místní symboly metody.</span><span class="sxs-lookup"><span data-stu-id="3dc3e-109">[out] A pointer to an [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dc3e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3dc3e-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3dc3e-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3dc3e-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dc3e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3dc3e-112">Requirements</span></span>  
 <span data-ttu-id="3dc3e-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dc3e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dc3e-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3dc3e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dc3e-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3dc3e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dc3e-116">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dc3e-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc3e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dc3e-117">See also</span></span>

- [<span data-ttu-id="3dc3e-118">GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="3dc3e-118">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="3dc3e-119">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3dc3e-119">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="3dc3e-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3dc3e-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
