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
ms.openlocfilehash: 534e3238a4b20e390c4f2168629e0ba93620f55a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="a61cb-102">ICorDebugInstanceFieldSymbol::GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="a61cb-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="a61cb-103">Získá posun v bajtech tohoto pole instance ve své nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="a61cb-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a61cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a61cb-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a61cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a61cb-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="a61cb-106">Ukazatel na počet bajtů, že je toto pole instance posunu v své nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="a61cb-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a61cb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a61cb-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a61cb-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="a61cb-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a61cb-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a61cb-109">Requirements</span></span>  
 <span data-ttu-id="a61cb-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a61cb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a61cb-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a61cb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a61cb-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a61cb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a61cb-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a61cb-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a61cb-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a61cb-114">See Also</span></span>  
 [<span data-ttu-id="a61cb-115">ICorDebugInstanceFieldSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="a61cb-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="a61cb-116">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="a61cb-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
