---
title: 'ICorDebugSymbolProvider:: GetObjectSize – – metoda'
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: a5c0fe6d73302abbfabe2272cc878d6fd8f5fdec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138820"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="e9cc4-102">ICorDebugSymbolProvider:: GetObjectSize – – metoda</span><span class="sxs-lookup"><span data-stu-id="e9cc4-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="e9cc4-103">Vrátí velikost objektu objektu na základě jeho signatury token TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="e9cc4-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9cc4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9cc4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9cc4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9cc4-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="e9cc4-106">pro Počet bajtů v signatuře token TypeSpec</span><span class="sxs-lookup"><span data-stu-id="e9cc4-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="e9cc4-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="e9cc4-107">typeSig</span></span>  
 <span data-ttu-id="e9cc4-108">pro Signatura token TypeSpec</span><span class="sxs-lookup"><span data-stu-id="e9cc4-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="e9cc4-109">mimo Ukazatel na velikost objektu.</span><span class="sxs-lookup"><span data-stu-id="e9cc4-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9cc4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9cc4-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9cc4-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e9cc4-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9cc4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9cc4-112">Requirements</span></span>  
 <span data-ttu-id="e9cc4-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9cc4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9cc4-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e9cc4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9cc4-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e9cc4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9cc4-116">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9cc4-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9cc4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9cc4-117">See also</span></span>

- [<span data-ttu-id="e9cc4-118">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9cc4-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="e9cc4-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e9cc4-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
