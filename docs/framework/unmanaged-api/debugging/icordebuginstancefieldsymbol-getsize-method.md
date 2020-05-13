---
title: 'ICorDebugInstanceFieldSymbol:: GetSize – metoda'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: 3d3c6881ecd54fc48be92e5ea0dc74a5cfdabd8f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209949"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="36664-102">ICorDebugInstanceFieldSymbol:: GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="36664-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="36664-103">Získá velikost pole instance v bajtech.</span><span class="sxs-lookup"><span data-stu-id="36664-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36664-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36664-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36664-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36664-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="36664-106">mimo Ukazatel na délku pole.</span><span class="sxs-lookup"><span data-stu-id="36664-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36664-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36664-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36664-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36664-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36664-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36664-109">Requirements</span></span>  
 <span data-ttu-id="36664-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36664-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36664-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="36664-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36664-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="36664-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36664-113">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36664-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36664-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="36664-114">See also</span></span>

- [<span data-ttu-id="36664-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36664-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="36664-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36664-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
