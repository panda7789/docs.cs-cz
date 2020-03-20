---
title: ICorDebugVariableSymbol::Metoda GetName
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: abc0e368f259df1a3542b0fc8e7fbfd7e06cf6eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178445"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="58311-102">ICorDebugVariableSymbol::Metoda GetName</span><span class="sxs-lookup"><span data-stu-id="58311-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="58311-103">Získá název proměnné.</span><span class="sxs-lookup"><span data-stu-id="58311-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58311-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58311-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58311-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="58311-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="58311-106">[v] Počet znaků ve `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="58311-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="58311-107">[out] Ukazatel na počet znaků skutečně zapsaných do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="58311-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="58311-108">Ukazatel na pole znaků, které obsahuje název proměnné.</span><span class="sxs-lookup"><span data-stu-id="58311-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58311-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58311-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58311-110">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="58311-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58311-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58311-111">Requirements</span></span>  
 <span data-ttu-id="58311-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58311-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58311-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58311-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58311-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58311-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58311-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58311-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58311-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="58311-116">See also</span></span>

- [<span data-ttu-id="58311-117">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58311-117">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="58311-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58311-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
