---
title: 'ICorDebugSymbolProvider:: GetStaticFieldSymbols – metoda'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: 2428521b9b08060fd147a7c9b9054239bf957f69
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379379"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="794c7-102">ICorDebugSymbolProvider:: GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="794c7-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="794c7-103">Získá symboly statického pole, které odpovídají token TypeSpec podpisu.</span><span class="sxs-lookup"><span data-stu-id="794c7-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="794c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="794c7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="794c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="794c7-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="794c7-106">pro Počet bajtů v `typeSig` poli.</span><span class="sxs-lookup"><span data-stu-id="794c7-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="794c7-107">pro Bajtové pole obsahující `typespec` podpis.</span><span class="sxs-lookup"><span data-stu-id="794c7-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="794c7-108">pro Počet požadovaných symbolů.</span><span class="sxs-lookup"><span data-stu-id="794c7-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="794c7-109">mimo Ukazatel na počet symbolů načtených metodou.</span><span class="sxs-lookup"><span data-stu-id="794c7-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="794c7-110">mimo Ukazatel na pole [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) , které obsahuje požadované symboly statických polí.</span><span class="sxs-lookup"><span data-stu-id="794c7-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="794c7-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="794c7-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="794c7-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="794c7-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="794c7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="794c7-113">Requirements</span></span>  
 <span data-ttu-id="794c7-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="794c7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="794c7-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="794c7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="794c7-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="794c7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="794c7-117">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="794c7-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="794c7-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="794c7-118">See also</span></span>

- [<span data-ttu-id="794c7-119">GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="794c7-119">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="794c7-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="794c7-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="794c7-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="794c7-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
