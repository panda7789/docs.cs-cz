---
title: "ICorDebugInstanceFieldSymbol::GetOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ab38a19d2bd2d06f2a04d7efafcdad6956ad7c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="f01fc-102">ICorDebugInstanceFieldSymbol::GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f01fc-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="f01fc-103">Získá posun v bajtech tohoto pole instance ve své nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="f01fc-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f01fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f01fc-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f01fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f01fc-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="f01fc-106">Ukazatel na počet bajtů, že je toto pole instance posunu v své nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="f01fc-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f01fc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f01fc-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f01fc-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="f01fc-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f01fc-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f01fc-109">Requirements</span></span>  
 <span data-ttu-id="f01fc-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f01fc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f01fc-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f01fc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f01fc-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f01fc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f01fc-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f01fc-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f01fc-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f01fc-114">See Also</span></span>  
 [<span data-ttu-id="f01fc-115">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f01fc-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="f01fc-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f01fc-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
