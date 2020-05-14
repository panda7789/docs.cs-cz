---
title: 'ICorDebugVariableSymbol:: GetName – Metoda'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: ea414a39e140c74df736764dbbb1bb3934bda78f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397131"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="77ca5-102">ICorDebugVariableSymbol:: GetName – Metoda</span><span class="sxs-lookup"><span data-stu-id="77ca5-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="77ca5-103">Získá název proměnné.</span><span class="sxs-lookup"><span data-stu-id="77ca5-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77ca5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77ca5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77ca5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77ca5-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="77ca5-106">pro Počet znaků ve `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="77ca5-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="77ca5-107">mimo Ukazatel na počet znaků skutečně zapsaných do `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="77ca5-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="77ca5-108">Ukazatel na pole znaků, které obsahuje název proměnné.</span><span class="sxs-lookup"><span data-stu-id="77ca5-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77ca5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77ca5-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77ca5-110">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="77ca5-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77ca5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77ca5-111">Requirements</span></span>  
 <span data-ttu-id="77ca5-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77ca5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77ca5-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="77ca5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77ca5-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="77ca5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77ca5-115">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77ca5-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77ca5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="77ca5-116">See also</span></span>

- [<span data-ttu-id="77ca5-117">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77ca5-117">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="77ca5-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77ca5-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
