---
title: "ICorDebugMergedAssemblyRecord::GetSimpleName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 085ca56b3a839689ea38459057957faa81d1dfc2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="642de-102">ICorDebugMergedAssemblyRecord::GetSimpleName – metoda</span><span class="sxs-lookup"><span data-stu-id="642de-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="642de-103">Získá jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="642de-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="642de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="642de-104">Syntax</span></span>  
  
```  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="642de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="642de-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="642de-106">[v] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="642de-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="642de-107">[out] Ukazatel na počet znaků, které jsou ve skutečnosti zapsána do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="642de-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="642de-108">Ukazatel na pole znaků.</span><span class="sxs-lookup"><span data-stu-id="642de-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="642de-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="642de-109">Remarks</span></span>  
 <span data-ttu-id="642de-110">Tato metoda načte jednoduchý název sestavení (například "System.Collections"), bez přípony, verze, jazykové verze nebo tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="642de-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="642de-111">Odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnost ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="642de-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="642de-112">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="642de-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="642de-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="642de-113">Requirements</span></span>  
 <span data-ttu-id="642de-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="642de-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="642de-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="642de-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="642de-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="642de-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="642de-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="642de-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="642de-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="642de-118">See Also</span></span>  
 [<span data-ttu-id="642de-119">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="642de-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="642de-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="642de-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
