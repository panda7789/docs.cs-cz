---
title: 'ICorDebugInstanceFieldSymbol:: GetSize – metoda'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: eb70c441441954e2ffce6ca832c58369c606b128
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782284"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="b25b5-102">ICorDebugInstanceFieldSymbol:: GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="b25b5-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="b25b5-103">Získá velikost pole instance v bajtech.</span><span class="sxs-lookup"><span data-stu-id="b25b5-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b25b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b25b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b25b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b25b5-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="b25b5-106">mimo Ukazatel na délku pole.</span><span class="sxs-lookup"><span data-stu-id="b25b5-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b25b5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b25b5-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b25b5-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b25b5-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b25b5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b25b5-109">Requirements</span></span>  
 <span data-ttu-id="b25b5-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b25b5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b25b5-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b25b5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b25b5-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b25b5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b25b5-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b25b5-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b25b5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b25b5-114">See also</span></span>

- [<span data-ttu-id="b25b5-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b25b5-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="b25b5-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b25b5-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
