---
title: "ICorDebugInstanceFieldSymbol::GetName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfd56230d391c44343bdb3f575247b07af1e98ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="2f8ec-102">ICorDebugInstanceFieldSymbol::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="2f8ec-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="2f8ec-103">Získá název pole instance.</span><span class="sxs-lookup"><span data-stu-id="2f8ec-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f8ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f8ec-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f8ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f8ec-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2f8ec-106">[v] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2f8ec-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2f8ec-107">[out] Ukazatel na počet znaků, které jsou ve skutečnosti zapsána do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2f8ec-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="2f8ec-108">[out] Pole znaků, který ukládá vrácený název.</span><span class="sxs-lookup"><span data-stu-id="2f8ec-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f8ec-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f8ec-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f8ec-110">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="2f8ec-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f8ec-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f8ec-111">Requirements</span></span>  
 <span data-ttu-id="2f8ec-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f8ec-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f8ec-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f8ec-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f8ec-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f8ec-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f8ec-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f8ec-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f8ec-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f8ec-116">See Also</span></span>  
 [<span data-ttu-id="2f8ec-117">ICorDebugInstanceFieldSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f8ec-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="2f8ec-118">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f8ec-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
