---
title: "ICorDebugMergedAssemblyRecord::GetVersion – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68fa2b1b7502f13876c6e613f012a0c78ab7c5d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="458b2-102">ICorDebugMergedAssemblyRecord::GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="458b2-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="458b2-103">Získá informace o verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="458b2-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="458b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="458b2-104">Syntax</span></span>  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="458b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="458b2-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="458b2-106">[out] Ukazatel na hlavní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="458b2-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="458b2-107">[out] Ukazatel na číslo podverze.</span><span class="sxs-lookup"><span data-stu-id="458b2-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="458b2-108">[out] Ukazatel na číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="458b2-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="458b2-109">[out] Ukazatel na číslo revize.</span><span class="sxs-lookup"><span data-stu-id="458b2-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="458b2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="458b2-110">Remarks</span></span>  
 <span data-ttu-id="458b2-111">Informace o sestavení čísla verzí, najdete v článku <xref:System.Version> třída tématu.</span><span class="sxs-lookup"><span data-stu-id="458b2-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="458b2-112">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="458b2-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="458b2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="458b2-113">Requirements</span></span>  
 <span data-ttu-id="458b2-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="458b2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="458b2-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="458b2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="458b2-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="458b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="458b2-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="458b2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="458b2-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="458b2-118">See Also</span></span>  
 [<span data-ttu-id="458b2-119">ICorDebugMergedAssemblyRecord rozhraní</span><span class="sxs-lookup"><span data-stu-id="458b2-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="458b2-120">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="458b2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
