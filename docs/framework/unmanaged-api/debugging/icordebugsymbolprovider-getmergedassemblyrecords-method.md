---
title: 'ICorDebugSymbolProvider:: GetMergedAssemblyRecords – metoda'
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: 6faf8960c06488c8fff5a076aae375529e1d0260
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138884"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="2b2b8-102">ICorDebugSymbolProvider:: GetMergedAssemblyRecords – metoda</span><span class="sxs-lookup"><span data-stu-id="2b2b8-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="2b2b8-103">Získá záznamy symbolů pro všechna Sloučená sestavení.</span><span class="sxs-lookup"><span data-stu-id="2b2b8-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b2b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b2b8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b2b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b2b8-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="2b2b8-106">pro Počet vyžádaných záznamů symbolů.</span><span class="sxs-lookup"><span data-stu-id="2b2b8-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="2b2b8-107">mimo Ukazatel na počet záznamů symbolů načtených metodou.</span><span class="sxs-lookup"><span data-stu-id="2b2b8-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="2b2b8-108">Ukazatel na pole objektů [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2b2b8-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b2b8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b2b8-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b2b8-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2b2b8-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b2b8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b2b8-111">Requirements</span></span>  
 <span data-ttu-id="2b2b8-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b2b8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b2b8-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2b2b8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b2b8-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2b2b8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b2b8-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b2b8-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b2b8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b2b8-116">See also</span></span>

- [<span data-ttu-id="2b2b8-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b2b8-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="2b2b8-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2b2b8-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
