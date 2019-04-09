---
title: ICorDebugMergedAssemblyRecord::GetVersion – metoda
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36cf8647b3caafeaae2db3c2fd53471496e922fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109536"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="20877-102">ICorDebugMergedAssemblyRecord::GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="20877-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="20877-103">Získá informace o verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="20877-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20877-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20877-104">Syntax</span></span>  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20877-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20877-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="20877-106">[out] Ukazatel na číslo hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="20877-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="20877-107">[out] Ukazatel na číslo podverze.</span><span class="sxs-lookup"><span data-stu-id="20877-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="20877-108">[out] Ukazatel na číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="20877-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="20877-109">[out] Ukazatel na číslo revize.</span><span class="sxs-lookup"><span data-stu-id="20877-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20877-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20877-110">Remarks</span></span>  
 <span data-ttu-id="20877-111">Informace o číslech verzí sestavení, najdete v článku <xref:System.Version> třídě.</span><span class="sxs-lookup"><span data-stu-id="20877-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20877-112">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="20877-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20877-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20877-113">Requirements</span></span>  
 <span data-ttu-id="20877-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20877-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20877-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20877-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20877-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20877-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="20877-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="20877-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="20877-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20877-118">See also</span></span>

- [<span data-ttu-id="20877-119">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20877-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="20877-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20877-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
