---
title: 'ICorDebugStaticFieldSymbol:: GetAddress – metoda'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: 7b8072234df172eeafd77db90287ea3319c08ec7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378757"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="5fe4e-102">ICorDebugStaticFieldSymbol:: GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="5fe4e-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="5fe4e-103">Získá adresu statického pole.</span><span class="sxs-lookup"><span data-stu-id="5fe4e-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fe4e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fe4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5fe4e-105">Parameters</span></span>  
 <span data-ttu-id="5fe4e-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="5fe4e-106">pRVA</span></span>  
 <span data-ttu-id="5fe4e-107">mimo Ukazatel na relativní virtuální adresu (RVA) statického pole.</span><span class="sxs-lookup"><span data-stu-id="5fe4e-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fe4e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5fe4e-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5fe4e-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5fe4e-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fe4e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5fe4e-110">Requirements</span></span>  
 <span data-ttu-id="5fe4e-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fe4e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fe4e-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5fe4e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fe4e-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5fe4e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fe4e-114">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fe4e-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fe4e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="5fe4e-115">See also</span></span>

- [<span data-ttu-id="5fe4e-116">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5fe4e-116">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="5fe4e-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5fe4e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
