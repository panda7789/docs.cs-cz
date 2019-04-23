---
title: ICorDebugInstanceFieldSymbol::GetName – metoda
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d23bf14fbb3d75534ac2d4a43eca0fbf3e994ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59161392"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="a3b07-102">ICorDebugInstanceFieldSymbol::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="a3b07-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="a3b07-103">Získá název pole instance.</span><span class="sxs-lookup"><span data-stu-id="a3b07-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3b07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3b07-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3b07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3b07-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="a3b07-106">[in] Počet znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a3b07-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a3b07-107">[out] Ukazatel na počet aktuálně zapsaných do znaků `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a3b07-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="a3b07-108">[out] Pole znaků, která ukládá vrácený název.</span><span class="sxs-lookup"><span data-stu-id="a3b07-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3b07-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3b07-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3b07-110">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a3b07-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3b07-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3b07-111">Requirements</span></span>  
 <span data-ttu-id="a3b07-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3b07-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3b07-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3b07-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3b07-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3b07-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3b07-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3b07-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b07-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3b07-116">See also</span></span>

- [<span data-ttu-id="a3b07-117">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3b07-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="a3b07-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a3b07-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
