---
title: ICorDebugInstanceFieldSymbol::GetOffset – metoda
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c77ac2eac1022fa591066901f48eaf609b5367af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413560"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="c6ea8-102">ICorDebugInstanceFieldSymbol::GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="c6ea8-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="c6ea8-103">Získá posun v bajtech tohoto pole instance ve své nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="c6ea8-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ea8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6ea8-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6ea8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6ea8-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="c6ea8-106">Ukazatel na počet bajtů, že je toto pole instance posunu v své nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="c6ea8-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6ea8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6ea8-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6ea8-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="c6ea8-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6ea8-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6ea8-109">Requirements</span></span>  
 <span data-ttu-id="c6ea8-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6ea8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6ea8-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6ea8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6ea8-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6ea8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6ea8-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6ea8-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ea8-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6ea8-114">See Also</span></span>  
 [<span data-ttu-id="c6ea8-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6ea8-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="c6ea8-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c6ea8-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
