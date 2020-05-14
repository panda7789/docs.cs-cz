---
title: 'ICorDebugVariableSymbol:: GetSize – metoda'
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: d924de33c8ec49501be0ee7700b2eee8c79bb950
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397112"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="65ed6-102">ICorDebugVariableSymbol:: GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="65ed6-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="65ed6-103">Získá velikost proměnné v bajtech.</span><span class="sxs-lookup"><span data-stu-id="65ed6-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ed6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65ed6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65ed6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65ed6-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="65ed6-106">Ukazatel na 32 unsigned integer, který obsahuje velikost proměnné.</span><span class="sxs-lookup"><span data-stu-id="65ed6-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65ed6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65ed6-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65ed6-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="65ed6-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65ed6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65ed6-109">Requirements</span></span>  
 <span data-ttu-id="65ed6-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65ed6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ed6-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="65ed6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65ed6-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="65ed6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65ed6-113">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65ed6-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ed6-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="65ed6-114">See also</span></span>

- [<span data-ttu-id="65ed6-115">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65ed6-115">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="65ed6-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65ed6-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
