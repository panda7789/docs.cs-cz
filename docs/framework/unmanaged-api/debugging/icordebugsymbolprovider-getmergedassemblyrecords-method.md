---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords – metoda
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 502e7e0b52bb147b5fe37dcc6e4f6d13d642b6f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417541"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="ba023-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords – metoda</span><span class="sxs-lookup"><span data-stu-id="ba023-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="ba023-103">Získá záznamy symbol pro sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="ba023-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba023-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba023-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba023-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba023-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="ba023-106">[v] Počet záznamů symbol požadovaný.</span><span class="sxs-lookup"><span data-stu-id="ba023-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="ba023-107">[out] Ukazatel na počet záznamů symbol načíst metodu.</span><span class="sxs-lookup"><span data-stu-id="ba023-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="ba023-108">Ukazatel na pole [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="ba023-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba023-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba023-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba023-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="ba023-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba023-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba023-111">Requirements</span></span>  
 <span data-ttu-id="ba023-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba023-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba023-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba023-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba023-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba023-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba023-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba023-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba023-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba023-116">See Also</span></span>  
 [<span data-ttu-id="ba023-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba023-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="ba023-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ba023-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
