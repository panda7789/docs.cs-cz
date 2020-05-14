---
title: 'ICorDebugVariableSymbol:: GetValue – metoda'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: f217f7226d53a27363f66eb90a340fd3604a0217
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396521"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="27f7d-102">ICorDebugVariableSymbol:: GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="27f7d-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="27f7d-103">Získá hodnotu proměnné jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="27f7d-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27f7d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27f7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27f7d-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="27f7d-106">pro Počáteční posun v proměnné, ze které se má číst hodnota</span><span class="sxs-lookup"><span data-stu-id="27f7d-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="27f7d-107">Tento parametr se používá při čtení polí členů v objektu.</span><span class="sxs-lookup"><span data-stu-id="27f7d-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="27f7d-108">pro Velikost argumentu v bajtech `context`</span><span class="sxs-lookup"><span data-stu-id="27f7d-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="27f7d-109">pro Kontext vlákna použitý ke čtení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="27f7d-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="27f7d-110">pro Velikost vyrovnávací paměti v bajtech `pValue` .</span><span class="sxs-lookup"><span data-stu-id="27f7d-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="27f7d-111">mimo Počet bajtů, které jsou ve skutečnosti zapsány do `pValue` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="27f7d-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="27f7d-112">mimo Bajtové pole, které obsahuje hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="27f7d-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27f7d-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27f7d-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27f7d-114">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="27f7d-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27f7d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27f7d-115">Requirements</span></span>  
 <span data-ttu-id="27f7d-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27f7d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27f7d-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="27f7d-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27f7d-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="27f7d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27f7d-119">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27f7d-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f7d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="27f7d-120">See also</span></span>

- [<span data-ttu-id="27f7d-121">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27f7d-121">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="27f7d-122">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27f7d-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
