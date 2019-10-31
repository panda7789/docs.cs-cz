---
title: 'ICorDebugVariableSymbol:: GetName – Metoda'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 9bc32d3372710b4c4e92aa89df5e6e7839ad3078
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121018"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="cbd43-102">ICorDebugVariableSymbol:: GetName – Metoda</span><span class="sxs-lookup"><span data-stu-id="cbd43-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="cbd43-103">Získá název proměnné.</span><span class="sxs-lookup"><span data-stu-id="cbd43-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbd43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbd43-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbd43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbd43-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="cbd43-106">pro Počet znaků ve vyrovnávací paměti `szName`.</span><span class="sxs-lookup"><span data-stu-id="cbd43-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="cbd43-107">mimo Ukazatel na počet znaků skutečně zapsaných do vyrovnávací paměti `szName`.</span><span class="sxs-lookup"><span data-stu-id="cbd43-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="cbd43-108">Ukazatel na pole znaků, které obsahuje název proměnné.</span><span class="sxs-lookup"><span data-stu-id="cbd43-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbd43-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cbd43-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbd43-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cbd43-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbd43-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cbd43-111">Requirements</span></span>  
 <span data-ttu-id="cbd43-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbd43-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbd43-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cbd43-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbd43-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cbd43-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbd43-115">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbd43-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbd43-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbd43-116">See also</span></span>

- [<span data-ttu-id="cbd43-117">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cbd43-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="cbd43-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cbd43-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
