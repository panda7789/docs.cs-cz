---
title: 'ICorDebugSymbolProvider:: GetObjectSize – – metoda'
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: 64324df49ad0b5dfa3c25455950bddc3d687b178
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379559"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="84077-102">ICorDebugSymbolProvider:: GetObjectSize – – metoda</span><span class="sxs-lookup"><span data-stu-id="84077-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="84077-103">Vrátí velikost objektu objektu na základě jeho signatury token TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="84077-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84077-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84077-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84077-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84077-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="84077-106">pro Počet bajtů v signatuře token TypeSpec</span><span class="sxs-lookup"><span data-stu-id="84077-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="84077-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="84077-107">typeSig</span></span>  
 <span data-ttu-id="84077-108">pro Signatura token TypeSpec</span><span class="sxs-lookup"><span data-stu-id="84077-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="84077-109">mimo Ukazatel na velikost objektu.</span><span class="sxs-lookup"><span data-stu-id="84077-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84077-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84077-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84077-111">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="84077-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84077-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84077-112">Requirements</span></span>  
 <span data-ttu-id="84077-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84077-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84077-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="84077-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84077-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="84077-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84077-116">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84077-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84077-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="84077-117">See also</span></span>

- [<span data-ttu-id="84077-118">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84077-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="84077-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84077-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
