---
title: 'ICorDebugSymbolProvider:: GetStaticFieldSymbols – metoda'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: 02cc62a421058f83e28ce945ae9e76745f768988
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791557"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="00a68-102">ICorDebugSymbolProvider:: GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="00a68-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="00a68-103">Získá symboly statického pole, které odpovídají token TypeSpec podpisu.</span><span class="sxs-lookup"><span data-stu-id="00a68-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00a68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00a68-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00a68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00a68-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="00a68-106">pro Počet bajtů v poli `typeSig`.</span><span class="sxs-lookup"><span data-stu-id="00a68-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="00a68-107">pro Bajtové pole obsahující podpis `typespec`.</span><span class="sxs-lookup"><span data-stu-id="00a68-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="00a68-108">pro Počet požadovaných symbolů.</span><span class="sxs-lookup"><span data-stu-id="00a68-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="00a68-109">mimo Ukazatel na počet symbolů načtených metodou.</span><span class="sxs-lookup"><span data-stu-id="00a68-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="00a68-110">mimo Ukazatel na pole [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) , které obsahuje požadované symboly statických polí.</span><span class="sxs-lookup"><span data-stu-id="00a68-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00a68-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00a68-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00a68-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="00a68-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00a68-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00a68-113">Requirements</span></span>  
 <span data-ttu-id="00a68-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00a68-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00a68-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="00a68-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00a68-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="00a68-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00a68-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00a68-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a68-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00a68-118">See also</span></span>

- [<span data-ttu-id="00a68-119">GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="00a68-119">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="00a68-120">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00a68-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="00a68-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="00a68-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
