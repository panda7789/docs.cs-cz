---
title: ICorDebugInstanceFieldSymbol::Metoda GetName
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: dd925cc213ed8a6c5d1def85b3e6335751c1b594
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178763"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="21f30-102">ICorDebugInstanceFieldSymbol::Metoda GetName</span><span class="sxs-lookup"><span data-stu-id="21f30-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="21f30-103">Získá název pole instance.</span><span class="sxs-lookup"><span data-stu-id="21f30-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21f30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21f30-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21f30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21f30-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="21f30-106">[v] Počet znaků ve `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="21f30-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="21f30-107">[out] Ukazatel na počet znaků skutečně zapsaných do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="21f30-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="21f30-108">[out] Pole znaků, které ukládá vrácený název.</span><span class="sxs-lookup"><span data-stu-id="21f30-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21f30-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21f30-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21f30-110">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="21f30-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21f30-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21f30-111">Requirements</span></span>  
 <span data-ttu-id="21f30-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21f30-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21f30-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21f30-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21f30-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21f30-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21f30-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21f30-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f30-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="21f30-116">See also</span></span>

- [<span data-ttu-id="21f30-117">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21f30-117">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="21f30-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21f30-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
