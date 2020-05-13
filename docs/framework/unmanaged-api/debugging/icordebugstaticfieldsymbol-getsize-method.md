---
title: 'ICorDebugStaticFieldSymbol:: GetSize – metoda'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: e36c94bf411e75f915cca86aee74cdf161674d25
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379416"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="0ec63-102">ICorDebugStaticFieldSymbol:: GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="0ec63-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="0ec63-103">Získá velikost statického pole v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0ec63-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ec63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ec63-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ec63-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ec63-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="0ec63-106">mimo Ukazatel na délku pole.</span><span class="sxs-lookup"><span data-stu-id="0ec63-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ec63-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ec63-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ec63-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0ec63-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ec63-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ec63-109">Requirements</span></span>  
 <span data-ttu-id="0ec63-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ec63-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ec63-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0ec63-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ec63-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0ec63-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ec63-113">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ec63-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ec63-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ec63-114">See also</span></span>

- [<span data-ttu-id="0ec63-115">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ec63-115">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="0ec63-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ec63-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
