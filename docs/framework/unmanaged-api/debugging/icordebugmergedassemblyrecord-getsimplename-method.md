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
ms.openlocfilehash: c0bf7bb3f52e76c34c03b322d7d6e82fa65adf8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="71706-102">ICorDebugMergedAssemblyRecord::GetSimpleName – metoda</span><span class="sxs-lookup"><span data-stu-id="71706-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="71706-103">Získá jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="71706-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71706-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71706-104">Syntax</span></span>  
  
```  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71706-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71706-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="71706-106">[v] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="71706-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="71706-107">[out] Ukazatel na počet znaků, které jsou ve skutečnosti zapsána do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="71706-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="71706-108">Ukazatel na pole znaků.</span><span class="sxs-lookup"><span data-stu-id="71706-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71706-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71706-109">Remarks</span></span>  
 <span data-ttu-id="71706-110">Tato metoda načte jednoduchý název sestavení (například "System.Collections"), bez přípony, verze, jazykové verze nebo tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="71706-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="71706-111">Odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnost ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="71706-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71706-112">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="71706-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71706-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71706-113">Requirements</span></span>  
 <span data-ttu-id="71706-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71706-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71706-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71706-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71706-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71706-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71706-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71706-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71706-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="71706-118">See Also</span></span>  
 [<span data-ttu-id="71706-119">ICorDebugMergedAssemblyRecord rozhraní</span><span class="sxs-lookup"><span data-stu-id="71706-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="71706-120">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="71706-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
