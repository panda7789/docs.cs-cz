---
title: ICorDebugInstanceFieldSymbol::GetOffset – metoda
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8ea777755aebb59f3e865df26c38c74ef68ae31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203870"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="f2a0b-102">ICorDebugInstanceFieldSymbol::GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f2a0b-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="f2a0b-103">Získá posun v bajtech tohoto pole instance v její nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="f2a0b-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a0b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2a0b-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2a0b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2a0b-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="f2a0b-106">Ukazatel na počet bajtů, že toto pole instance je posun v jeho nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="f2a0b-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2a0b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2a0b-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2a0b-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f2a0b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2a0b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2a0b-109">Requirements</span></span>  
 <span data-ttu-id="f2a0b-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2a0b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2a0b-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2a0b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2a0b-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2a0b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2a0b-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2a0b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a0b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2a0b-114">See also</span></span>

- [<span data-ttu-id="f2a0b-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2a0b-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="f2a0b-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f2a0b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
