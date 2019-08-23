---
title: 'ICorDebugSymbolProvider:: GetObjectSize – – metoda'
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59054d7b939ab29cb08c30961601a323529ce06b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955633"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="52789-102">ICorDebugSymbolProvider:: GetObjectSize – – metoda</span><span class="sxs-lookup"><span data-stu-id="52789-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="52789-103">Vrátí velikost objektu objektu na základě jeho signatury token TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="52789-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52789-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52789-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52789-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52789-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="52789-106">pro Počet bajtů v signatuře token TypeSpec</span><span class="sxs-lookup"><span data-stu-id="52789-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="52789-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="52789-107">typeSig</span></span>  
 <span data-ttu-id="52789-108">pro Signatura token TypeSpec</span><span class="sxs-lookup"><span data-stu-id="52789-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="52789-109">mimo Ukazatel na velikost objektu.</span><span class="sxs-lookup"><span data-stu-id="52789-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52789-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52789-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52789-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="52789-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52789-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52789-112">Requirements</span></span>  
 <span data-ttu-id="52789-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52789-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52789-114">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="52789-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52789-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52789-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52789-116">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52789-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52789-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52789-117">See also</span></span>

- [<span data-ttu-id="52789-118">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52789-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="52789-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="52789-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
