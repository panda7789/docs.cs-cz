---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords – metoda
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b436bd844f917aab3c653428c7cd38809be870b8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771393"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="a2029-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords – metoda</span><span class="sxs-lookup"><span data-stu-id="a2029-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="a2029-103">Získá záznamy symbolů pro sloučený sestavení.</span><span class="sxs-lookup"><span data-stu-id="a2029-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2029-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2029-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2029-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2029-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="a2029-106">[in] Počet záznamů symbol požadavku.</span><span class="sxs-lookup"><span data-stu-id="a2029-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="a2029-107">[out] Ukazatel na počet záznamů symbol načíst pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="a2029-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="a2029-108">Ukazatel na pole [icordebugmergedassemblyrecord –](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="a2029-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2029-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2029-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2029-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a2029-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2029-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2029-111">Requirements</span></span>  
 <span data-ttu-id="a2029-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2029-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2029-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2029-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2029-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2029-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2029-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2029-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2029-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2029-116">See also</span></span>

- [<span data-ttu-id="a2029-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2029-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="a2029-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a2029-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
