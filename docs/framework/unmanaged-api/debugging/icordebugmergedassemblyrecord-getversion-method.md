---
title: 'ICorDebugMergedAssemblyRecord:: GetVersion – metoda'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d9133ab1b7d3985d3a383bb36dcbea315548c00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939930"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="36a6c-102">ICorDebugMergedAssemblyRecord:: GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="36a6c-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="36a6c-103">Získá informace o verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="36a6c-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36a6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36a6c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36a6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36a6c-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="36a6c-106">mimo Ukazatel na hlavní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="36a6c-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="36a6c-107">mimo Ukazatel na číslo dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="36a6c-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="36a6c-108">mimo Ukazatel na číslo buildu.</span><span class="sxs-lookup"><span data-stu-id="36a6c-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="36a6c-109">mimo Ukazatel na číslo revize.</span><span class="sxs-lookup"><span data-stu-id="36a6c-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36a6c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36a6c-110">Remarks</span></span>  
 <span data-ttu-id="36a6c-111">Informace o číslech verzí sestavení naleznete <xref:System.Version> v tématu třídy.</span><span class="sxs-lookup"><span data-stu-id="36a6c-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36a6c-112">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36a6c-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36a6c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36a6c-113">Requirements</span></span>  
 <span data-ttu-id="36a6c-114">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36a6c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36a6c-115">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="36a6c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36a6c-116">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36a6c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36a6c-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36a6c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36a6c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36a6c-118">See also</span></span>

- [<span data-ttu-id="36a6c-119">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36a6c-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="36a6c-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="36a6c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
