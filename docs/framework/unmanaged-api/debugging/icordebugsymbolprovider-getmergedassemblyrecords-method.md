---
title: "ICorDebugSymbolProvider::GetMergedAssemblyRecords – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75c8a98b4e7b2e3250adfb75a5d2dcb29a71ff27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="7eb6a-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords – metoda</span><span class="sxs-lookup"><span data-stu-id="7eb6a-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="7eb6a-103">Získá záznamy symbol pro sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="7eb6a-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eb6a-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7eb6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7eb6a-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="7eb6a-106">[v] Počet záznamů symbol požadovaný.</span><span class="sxs-lookup"><span data-stu-id="7eb6a-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="7eb6a-107">[out] Ukazatel na počet záznamů symbol načíst metodu.</span><span class="sxs-lookup"><span data-stu-id="7eb6a-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="7eb6a-108">Ukazatel na pole [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="7eb6a-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7eb6a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7eb6a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7eb6a-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="7eb6a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eb6a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7eb6a-111">Requirements</span></span>  
 <span data-ttu-id="7eb6a-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eb6a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eb6a-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7eb6a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7eb6a-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7eb6a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7eb6a-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eb6a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eb6a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7eb6a-116">See Also</span></span>  
 [<span data-ttu-id="7eb6a-117">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7eb6a-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="7eb6a-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7eb6a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
