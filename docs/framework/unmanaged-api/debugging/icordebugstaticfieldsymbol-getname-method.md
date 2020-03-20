---
title: ICorDebugStaticFieldSymbol::Metoda GetName
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: b1f5ca266f51df730dfb840c7bf003c47f31ece9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178513"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="47efe-102">ICorDebugStaticFieldSymbol::Metoda GetName</span><span class="sxs-lookup"><span data-stu-id="47efe-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="47efe-103">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="47efe-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47efe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47efe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47efe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="47efe-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="47efe-106">[v] Počet znaků ve `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="47efe-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="47efe-107">[out] Ukazatel na počet znaků skutečně zapsaných do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="47efe-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="47efe-108">[out] Pole znaků, které ukládá vrácený název.</span><span class="sxs-lookup"><span data-stu-id="47efe-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47efe-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47efe-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47efe-110">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="47efe-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47efe-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47efe-111">Requirements</span></span>  
 <span data-ttu-id="47efe-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47efe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47efe-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47efe-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47efe-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47efe-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47efe-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47efe-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47efe-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="47efe-116">See also</span></span>

- [<span data-ttu-id="47efe-117">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47efe-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="47efe-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47efe-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
