---
title: "ICorDebugMergedAssemblyRecord::GetCulture – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7791491a050e31d8d6c5dfb6ef9ffe209921753d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="5a993-102">ICorDebugMergedAssemblyRecord::GetCulture – metoda</span><span class="sxs-lookup"><span data-stu-id="5a993-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="5a993-103">Získá řetězec název jazykové verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="5a993-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a993-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a993-104">Syntax</span></span>  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a993-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a993-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="5a993-106">[v] Počet znaků `szCulture` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5a993-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="5a993-107">[out] Počet znaků, které jsou ve skutečnosti zapsána do `szCulture` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5a993-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="5a993-108">[out] Pole znaků, který obsahuje název jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="5a993-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a993-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a993-109">Remarks</span></span>  
 <span data-ttu-id="5a993-110">Název jazykové verze je jedinečný řetězec, který určuje jazykovou verzi, jako je například "en US" (pro jazykovou verzi Czech (Czech Republic)), nebo "neutrální" (pro neutrální jazykovou verzi).</span><span class="sxs-lookup"><span data-stu-id="5a993-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a993-111">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="5a993-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a993-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a993-112">Requirements</span></span>  
 <span data-ttu-id="5a993-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a993-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a993-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a993-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a993-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a993-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a993-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a993-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a993-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a993-117">See Also</span></span>  
 [<span data-ttu-id="5a993-118">ICorDebugMergedAssemblyRecord rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a993-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="5a993-119">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a993-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
