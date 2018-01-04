---
title: Metoda ICorDebugLoadedModule::GetName
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 605bbaf1e98983af222a99bada1ca9451fe9337e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="814f6-102">Metoda ICorDebugLoadedModule::GetName</span><span class="sxs-lookup"><span data-stu-id="814f6-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="814f6-103">Získá název načíst modulu.</span><span class="sxs-lookup"><span data-stu-id="814f6-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="814f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="814f6-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="814f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="814f6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="814f6-106">[v] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="814f6-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="814f6-107">[out] Ukazatel na počet znaků, které jsou ve skutečnosti zapsána do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="814f6-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="814f6-108">[out] Pole znaků, které obsahují název načíst modulu.</span><span class="sxs-lookup"><span data-stu-id="814f6-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="814f6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="814f6-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="814f6-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="814f6-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="814f6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="814f6-111">Requirements</span></span>  
 <span data-ttu-id="814f6-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="814f6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="814f6-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="814f6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="814f6-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="814f6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="814f6-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="814f6-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="814f6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="814f6-116">See Also</span></span>  
 [<span data-ttu-id="814f6-117">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="814f6-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="814f6-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="814f6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
